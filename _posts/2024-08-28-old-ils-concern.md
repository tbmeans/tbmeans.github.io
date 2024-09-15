---
layout: post
title: "Search and discovery in online library catalogs"
date: 2024-08-28 09:13:38 -0400
categories: jekyll update
tag: ILS Evergreen Open Library Software Blog Consider it coded!
---

So today i'm facing the difficulty of finding books with age hold protection in 
the concerto database.
My first guess is to search for concerto's new books. I do this through advanced
search and tick off new arrivals, but no results.
I go to my local library's implementation of the Evergreen-ILS OPAC and try the same
advanced search for its new books, and, latency. Spinning its wheels far longer than
my short attention span can tolerate.

I still "dream" about a book object with properties that facilitate "orgunitsettings"
like if the book had a property that it's age protected, then you have a rule that
excludes any book with that property from any available holds calcs.
well how do i know that's not how it's already coded in koha or eg.
AND then there's the problem of storing all those objects. yeah, what you would
actually store is a database full of property values and then construct a book object
from a set of them. googled java object database

it used to be that you wanted an ils with the discovery power of amazon.
i felt the need for that again today when it seemed like an act of congress to
just get some paginated search results for all the new books in one system from evergreen,
and i found myself using an old trick of the trade from library days, going to amazon to
 to discover what the bestselling new books actually are right now, so i can search a
specific title in evergreen and not tax it's search power.

but it's 2024 now. maybe you should look beyond amazon/google type searching and
see how llm could be your discovery and reader assistance... yikes sounds like
ai is coming for a librarian's job.
