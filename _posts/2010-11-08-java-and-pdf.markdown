---
layout: post
title: java and pdf
date: 2010-11-08 23:00:00 -05:00
categories:
  -- client
  -- java
  -- pdf
---

Today was a busy day at the Chicago office.  I was creating a PDF template for one of the features in the project.  The PDF is generated from a custom library in Java that depends on a pretty well known PDF library called iText.  I was constantly at the javadoc looking for clues to create the template.  The other templates Paul made were purely text\-based, but this template required the use of tables, so I had to do a bit more research.  I was also thinking about how to create tests around the template.  I ended up going back to the abstract class (which the template extends on) and refactored a bit to make it DRY.  I think I may go back some more and write more tests.  I get an itch on the back of my neck whenever there are little to no tests.  The discipline I learned the past five months taught me to write tests first.  The LOCs in the tests should be about the same as the LOCs in the source.   

Unfortunately, I did not finish by the end of the day, so I'm going to finish it up tonight and I'll be working on more templates tomorrow and get through the stories for this week.  Tomorrow is 8th Light's second hack night, so I look forward to pairing with someone and learn more about Rails and get through some of the stories for the 8th Light website.
