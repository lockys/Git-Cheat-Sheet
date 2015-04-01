Git Cheat Sheet Traditional Chinese
===============


###目錄
* [建立](#建立)
* [本地端變更](#本地端-變更)
* [搜尋](#搜尋)
* [送交歷史記錄](#送交-歷史紀錄)
* [分支 & 標籤](#分支--標籤)
* [更新 & 發布](#更新--發布)
* [合併 & Rebase(中文翻作衍合)](#合併--衍合)
* [撤銷](#撤銷)
* [同步](#同步)

<hr>
###建立

如何複製一個現成的程式庫(repository):
```
$ git clone ssh://user@domain.com/repo.git
```

在本地端建立一個程式庫，並由 git 所管理
```
$ git init
```

<hr>
###本地端的變更

查看在你的工作目錄下，有哪些檔案被做修改，或其他變更
```
$ git status
```

查看上一次 commit (送交) 的版本與現在工作目錄下檔案的不同
```
$ git diff
```

把現在所有的變更送至 staging area 中。
```
$ git add
```

只將對 &lt;file&gt; 的變更送至 staging area 中:
```
$ git add -p <file>
```

將所有於 staging area 中的檔案送交 repository(程式庫):
```
$ git commit -a
```

Commit previously staged changes:
```
$ git commit
```

Commit with message:
```
$ git commit -m 'message here'
```

Commit to some previous date:
```
git commit --date="`date --date='n day ago'`" -am "Commit Message"
```

Change last commit:<br>
<em><sub>Don't amend published commits!</sub></em>
```
$ git commit --amend
```
Move uncommitted changes from current branch to some other branch:<br>
```
git stash
git checkout branch2
git stash pop
```

<hr>
###Search

A text search on all files in the directory:
```
$ git grep "Hello"
```

In any version of a text search:
```
$ git grep "Hello" v2.5
```

<hr>
###Commit History

Show all commits, starting with newest (it'll show the hash, author information, date of commit and title of the commit):
```
$ git log
```

Show all the commits(it'll show just the commit hash and the commit message):
```
$ git log --oneline
```

Show all commits of a specific user:
```
$ git log --author="username"
```

Show changes over time for a specific file:
```
$ git log -p <file>
```

Who changed, what and when in &lt;file&gt;:
```
$ git blame <file>
```

<hr>
###Branches & Tags

List all existing branches:
```
$ git branch
```

Switch HEAD branch:
```
$ git checkout <branch>
```

Create a new branch based on your current HEAD:
```
$ git branch <new-branch>
```

Create a new tracking branch based on a remote branch:
```
$ git branch --track <new-branch> <remote-branch>
```

Delete a local branch:
```
$ git branch -d <branch>
```

Mark the current commit with a tag:
```
$ git tag <tag-name>
```

<hr>
###Update & Publish

List all current configured remotes:
```
$ git remote -v
```

Show information about a remote:
```
$ git remote show <remote>
```

Add new remote repository, named &lt;remote&gt;:
```
$ git remote add <remote> <url>
```

Download all changes from &lt;remote&gt;, but don't integrate into HEAD:
```
$ git fetch <remote>
```

Download changes and directly merge/integrate into HEAD:
```
$ git remote pull <remote> <url>
```

Get all changes from HEAD to local repository:
```
$ git pull origin master
```

Publish local changes on a remote:
```
$ git push remote <remote> <branch>
```

Delete a branch on the remote:
```
$ git push <remote> :<branch> (since Git v1.5.0)
or
git push <remote> --delete <branch> (since Git v1.7.0)
```

Publish your tags:
```
$ git push --tags
```

<hr>
###Merge & Rebase

Merge <branch> into your current HEAD:
```
$ git merge <branch>
```

Rebase your current HEAD onto &lt;branch&gt;:<br>
<em><sub>Don't rebase published commit!</sub></em>
```
$ git rebase <branch>
```

Abort a rebase:
```
$ git rebase --abort
```

Continue a rebase after resolving conflicts:
```
$ git rebase --continue
```

Use your configured merge tool to solve conflicts:
```
$ git mergetool
```

Use your editor to manully solve conflicts and (after resolving) mark file as resolved:
```
$ git add <resolved-file>
```
```
$ git rm <resolved-file>
```

<hr>
###Undo

Discard all local changes in your working directory:
```
$ git reset --hard HEAD
```

Get all the files out of the staging area(i.e. undo the last `git add`):
```
$ git reset HEAD
```

Discard local changes in a specific file:
```
$ git checkout HEAD <file>
```

Revert a commit (by producing a new commit with contrary changes):
```
$ git revert <commit>
```

Reset your HEAD pointer to a previous commit and discard all changes since then:
```
$ git reset --hard <commit>
```

Reset your HEAD pointer to a remote branch current state. 
```
git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes:
```
$ git reset <commit>
```

Reset your HEAD pointer to a previous commit and preserve uncommitted local changes:
```
$ git reset --keep <commit>
```

<hr>
###Sync


