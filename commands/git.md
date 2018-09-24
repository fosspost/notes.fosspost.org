# Git

## [Tip] List unpushed Commits

### Description

Let's say that you have many local commits which you didn't push yet, and you want to see a list of them.

### Solution

Run the following command:

    git log origin/master..HEAD

## [Problem] Undo all uncomitted changes

### Description

Say that you have some commits in your current tree, and after that, you modified some other files but didn't commit them yet and you want to go back to the last commit.

### Solution

If you want to undo all your changes up to your last local commit, you can run (in your root Git folder):

    git checkout .