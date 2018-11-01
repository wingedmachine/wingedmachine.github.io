---
layout: post
title:      "Chewing it anyway"
date:       2018-11-01 12:21:59 -0400
permalink:  chewing_it_anyway
---

### a cautionary tale about ballooning project scale

I'm writing this a day too late to make a Halloween joke about "feature creepiness".

My two main interests are roller derby and coding, so it made sense to bring them together as a CLI: a simple program to scrape and display some league(1) data. Not a particularly useful program, since it mostly duplicates functionality of the site I'm scraping, but an entertaining enough project for me to work on.

So I scraped some data, with the thought that I'd maybe allow users to search by name. And then I realized I wasn't going to be able to display all nearly 470 leagues at once, so I decided to show "pages" of ten at a time and allow users to move forward and back as well as to any specific page. And then I saw the original page allows sorting by country, so I thought"why not add a location search?" but the page only gave countries as a two-letter code, so I figured I'd scrape another site to get the info to translate that into country names. Oh, and it would be neat if I had each search take place inside the results of the previous search so users could progressively narrow down the list they were looking at! Which of course necessitates a way to reset, and why not also throw in a way to take back just the most recent search?

I was throwing ideas into my mental model of the program as I went, without paying any attention to the ominous way they were piling up. I was biting off more and more, and I had barely even begun trying to chew it.

The cost of this was time and technical debt. I had set a goal of finishing in three days. I wasn't sure I could make that, but I wanted to aim high. It took me twice that long. And toward the end of that time, I began implementing hack solutions and things out. I had planned to run the project as TDD to get experience with that, but the final class I completed has no tests, because I needed to move faster. That class is also a large, jumbled collection of methods with no real organization to it because by the time I had it working, I was tired of the project, and more than ready to move on, so I didn't bother to refactor it. If this were a project I was ever planning to come back to, I'd curse myself for making me deal with that mess. I know that because I've had to deal with code other people left in that state, and I cursed them. Dealing with that for the first time taught me the value of clean code. Dealing with this taught me the importance of keeping an eye on the scope of your project.

And it taught me how to handle biting off more than I can chew. You can spit some of it out, and you can can swallow some of it whole, but mostly? You chew it anyway.

*Notes:*
(1) A "league" in modern roller derby isn't equivalent to a sports league like the NFL or NHL but to somethink more like a club in soccer. A league is a local organization consisting of one or more teams. These are mostly teams that play teams from other leagues, but leagues can also include teams that primarily play each other within the league. (The later was originally the only form of team, which is the reason "league" has the meaning it does in the sport.) Each league has one team in particular that represents them on the global stage, and the league as a whole is often referred to synechdochically when speaking about that team.
