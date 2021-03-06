---
layout: post
title: Git commands - git revert
subtitle:
tags: [git, git commands]
comments: true
---



{: .box-note}
## git revert

To review, `git reset` is a powerful command that is used to undo local changes to the state of a Git repo.
#### Use Case

Below are the 2 use cases for git rm.

| Case                                                               | Command                  |
|--------------------------------------------------------------------|--------------------------|
| Reset at commit level | git reset COMMIT |
| Reset at file level | git reset FILES |


Besides, there are 3 common options.

| Option | Meaning |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --soft | The -foption is used to override the safety check that Git makes to ensure that the files in HEAD match the current content in the staging index and working directory. |
| --mixed | The "dry run" option is a safeguard that will execute the git rm command but not actually delete the files. Instead it will output which files it would have removed. |
| --hard | The separator option is used to explicitly distinguish between a list of file names and the arguments being passed to git rm. This is useful if some of the file names have syntax that might be mistaken for other options. |


{: .box-note}
## git rm

The primary function of `git rm` is to remove tracked files from the Git index. Additionally, git rm can be used to remove files from both the staging index and the working directory. There is no option to remove a file from only the working directory. 

#### Use Case

Below are the 2 use cases for git rm.

| Case                                                               | Command                  |
|--------------------------------------------------------------------|--------------------------|
| Remove tracked files from the Git index | git rm --cached FILES |
| Remove  both the staging index and the working directory files | git rm FILES |


Besides, there are 3 common options.

| Option           | Meaning                                                                                                                                                                                                                      |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -f | The -foption is used to override the safety check that Git makes to ensure that the files in HEAD match the current content in the staging index and working directory.                                                      |
| -n | The "dry run" option is a safeguard that will execute the git rm command but not actually delete the files. Instead it will output which files it would have removed.                                                        |
| --               | The separator option is used to explicitly distinguish between a list of file names and the arguments being passed to git rm. This is useful if some of the file names have syntax that might be mistaken for other options. |

