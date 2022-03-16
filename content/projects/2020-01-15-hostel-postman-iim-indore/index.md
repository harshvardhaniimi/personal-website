---
title: Hostel Postman, IIM Indore
summary: Automated systems at IIM Indore's Hostel Office
author: Harshvardhan
date: '2020-01-15'
slug: []
categories:
  - package
tags: []
---

The package retrieval system at my institute, IIM Indore, had a rudimentary design. All parcels --- Amazon, Flipkart, India Post --- were received by the Hostel Postman (an institute employee). He would put the details in a spreadsheet with the receiver's name and details, package type, and date of arrival. Every day around 5 pm, he'd send the spreadsheet with all the details to every student on campus.

This system had several flaws:

1.  The privacy of receivers was zero. Any Tom, Dick and Harry could know who received what parcel on campus.

2.  Students had to dig through the emails every day to see if they received anything.

3.  The postman got over thirty calls a week from students asking if they received anything.

[Pradeep Charan](https://www.linkedin.com/in/pradeep-charan/?originalSubdomain=in) and I decided to solve this problem. I used Google Sheets to design a system that required putting in the student's name and package details --- just like the previous workflow. However, instead of sending the spreadsheet to all students, the system intelligently identified the students' emails and sent them an alert --- only to those who had received a parcel. In the backend, I implemented this automation using [Google Apps Script](https://www.google.com/script/start/).

![](images/Screen%20Shot%202022-03-16%20at%2011.28.05%20AM.png)

Each reminder (email) was a personal one. It only contained details about their parcel. After two days, the students also received a second alert if the package remained uncollected. This system was loved by everyone and for obvious reasons. Students weren't spammed, Hostel Postman didn't spend hours in mundane details, and most importantly, everyone's privacy was preserved.

The infrastructure committee appreciated the project for its impact. I have worked on several projects before and since then, but this has to be the one with the largest impact.

### In summary,

-   Designed a spreadsheet-based dashboard for automating sending personalised reminders about their parcels and couriers received,

-   The system handled 1000+ campus residents and 10+ courier companies, severely reducing the manual workload and saving everyone from generic spam.
