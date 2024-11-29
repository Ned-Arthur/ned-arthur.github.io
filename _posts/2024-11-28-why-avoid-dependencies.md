---
layout: post
title: "Why avoid dependencies?"
date: 2024-11-28 11:44:00 +1000
categories:
author: "Ned Murry"
---
## My experiences with dependencies
I've been programming on and off for quite a few years, mostly on windows 10
until recently. I've reached a point where I need to back up my files and
reinstall windows to have a clean and useful OS - I have zero confidence that
regular uninstalls will properly clean up behind themselves, or that I'll even
be able to find all the junk that I've used. This post is about how I got here,
and how I've changed my approach to programming.

### Programming languages and packages/libraries
Python was my first programming language, and after a bit of confusion on the
website we eventually got IDLE installed and working on the family laptop. I
happily learned basic syntax and tried a few projects: number guessing games,
picking random items from a list, and turtle graphics, but didn't go much beyond
that.  When I got my own laptop for high school I installed Python again, but I
missed the PATH configuration in the installer (I didn't know its significance
at the time). After some more messing around I eventually needed to install a
package. Of course, without pip in the path and no idea of virtual environments,
I quickly hit a wall. Somehow my googling didn't find the actual problem, but my
bulletproof solution was to keep a text file with the directory I had to run pip
commands in. This wasn't a big issue, but eventually more little things would
pile up.

Eventually (after dabbling in Unity, Java, HTML/CSS, and some others), I wanted
to learn C++. After some digging I decided to use the GCC compiler, so I needed
MinGW and whatever else came with that setup. After wrestling install wizards
for a few hours I finally got it working. Later I decided to try graphics
programming, which required at least two GL__ libraries. I only ever got a
handful of projects to actually work with this setup, but to this day I still
have all of that toolkit somewhere deep in the Windows filesystem.

Go handles dependencies really well, but it's still really easy to get
cluttered.  I started learning Go properly a couple of weeks ago, and I'm really
loving the standard library. It's very comprehensive, with http routing, regex,
cryptography, and plenty of stuff I haven't discovered yet. All these 'packages'
come with go, so there's no need to install anything new. Where go struggles,
though, is external packages. It's super easy to add the URL to `import ( ... )`
and `go get` the library, but what about removing packages?

I tried using SQLite in an early project but got hung up on properly using
the recommended package, so eventually decided to switch to CSV (which has built
in support). I didn't want to clutter my filesystem, so I tried to remove the
package. Somehow, `go mod tidy` isn't at the top of google, and most people
recommend `go install package@none` and neither are clear about whether they
truly purge all files or just remove the dependency in the project. Luckily, the
standard library covers most projects, and the go filesystem makes it easy to
find errant files.

### Text editors
Another time I've struggled with dependencies is Visual Studio Code. On my
Windows laptop I've got 55 extensions installed. While this does include vital
tools like vscode-pets and brainf\*ck syntax highlighting, I also have 7 for
Java, 4 for C/C++, 8 for Python, and a ton of other junk. This would be fine,
but I have no idea what most of them do (why do I have `C/C++ extension pack`
*and* `Better C++ Syntax`?). The much bigger problem, to me at least, is that
they extract away what's actually going on. Sure, it's practical to hit F5 to
run/debug, but I also spent most of my time with C++ trying to write a dodgy
JSON file to recompile my project for me (I probably didn't find `make` at the
time becasue I was looking for "vscode" solutions and using Windows). I
eventually learned Vim when I started using Linux in 2023, and since then have
been strict on limiting useless installs.

I learned basic Vim motions in the inbuilt tutorial, but quickly got distracted
by neovim. I blindly followed a tutorial for NVChad which, while obviously very
powerful, became too much. I knew I'd never memorise all the keybinds, and the
file browser seemed to break every other time I used it (user error, I'm sure).
Anyway, after installing and reinstalling and switching between Vim and NVim, I
eventually wrote a small .vimrc and wrote most of my code with that. Now I'm on
a new computer with a fresh install of vim, and I've got a pretty comprehensive
config. It isn't perfect, but when I find something I want to change, I can just
do it. I know where everything is, and the only documentation I need is Vim's. I
don't have to dig through deeply nested directories of files which each have
only a few lines of config, but I *could* set that up if I wanted to. I can
`map` a new keybind if I find typing `:ter<enter> <C-w>J <C-W>15-` too tedious
for a small terminal along the bottom of my screen, or I can throw in an
`autocmd` to set my indentation for HTML to two spaces. Essentially, writing my
own config allows me to know everything that's going on in my editor, and fix
issues when they arise.

## So what?
A lot of people are very productive with VSCode and a massive `node_modules`,
but I like knowing exactly what's on my computer. I want to build and use
software which is self-contained and simple to both use and configure. I also
want to write "tutorials" that focus more on guidance for completing a project
and solving problems, rather than copy/pastable steps, and do so in a way which
will work long into the future and is adaptable across languages, rather than
requiring an IDE which is no longer maintained and libraries which have
completely changed since the tutorial was written.

Hopefully someone will find this blog useful, and just maybe I'll learn some
things too.

