---
layout: post
title: Pivot Table Wizard
published: yes
---
<style>
        @font-face {
            font-family: "Coelnische Fraktur M";
            src: url(/fonts/CoelnischeFraktur_M.otf) format("opentype");
            }
        p.prelude {
			font-size: 1.8em; /* 18 */
			float: right;
			text-indent: 0 !important;
			display: block;
			}
            p.prelude:first-letter {
				margin-left: -1.071em; /* We have 120 of space */
				margin-right: 100%;
				margin-bottom: -0.894em;
				font-size: 6.222em; /* 112 */
				padding-right: 0.071em; /* 8 */
				line-height: 0.9; /* Aligns to cap-height of para. */
				color: #BB0000;
				text-align: right;
				float: right;
				font-family: "Coelnische Fraktur M", Georgia, "DejaVu Serif", Times, "Times New Roman", serif;
				font-style: normal;
				}
			p.prelude:first-line {
				font-variant: small-caps;
				letter-spacing: 0.06em; /* 2 */
				text-indent: 0;
				}

    span.scale { color: #BB0000; padding-left: 2.4em; }
        span.scale-six { font-size: 0.6em; }
        span.scale-seven { font-size 0.7em; }
        span.scale-eight { font-size: 0.8em; }
        span.scale-nine { font-size: 0.9em; }
        span.scale-ten { font-size: 1em; }
        span.scale-eleven { font-size 1.1em; }
        span.scale-twelve { font-size: 1.2em; }
        span.scale-thirteen { font-size: 1.3em; }
        span.scale-fourteen { font-size: 1.4em; }
        span.scale-sixteen { font-size: 1.6em; }
        span.scale-eighteen { font-size: 1.8em; }
        span.scale-twenty-one { font-size: 2.1em; }
        span.scale-twenty-four { font-size: 2.4em; }
        span.scale-thirty-four { font-size: 3.4em; }
        span.scale-thirty-six { font-size: 3.6em; }
        span.scale-forty-eight { font-size: 4.8em; }
        span.scale-fifty-five { font-size: 5.5em; }
        span.scale-sixty { font-size: 6em; }
        span.scale-sixty-four { font-size: 6.4em; }
        span.scale-seventy-two { font-size: 7.2em; }
        span.scale-eighty-nine { font-size: 8.9em; }
    
    span.equation {&thinsp;&mdash;&thinsp;
        color: #555;
        font-size: 1.8em;
        font-family: Monaco, "Andale Mono", "Courier New", Courier, monospace;
        display: block;
        text-align: center;
        padding: 0.888em;
        }
        span.value { color: #111; }
        span.result { color: #4881D6; }
</style>

<p class="prelude">Last year I found myself thrust into a data analysis project at work.  There was a decent amount of data, and a lot of noise to wade through and ultimately weeded out.  It didn't take me long to realize that my time working with this data would be a lot less painful if I were to put together a few scripts to manipulate the data. 

Being able to leverage a script and common Linux commands like fgrep, sed, awk, cut and csvfix just made more sense than trying to do what needed to be done in excel with a decent sized (1GB+) CSV file.  At the time the validity of the data was also in question, so having a clearly documented and repeatable process that wasn't prone to human error made a lot of sense.

Once the file was massaged into submission, Excel was used for creation of the pivot table and slicers.   Before we go any further it only makes sense to define what a pivot table is.  According to Wikipedia:

<blockquote cite="Wikipedia">
"In data processing, a pivot table is a data summarization tool found in data visualization programs such as spreadsheets or business intelligence software. Among other functions, a pivot-table can automatically sort, count total or give the average of the data stored in one table or spreadsheet."
</blockquote>

In a nutshell, pivot tables (or pivot charts) let you dynamically slice up and visually display your table data quickly and easily in any number of combinations or groups.  Let's look at an example.  The fictional widget company is planning on serving a spaghetti and meatball dinner to all of its employees.  They have put together a table indicates the employee's meatball preference (mild or spicy).  Since this is an international company they have data for their international offices, and have included everyone's department area in the collected data.

After inserting the pivot table you will need to tell it what fields to popular in the table.  Items put in the rows area dictate the group and sub-grouping (if multiple values are selected) of the row data.  In this example the row group included the "LOCATION" field with a sub-grouping of the "TEAM" field.  Since we are trying to find out how much of each kind of meatball to buy, our column heading for the pivot will be "SPICE LEVEL".  Finally, since we need to know how many meatballs to buy, our value section will be "Count of MEATBALLS". 

<img src="/images/pivot-table-field-list.png">

Once you have selected the fields to display the pivot table will be dynamically build.  With the above field list choices, and with all of the fields collapsed, our pivot looks now looks like the table below.

<img src="/images/meatball-pivot.png">

If we were to expand out one of the sections we would be able to see the breakout of meatballs and types by department area.

<img src="/images/meatball-slicers.png">

Something that should jump out of you immediately are the boxes that surround the table.  These are called "Slicers" and allow us to easily filter what data is displayed.  For example, if we only wanted to see the Canada Meatball data for just the open systems and windows group, we would simply select the slicer data fields to display.

<img src="/images/meatball-slicers2.png">

Or by changing the order of the field list fields we can easily change the grouping of data at a high level. 

<img src="/images/meatball-slicers3.png">

Hopefully you have seen the power of pivot tables and the flexibility that slicers offer.  In every one of these examples the data sheet has never been changed.  I really find pivot tables and slicers to be a great lightweight alternative to using Access or another database.  I personally can't stand working in Microsoft Access, so for me learning about pivot tables and slicers was a huge revelation.  As always there are some great tutorials out there on pivot tables that are only a Google search away.