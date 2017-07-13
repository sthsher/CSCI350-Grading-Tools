# CSCI350-Grading-Tools
## Hello there

Hello, if you are here because you are a member of the USC CSCI 350 teaching team (Professor, TA, CP), then you are at the right place! Here are the tools I have made to make grading easy.

If you are not a member of the CSCI 350 teaching team (student, or just someone else), then feel free to poke around. I'll just let you know right away that you won't find answers to anything here, so don't waste your time trying.

## Documents

In the *documents* directory, you will find some guides to give to the students as well as the designdoc answers.

## Forms

CSCI 350 students will need to fill out 2 forms:

1. Partner Signup Form: If the professor is allowing partners, they will need to fill out this form in order to get a partner repo.

2. Late Day Form: When a student uses a late day(s), they will need to fill this form in order to notify the grader which commit they want to be graded.

Since these forms were done through google docs, I will link the forms used below for your reference to create your own google form. Please note that you can only access these forms via your USC gmail account:

1. Partner Signup Form: https://goo.gl/forms/jGvsND868BLYoqCp2

2. Late Day Form: https://goo.gl/forms/85QhkF94NNR60iwC3

## Presentations

For each project, there will be a powerpoint presentation as an introduction to the project. You can find the powerpoints I used in the "presentations" directory.

## Scripts

### Prerequisites

#### Submission Repo
You'll need to have scraped the student repositories before you use these scripts. Here are some musts for the scripts to work:

1. Place the submission repository one directory up (../).
2. You must name your repo directory as *submissions_proj\<i\>* replacing the *\<i\>* with the project number (eg. "*submissions_proj2*").
3. You must create a directory named "*DESIGNDOC*" in the submissions directory.
4. You must create a directory named "*GRADES*" in the submissions directory.

#### Student Repo

Each student's repo must be organized in a specific manner:

1. Each project must be named "*proj\<i\>*" in the root directory (eg. "proj2")
2. The designdoc must be named "DESIGNDOC" and placed under each respective project's main source directory. For example for project 2, the designdoc must be named "DESIGNDOC" and placed under "proj2/src/userprog/".

You'll also need to have a csv file ready with all the student's repo names. The format is simply the repo name (eg. pintos-ttrojan) on each line. Please make sure to include an empty line at the end of the file, otherwise the last line will be omitted from the script.

#### Python Packages

Make sure you have the relevant python packages installed:

```
$ sudo apt-get update
$ sudo apt-get install python-pip
$ pip install requests

```

### designdoc Script

The designdoc script simply copies every student's designdoc and places it under the DESIGNDOC driectory in the submissions repo with the student's username in the filename. It simply allows quick access to every student's designdoc.

To run the script, simply enter in the command line:

```
$ python designdoc_proj<i>.py <repos>.csv
```

Replacing \<i\> with the project number and the \<repos\> with the repo csv filename.

### make_grade Script

The make_grade script compiles and runs "make grade" on every student's repo, then copies the relevant number of tests passing information from the grade report generated to the GRADES directory in the submission repo.

To run the script, simply enter in the command line:

```
$ python make_grade_proj<i>.py <repos>.csv
```

Replacing \<i\> with the project number and the \<repos\> with the repo csv filename. Note that this script will run for a very long time as it needs to compile and run every pintos test for every studnet's submission. You might want to split the grading up into batches (hence the two csv files repos_all.csv for every student repo name and repos.csv for a subset), or running it on a dedicated machine overnight.

Every once in a while a student's submission will infinitely loop the grading script. Usually the pintos tests have a timeout that will fail the test automatically, but in some strange circumstances the script will still get stuck. If you suspect a student's submission is clogging up the script, simply remove the student from the csv and grade it manually.

## Closing Remarks

If you have any questions, feel free to contact me at stephen.sher.94@gmail.com. I'll try to help as much as I can. Have fun and happy grading!