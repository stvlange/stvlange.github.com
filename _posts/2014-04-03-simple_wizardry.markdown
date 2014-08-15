---
layout: post
title: Pivot Table Wizard
modified: 2014-04-03
categories: Tips
tags: [excel, pivot, table]
comments: yes
image:
  feature:
---
Last year I found myself thrust into a data analysis project at work.  There was a decent amount of data, and a lot of noise to wade through and ultimately weeded out.  It didn't take me long to realize that my time working with this data would be a lot less painful if I were to put together a few scripts to manipulate the data.

Being able to leverage a script and common Linux commands like fgrep, sed, awk, cut and csvfix just made more sense than trying to do what needed to be done in excel with a decent sized (1GB+) CSV file.  At the time the validity of the data was also in question, so having a clearly documented and repeatable process that wasn't prone to human error made a lot of sense.

Once the file was massaged into submission, Excel was used for creation of the pivot table and slicers.   Before we go any further it only makes sense to define what a pivot table is.  According to Wikipedia:

<blockquote cite="Wikipedia">
"In data processing, a pivot table is a data summarization tool found in data visualization programs such as spreadsheets or business intelligence software. Among other functions, a pivot-table can automatically sort, count total or give the average of the data stored in one table or spreadsheet."
</blockquote>

In a nutshell, pivot tables (or pivot charts) let you dynamically slice up and visually display your table data quickly and easily in any number of combinations or groups.  Let's look at an example.  The fictional widget company is planning on serving a spaghetti and meatball dinner to all of its employees.  They have put together a table indicates the employee's meatball preference (mild or spicy).  Since this is an international company they have data for their international offices, and have included everyone's department area in the collected data.

After inserting the pivot table you will need to tell it what fields to popular in the table.  Items put in the rows area dictate the group and sub-grouping (if multiple values are selected) of the row data.  In this example the row group included the "LOCATION" field with a sub-grouping of the "TEAM" field.  Since we are trying to find out how much of each kind of meatball to buy, our column heading for the pivot will be "SPICE LEVEL".  Finally, since we need to know how many meatballs to buy, our value section will be "Count of MEATBALLS".

<center><img src="/images/pivot-table-field-list.png"></center>

Once you have selected the fields to display the pivot table will be dynamically build.  With the above field list choices, and with all of the fields collapsed, our pivot looks now looks like the table below.

<center><img src="/images/meatball-pivot.png"></center>

If we were to expand out one of the sections we would be able to see the breakout of meatballs and types by department area.

<center><img src="/images/meatball-slicers.png"></center>

Something that should jump out of you immediately are the boxes that surround the table.  These are called "Slicers" and allow us to easily filter what data is displayed.  For example, if we only wanted to see the Canada Meatball data for just the open systems and windows group, we would simply select the slicer data fields to display.

<center><img src="/images/meatball-slicers2.png"></center>

Or by changing the order of the field list fields we can easily change the grouping of data at a high level.

<center><img src="/images/meatball-slicers3.png"></center>

Hopefully you have seen the power of pivot tables and the flexibility that slicers offer.  In every one of these examples the data sheet has never been changed.  I really find pivot tables and slicers to be a great lightweight alternative to using Access or another database.  I personally can't stand working in Microsoft Access, so for me learning about pivot tables and slicers was a huge revelation.  As always there are some great tutorials out there on pivot tables that are only a Google search away.
