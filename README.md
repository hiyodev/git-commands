# Git Commands Cheatsheet
> Adding some useful git commands that I use often at work, onto here along with a simple setup to help anyone who is interested. If you spot any mistakes or have any suggestions, please feel free to contribute. 

#### Initial Setup
1. This will create a ```git_demo``` directory, initialize git inside it and create 3 dummy files.
```shell
mkdir git_demo && cd git_demo && git init && touch file{1..3}.txt
```

#### Table of Content
- In Progress...

## Common `git rebase` Scenarios.

#### 1. Too many commits in branch's commit history.
You have 3 or more number of commits in your current working branch and you want to modify it to just be 1 commit to clean up your commit history. It could be for any reason, maybe you have typos in your other commits, maybe you have multiple commits that are the same thing such as **adding 3 files** and would like to keep it concise.

#### Setup
1. We will create a branch for ourselves and switch to it.
2. Create 3 commits by adding each file and push them onto our branch.
3. The logs will show us 3 different commits.
```shell
git checkout -b git_demo1
git add file1.txt && git commit -m "added file1.txt"
git add file2.txt && git commit -m "added file2.txt"
git add file3.txt && git commit -m "added file3.txt"
git push --set-upstream origin git_demo1
git log
```

#### Solution
1. ```git rebase -i``` initiates a interactive UI in your CLI.
2. ```HEAD~3``` means you want to go back 3 commits from your current HEAD.
```shell
git rebase -i HEAD~3
```
After executing this command:
1. Press `i` key to enter `INSERT` mode.
2. Press `esc` key and type `wq` followed by `ENTER` key to write and quit.
3. Use your arrow keys to move.

#### 1.1: Squashing 3 similar commits ( adding of files ) into 1 concise commit.

https://github.com/user-attachments/assets/ae053d99-c55a-4335-bc23-7ae6075723fb

#### 1.2: Dropping 1 commit and modifying another commit that has a typo in the commit message.

https://github.com/user-attachments/assets/30a27a50-b5ef-403f-849a-6616c437ebc7

#### 1.3: Modifying 1 commit that has a typo in the file's content. 

https://github.com/user-attachments/assets/d228a4f5-16a9-4820-80ab-c4066f94b24b

____

## Common `git merge` / `git pull` Scenarios.

#### 1. Your branch is no longer up to date with the remote branch ( main / masters ).
You were working on your branch and a dev on your team has raised a PR to merge his/her changes onto the remote branch. Your current working branch is now no longer up-to-date. 
