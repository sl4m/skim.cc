---
layout: post
title: http server in java
date: 2010-10-06 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- http server
  -- apprenticeship challenge
---

To describe in detail, I am to write an HTTP server that does the following:

* uses only standard Java libraries
* no porting of other HTTP server libraries (e.g., WEBrick, Micah's own HTTP server)
* cannot view the source of said HTTP server libraries
* must be written TDD style
* serves multiple clients simultaneously
* serves static files and all default MIME types
* when navigating to a specific path, it will display POST params on page

I came up with a list of common MIME types and HTTP status codes [here](http://gist.github.com/613883) and [here](http://gist.github.com/613597).  I may store these in HashMaps.

Here's what I believe needs to happen in order to create this server:

* create a simple HTTP client to test server
* create a service that handles client socket connection requests (multi-threading will be involved)
* create classes to handle request and response
* support GET/POST request methods
* possibly create a route manager to handle paths

Resources that will be helpful:

* [java.net package](http://download.oracle.com/javase/6/docs/api/)
* [javax.net package](http://download.oracle.com/javase/6/docs/api/)
* [RFC HTTP/1.1](http://www.w3.org/Protocols/rfc2616/rfc2616.html)
* [URI : Java Glossary](http://mindprod.com/jgloss/uri.html)
* [Java Socket Programming](http://www.ibiblio.org/java/slides/sd2003west/sockets/Java_Socket_Programming.html)

## It's all about Sockets

During today's research and a bit of spiking, I discovered that the lowest level component used to communicate between two computers is a socket.  [Recalling a story](http://skim.cc/2010/09/22/socket-server-in-java) I worked on a couple of weeks ago, my time server listened for a client's connection request.  Once the connection has been made, it used the socket's getOutputStream to write a message that included the current time, and closed the socket connection.  This message during the telnet demo displayed on the console.

A socket is considered to be a reliable connection for transmission of data between two hosts.  Fortunately, Sockets and ServerSocket are part of the standard Java library.  I avoid the need to worry about packet encoding, lost and retransmitted packets, and unordered packets which Socket class handles for me.

I wrote a test to see what the difference was between the socket on the server side and the socket on the client side.  Sure enough this is the difference:

{% highlight text %}
// client socket
<Socket[addr=localhost/127.0.0.1,port=7546,localport=60989]>

// server socket
<Socket[addr=/127.0.0.1,port=60989,localport=7546]>
{% endhighlight %}

I tried connecting to the time server using the browser and to my surprise, it displayed the time message in plain text.  Bingo, this has to be the way to send responses.  I looked at the javadoc for Socket class and sure enough, it supports these methods: getInputStream() and getOutputStream().  These two methods should allow the server to read the client's request and send the appropriate response to the client.  During trial and error, I found out the request doesn't come packaged in a pretty format like it does in Rails or any other web framework. The request has to be read in bytes, parsed, and the response written out "by hand" and sent to the client.  Fortunately though, both protocols are standardized and defined by RFC 2616 (aka HTTP/1.1):

{% highlight text %}
        Request       = Request-Line              ; Section 5.1
                        *(( general-header        ; Section 4.5
                         | request-header         ; Section 5.3
                         | entity-header ) CRLF)  ; Section 7.1
                        CRLF
                        [ message-body ]          ; Section 4.3

       Response      = Status-Line               ; Section 6.1
                       *(( general-header        ; Section 4.5
                        | response-header        ; Section 6.2
                        | entity-header ) CRLF)  ; Section 7.1
                       CRLF
                       [ message-body ]          ; Section 7.2
{% endhighlight %}

#### Request Protocol

It has three components:

* method\-URI\-Protocol/Version (e.g., POST /index.html HTTP/1.1)
* request headers (pairs of name:value)
* entity body (e.g., POST params)

An odd, but important part of the request is the blank line after the request headers and before the entity body.  This blank line separates the two.  If you find a blank line before let's say the method\-URI\-Protocol/Version or request headers, it should be ignored.

### Response Protocol

It also has three components:

* Protocol\-Status Code\-Description (e.g., HTTP/1.1 200 OK)
* response headers (pairs of name:value)
* entity body (e.g., raw html)

Same important blank line applies here as well.  It must be in between response headers and entity body.  Any respectable browser will do that for you.

## To be continued

Now I need to start spiking and get some request/response actions going between client and server.
