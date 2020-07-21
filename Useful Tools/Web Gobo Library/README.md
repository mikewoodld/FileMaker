In this directory, you will find information on how to use the gobo image library tool. 
There is a .fmp12 demo file containing the scripts, as well as text and pdf versions of the scripts themselves.


<h1>Introduction</h1>
I wanted to create a way to automatically insert a gobo image into a gobo image container without having to search the internet each time for the image or create a storage-space-hungry table in my FileMaker solution. 

I moved all my gobo images over to a public directory and then wrote a FileMaker script that can pull the image into a container. 

<h2>What you need</h2>

- Working internet connection

- FileMaker solution built with at least a Gobos Table

- 2 fields: "Gobo Name" (text) and "Gobo Image" (container

- Rosco, Gam, and Apollo gobos

<h2>How it works</h2>

The script works by inserting an image based on a calculated URL. The URL is calculated using the "gobo name" field in your table. 
I wanted to make the script as user-proof as possible, as different people have different ways of labeling their gobos. 

There is documentation at the top of the script itself, but I'll summarize here as well:
Essentially, the only rule that you need to be aware of is that the first occurence of a text character in your "gobo name" field must be R,G,A, or M. The script only cares about that very first text character. It does not matter what position that character is in in your overall name. For example:

G579, GAM579, G-579, GAM-579, G579A, G579B, G579-A, 579G, 579GAM, 579GAMYAYYYYYY

All return the same result. 

While you can have as many/whatever characters you want after that first occurence, the only integers that can be in your "Gobo Name" field are the actual gobo numbers. So you can't put a count, inventory, qty number, etc at the end of the field. Nor should you want to, that kind of information would be best in a separate field anyway.

You can simplify this script a lot if you commit to only using gobo names that are formatted the exact same way as they're found in the gobo directory at https://www.lightingpaperwork.com/gobos, but we all know that people have different preferences. 


Most all of the gobos on the site are saved as .jpgs, but there are a few Roscos that are PNGs. (More on this in a bit)

At the end of the script, it checks to see if the container has anything in it. If it doesn't, it automatically tries again using the .png extension. Then it checks again. If it still doesn't have anything in it, a user-prompt appears asking the user what they'd like to do. There are three options:

1) Search google for the gobo (this uses a separate script, but it really doesn't need to.)
2) Cancel
3) Alert Mike (via email) that the gobo is missing - this really won't help you immediately, but it lets me know that there's a gobo missing so I can add it later. 

The URL is calculated as follows:
            http://www.lightingpaperwork.com/gobos/$company/$letter$number.jpg (or .png)
            
            $company - rosco, gam, or apollo. Calculated automatically based on first text character in field.
            $letter - G, R, A, M - again, automatically calculated. There is an "upper" script step that makes sure it is uppercase.
            $number - the number of the gobo itself
            .jpg or .png - file extension (see notes earlier about checking for pngs)
            
Eventually, all the images will be jpg and I'll get rid of the png stuff from the code.


Enjoy!
            
