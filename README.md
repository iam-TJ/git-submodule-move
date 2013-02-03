Git helper shell-script to move submodules within the super-repository

    Usage: git-submodule-move [-v|--verbose] path/to/submodule new/path/

Example:

    git-submodule-move path/to/submodule new/path/
     updating super-repository's submodule name
     updating super-repository's submodule path
     updating super-repository's submodule repository config
     updating submodule's pointer to super-repository config
     moving super-repository's submodule repository
     moving submodule directory
    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #	modified:   .gitmodules
    #	renamed:    path/to/submodule -> /new/path/submodule
    #
    Please inspect the changes and if satisfied commit the change


The directory layout changes thus:

    before: ./path/to/submodule
    after:  ./new/path/submodule

Confirm the changes are acceptable (git status) then COMMIT them

To revert a submodule move before commiting it simply reverse the arguments. E.g.

    git-submodule-move path/to/submodule new/path/
    ...
    # On branch master
    # Changes to be committed:
    #  (use "git reset HEAD <file>..." to unstage)
    #
    #	modified:   .gitmodules
    #	renamed:    path/to/submodule -> new/path/submodule
    #

    git-submodule-move new/path/submodule path/to/
    ...
    # On branch master
    nothing to commit, working directory clean
    Please inspect the changes and if satisfied commit the change

The script can move submodules that use local (path) and external (protocol, e.g. git://) URLs in the .gitmodules file
