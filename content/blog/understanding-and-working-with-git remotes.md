+++
title = "Understanding and working with git remotes"
date = "2023-01-04"
page_template = "page.html"
description = "Understanding and working with git remote. Do you have same git repository over different platforms? Are you searching for the convenient way to manage them all at once within a single local repository?"
[extra]
gotoTop = true
shareable = true
keywords = "Working with Git remotes and pushing to multiple Git repositories, Git, Version control, Remote repository, Fetch, Push, Pull, Branch, Merge, Git hosting service, GitHub, GitLab, Bitbucket, Remote tracking branch, Upstream repository, Collaboration, Git workflows, CLI (Command Line Interface), GUI (Graphical User Interface), SSH (Secure Shell), HTTPS (Hypertext Transfer Protocol Secure)"
+++
Do you have same git repository over different platforms? Are you searching for the convenient way to manage them all at once within a single local repository?
<!-- more -->

## Introduction to git remote?

A remote in Git is a version of your repository that is hosted on the Internet or network somewhere. Remotes make it easy to collaborate with others, as you can fetch and push changes. You can also use them to create backups of your repository.

It's common to have a single remote, called `origin`, but you can have multiple remotes. This can be useful in a few different scenarios. For example, you might want to contribute to someone else's repository and have a remote for their repository. Or, you might want to set up a `mirror` of your repository on a different hosting service.

### How does a git remote work?

There are two link urls for a remote git repository.

1. fetch url: to perform operations like fetch and pull from remote server to local computer.
2. push url: to perform push operations from local computer to remote server.

To check the all the remotes within a repository, you can use the git remote command.

``` 
$ git remote -v
origin	git@github.com:whoisYoges/website.git (fetch)
origin	git@github.com:whoisYoges/website.git (push)
```

Here, for a remote named `origin`, we have the same urls for both fetch and push operations cause we're fetching/pulling from and pushing to the same remote repository. If you fetch/pull from one repository and push to other the urls can be different even in same remote.

## Adding a new remote

To add a new remote to your repository, use the git remote add command. The basic syntax is:

```
git remote add <name> <url>
```

Replace &lt;name&gt; with a short, memorable name for the remote, and &lt;url&gt; with the URL of the remote repository. For example, if you want to add a remote for a repository of this website hosted on GitHub, you might use a command like this:

```
git remote add github git@github.com:whoisYoges/website.git
```

This will add a remote called `github` that points to the specified repository. You can then use this remote like any other. For example, to fetch changes from the remote, you can use the git fetch command:

```
git fetch github
```

Again, if you want to add another remote for the same repository hosted on sourcehut, you might use a command like this:

```
git remote add sourcehut git@git.sr.ht:~whoisyoges/website
```

This will add a remote called `sourcehut` that points to the specified repository and then you can use this remote like any other. For example, to push changes to the remote, you can use the git push command.  
For example, to push your local `master` branch to the `sourcehut` remote, you can use a command like this:

```
git push sourcehut master
```

This can be useful for collaborating with others, as you can push your work-in-progress to a branch on the remote and ask for feedback before merging it into the main branch.

You can view a list of your remotes at any time by running the git remote command with no arguments. This will list the names of all your remotes.

```
$ git remote
github
sourcehut
```

To see more information about a specific remote, use the git remote show command, followed by the name of the remote. This will display information about the `sourcehut` remote, including the URL and the branches that are being tracked. For example:

```
$ git remote show sourcehut
* remote sourcehut
  Fetch URL: git@git.sr.ht:~whoisyoges/website
  Push  URL: git@git.sr.ht:~whoisyoges/website
  HEAD branch: master
  Remote branch:
    master tracked
  Local ref configured for 'git push':
    master pushes to master (fast-forwardable)
```

## Multiple push urls in a single remote

The above method allows us to add multiple remotes and push the local repository to the them one by one, but we cannot push our local repository to all of the remotes at once.

So, Follow the procedure below for adding multiple push urls in a single remote to push a local repository to all of the remotes at once using a single command.

Define a git remote which will point to multiple git remotes, we call it `all`.

`git remote add all REMOTE-URL-1`.

This REMOTE-URL-1 will be used to perform fetch/pull operations.

```
git remote add all git@git.sr.ht:~whoisyoges/website
```

Now, add all the push urls one by one in the remote `all`.  
Here, I'm adding the remote repositories of this website available in sourcehut, github, and codeberg.
```
git remote set-url --add --push all git@git.sr.ht:~whoisyoges/website
```

```
git remote set-url --add --push all git@github.com:whoisYoges/website.git
```

```
git remote set-url --add --push all git@codeberg.org:whoisYoges/website.git
```

Confirm the addition of remote urls by using git remote command.

```
$ git remote -v
all	git@git.sr.ht:~whoisyoges/website (fetch)
all	git@git.sr.ht:~whoisyoges/website (push)
all	git@codeberg.org:whoisYoges/website.git (push)
all	git@github.com:whoisYoges/website.git (push)
```

Push a branch to all the remotes with `git push all BRANCH` – replace BRANCH with a real branch name.
You cannot fetch updates from multiple remotes in this method.

*` Note: The branch name of all the remote repositories must be same. `*

## Conclusion

In summary, adding and using multiple remotes in a Git repository can be a useful way to collaborate with others and make backups of your work. By using the git remote and git push commands, you can easily work with multiple remotes and push and fetch changes as needed.
