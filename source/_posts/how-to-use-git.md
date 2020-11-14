---
title: How to Use Git
date: 2020-11-12 20:23:07
tags: [tool]
categories: [collaboration] 
---

Description: 
This post summaries the book [ProGit](https://www.git-scm.com/book/en/v2).


# Getting Started

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

- All setting file directories: 
	- `git config --list --show-origin`
- All settings: 
	- `git config --list`
- Identity: 
	- `git config --global user.name "User Name"` 
	- `git config --global user.email user@example.com`
- Getting help: 
	- `git help <verb>`


# Git Basics

## Get a Git repository

- Initialize: 
	- `git init` 
	- `git add *.c` 
	- `git add LICENSE` 
	- `git commit -m 'Initial project version'`
- Clone:
	- `git clone <url>`

## Record Changes to the Repository

- checking the status of files: `git status`
	- untracked files: Git sees a file which has no previous snapshot
	- new file
	- modified
- tracking new files: `git add <filename>`
	- if you modify a file after you run `git add`, you have to run `git add` again to stage the latest version of the file
- short status: `git status -s` or `git status -short`
- ignore files (.gitignore): 
	- ignore syntax (#, /, !)
- see changes (TO BE CHECKED): 
	- unstaged changes: `git diff` 
	- staged changes: `git diff --staged` 
	- staged changes: `git diff --cached`
- commit: `git commit` `git commit -m "message"`
- remove files from Git: `git rm`
- move files: `git mv file_from file_to`

## View the Commit History (TO BE ADDED)

`git log`

## Undoing Things

`git commit --amend`



# Git Branching

# Git on the Server

# Distributed Git

# GitHub

# Git Tools

# Customizing Git

# Git and Other Systems

# Git Internals
