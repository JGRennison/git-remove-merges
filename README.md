## git-remove-merges
**Remove merges from a linear series of commits**  

### Use case:

The intended use case is to make it easier to rebase/reorder/modify commit sequences which include non-trivial merges.

`git remove-merges` can be used to remove the second and later parents from a linear commit sequence.  
This enables simple commit manipulation using tools such as `git rebase -i`.  
`git unremove-merges` can then be used to re-add previously removed parents.

### Usage:

    git remove-merges [options] commit

This removes merges from a linear sequence of commits from <commit> to HEAD.  
Removed non-first parent commits are added to the commit message.

    git unremove-merges [options] commit

This performs the opposite transformation to: git remove-merges.  
This re-adds merges from a linear sequence of commits from <commit> to HEAD.  
Parent commits are added from the commit message.

### Commits replaced:

For both commands, the commits replaced are those given by `git log --ancestry-path --first-parent <commit>..HEAD`.  
These commands do not touch the index or working tree.

### Options:
* -b, --branch *branch*  
  replace all uses of HEAD with *branch*
* -n, --dry-run  
  print the new commit hash instead of resetting HEAD
* -c, --keep-committer  
  Preserve committer name, email and date
* -v, --verbose  
  be verbose
* -h, -?, --help  
  show help

### Dependencies:
* Perl 5:  
  * Proc::Hevy  
  * Getopt::Long

### URLs:
This project is hosted at https://github.com/JGRennison/git-remove-merges

### License:
New BSD License, see LICENSE.txt
