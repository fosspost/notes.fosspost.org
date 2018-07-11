# Sed

## [Tip] Use Sed To Manipulate SVG Files

### Description

If you have a SVG file and you want to edit it using command line quickly. You can use **Sed** (or any other text manipulation tool). Try to open the SVG file using text editor and you would see a lot of specifiers and things which you can change using Sed and other tools.

### Solution

For example, if you want to change a text called "DUMMY TEXT" into "NEW TEXT" in a SVG file, you can run the following command:

    sed "s/DUMMY TEXT/NEW TEXT/g" old.svg > new.svg

A new.svg file would be created containing the new text instead of the old. You can do the system process for anything you need in the SVG file.

### Additional Info

Check the [description of SVG files](https://inkscape.org/en/develop/about-svg/) in order to understand what you can change to obtain the results you want.

By the way, this method is what FOSS Notes uses to generate notes' thumbnails automatically using a Bash script. Nobody has the time to design all of this manually.


## [Note] Sed Produces Empty Files

### Description

If you are using Sed like this:

    sed -e s/STRING1/STRING2/g oldfile > newfile

Then you may notice that the contents of **newfile** are empty. This is because the **>** operator tells the Shell to open that file for writing. Which instantly removes all the contents from the file.

### Solution

A simple workaround would be:

    sed -e s/STRING1/STRING2/g oldfile > newfile.tmp && mv newfile.tmp newfile

## [Problem] Sed Outputs Correctly to Terminal, but not to Files

### Description

Sometimes you may notice that your **sed** command is printing its output to your terminal instead of just writing it to the file you chose. For example if you created a **sed** command to replace all occurrences of the word "test" in a file, you'll notice that **sed** is printing the changed file inside your terminal, not in the file.

### Solution

Make sure you are using the **-i** flag (inline mode) with your **sed** command. For example:

    sed -i '/^#[^#]/a \'"$s" file.txt
