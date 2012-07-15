dotzsh
======

Forked from sorin-ionescu's oh-my-zsh but adds support for zsh 4.2.6 as found on CentOS5/EL5
as well as a few extra modules

dotzsh is a configuration framework for [Zsh][1] that enriches the command line
interface environment with sane defaults, aliases, functions, auto completion,
and prompt themes.

Installation
------------

dotzsh will work with any recent release of Zsh, but the minimum recommended
version is 4.2.6.

  1. Clone the repository:

        git clone --recursive https://github.com/dotphiles/dotzsh.git ~/.zsh

  2. Create a new Zsh configuration by copying the Zsh configuration file
     templates provided:

        for rcfile in ~/.zsh/templates/z{shenv,shrc,login,logout}; do
          cp -f $rcfile ~/.$rcfile:t
        done

  3. Set Zsh as your default shell:

        chsh -s /bin/zsh

  4. Open a new Zsh terminal window or tab.

### Mac OS X

If you have administrator privileges, you must fix an Apple-introduced problem
in Mac OS X 10.5 Leopard by executing the following command, or BASH and Zsh
will have the wrong `PATH` when executed non-interactively.

    sudo chmod ugo-x /usr/libexec/path_helper

`path_helper` is intended to make it easier for installers to add new paths to
the environment without having to edit shell configuration files by adding
a file with a path to the */etc/paths.d* directory.

Unfortunately, `path_helper` always reads paths from */etc/paths* set by Apple
then paths from */etc/paths.d* set by third party installers, and lastly paths
from the `PATH` environment variable set by the parent process, which
ultimately is set by the user with `export PATH=...` Thus, it reorders path
priorities, and user */bin* directories meant to override system */bin*
directories end up at the tail of the array.

### Troubleshooting

If you are not able to find certain commands after switching to *dotzsh*,
modify the `PATH` variable in *~/.zshenv* then open a new Zsh terminal
window or tab.

Usage
-----

dotzsh has many features disabled by default. Read the source code and
accompanying README files to learn of what is available.

### Modules

  1. Browse *~/.zsh/modules/* to see what is available.
  2. Load the modules you need in *~/.zshrc* then open a new Zsh terminal window
     or tab.

### Local Modules

  1. Add your own modules to *~/.zsh.local/modules/* to override existing modules.
  2. Load the modules you need in *~/.zshrc* then open a new Zsh terminal window
     or tab.
 
### Themes

  1. For a list of themes, type `prompt -l`.
  2. To preview a theme, type `prompt -p name`.
  3. Load the theme you like in *~/.zshrc* then open a new Zsh terminal window
     or tab.

     ![sorin theme][2]

### Troubleshooting

  `dzinfo` will show which module are loaded and how long they took to start.

Customization
-------------

The project is managed via [Git][3]. It is highly recommend that you commit
your changes and push them to [GitHub][4] to not lose them. If you do not know
how to use Git, follow this [tutorial][5] and bookmark this [reference][6].

### Completions

Submit program completions to the [zsh-completions][7] project. The dotzsh
completions directory will be synchronized against it.

Resources
---------

The [Zsh Reference Card][8] is indispensable.

Contribute
----------

This project would not exist without all of its users and [contributors][9].

If you have ideas on how to make the configuration easier to maintain or
improve its performance, do not hesitate to fork and send pull requests.

### Issue Reporting

   - Check that the issue has not already been reported.
   - Check that the issue has not already been fixed in the latest code.
   - Open an issue with a clear title and description in grammatically correct,
     complete sentences.

### Pull Request

   - Read [how to properly contribute to open source projects on GitHub][10].
   - Use a topic branch to easily amend a pull request later, if necessary.
   - Write [good commit messages][11].
   - Squash commits on the topic branch before opening a pull request.
   - Use the same coding style and spacing.
   - Open a [pull request][12] that relates to but one subject with a clear
     title and description in gramatically correct, complete sentences.

#### Modules

   - A *README.md* must be present.
   - Large functions must be placed in a *functions* directory.
   - Functions that take arguments must have completion.

### Return Codes

   - Modules will return with the following the Codes

     - `-1` old zsh, degrading
     - `0` loaded ok
     - `1` error, disabling
     - `2` required command not available, disabling
     - `3` dumb terminal, disabling
     - `4` wrong os, disabling
     - `8` module not found, disabling
     - `9` zsh too old, disabling

#### Themes

   - A screenshots section must be present in the file header.
   - The pull request description must have must have [embedded
     screenshots][13].

License
-------

Copyright (c) 2012 Ben O'Hara <bohara@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[1]: http://www.zsh.org
[2]: http://i.imgur.com/aipDQ.png "sorin theme"
[3]: http://git-scm.com
[4]: https://github.com
[5]: http://gitimmersion.com
[6]: http://gitref.org
[7]: https://github.com/zsh-users/zsh-completions
[8]: http://www.bash2zsh.com/zsh_refcard/refcard.pdf
[9]: https://github.com/dotphiles/dotzsh/contributors
[10]: http://gun.io/blog/how-to-github-fork-branch-and-pull-request
[11]: http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
[12]: https://help.github.com/articles/using-pull-requests
[13]: http://daringfireball.net/projects/markdown/syntax#img

