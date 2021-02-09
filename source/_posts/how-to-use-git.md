---
title: How to use Git
date: 2020-11-12 20:23:07
tags: [tool]
categories: 
- [notes]
- [collaboration]
---

Description: 

This post is a brief summary of book [ProGit](https://www.git-scm.com/book/en/v2), written by Scott Chacon and Ben Straub (2014). It introduced version control system, basic and advanced Git commands, and Github services.


# Chapter 1. Getting Started

## Version Control

**Version control system**: a system that records changes to a file or set of files over time so that you can **recall** specific versions later.

Local, Centralized, and Distributed Version Control Systems:
- Local: uses local version database to track changes
- Centralized: use shared repository to track changes (single server for collaboration such as MS Office online and Google Drive Docs. single place, single server failure, lose everything)
- Distributed: use multiple repository to track changes (full version history included when copying repository)



## Git

Git thinks about its data like a stream of **snapshots**.

Three file states:
- modified: file changed but not committed
- staged: modified file marked for the next commit snapshot
- committed: version data safely store in local database

Three project sections:
- working tree: single checkout of one version of the project
- staging area: stores what will go into the next commit
- Git directory (.git): metadata and object database for the project

Basic Git workflow:
1. modify files in the working tree
2. selectively stages changes for the next commit
3. commit the files in staging area, stores the snapshot permanently to the Git directory


## Git installation and Setup

- Show all Git settings: 
	- `git config --list` 
- Directories of all setting files: 
	- `git config --list --show-origin`
- Identity: 
	- `git config --global user.name "User Name"` 
	- `git config --global user.email user@example.com`
- Getting help: 
	- `git help <verb>`


# Chapter 2. Git Basics

## Get a Git repository

- Initialize: 
	- `git init` 
	- `git add *.c` 
	- `git add LICENSE` 
	- `git commit -m 'Initial project version'`
- Clone:
	- `git clone <url>`


## Record Changes to the Repository

- check the status of files: `git status`
	- untracked files: a file with no previous snapshot
	- new file
	- modified


- track new files & staging modified files: 
	- `git add <filename>`
	- if you modify a file after you run `git add`, you have to run `git add` again to stage the latest version of the file


- short status: 
	- `git status -s` or `git status --short`
		- ??: files not tracked
		- A: files added to index
		- M: files modified
		- D: deleted from index


- ignore files (.gitignore): 
	- ignore syntax (#, /, !)


- view staged and unstaged changes: 
	- unstaged changes: `git diff` 
	- staged changes: `git diff --staged` 
	- staged changes: `git diff --cached`


- commit: `git commit -m "message"`
	- skip staging area: `git commit -a -m "message"` (`git add` + `git commit`)

- remove files from Git: `git rm <filename>`

- move files: `git mv file_from file_to`
	- usually applied after renaming files


## View the Commit History

- list the commits: `git log`
	- show the difference introduced in each commit: `git log -p`
	- show statistics for files modified in each commit: `git log --stat`
	- show commits in an alternate format: `git log --pretty=short`
	- shorthand for `--pretty=oneline --abbrev-commit` used together: `git log --oneline --decorate`
	- display an ASCII graph of the branch and merge history: `git log --graph`
- show various types of objects: `git show <beginning_hash_characters>`

## Undo Things (skipped)

- redo that commit, make the additional changes you forgot, stage them, and commit again: `git commit --amend`
- unstage a staged file: 
	- `git reset HEAD <file>...`
	- `git restore --staged <file>...`
- unmodifiy a modified file: 
	- `git checkout -- <file>...`
	- `git restore <file>`

## Work with Remotes

- clone remote repositories:
	- `git clone <url>`
- show remotes: 
	- list shortnames of each remote handle: `git remote`
	- show URLs stored for shortnames: `git remote -v`
- add remote repositories:
	- `git remote add <shortname> <url>`
- fetch and pull from remotes: `git fetch <remote>`
- push to remotes: `git push <remote> <branch>`
- inspect a remote: `git remote show <remote>`
- rename a remote: `git remote rename name_from name_to`
- remove a remote: `git remote remove <remote>`

## Tag

- tag important history and mark release points (v1.0, v2.0, et.)
	- `git tag`
- create tags
	- annotaged tags: `git tag -a v1.4 -m "tag message"`
	- lightweight tags: `git tag v1.4-lw`
- delete tags
	- `git tag -d <tagname>`
- checkout tags
	- `git checkout <tagname>`


# Chapter 3. Git Branching

## Branches in a Nutshell

- branch: lightweight movable pointer to one of these commits
- create a new branch: 
	- `git branch <branch_name>`
- create a new branch and switch to it: 
	- `git checkout -b <branch_name>`
- switch branches: 
	- `git checkout <branch_name>`  
	(`git switch` is available for `git checkout` after Git v2.23)

## Basic Branching and Merging

- fast-forward:
	1. have a clean working state when switching branches
	2. main branch with no change, new-feature branch ahead of it: pointer directly move to the next snapshot
	3. delete the new-feature branch after merging: `git branch -d <branch_name>`
- basic merge:
	1. common ancestor snapshot: S1
	2. main branch on next snapshot: S1 --> S2
	3. new-feature branch (ex. issue51) on next snapshot: S1 --> S3 --> S4
	4. merge commit: 
		- switch to main: `git checkout main`
		- merge new feature: `git merge issue51`
	5. three way merge (S1, S2, S4):
		- new commit created with two parents S2 & S4
- basic merge conflicts:
	- changes in the same part of the same file differently in two branches result in conflicts
	- conflicts needs to be fixed before merging

## Branch Management

- git branch command:
	- listing of current branches: `git branch`
	- last commit on each branch: `git branch -v`
	- delete branch: `git branch -d <branch_name>`
	- change branch name:
		1. rename branch locally: `git branch --move old-name new-name`
		2. rename branch on remote: `git push --set-upstream origin new-name`
		3. delete old branch on remote: `git push origin --delete old-name`

## Branch Workflows

- long-running branches
	- main branch
	- develop branch
	- topic branch

- top branches

## Remote Branches (skipped)

## Rebasing (skipped)