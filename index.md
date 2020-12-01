what I have found helpful when learning Git:

I used Michael Hartl's introduction: [Learn Enough Git to Be Dangerous ](https://learnenough.com/git-tutorial). This is a really beginner-friendly, hands-on approach which helped me get the basics. I also have covered Micahel`s tutorials on [basic command line](https://www.learnenough.com/command-line-tutorial/basics) and [editor](https://www.learnenough.com/text-editor-tutorial/vim) so I felt encouraged to experiment on my own using [git man pages](https://helpmanual.io/man1/git/) and [ProGit](https://git-scm.com/book/en/v2).

[Git Visualiser](http://git-school.github.io/visualizing-git/) - I had problem memorizing commands despite the logic of the workflow was fairly easy at the start.
Interactive picture speaks a thousand words! 

 with git-completion and git-prompt scripts - these make things easier when working a lot with Git.
When trying make script work I initially encountered errors about invalid new line char., etc. I imported the scripts from GitHub as recommended in the book and other places on the Internet. 

Through some research I found out that the solution lies in file compatibility with the bash version.
So I ended up installing latest bash 

So I updated Git on my desktop: brew install git

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

this made things working like a charm.
-------

## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/kryska44/website/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/kryska44/website/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
