---
layout: post
title: using state machine for parsing - part 2
date: 2010-09-28 15:00:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- statemachine
---

On Sunday, I covered the very basics of a statemachine to create a parser.  Yesterday and today, I worked on the code to create that parser.  Using Micah's statemachine gem, I wrote a Ruby script that generates the statemachine code by listing all transitions.

{% highlight ruby %}
begin
  require 'statemachine'
  require 'statemachine/generate/java/java_statemachine'
rescue LoadError
  require 'rubygems'
  require 'statemachine'
  require 'statemachine/generate/java/java_statemachine'
end

SRC_DIR = File.expand_path(File.dirname(__FILE__) + "/src/")

def generate_parser_sm
  sm = Statemachine.build do
    trans :nothing,            :whitespace,        :nothing
    trans :nothing,            :new_line,          :nothing
    trans :nothing,            :open_curly_brace,  :nothing,            :error
    trans :nothing,            :close_curly_brace, :nothing,            :error
    trans :nothing,            :alphanumeric,      :name,               :add_to_name
    trans :name,               :alphanumeric,      :name,               :add_to_name
    trans :name,               :whitespace,        :finding_curly
    trans :name,               :new_line,          :finding_curly
    trans :name,               :open_curly_brace,  :finding_attributes, :create_style
    trans :finding_curly,      :whitespace,        :finding_curly
    trans :finding_curly,      :new_line,          :finding_curly
    trans :finding_curly,      :open_curly_brace,  :finding_attributes, :create_style
    trans :finding_attributes, :whitespace,        :finding_attributes
    trans :finding_attributes, :new_line,          :finding_attributes
    trans :finding_attributes, :close_curly_brace, :nothing
    trans :finding_attributes, :alphanumeric,      :attr_name,          :add_to_attr_name
    trans :attr_name,          :alphanumeric,      :attr_name,          :add_to_attr_name
    trans :attr_name,          :whitespace,        :finding_attr_value
    trans :finding_attr_value, :whitespace,        :finding_attr_value
    trans :finding_attr_value, :alphanumeric,      :attr_value,         :add_to_attr_value
    trans :attr_value,         :alphanumeric,      :attr_value,         :add_to_attr_value
    trans :attr_value,         :close_curly_brace, :nothing
    trans :attr_value,         :whitespace,        :attr_value
    trans :attr_value,         :new_line,          :finding_attributes, :add_attribute
    startstate :nothing
  end
  sm.to_java(:output => SRC_DIR, :name => "LLParser", :package => "limelight.parser")
end

if $0 == __FILE__
  generate_parser_sm
end
{% endhighlight %}

As said previously, calling the *to_java* method will generate the statemachine code in Java.  Had I've been writing this parser in Ruby, I would have not needed to generate the code.  I could have left the build method intact and call it in another Ruby class, and have the code generated in memory, on the fly.  According to [Eric Smith](http://twitter.com/paytonrules), this is how it's done for one of their client projects.

### Typically how it's done when working in Ruby

{% highlight ruby %}
require 'rubygems'
require 'statemachine'


module ParserStatemachine
  def self.create_with(parser_context)
    return Statemachine.build do
      trans :code, :other, :code, :print
      trans :code, :pigpen, :code, :print
      trans :code, :endl, :new_line, :print
      trans :new_line, :other, :code, :print
      trans :new_line, :pigpen, :in_comment
      trans :new_line, :endl, :new_line, :print
      trans :in_comment, :other, :in_comment
      trans :in_comment, :pigpen, :in_comment
      trans :in_comment, :endl, :new_line
      startstate :new_line
      context parser_context
    end
  end
end
{% endhighlight %}

The important piece of information I needed to figure out was what to implement after the Java code was generated from the statemachine gem.  After reading through the code and help from Eric, I found out it was the context interface class that needed to be implemented.

{% highlight java %}
public interface LLParserContext
{
  // Actions
  void addToAttrName();
  void addToAttrValue();
  void addToName();
  void error();
  void findAttrValue();
  void findAttributes();
  void findAlphanumeric();
}
{% endhighlight %}

I created a class that implemented LLParserContext and inside this class, it wrote style names and their attributes to the output string.  When this all said and done, the idea is for the jar file to spit out Java code equivalent of a Limelight styles.rb file in the console.  Fortunately, with Micah's help today, I was able to able to get through this story and complete it with tests.  It's amazing how much you can get done when pairing with someone else, even better when pairing with an experience Java programmer.  The result of this story is shown in my GitHub [repo](http://github.com/sl4m/limelight_styles_converter).  Unfortunately, I forgot to take into account comments, so I'm working on that issue now, but for any styles.rb file without comments, it should convert it nicely to Java code.

{% highlight java %}
import limelight.styles.RichStyle;
import java.util.HashMap;

HashMap<String, RichStyle> styles = new HashMap<String, RichStyle>();
RichStyle style = null;

style = new RichStyle();
styles.put("title", style);
style.setWidth("100%");
style.setFontSize("30");
style.setFontFace("ArialRoundedMTBold");
style.setTextColor("white");
style.setHorizontalAlignment("center");
style.setBottomPadding("10");

style = new RichStyle();
styles.put("label", style);
style.setWidth("50%");
style.setFontSize("12");
style.setFontFace("arial");
style.setFontStyle("plain");
style.setTextColor("#363636");
style.setHorizontalAlignment("right");
style.setRightPadding("5");

style = new RichStyle();
styles.put("bold_label", style);
style.setWidth("50%");
style.setMinHeight("1");
style.setFontSize("12");
style.setFontFace("arial");
style.setFontStyle("bold");
style.setTextColor("#363636");
style.setHorizontalAlignment("left");
style.setLeftPadding("5");

style = new RichStyle();
styles.put("advise", style);
style.setWidth("100%");
style.setFontSize("12");
style.setFontFace("arial");
style.setFontStyle("plain");
style.setTextColor("#363636");
style.setHorizontalAlignment("left");
style.setTopPadding("10");

style = new RichStyle();
styles.put("buttons", style);
style.setWidth("100%");
style.setPadding("5");
style.setHorizontalAlignment("center");
style.setTopPadding("20");

style = new RichStyle();
styles.put("button", style);
{% endhighlight %}

While I did pull some hair out initially, this was a fun challenge.  I really enjoyed learning about the state machine and how it can be used to represent a system.  I could have used regular expressions instead of the state machine, but I felt this approach made more sense and visually I was able to understand what state, transition, event I was in.  If I were working in regular expressions, I would be in regex hell, plus it wouldn't have been fun.
