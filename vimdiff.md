# Vim Diffing

http://vimcasts.org/episodes/fugitive-vim-resolving-merge-conflicts-with-vimdiff/

Merging a feature branch into master may yield plenty of merge conflicts

They can be resolved using Vim and fugitive plugin

First hunk in a diff is target branch / ie one you've checked out / one that is active when you run git merge

2nd hunk is merge branch / one that is named in the git merge command

In Vim: Gdiff creates three windows and performs a vimdiff between the working copy and the
two conflicting parent versions

LEFT = target branch = filename.ext
MIDDLE = working copy = path/2/filename.ext
RIGHT = merge branch = path/3/filename.ext


To resolve, either use DIFFGET or DIFFPUT

Sync diff highlighting by running
    :diffupdate
   

## DIFFGET

Keep cursor in the middle (working copy) with the buffspec of the file you want to keep
    :diffget 2      # gets the target branch version

## DIFFPUT

Position your cursor on the file you want to keep and run
    :diffput 1

## VIMDIF navigation
    [c      jump to previous changeset
    ]c      jump to next change set
    
## Gwrite!
To add a file wholesale to the index, just run
    :Gwrite!
