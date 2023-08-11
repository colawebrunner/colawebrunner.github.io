---
layout: post
title:  "Terraform - Installing on Ubuntu 18.04 Desktop"
date:   2023-03-10 15:09:31 +0100
categories: git,github
excerpt_separator: <!--more-->
---
## brief

We had some older code stored in Team Foundation Server (TFS) projects and we are now starting to use Git and GitHub. So this is how we managed to to migrate the code, keeping commit history.
<!--more-->

## method

> Disclaimer: I hold no responsability for the use of this code. This process worked for me. But I did heavily test and used a test repo in this instance to ensure the code did as expected, I advise you to do the same.

The scenario is that we used to use TFS for some older software code and the develeopers continued to use that we all projects, even those started in the last couple of years. We have had some issues with TFS and the also the process for updating different system environments. It has now been decided to migrate a particular peice of software code to Git and in turn GitHub, while keeping the commit history.

Firstly we need a GitHub repo to put the migrated code into. I have GitHub CLI installed, so the commands are based on using that, but you can also do this using the web interface: <https://docs.github.com/en/get-started/quickstart/create-a-repo>.

This command will create a private GitHub repo named *my-project*

`gh repo create my-project --private`

Now we need to clone the repo to our local machine. `[myghuser]` is a variable, insert your own username here.

`gh repo clone [myghuser]/my-project`

Change into that local directory just created by the clone of the repo.

`cd .\my-project`

We now have a GitHub repository setup and have cloned it to our local machine. To make this migration possible I used a tool call git-tfs, you need to install this to proceed with this guide.

This software project is hosted on GitHub: <https://github.com/git-tfs/git-tfs>. As per the Get git-tfs section <https://github.com/git-tfs/git-tfs#get-git-tfs> I used chocolatey to install it, as I was doing this on Windows and had chocolatey installed. *Chocolatey is a package manager for Windows: <https://chocolatey.org/>*

From an Admin powershell window I installed git-tfs

`choco install gittfs`

Now we can use git-tfs to help migrate our TFS projects to Git. Firstly we need to clone the TFS project to our local git project folder. This requires 3 peices of information:

1. The root URL of the TFS project: In our instance we had this in Azure devops so our base URL was: `https://dev.azure.com/[owner name]`
2. The project name you want to clone.
3. Destination folder

`git-tfs `

{% gist %}