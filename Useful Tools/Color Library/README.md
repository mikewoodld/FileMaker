<h1> Gel Color Library for FileMaker Solutions </h1>
In this directory, you will find a .fmp12 file with a single table containing gel swatches for Apollo, Rosco, Lee, and Gam color. 


This file will be used in chapter 2.1 of the YouTube tutorials:

https://www.mikewoodld.com/filemaker-2-1/


<h2> Documentation </h2>

The table works by creating swatches based on RGB values for each gel color. The swatches are unicode blocks ▆▆▆ that get formatted based on the text values using the TextColor function:
https://fmhelp.filemaker.com/help/12/fmp/en/html/func_ref3.33.96.html

Since you can't edit a calculation field, there is a separate field for a "manual swatch" - this is just a copy of the calculated swatch, but you can edit it. 
You'd use this if you wanted to create split colors or RGB swatches, for example. 

When planning your solution, you should think about if you'll ever want to add custom color swatches. I recommend showing the "manual" swatch on your various reports.  

If you want to use another character other than the block for your swatch, you can just change the calculation in the database manager to be whatever characters you'd like. I included an extra "sample text" field so you can examine how this works. 

If you do change the character, you'll need to modify and then run the included script to update the "manual" records. 

You can export these records (as a .mer) to import them into your FileMaker solution, but you'll need to recreate the database fields. See chapter 2.1 for info.

<h3> IMPORTANT </h3>
If you downloaded this file before 18:00 CST 07/23/2020, some swatches were broken. It has been updated/fixed. If you don't want to download the new version, there is a script in the old version that will automatically fix the swatches for you.
