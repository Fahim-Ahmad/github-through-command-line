# GitHub-Through-Command-Line

## Introduction

If you don't have any GitHub account, click [here](https://GitHub.com) and go to `Sign up` page then enter a username, valid email address, and password for your GitHub account. Once you created an account on GitHub, login to your account and click the `+` sign in the upper-right corner and then click `New repository`. This will take you to a page where you can create a repo. Please remember that it is always suggested to initialize the repo with a README. 

The contents of README file are automatically shown on the front page of repo which enables you to describe your project in more details. 

Once the repo is created, there are at least two ways to upload your files, codes, etc there.

1. Uploading files manually through `Upload files` tab in the main page of repository.
2. Uploading files through command.

When I first started using GitHub, I was uploading everything manually which worked perfect to me and was very simple with three clicks. • navigate to the main page of the repo and click `Upload files` • Drag and drop the file you'd like to upload to your repo onto the file tree • click `Commit changes`.

However, when I was working with large data files and tried to upload it into the GitHub, I realized the first method is not adequate and I decided to push files into GitHub repository through command and in more standard way.

## GitHub through command line

In order to upload files into a specific repo we need to clone the repo to computer, add new files or modify existing files in the cloned repo, and push everything back to the GitHub. All we need to know is to be familiar with `git clone`, `git status`, `git add`, `git commit`, and `git push`. No panic! Below I will describe each one.

On Mac computers, open terminal and change the working directory to a desired folder where you want to clone the repo.

* Type `pwd` to check the current working directory. (`cd` for windows)
* Type `cd` to change the working directory into a particular path.
* Type `ls` to display contents of current working directory. (`dir` for windows)

I already have a folder called **learning** in **documents**, so I set the directory there.

```{r eval=FALSE, include=TRUE}
# check the current directory
$ pwd
# set the directory into documents > git
$ cd ~/documents/learning
# check contents of the directory
$ ls
```

To create a local copy of GitHub repo on your computer, navigate to the main page of repo and click `Clone or download` then copy the clone URL for the repository.

In `terminal`, type `$ git clone` following by the repo URL.


```{r eval=FALSE, include=TRUE}
# copy the repo from your GitHub account to local directory
$ git clone https://github.com/Fahim-Ahmad/GitHub-Through-Command-Line.git
```

To verify that your repository is cloned, type `ls` in `terminal`. You should see a directory with the same name as the repository that you created previously on GitHub

Change the working directory in the cloned folder and type `ls` to see the cloned files.

```{r eval=FALSE, include=TRUE}
# change working directory in the cloned folder
$ cd ~/documents/learning/GitHub-Through-Command-Line
# see the cloned files
$ ls
```

Next, go to the cloned folder and modify an existing file or add a new file.
It's clearly your decision how you want to add new files in the cloned folder. You can either copy files from other folders and paste it there or use `touch` in `terminal` to add a new file.

```{r eval=FALSE, include=TRUE}
# add a markdown document named as results
$ touch Example1.Rmd
# add another markdown document named as plots
$ touch Example2.Rmd
# check if those documents are added successfully
$ ls
```

Once we added a new file or data in the cloned repo, we can use `git status` to check any changes we made in the cloned folder.

```{r eval=FALSE, include=TRUE}
$ git status
```

All changes are displayed in red color, and we can mark the desired changes for inclusion into the local repository with `git add`.

```{r eval=FALSE, include=TRUE}
# to accept and add all changes
$ git add -A
# to add only a particular file
$ git add <filename>
```

After `git add`, to know which files are added check the status once again using `git status`. All changes are displayed in green color at this stage.

```{r eval=FALSE, include=TRUE}
# to check the status of files
$ git status
```


After `git add` we can save and lock the changes in the local repository using `git commit`. Type `git commit` and `-m` with a message inside quotes in terminal.

```{r eval=FALSE, include=TRUE}
# commit the changes and set the commit's message
$ git commit -m "My first commit."
```

After `git commit` all changes will be committed into local repo on the computer and not into remote repo on GitHub.com. The `git push` is used to upload local repository content to the remote repo.

```{r eval=FALSE, include=TRUE}
# transfer commits from local repo to the remote repo
$ git push
```

If you don't get any message to type your *username* and *password*, congratulations! Your files are in the remote repo on GitHub.com.


## Fixing authentication error

When I first used `git push` I got below error:

```{r, eval=FALSE, include=TRUE}
Username for 'https://GitHub.com': <user name>
Password for 'https://Fahim-Ahmad@GitHub.com': <password>
remote: Invalid username or password.
fatal: Authentication failed for 'https://GitHub.com/Fahim-Ahmad/GitHub-through-command-line.git'
```


I am not alone!

I realized many other people got the same error when trying to use `git push` for the first time. Here I will not talk what causes this error, but below I explain very briefly how I solved it which might be of your help if you get the same error.

1. Go to your GitHub account.
2. In the upper-right corner of any page, click your profile photo, then click **Settings**.
3. In the left sidebar, click **Developer settings**.
4. In the left sidebar, click **Personal access tokens**.
5. Click **Generate new token**.
6. Give your token a descriptive name, and mark **repo**.
7. Click **Generate token**.
8. Copy the token.

Once the token is generated, use it instead of your password after `git push` and wait until the magic happen.

```{r eval=FALSE, include=TRUE}
# transfer commits from local repo to the remote repo
$ git push
Username: <your_username>
Password: <your_token>
```

## Summary

1. create a GitHub account [here](https://github.com).
2. click the `+` sign in the upper-right corner and then click `New repository` to create a new repo.
3. open `terminal` and type `git clone` following by URL to the repository to clone the repo into the computer.
4. change working directory in the cloned folder by typing `cd <path to the cloned repo>`
5. Modify existing files or add new files there.
6. check the changes using `git status`.
7. accept the changes using `git add -A`.
8. commit the changes to local repo using `git commit -m "My first commit."`
9. add all changes from local repo to remote repo using `git push`.
