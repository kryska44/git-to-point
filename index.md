what I have found helpful when learning Git:

I used Michael Hartl's introduction: [Learn Enough Git to Be Dangerous ](https://learnenough.com/git-tutorial). This is a really beginner-friendly, hands-on approach which helped me get the basics. I also have covered Micahel`s tutorials on [basic command line](https://www.learnenough.com/command-line-tutorial/basics) and [editor](https://www.learnenough.com/text-editor-tutorial/vim) so I felt encouraged to experiment on my own using [git man pages](https://helpmanual.io/man1/git/) and [ProGit](https://git-scm.com/book/en/v2).

[Git Visualiser](http://git-school.github.io/visualizing-git/) - I had problem memorizing commands despite the workflow logic was fairly easy at the start.
Interactive picture speaks a thousand words! 

At some point I wanted to adopt git-completion.bash (git-specific command completion with Tab) and git-prompt.sh (current git branch as part of shell prompt) - these scripts make things easier when working a lot with Git.

I imported the scripts from GitHub, made them executable, activated in my shell profile but encountered errors about invalid newline char., etc. 

Through some research I found out that the solution lies in file [compatibility with the bash version](https://itnext.io/upgrading-bash-on-macos-7138bd1066ba).
So I ended up installing latest Bash and lasted Git. 

brew install bash
brew install git

Searched for local copies of bash_completion and git-prompt.

$ find / -name 'git-completion.bash' -type f -print -quit 2>/dev/null
/usr/local/Cellar/git/2.26.0/etc/bash_completion.d/git-completion.bash

put a line with . ~/.git-completion.bash in your ~/.bash_profile

$ find / -name 'git-prompt.sh' -type f -print -quit 2>/dev/null
/Library/Developer/CommandLineTools/usr/share/git-core/git-prompt.sh

Copied both files to ~. Made them hidden and executable.
cp /Library/Developer/CommandLineTools/usr/share/git-core/git-prompt.sh ~/.git-prompt.sh
chmod + x ~/.git-prompt.sh

edited ~/.bashrc to get my git-prompt working.
. ~/.git-prompt.sh
export GIT_PS1_SHOWDIRTYSTATE=1
export PS1='\w$(__git_ps1 " (%s)")\$

added this line to my ~/.bash_profile
. ~/.git-completion.bash

this made things working.

-------
A shortcut on macOS to produce backslash is __\__ Option-Shift-7, __|__ Option-7, and __~__ Option-^ (immediately left to the Enter key on Norwegian MacBook Pro). On Norwegian iMac keyboard Option-k produses __~__

