---
layout: post
title: "'Case notes' for library software"
date: 2024-09-15 01:00:00 -0400
categories: jekyll update
tag: ILS CSR case notes Evergreen Open Library Software Blog Consider it coded!
---

A bug ticket for an open source library software feature request made me think of a "cultural" difference between the workflows for public-facing library employees and customer support representatives. I have had experience with both workflows. One big difference on the surface is in the jargon, patrons (the users of a public library) vs. customers.

There's really no formal ticket system when helping patrons. Opening a "ticket" of sorts for every patron would be overkill, but the de facto standard of library transactions, where there is in all but the most complicated or escalated issues a complete lack of any sort of log after helping a patron, is not very helpful either. 

In my experience there have been times where you wish you could talk to the coworker who last helped the patron, because the patron is back and things are not resolved, but neither you nor the patron can identify who helped them. I can also recall times working with CSR software at call centers, where you were given a short set amount of time to write case notes summarizing the support given before the next call in queue was put through. So every transaction was automatically logged and traceable to the CSR who handled it.

Use of ILS patron notes feature on every transaction is the closest approximation to a CSR case notes workflow, but patron notes wasn't meant to log a patron's entire transaction history, all of which would have to be stored in server databases, and it isn't customary for library workers to take notes after every patron.

tldr;
Could an ILS be set up to generate locally-stored logs for every transaction? Pass the storage burden to all the local workstations that outnumber the servers.  
Implement logs by an additional action for every transaction-finishing button in the UI. The action would be to newline append staff member name, patron barcode, and a timestamp to a local log file. For privacy no book titles/barcodes go into the logs.
There would have to be some kind of workstation counter state, after x number of appends to a text file, make a new one, so that you don't have experience latency running the native text editor due to MB-size text files. So you imagine a log folder full of text files for even a month. On windows at least, the individual content of all text files in the pwd can be searched using the windows explorer ui. 

Let me not go down the rabbit hole about the details of local storage for log files.

Imagine a patron is back with an unresolved issue but neither staff nor the patron can identify who last helped the patron.

To better log for follow up with the previous staff member, log out and log back in to the web staff client every time the next staff member goes on duty, and they should log in with either a user name or workstation name that identifies the staff member.

But in my experience, everyone logs in with the same username, the one for the library department, and everyone's in a habit of
1. leaving the workstation name as the same arbitrary codename from first use and
1. leaving workstations logged into the same session from the time we open until the time we close, unless the browser is closed inadvertently.

Given these usage habits, I would suggest the following:
1. add a 4th input for the staff member's name to the staff login sign in form, and
1. that the username @ workstation ID + Staff Name be enlarged in font and moved from the navbar corner to the center of the home splash with the Evergreen logo

Seeing someone else's name in big print will encourage the next staff member at the workstation to update.

Instead of printing the staff name on the home splash, duplicate an `<input>` pre-filled from whatever was submitted on the login, and the staff name can be easily edited, as well as recognized as editable, when the next staff member comes to the workstation.

Every transaction-finishing button can append info from the sign in form to the log, whether that log goes into the database or local storage as a text file log.
