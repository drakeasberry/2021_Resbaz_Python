# Shell Lessons

## Getting started

In your browser

* Open a tab and go to [workshop website](https://ua-carpentries-workshops.github.io/2020-02-15-Tucson/) and make sure 
you have installed the required software for your system. `Red sticky` if you need help.
* Open a tab and go to the [Etherpad](https://pad.carpentries.org/2020-02-15-Tucson)
* Open a tab and go to [Github](https://github.com/) and login with your account
* Open a tab and go to our Github repository. Use the link in the Etherpad.
* Open a tab and go to [Explain Shell](http://explainshell.com/)
* Open a tab and go to the Shell Share in the link in the Etherpad
* Open `Terminal` or `git bash` and enter `nano` to make sure you have `nano` installed.

## What is the shell?

[Software Carpentry Intro to Shell](https://swcarpentry.github.io/shell-novice/01-intro/index.html)

The shell is a program that gives you a way to access commands that let you do stuff on your computer. 

We are going to learn all of the most common commands and how we can combine them to automate complex tasks.

It is also called the command-line interface because you type commands on a line like this:

> ```$ ls -la ```

In this case we are using BaSh (Born Again Shell), but there are lots of different shells. BaSh is very common on UNIX 
and Linux operating systems.

## The three shells used in this workshop

### Windows

If you are on Windows you are using the BaSh emulator that you installed with Git. This is an emulator because it 
basically fakes the real BaSh commands to make them work on Windows.

### MacOS

MacOS is built on UNIX so it has a built-in command-line with all of the UNIX commands we need for this workshop.

### Linux

Most versions of Linux come with BaSh by default.

## What is it good for?

The shell provides a lot of commands that you can combine to manage and process your data. You can use these commands 
to build scripts that you can to automate repetitive tasks.

For example, many researchers use the bash commands to convert their unstructured data into structured data.

# Navigating Files and Folders (Directories)

[Software Carpentry Navigating Files and Folder](https://swcarpentry.github.io/shell-novice/02-filedir/index.html)

Open File Explorer and go to the `home` directory. Snap this window next to the terminal or git-bash window so you can 
see them side-by-side. 

(Windows people can use Window-key + arrow to snap windows)

```
C:\Users\<your user name here>
```

Let's start with listing files and folders.

```
$ ls
```

What did you see? Does it look the same as what you saw in File Explorer?

`ls` lists files and folders.

## Where am I?

Knowing where you are in the filesystem is harder on the command line, but we have a command to help us with that.

```
pwd
```

`pwd` stands for `present working directory` and it will tell you the `path` to where you are in the filesystem. 
It starts with the root.

In UNIX this is `/` and in Windows this will likely be something like `C:\`.

What did you see? Does it look like the path you see in File Explorer?

## `ls` (list files and folders)

Let's get back to `ls`.

`ls` has lots of options that you can use to sort and format the listing, just like you can do in File Explorer.

Let's see what they are. On Windows you can run the command:

```
ls --help
```

and on Mac you can use:

```
man ls
```

What did you see? A description and lots of options? Great.

Let's try one of the options.

```
ls -l
```

What did you see? It looks a little different than the output from 

```
ls
```

Try them both. See the difference?

`ls -l` shows us more details about the files:

* permissions
* last date modified (or created)
* size


This is called the `long` format, hence `-l`.

Sometimes there are hidden files and folders. These start with a `.`. `ls` won't show hidden things unless you give it 
the -a option.

```
ls -a
```

Now you will see all files or folders.
# How do we do this in Windows Explorer
On a Windows:


On a Mac:

```
Command + Shift + .
```
You can also combine options like this:

```
ls -la
```

or like this

```
ls -l -a
```

Try them both. You should see the same output.

This shows all files and outputs the long format.

> REMEMBER: You can combine options for any of the shell commands that have options.

## Moving around

You know how you can double-click on a folder to see inside of it? There is a command for that in shell. 

```
cd --help
man cd
```

`cd` stands for `change directories`.

There are two ways to `change directories`.

`cd` plus a `path` to where you want to go
Introduce Tab complete here and reinforce it throughout the workshop

```
cd /lets/go/here
```
`cd` plus `..` to go up one level in the filesystem (go into the parent folder)
```
cd ..
```

### Going home
We started in the `home directory`, this is a location in the filesystem where your your personal files are stored by default. 
It is a common operating system convention.

If you were playing with `cd` commands with us, you are no longer in the home directory. How do we check?
Use `pwd` to check your location in the computer file system.

On Windows this will be:
```
C:\Users\<your user name here>
```

On Mac this will be:
```
/Users/<your user name here>
```

There is a shortcut for something called the `home` directory. 

```
cd ~
```

If you ever get lost and need to get back home, use the above command. Try it now and then list the files.

```
cd ~
ls -la
```

Do you see the same thing you did before?

## Absolute paths and relative paths

Let's talk about paths some more. We can get to directories with a `relative` path or an `absolute` path.

### Absolute paths

Absolute paths always start from the `root` of the filesystem.

```
/c/folderA/folderB/folderC
```

### Relative paths

Relative paths are relative to the current location

```
folderB/folderC
```

You can also go up levels `relative` to the current location.

```
cd ../../..
```

# Working with Files and Directories

[Software Carpentry Working with Files and Directories](https://swcarpentry.github.io/shell-novice/03-create/index.html)

We can create folders and files. Let's setup the directory structure that we can use for the workshop. 
It is going to look like this:
 
```
SDC_02-15-2020
    |
    repository
        |
        thesis
        analyses
        data 
            |
            original_data
            processed_data
```

Let's create the `SDC_02-15-2020` folder on our Desktop with the `make directory` command.

How do we navigate to our Desktop?

```
cd ~/Desktop
```

```
mkdir SDC_02-15-2020
```

Now we can use `tab complete` to create the rest of the directories. 
You can also use the `up-arrow` to bring up the previous commands.

```
mkdir SDC_02-15-2020/repository
mkdir SDC_02-15-2020/repository/thesis
mkdir SDC_02-15-2020/repository/analyses
mkdir SDC_02-15-2020/repository/data
```

```
mkdir SDC_02-15-2020/repository/data/original_data
mkdir SDC_02-15-2020/repository/data/processed_data
```

Let's go into the `SDC` directory. We will spend the rest of the workshop here.

How do we get there?

```
cd SDC_02-15-2020
```

Also use File Explorer to drill into this folder. Do you see the sub-folders?

Let's see what's in here. How do I list the files and folders under repository?

```
ls -la repository
```

Do you see the analyses and data folder?

What is under data? How do I list it?

> use the relative path

```
ls -la repository/data
```

> use the absolute path and the shortcut to home

```
ls -la ~/Desktop/SDC_02-15-2020/repository/data
```

Do you see the directories? Were they the same for each path you used?

LET'S REVIEW

> Use `cd` to move around in the SDC folder. See if you can use relative and absolute paths to move around. 
> Check where you are are `pwd`. Do you end up where you expected to be?

When you are done playing around, make sure you are in the SDC repository folder.

How do you do that?

```
cd ~/Desktop/SDC_02-15-2020/repository
```

## ASSESSMENT

How do I get to my home directory?

1) cd ~
2) ls ~
3) cd /
4) cd /c/home
5) cd /c/Users/marneedearman


## Creating and Editing Files

Let's create a file called. There are two ways of doing this.

### use `nano`

`nano` is a file editor like Notepad or the Mac equivalent.

Let's use it to create a new file.

```
nano thesis.txt
```

This will open `nano`.

> Let's learn about nano. All of the nano commands are shown at the bottom of the window

Start typing in the nano window. You see text.

If you want to save, hit 

```
Ctl + o
```
It then asks for the filename to save.

Press `Enter` when filename is given as you wish.

If you want to exit, hit

```
Ctl + x
```

Check to see if the file is there.

```
ls -la
```

### use touch

Let's create a new file but without using a file editor.

```
touch draft.txt
```

```
ls -la
```

Do you see your two files?

Open draft.txt in nano. How do you do that? Use tab complete.

```
nano draft.txt
```

You should see nano and no text.

Exit nano. Do you remember how to do that?

Let us open draft.txt and make an edit. Use `Ctrl + X` to close after editing. This time we get a different message, why?

> It is telling us that we have not saved changes we made.

Y = Yes
N = No
Ctrl + C = Cancel 

Let's choose `Y` and then we see the same save filename as again like before.

```
ls -la
```

# Moving files around

You know how you can click and drag files around in File Explorer? We can move files around using the shell too.

To move files we use the `mv` command. `mv` stands for `move`.

Let's move thesis.txt into the thesis directory.

To do this you use the `mv` command and tell it the `path to` and the `name of` the file you want to move and 
the path to the new location. You can use the relative or absolute path. Let's use the relative path.

```
mv draft.txt thesis/
```

What happened? Let's list the files.

```
ls -la
```

You dont see thesis.txt where you created it, but you should see it where you moved it.

```
ls -la thesis/
```

> You can also use mv to rename files

Let's rename thesis.txt to thesis_final.txt

```
mv thesis/draft.txt thesis/thesis_final.txt
```

```
ls -la thesis/
```

You should see the new file name.

## Copying files

Let's make a copy of thesis_final.txt. To do this you use the `cp` command.  Just like `mv`, you tell it the `path to` and the `name of` the file you want to move and the path to the new location. You can use the relative or absolute path. Let's use the relative path.

```
cp thesis/thesis_final.txt thesis/thesis_copy.txt
```

```
ls -la thesis
```

Do you see your two files?


## Delete files and directories

To delete a file we use the `rm` command. `rm` stands for `remove`.

Let's try to delete thesis_copy.txt

```
rm thesis/thesis_copy.txt
```

What happened?

```
ls -la
```

You should not see thesis_copy.txt.

> `rm` is forever. Files do not go in the recycle bin.

## ASSESSMENT

I want to move a file from one location to another. What command do I use?

1) mp
2) mv
3) cp
4) cv

# Github and git and our source files

We are going to be working with a number of data files for the rest of the workshop. We will get those from Github 
and we will use `git` to pull them down from Github.

Go to this link (it is in the Etherpad)

> https://github.com/UA-Carpentries-Workshops/2020_February_Bash_Python

Go to the top right corner of the page where it says `Fork`

Click `Fork`

This will make a copy of our `repository` in your account.

We will download a copy of the repository using `git clone`.

> Make sure you are in the SDC directory, up one level from repository

```
cd ~/Desktop/SDC_02-15-2020
```

OR go up one level

```
cd ..
```

Check

```
pwd
```

Are you here?

`SDC_02-15-2020`

## git clone

On your Github account's repository page, click the Big Green Button and then click the clipboard button. 
This will copy the URL of the files to your clipboard.

Go back to the shell and type

```
git clone
```

and then paste the URL so that it looks like this

```
git clone https://github.com/UA-Carpentries-Workshops/2019-02-23-WorkshopResources
```

Hit enter.

Some things happened. Once it is done, list the files and folder. Do you see a new directory?

It is named the same as the name of the repository you cloned.

List what is inside of that directory using the command `ls 2020_February_Bash_Python`. Do you see the `shell-lessons` folder?

Move into the `2020_February_Bash_Python/shell-lessons` folder and run `ls` again. Do you see a `data` folder? 
This is the source data for our workshop.

Let's prepare this data for our workshop by making a copy in the repository data folder we created earlier. 
First let's move back up to the `~/Desktop/SDC_02-15-2020` folder:

```
cd ~/Desktop/SDC_02-15-2020
```

## copy the cloned data files into the original_data folder

What is the copy command?

Let's try to guess how to copy. We did this earlier with a single file at a time, but we need the content of the data 
directory copied to the `data/original_data` directory.

To copy a directory we need to use the `-r` option. This tells the copy command that it needs to be `recursive`, 
meaning that it needs to dig through the directory.

```
cp -r
```

We also need to tell the copy command what files to copy. To copy the contents of a directory we put in the path 
to the directory and add a *. This is the syntax that tells the cp command to get the contents but not the directory.

```
cp -r 2020_February_Bash_Python/shell-lessons/data/* repository/data/original_data/
```

What was copied? List the contents of the original_data directory.

```
ls -la repository/data/original_data
```

What is inside the gapminder_by_country directory?

```
ls -la repository/data/original_data/gapminder_by_country
```

That's a lot of files. Let's start working with them.

But first change directories so you are in the `repository` folder.

```
cd repository
```

```
pwd
```

## Gapminder

The gapminder study collected data on GDP and life expectancy over time for a bunch of countries. 
In the gapminder_by_country you see all of the countries with their GDP data. Let's look at one of them.

# Output

We don't need to use nano to see what is inside a file. We can send (output) the contents of a file to the screen. 
There are two commands we can use to do that. We wil start with `cat`.

## cat

`cat` will output the entire contents of a file to the screen all at once. Let's see that in action.

```
cat data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

What did you see?

## tail and head

We can out put only parts of a file, too.

### tail

`tail` will output the last 10 lines in a file. Let's see what it does.

```
tail data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

We see pretty much the same thing. But let's say we want to see the very last line. We can tell tail to do that.

```
tail -1 data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

We could also see the last 2 lines

```
tail -2 data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

### head

`head` will output the first 10 lines in a file

```
head data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

And we can tell it how many lines like `tail`.

```
head -1 data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

```
head -2 data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

## word and line count

`wc` will count the number of words or lines in a files

> From the help: Print newline, word, and byte counts

```
wc data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

How many lines do we expect to see?

```
wc -l data/original_data/gapminder_data/gapminder_by_country/afghanistan.cc.txt
```

# One gapminder file

Let's use what we have learned to create one big Gapminder data file. First let's change into the original_data directory 
for the sake of shorter commands.

```
cd data/original_data/gapminder_data/gapminder_by_country/
```

```
cat country.cc.txt
```

This is the file with the headers of the data in each country file. Each country does not have a header, but we want 
our `one file to rule them all` to have a header.

Rename the country file to header.cc.txt. How do you do that?

```
mv country.cc.txt header.txt
```

Did that work?

```
cat header.txt
```

We can `cat` more than one file at a time. Let's try that.

```
cat Afghanistan.cc.txt Vietnam.cc.txt
```

We can use a wildcard to cat any file that matches a pattern. Let's try to cat every country file. 
What do they all have in common? Their file extension `.cc.txt`

```
cat *.cc.txt
```

The star is a wildcard and it acts as a placeholder for the file names. 

That was a lot of stuff that went by really fast. What if I want to checkout the file? We can use a command `less` that 
will paginate the output for us. To do this we can combine commands into a pipeline of commands for a final output. 
To do this we use the pipe character `|`. Let's try it.

```
cat *.cc.txt | less
```

The only problem here is that we don't have the headers. So we need to cat the country files with the header file. 
We want the header first. How would we do that?

```
cat header.txt *.cc.txt
```

This make a lot of output. What can we do with it?

## output redirect

We can create a new file using a output redirect commands.

`>>` will create a new file or append the existing file
`>` will create a new file or overwrite the contents to the existing file

```
cat header.txt *.cc.txt >> ../../../processed_data/all_countries.txt
```

## check the file

Let's go where we outputted the file

```
cd ../../../processed_data/
```

If the commands worked you should see 1705 lines. How do we count the lines?

```
wc -l all_countries.txt
```

Let's look at the top 10 lines

```
head all_countries.txt
```

And the last 10 lines?

```
tail all_countries.txt
```

Lets see if we have completed everything correctly. The `diff` command allows us to compare two documents line by 
line for differences.

```
diff all_countries.txt ../../../2020_February_Bash_Python/shell-lessons/data/gapminder_data/.gapminder_final.txt
```

# Process the data

[Software Carpentry Pipes and Filters](http://swcarpentry.github.io/shell-novice/04-pipefilter/index.html)

Let's answer a question.

> What was the GDP in 2007?

## Get only the rows for year 2007

We only want to look at the data for 2007. This means we need to filter our data. We have a command for that called `grep`.

`grep` works on a file or output and takes a pattern to search on. The `grep` command has an odd name. It's a shortcut 
for 'get regular expression and print'. (You don't need to remember that though.) The important thing to remember about 
grep is that it will search for strings or words in files, and show you which lines contain those strings or words. 

Let's look at the line count for each of these grep commands. To do this we can combine commands into a pipeline of
commands for a final output. Again, we will use the `|` character. Let's country the grep output.

```
grep 2007 all_countries.txt | wc -l
```

```
grep "\b2007\b" all_countries.txt | wc -l
```

Notice that the counts are different.

Lets explore more by printing to the screen and see if we understand why the outputs are different.
```
cat | grep 2007 all_countries.txt 
```

What do you notice about the output?

```
cat | grep "\b2007\b" all_countries.txt
```

These two options give us different results. What does the "word boundary" do?

## sort

We can sort the data too. Let's sort in reverse alpha order.
`sort` command with no flags sorts the information from A to Z.
`sort` with the flag `-r` sorts the information from Z to A
```
grep "\b2007\b" all_countries.txt | sort -r
```

Change the sorting to A to Z
```
grep "\b2007\b" all_countries.txt | sort
```
## more chaining

Get the top 10 lines

```
grep "\b2007\b" all_countries.txt | sort -r | head
```

## Create a 2007 data file

How would we create a file with the 2007 data in it?
How do we also include a header?

Let's make this output into a file. What command do we add?

```
grep "\b2007\b" all_countries.txt > 2007_gdp.txt
```

## Cutting

We can use the `cut` command to extract a particular field or column of data from files with delimited columns.
The -f option tells the number(s) of the columns or fields we want to extract. Try these commands:

Use the Up-arrow key to scroll back through your command history to find the command that showed the contents of the
header.txt file. Press the Enter/Return key to execute the command again.

Mac Shortcuts:
`Ctrl + a` Moves cursor to beginning of line
`Ctrl + e` Moves cursor to end of line

Windows Shortcuts:
`Ctrl + Left-Arrow` Moves cursor to beginning of line
`Ctrl + Right-Arrow` Moves cursor to end of line

```bash
cut -f 2 ../original_data/gapminder_data/gapminder_by_country/Zimbabwe.cc.txt
cut -f 5 ../original_data/gapminder_data/gapminder_by_country/Zimbabwe.cc.txt
cut -f 5,6 ../original_data/gapminder_data/gapminder_by_country/Zimbabwe.cc.txt
cut -f 3-4,6 ../original_data/gapminder_data/gapminder_by_country/Zimbabwe.cc.txt
```

## sorting
```bash
cut -f 5 Zimbabwe.cc.txt | sort -n
```

We use the -n option with sort to get a numeric sort from low to high values (by default sorting is alphabetical, and
it's important to use the right type of sorting for a given type of data.) Let's extend our pipe so that after sorting,
it displays only the top 2 lines of output:

```bash
cut -f 5 Zimbabwe.cc.txt | sort -n | head -2
```

Lets combine what we learned about cutting with 2007 only data from before. What will this output?
```
grep "\b2007\b" all_countries.txt | sort -r | head | cut -f1
```

This will show only the first column for the first 10 lines in the data, which is the country name, starting in reverse
alphabetical order.

Thus far we have only worked with one file at a time, but we can use pattern matching to look at several files.
Lets change back to the original data folder with all of the individual files by country.

```
cd ../original_data/gapminder_data/gapminder_by_country/
```

Type a command that will show the contents of all of the .txt files with names starting with Z

```bash
cat Z*.txt
```

The `*` is a wildcard character that matches one or more occurrences of any character. If we want to look at what is in 
the files with names starting with W and Z, we can run the command:

```bash
cat [WZ]*.txt
```

> What do you think will be output by the following command:

```bash
cat [W-Z]*.txt
```

Lets combine the `grep` and pattern matching we have just covered. 

```bash
grep "2007" [W-Z]*.txt
```

```bash
grep "2007" [L-P]*.txt
```

> Can you spot lines containing years other than 2007? Write the countries for which this occurred.
We can fix this problem by telling grep to search for 2007 with white space on either side of it. We specify the 
whitespace using the string "\b" (the "\" is a backslash character, often found on the key above Enter or Return.) 
Make sure you understand the difference between backslash and forward slash.

Now try out the backslash:

```bash
grep "\b2007\b" [L-P]*.txt
```

This example shows the need to be very careful when working with large data sets. You should think carefully about what 
could go wrong while processing your data, and run sanity checks to make sure your outputs are correct.

The `grep` command is often combined with `wc -l` to count the number of lines that contain a specified word or pattern. 
Run this pipe:

```bash
grep "\b2007\b" *.txt | wc -l
```

How many files have a line in them that contains data for the year 2007? Compare this number to the output of the pipe:

```bash
ls *.txt | wc -l
```

We'll use the word count `wc` command to
list the number of lines in each file. Run the `wc -l *` command.
```
wc -l *
```

We're starting to see a powerful feature of the shell, which is called a '*character class*'. There are many more ways 
to do pattern matching with the shell, but they are beyond the scope of this class. Feel free to explore these on your 
own! One useful source is: https://wiki.bash-hackers.org/syntax/pattern

Lets make sure we have saved our changes:

```
git status
git add
git commit
git push
```

# Optional more Advanced Material

## Analyze the data (exta credit)

> What are the top 10 countries for GDP in 2007?
> What are the bottom 10 countries for GDP in 2007?

## Types of files

The gapminder data files we've explored were named `*.cc.txt` where the .txt suffix indicates that the files are
"plain text" files. The fields in these files are delimited with Tabs, so another good way of naming them is to
use `*.tsv` (tab separated values.) You may also be familiar with `.csv` files. In the Etherpad, type the meaning
of 'csv.' All of the aforementioned files (.txt, .tsv, .csv) are examples of "plain text" files and you can easily
work with them on the command line. If you have '.xlsx' files, these include special formatting information that is
not plain text, so you will need to export these as comma- or tab-separated files if you want to work with them on
the command line.

## Exploring differences between files

Think back to our earlier example of running `grep` to find all lines in gapminder data files containing 2007, and
the issue we uncovered if our pattern did not pad the "2007" string with white space. How could we diagnose what's
going on? Remember that we can use '>' to send the output of a command to a file. Run the following commands:

```bash
cd ~/Desktop/SDC_02-23-2019/2019-02-23-WorkshopResources/repository/data/gapminder_data/gapminder_by_country
grep "2007" *.txt > ../../processed_files/Found2007
grep "\b2007\b" *.txt > ../../processed_files/Found2007b
```

Write a command that would show the sizes of both of the new files. The `diff` command will show us the differences 
between 2 files:

```bash
diff ../../processed_files/Found2007 ../../processed_files/Found2007b
```

##################### Stopped Testing Here ################

# git

`git` is a command line change tacking program. You use it to keep a history of changes to your files.

## Why is this important?

An example: are you working with data files? Using `git` you can track all changes that you made to your data for proof 
of work.

An example: you are working on your thesis and you want to track changes to your thesis so you can go back to previous 
revisions as needed. Instead of keep a bunch of files with all the different revisions, you can keep track of them with 
git and only have one file. You can keep track of small changes and major changes, as you see fit. It is more flexible 
that way.

An example: Working on a program with others. Use git to collaborate. You can keep each other from overwriting the 
others's work and you can see what everyone has been changing and working on.

## Git v Github

`git` is the command line tool we use to manage changes to our files. Github is a place on the internet where we can 
store our files and that also keeps track of the changes to our files. We use `git` to send our files to Github and to 
get files from Github, along with the history of changes to those files.

Github is basically a place on the internet where you can share your work with the whole world.

Put on Github and share with the world!!

## get help with git

```
git --help
```

Lets create a new directory structure for a potential project on our Desktop
Github_Project
-> Original_Data
-> Processed_Data

Change directory into Github_Project.
Check to ensure we are where we think we are

## git init (create a new git repository)

This allows us to take a project on our local machines and set it up to be stored on GitHub if we choose.

## git status (see what has changed)

Intially, there is nothing to be added because we have made no changes
Lets add a README file to the Github_Project Directory

Repeat `git status`

## git add (stage what you want to save)

Now, we can use the `git add` to start tracking the README file that we just created.

### what is staging and why do we do this?

`git add` adds the files that we want to save to the staging area
You dont always want to save every change that you have made. We can stage changes and save only the changes we are 
ready to save.

## git commit

`git commit -m 'Enter message between quotes'`
This allows us to save our changes and give a note about what was changed. This is required and if you try to omit
the message it will automatically open your default text editor (Likely Nano) and force you to add a commit message.

## git push

Before we can push we need a remote repository to push to. Let's try creating that on Github.

# Other useful git commands

## git log 
see a log of all the commits

## git diff
see the changes

## git checkout
checkout the changes for a file or an entire commit

## staging and committing (workflow)

CHANGED FILES       STAGED FILES        COMMIT

FA

FB                  FB

FC                  FD                  COMMIT -->      CHANGES ARE SAVED

FD