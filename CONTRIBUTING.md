# Contributing to FMEasySync

Contributions to this project are encouraged. If you've used FMEasySync and made improvements to it; please consider adding those improvements to this project.


## Submitting Issues

You can [create an issue](https://github.com/dansmith65/FMEasySync/issues/new) if you have questions about this project, bugs to report, code to contribute, etc. Think of issues as a forum for this project.


## Pull Requests

Since FileMaker files cannot be merged, only one person can be working on a file at a time, so it's best to [create an issue](https://github.com/dansmith65/FMEasySync/issues/new) letting everyone know you'd like to start working on changes to submit via a pull request. Additionally, see the notes on Git-LFS and fmpvc:

### GIT-LFS
This repository uses [Git Large File Storage](https://git-lfs.github.com/) to store FileMaker database files. See [Collaboration with Git Large File Storage](https://help.github.com/articles/collaboration-with-git-large-file-storage/). If you're GitHub account does not have Git LFS enabled and you want to contribute, [create an issue](https://github.com/dansmith65/FMEasySync/issues/new) and we'll work something out.

### FMPVC
For every commit that modifies a FileMaker database file, I have been using [fmpvc](https://rubygems.org/gems/fmpvc) to create diffable text files from a DDR.