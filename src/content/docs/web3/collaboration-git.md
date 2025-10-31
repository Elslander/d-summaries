---
title: Collaboration with Git
description: collaboration with git
---

So far we have worked locally with hit. You can also collaborate with several people on 1 repo by working with a remote server. Everyone has a local copy of the repo, and can synchornise their changes via a remote server with other people who have the repo.

In theory, you can use any computer on which you have installed the git command tools as a server. It's just not that practical to work together from home, you have to make sure that your computer can be reached externally and everyone who works together must know your ip address or hostname.

This is why we use a hosted git environment. There are several options for this, we will use GitHub.

## Create & link GitHub account

We will create a GitHub accout and link our GitHub credentials to our computer, so that we don't have to re-enter our password every time.

Visit [github.com](https://github.com) and create an account. (with your @student.howest.be account) Then go to [education.github.com](https://education.github.com/pack) and request an educational pack by clicking "Get your pack", this will be useful to create private repos.

Then open a terminal window. We'll link our name & email address to git so git knows who is doing a commit. Make sure your email address is the one you used to create your GitHub account:

```sh
git config --global user.name "name here"
git config --global user.email "email@student.howest.be"
```

## SSH key

To authenticate yourself with GitHub, you need to create an SSH key. This is a key that is stored on your computer and is used to authenticate yourself with GitHub. You can create a key with the following command:

```sh
ssh-keygen -t ed25519 -C "email@student.howest.be"
```

When asked for the location of the key, you can give the key a more describing name:

```sh
# Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM):
/Users/YOUR NAME/.ssh/github
```

You can press enter to leave the passphrase empty (this can be a security issue).

Now go to your .ssh directory to check if everything is there. You should see (at least) 2 files: `github` and `github.pub`.

```sh
cd
cd .ssh
ls -al
```

### SSH agent

Make sure you are still in the .ssh directory.

Create a `condig` file if there isn't one yet:

```sh
touch config
```

And open it in the editor of your choice. (we are using `code` here)

```sh
code config
```

Now add this to the config file and save it:

```
Host *
  AddKeysToAgent yes
  IdentityFile ~/.ssh/github
```

(note that we didn't add the UseKeychain option - as mentioned in the guide - since we are not using a passphrase)

Now we can add the kay to the ssh-agent:

```sh
ssh-add github
```

### Adding the key to GitHub

Copy the contents of the public key (make sure youa re in the .ssh directory) the command `pdcopy` lets us put content in our clipboard, it is like a 'cmd-c'.

```sh
pbcopy < github.pub
```

On GitHub, go to `Settings < SSH and GPG keys < New/add SSH key < Give it a descriptive name (eg. Macbook"") < Paste the key < Add SSH key`.

You can test if everything is working by running the following command:

```sh
ssh -T git@github.com
```

Remember to choose the SSH option (instead of the HTTPS option) when cloning a repo.

## Create a repo & first push

Login to your GitHub account, and click the "New repository" button. Choose a name for you repository and click the "Create Repository" button.

Don't add a `readme.md` or a `.gitignore` file yet. Since we will sinc this repo with an existing one (the one we create in a previous chapter) things will get complicated if there are files on both ends. (It is definitely possible to fix this, but we won't go in to that now) If you would start completely from scratch, this wouldn't be an issue.

Open a terminal window and navigate via `cd` commands to the directory of the git repo containing the "hello world" files. We will make sure that we can synchronise our local repo via GitHub, by adding a "remote". A remote is a location where you can synchronise a git repo (Don't forget to change `git&github.com:demouser/hellogit.git` with your own repo url, you can find it under the green 'code' button on your GitHub repo.):

```sh
git remote add origin git@github.com:demouser/hellogit.git
git push -u origin main

# Enumerating objects: 17, done.
# Counting objects: 100% (17/17), done.
# Delta compression using up to 12 threads
# Compressing objects: 100% (10/10), done.
# Writing objects: 100% (17/17), 8.98 KiB | 4.49 MiB/s, done.
# Total 17 (delta 1), reused 0 (delta 0)
# remote: Resolving deltas: 100% (1/1), done.
# To git@github.com:demouser/hellogit.git
#     * [new branch]      main -> main
# Branch 'main' set up to track remote branch 'main' from 'origin'.
```

The `git push` command will upload local, unsynchronised changes to the remote location. You use the `-u` attribute the very first time, to ensure that you don't have to specify the remote name in future synchronisations. You can just run `git push` in the future.

### Git add - commit - push

From now on you can start pushing commits to the inline repo. Usually you bundle several loca commits when you push. In fact, we already did this with our first push: all the commits we ran earlier are now also in the online repo.

Delete the `world.txt` file, add commit. We use `git add -u .` to ensure that the delete action of that file is staged:

```sh
rm world.txt
git add -u .
git commit -m "removed world file"

# [main 0b0d3b8] removed world file
#     1 file changed, 1 deletion(-)
#     delete mode 100644 world.txt
```

Create a README.md file, with a little info about the repo:

```sh
echo "Demo repo" > README.md
git add .
git commit -m "added readme file"

# [main a8515e0] added readme file
#     1 file changed, 1 insertion(+)
#     create mode 100644 README.md
```

Execute `git status`. You can see in the status report that the repo is 2 commits ahead of the online version:

```sh
# On branch main
# Your branch is ahead of 'origin/main' by 2 commits.
# (use "git push" to publish your local commits)
# nothing to commit (working directory clean)
```

Execute `git push` to put your commits on GitHub:

```sh
# Enumerating objects: 6, done.
# Counting objects: 100% (6/6), done.
# Delta compression using up to 12 threads
# Compressing objects: 100% (4/4), done.
# Writing objects: 100% (5/5), 488 bytes | 488.00 KiB/s, done.
# Total 5 (delta 2), reused 0 (delta 0)
# remote: Resolving deltas: 100% (2/2), completed with 1 local object.
# To git@github.com:demouser/hellogit.git
#     f1e8b69..a8515e0  main -> main
```

When you view the repo through your browser, you will see that the contents of the `README.md` file are shown below the list of files. This is a file in the Markdown format. (the same for the file you are reading now...) Markdown is a simple markup language for formatting documents. More information about this can be found on Wikipedia.
