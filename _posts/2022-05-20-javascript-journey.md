---
layout: post
title: "JavaScript journey"
date: 2022-05-20 14:00:00 -0500
categories: jekyll update
tag: JavaScript chess frontend Blog
---

Making a chess game has been the pet project nearest and dearest to my heart.
Through making a chess game, I built up my HTML, CSS, and JavaScript skills,
tried out several styling aids such as Bootstrap, Sass, and Bulma, learned
about MVC architecture, and did a deep dive into writing elegant/efficient
solutions in the problem domain. MDN Web Docs were my JavaScript and Web API
reference of choice, and I was appreciative of hints into the problem domain
offered by sites like Chess Programming Wiki without giving away specific "code
spoilers," speaking of which, I know there are existing, proven solutions out
there for chess engines and frontends: Stockfish, GNU Chess, Lichess, etc., and
reinventing the wheel was just my way of teaching myself to code with something
that interested me.

I first attempted MVC with the UI and the data-generating backend modules both
coded in vanilla JS, with a NodeJS simple server. It was a challenge to avoid
antipatterns and ensure SoC without writing within a framework, and sometimes I
wondered if MVC was even the best design for a chess game, so I was pleased to
finally refactor the code into the React framework, creating a working UI in
much less time than it took for me to code vanilla MVC View objects!
