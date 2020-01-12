# GitPerm
A simple branch-based permission manager for git.

Welcome to my first GitHub project.
It's a little bash-script letting you define rules to grant per branch per user/group push access to git.

To install it just copy the file pre-receive to .git/hooks/ of your git repository.

Then you can define rules in .git/gitperms.conf like this: 

    # Allow only root to update the master-branch
    master allow user root
    master deny * Master is write protected. Please ask root to merge your commits.
    
    # Allow members of the group developer (and myself) to push to branch development
    development allow group developer
    development allow user johanneswilke 
    development deny * Only users of group development can push to this branch.
    
    # Forbid to create new branches or push to any other branch
    * deny *
    
    # Note that the config has to end with a newline due to posix standard
    # otherwise the last-line is ignored
    

In general a rule has the following format:

    branch [allow|deny] [user value|group value|*] (Message)

Where (...) is optional and for [a|b|...] you can choose either a or b.