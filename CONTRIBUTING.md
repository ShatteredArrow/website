# How to Contribute

👍🎉 First off, thanks for taking the time to contribute! 🎉👍

The following is a set of guidelines for contributing to the website repository, which is hosted in the hackforla Organization on GitHub. These are mostly guidelines, not rules. Use your best judgment, and feel free to propose changes to this document in a pull request.

** <sub>The guide below assumes that you already have a github account. If you do not have a github account yet, [Sign Up Here](https://github.com/join)</sub>
<br><br>
## Table of Contents

### Setting up the development envirnoment
1. [Join the repository team](#Join-the-repository-team-[1])
2. [Fork the repository](#Fork-the-repository-[2])
3. [Clone the forked repository](#Clone-the-forked-repository-[3])
4. [Set up Docker](#step-4-setting-up-docker)
5. [Build and serve the website locally](Build-and-serve-the-website-locally-[5])
### Working on your first issue and making your first pull request
1. [Switch to new issue branch before you start making changes](#step-6-change-to-a-new-branch)
2. [Check upstream before you push](#step-7-check-upstream-before-you-push).
3. [No changes in the upstream repo](#step-7a-no-changes-in-the-upstream-repository)
4. [Conflicting changes in the upstream repo](#step-7b-conflicting-changes-in-the-upstream-repository) and how to resolve them
5. [Complete the pull request](#step-8-complete-the-pull-request)
### Resources and Documentation
1. [Hack for LA's Site Architecture](https://github.com/hackforla/website/wiki/Hack-for-LA's-Site-Architecture)
2. [GitHub Pages](https://pages.github.com/)
3. [Jekyll Docs](https://jekyllrb.com)
4. [Github Guides](https://guides.github.com/) 
5. [Docker](https://docs.docker.com/get-started/)
   - [Docker Compose](https://docs.docker.com/compose/gettingstarted/)
   - [Docker Desktop](https://docs.docker.com/install/)

<br>

# Setting up the development envirnoment
## Join the repository team [1]

In the `hfla-site` slack channel, send your GitHub name to the project manager (or on the slack channel thread) and we'll add you as a member to the GitHub repository Team.

Once you have accepted the GitHub invite (comes via email or in your GitHub notifications), please do the following:

1. Mark your own membership public https://help.github.com/en/articles/publicizing-or-hiding-organization-membership#changing-the-visibility-of-your-organization-membership

1. Setup two factor authentication on your account https://github.com/hackforla/governance/issues/20


## Fork the repository [2]

In https://github.com/hackforla/website, look for the fork icon in the top right. Click it and create a fork of the repository.

<sub>For git beginners, a fork is a copy of the repository that will be placed on your GitHub account </sub>


It should create a copy here -> `https://github.com/your_GitHub_user_name/website`,
where `your_GitHub_user_name` is replaced with exactly that.

Note that this copy is on a remote server on the GitHub website and not on your computer yet.

If you click the icon again, it will not create a new fork but instead give you the URL associated with your fork.

## Clone the forked repository [3]

The assumption from here on out is you have git installed on your system. If that is not the case. You can find instructions for installing git on your operating system [**here**](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).The following steps will create a third copy of the repository on your local desktop.

   1. Create a new folder on your desktop that will contain `hackforla` projects.

      In your shell, navigate there then run the following commands:

      ```bash
      git clone https://github.com/your_GitHub_user_name/website.git
      ```

      You should now have a new folder in your `hackforla` folder called `website`. Verify this by changing into the new directory:
      ```bash
      cd website
      ```

  2. Verify that your local cloned repository is pointing to the correct `origin` URL (that is, the forked repo on your own Github account):

     ```bash
     git remote -v
     ```
     You should see `fetch` and `push` URLs with links to your forked repository under your account (i.e. `https://github.com/YOURUSERNAME/website.git`). You are all set to make working changes to the website on your local machine.

     However, we still need a way to keep our local repo up to date with the deployed website. To do so, you must add an upstream remote to incorporate changes made while you are working on your local repo. Run the following to add an upstream remote URL & update your local repo with recent changes to the `hackforla` version:

     ```bash
     git remote add upstream https://github.com/hackforla/website.git
     git fetch upstream
     ```

     After adding the upstream remote, you should now see it if you again run `git remote -v` :
     ```bash
      origin  https://github.com/YOURUSERNAME/website.git (fetch)
      origin  https://github.com/YOURUSERNAME/website.git (push)
      upstream        https://github.com/hackforla/website.git (fetch)
      upstream        https://github.com/hackforla/website.git (push)
      ```
      <details>
      <summary><i>If you accidentally cloned using the repository URL from the HackForLA Github (instead of the fork on your Github)</i> 
      </summary>

      1) Set your forked repo on your Github as an `origin` remote:

      ```bash
      git remote set-url origin https://github.com/your_user_name/website.git
      ```

      2) Add another remote called `upstream` that points to the `hackforla` version of the repository. This will allow you to incorporate changes later:

      ```bash
      git remote add upstream https://github.com/hackforla/website.git
      ```
      </details>
      <br>

## Setting up Docker [4]

Docker is the recommended approach to quickly getting started with local development. Docker helps create a local/offline version of the hackforla.org website on your computer so you can test out your code before submitting a pull request

The recommended installation method for your operating system can be found [here](https://docs.docker.com/install/). <sub><i>Feel free to reach out in the hfla slack channel if you have trouble installing docker on your system</i></sub>

<details>
<summary>Docker Installation Troubleshooting</summary>

If you are on Windows and get 'You are not allowed to use Docker, you must be in the "docker-users" group' as an error message, the following wiki page is a guide for solving te issue:
- [Windows docker-users group error guide](https://github.com/hackforla/website/wiki/Adding-local-user-accounts-to-the-docker-users-group-on-Windows-10)

Installing WSL2 on windows
- https://docs.microsoft.com/en-us/windows/wsl/install-win10
</details>
<br>

## Build and serve the website locally [5]

### Build Up

- This command starts a jekyll server locally. The server watches for changes to
the source files and rebuilds and refreshes the site automatically in your browser.

  Navigate to within the `website` directory that you cloned earlier in your terminal then run the below command

   ```bash
   docker-compose up
   ```

   Running the above command will result in the following output in your terminal

  <details>
  <summary>Terminal Output</summary>

  ```bash
  Starting hfla_site ... done
  Attaching to hfla_site
  hfla_site    | ruby 2.7.1p83 (2020-03-31 revision a0c7c23c9c) [x86_64-linux-musl]
  hfla_site    | Configuration file: _config.yml       
  hfla_site    | Configuration file: _config.docker.yml
  hfla_site    |             Source: .
  hfla_site    |        Destination: /srv/jekyll/_site
  hfla_site    |  Incremental build: enabled
  hfla_site    |       Generating...
  hfla_site    |                     done in 33.641 seconds.
  hfla_site    |                     Auto-regeneration may not work on some Windows versions.
  hfla_site    |                     Please see: https://github.com/Microsoft/BashOnWindows/issues/216
  hfla_site    |                     If it does not work, please upgrade Bash on Windows or run Jekyll with --no-watch.
  hfla_site    |  Auto-regeneration: enabled for '.'
  hfla_site    | LiveReload address: http://0.0.0.0:35729
  hfla_site    |     Server address: http://0.0.0.0:4000/
  hfla_site    |   Server running... press ctrl-c to stop.
  ```

  </details>

   When you see the above output, it means the site is now running and now you can browse to http://localhost:4000

### Tear Down

 - To stop and completely remove the jekyll server (i.e. the running Docker container):

   *(do this anytime Docker or jekyll configuration or other repository settings change)*

   ```bash
   docker-compose down
   ```

   To stop the server, but not destroy it (often sufficient for day-to-day work):

   ```bash
   docker-compose stop
   ```

   Bring the same server back up later with:

   ```bash
   docker-compose up
   ```
<br>

# Working on your first issue and making your first pull request

## Work on an issue using git

Create a new branch for each issue you work on. Doing all your work on topic branches leaves your repository's main branch (named `gh-pages`) unmodified and greatly simplifies keeping your fork in sync with the main project.

1. Check current branch

   The `git branch` command will let you know what branch you are in, and what branch names are already in use.

   ```bash
   git branch
   ```

   You will see a list of all of your branches. There will be a star (`*`) next to the branch that you are currently in. By default you should start on the `gh-pages` branch.

   <sub>** *when you work on future issues, you must always be in the `gh-pages` branch when creating a new branch.*</sub>

   If you are not currently in the `gh-pages` branch, run the following command to return to it:

   ```bash
   git checkout gh-pages
   ```

2. Create a new branch where you will work on your issue

   The `git checkout` command will create and change to a new branch where you will do the work on your issue.  In git, the checkout command lets you navigate between different branches.  Using the `-b` flag you can create a new branch and immediately switch into it. 

   To create a new issue branch, and switch into it: 

   ```bash
   git checkout -b fix-logo-width-311
   ```

   The text after the `-b`, in the example `fix-logo-width-311`, will be the name of your new branch. Choose a branch name that relates to the issue you're working on. (No spaces!)

   The format should look like the scheme above where the words are a brief description of the issue that will make sense at a glance to someone unfamiliar with the issue. 

   <sub>*No law of physics will break if you don't adhere to this scheme, but laws of git will break if you add spaces.*</sub>

   When you've finished working on your issue, follow the steps below to prepare your changes to push to your repository. 

3. Prepare your changes to push to your repository

   Once you are done with the work on your issue you will push it to your repository.  Before you can push your work to your repository, you will stage and commit your changes.  These two commands are similar to the save command that you have used to in other programs. 

   <sub>** *If you are using Visual studios code you can use the Git graphical user interface to stage your changes. For instructions check out the [Git Gui Wiki](https://github.com/hackforla/website/wiki/Using-Git-GUI-(Graphical-user-Interface)-in-Visual-Studios-Code)*</sub>
   

   - Use the `git add` command to stage your changes.  
      This command prepares your changes before you commit them. You can stage files one at a time using the filename. 

      Run the command: 
      ```bash
      git add “filename.ext”
      ```

   - Use the `git status` command to see what files are staged

      This command will list the files that have been staged.  These are the files that will be committed (saved) when you run the next command, `git commit`. Please be sure all your staged changes are relevant to the issue you are working on. If you find you have included unrelated changes, please unstage them before making this commit - and then make a new commit for the unrelated changes. (The commands for unstaging commits are provided in the output of your `git status` command.)


   - Use the `git reset HEAD` command to remove a staged file. 

      This command will remove a file that has been staged.  This file will not be committed (saved) when you run the next command, `git commit`. This only works if the wrong files were added, but they were not yet committed. The file will be removed from the staging area, but not actually deleted:
      ```bash
      git reset HEAD “filename.ext” 
      ```

    - Use the `git commit` command

      This command saves your work, and prepares it to push to your repository.  Use the `-m` flag to quickly add a message to your commit. Your message should be a short description of the issue you are working.  It will be extremely helpful if other people can understand your message, so try to reisst the temptation to be overly cryptic.

      To commit your changes with a message, run:
      ```bash
      git commit -m “insert message here”
      ```

4. Check upstream before you push

   Before you push your local commits to your repository, check to see if there have been updates made in the main Hack For LA website repository. `git fetch` will check remote repositories for changes without altering your local repository.

   ```bash
   git fetch upstream
   ```

    - <details>
      <summary>No changes in the upstream repository</summary>

      If you do not see any output, there have not been any changes in the
      main Hack for LA website repository since the last time you
      checked. So it is safe to push your local commits to your fork.

      If you just type `git push` you will be prompted to create a new branch in your GitHub repository. The more complete command below will create a new branch on your copy of the website repository, and then push your local branch there. The name at the end of this command should be the same as the name of the local branch that you created back in step 3, as in the example below:  

      ```bash
      git push --set-upstream origin fix-logo-width-311
      ```
      </details>
    - <details>
      <summary>Conflicting changes in the upstream repository</summary>

      PASTE_YOUR_IMAGE_HERE

      </details>

5. Complete the pull request

   instructions on how to complete the PR TBD

   <sub>
   <details>
   <summary>Edits to pull request</summary>

   <i>If you find an error in your code or your reviewer asks you to make a change, please avoid editing your code directly from the pull request. Instead update it in your local branch first and then push it to your origin remote. This will update the original pull request.</i> 

   </details>
   </sub>

<br><p style="text-align: center;">🎉🎉🎉<b>Congratulations!  You have successfully made your first pull request. Thank you for contributing !</b>🎉🎉🎉 </p><br>

# [Back to Top](#overview)
