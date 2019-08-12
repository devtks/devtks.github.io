---
layout: post
comments: true
title: Process - Using Git Flow with GitKraken and Azure Devops
gh-repo: devtks/devtks.github.io
gh-badge: [star, fork, follow]
tags: [git, gitkraken, tuto, process, azure-devops]
---

In 2019 we had the chance to start a new project from scratch for a new customer. We decided to experiment with a new approach in our workflow by trying to resolve recurring issues from other projects and use the maximum potential of a few things. For Example, being a Microsoft Gold Partner shop we are mostly using Microsoft Product for collaboration and project management. (MS Teams, Azure DevOps, etc....).

One of the biggest changes was the switch from TFS to Git for our code repository plus the fact that we are using Microsoft Azure Devops.

This article will try to summarize our approach using those tools including the git client GitKraken which implements the GitFlow workflow approach. Each concept can be used separately but for us, those tools combined gave us a nice and smooth experience.

Note: GitKakren is normally a free git client desktop but for this tutorial, we are using the pro version to be able to connect to Azure Devops

- [Challenges and problems we tried to resolve](#challenges-and-problems-we-tried-to-resolve)
  - [Teamwork](#teamwork)
    - [Git Flow to the rescue](#git-flow-to-the-rescue)
  - [Code Review](#code-review)
    - [Pull Request & Azure DevOps to the rescue](#pull-request--azure-devops-to-the-rescue)
- [Definition & Tool](#definition--tool)
  - [Git](#git)
    - [Why git is called a distributed source control system?](#why-git-is-called-a-distributed-source-control-system)
  - [Azure DevOps](#azure-devops)
  - [GitKraken](#gitkraken)
  - [GitFlow](#gitflow)
    - [Key Benefits](#key-benefits)
      - [Parallel Development](#parallel-development)
      - [Collaboration](#collaboration)
      - [Release Staging Area](#release-staging-area)
      - [Support For Emergency Fixes](#support-for-emergency-fixes)
- [Environment Setup](#environment-setup)
  - [Create a new project](#create-a-new-project)
  - [Connect GitKraken to Azure Devops](#connect-gitkraken-to-azure-devops)
  - [Clone your Git Repo from GitKraken](#clone-your-git-repo-from-gitkraken)
  - [Initialize Git Flow branches from GitKraken.](#initialize-git-flow-branches-from-gitkraken)
  - [Setting Branch Policies and Pull Request](#setting-branch-policies-and-pull-request)
- [WorkFlow in Action](#workflow-in-action)
  - [Starting a feature](#starting-a-feature)
  - [Creating a feature from GitKraken](#creating-a-feature-from-gitkraken)
  - [Create Pull Request with GitKraken](#create-pull-request-with-gitkraken)
  - [Pull Request on Azure Devops](#pull-request-on-azure-devops)
    - [General View](#general-view)
    - [Adding Work Items](#adding-work-items)
    - [Adding Reviewers](#adding-reviewers)
    - [Set auto-complete](#set-auto-complete)
  - [Pull Request Approval and Code Review](#pull-request-approval-and-code-review)
    - [Feedback on code](#feedback-on-code)
  - [Multiple Features / Conflicts](#multiple-features--conflicts)
    - [Merging and Resolving Conflicts using GitKraken](#merging-and-resolving-conflicts-using-gitkraken)
- [Conclusion](#conclusion)

# Challenges and problems we tried to resolve

This is a short resume of what we tried to achieve and why we think those tools combined helped us a lot in many areas: collaboration, git concept learning curve, code quality, code consistency, and code stability.

## Teamwork

Having multiple developers working on the same projects isn't always easy especially when you try to not step on the feet of each other. A new junior coder (or any coder really) on the team can break the project branch with one wrong commit and affect all other members. Which sometimes ends with stressful and complete chaos for a short (sometimes long) period time on the entire team. Unit test can't be done on dev because the feature isn't completed yet. What features being worked on by who.

### Git Flow to the rescue

With Git Flow branching strategy and some settings on Dev Ops **no commit can be done** directly on the `develop` branch. Each developer always has to create a feature branch and do their work on the feature they are working on. Once a feature is consider done by the developer he has to create a pull request to merge his feature changes to the `develop` branch. His pull request has to be review and approved by another member of the team (Git Flow is explained below)

Pros we see:

- It forces the project to be split into little features
- Corrupted commits don't affect other team members
- Dev can easily relate their feature (pull request ) with bugs, task stories etc
- Dev branch will receive only approved code (more stable, less potential bugs etc)

## Code Review

As a small company that are dealing with sometimes small and low budget projects, it was always hard to put in place code review. It can be hard to find a tool to review commits correctly or easily provide feedback on the developer's code you are reviewing. Azure DevOps offer a smart and very user-friendly way to remedy that challenge and it was a huge success using this feature during our last project. (see Pull Request section)

### Pull Request & Azure DevOps to the rescue

As mentioned in the previous point. Once a feature is considered done the developer has to create a pull request asking his feature to be merged to the `develop` branch. We couple settings on Azure DevOps we can set multiple criteria for a pull request to be approved.

- Be approved by one or multiple team members
- The project has to build with no errors
- Code commentary has to be all resolved
- ....

That gave us an incredible way to keep the code consistent, easily explain to your peers what is wrong with their code or approach and at the end lower the number of bugs present in the application.

# Definition & Tool

## Git

Git is a [free and open source](https://git-scm.com/about/free-and-open-source) distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

Git is [easy to learn](https://git-scm.com/doc) and has a [tiny footprint with lightning fast performance](https://git-scm.com/about/small-and-fast). It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like [cheap local branching](https://git-scm.com/about/branching-and-merging), convenient [staging areas](https://git-scm.com/about/staging-area), and [multiple workflows](https://git-scm.com/about/distributed).

[source](https://git-scm.com/)

### Why git is called a distributed source control system?

This is very important and probably one of the biggest mindset change we had to do from switching from TFS to Git.

Short Definition :
It is not different with client/server model except a local copy, so why is it called a "distributed" one?
In the diagram below _alice_ and _david_ can interact because the system is _distributed_.

![](/img/gitflow-azuredvops/distributed-diagram.PNG)

[source](https://stackoverflow.com/questions/7212740/why-git-is-called-a-distributed-source-control-system)

## Azure DevOps

Azure DevOps formerly known as (VSTS) is a recent continuous integration (CI) and continuous delivery (CD) service provided by Microsoft. It works with any managed Git provider and can deploy to most major cloud services, which allow for Azure services. Azure DevOps provides pipelines to configure and automate builds and releases to different environments. These pipelines can be in YAML or as visual models in the Azure DevOps webpages. Azure DevOps is a fast way to automate build (CI) and deploy (CD) projects and make them available to users. [source](https://dzone.com/articles/introduction-to-azure-pipelines)

![](/img/gitflow-azuredvops/devops-services.PNG)

## GitKraken

GitKraken is a Git GUI client for Windows, Mac and Linux. It helps developers become more productive and efficient with Git. It's free for non-commercial use. (**Need a Pro license to connect to Azure Devops**)

GitKraken simplifies complicated commands into drag and drop actions. It makes working with remote repositories easier through integrations with GitHub, Bitbucket and GitLab. It allows you to resolve merge conflicts without ever leaving the app. And it supports Gitflow, Git Hooks, LFS, and more. [source](https://www.producthunt.com/posts/gitkraken-4)

Official site <https://www.gitkraken.com/git-client>

![](/img/gitflow-azuredvops/gitKrakenLogo.png)

## GitFlow

[GitFlow](http://nvie.com/posts/a-successful-git-branching-model/) is a branching model for Git, created by Vincent Driessen. It has attracted a lot of attention because it is very well suited to collaboration and scaling the development team.

![](/img/gitflow-azuredvops/GitFlow-Diagram.PNG)

### Key Benefits

#### Parallel Development

One of the great things about GitFlow is that it makes parallel development very easy, by isolating new development from finished work. New development (such as features and non-emergency bug fixes) is done in **feature branches**, and is only merged back into main body of code when the developer(s) is happy that the code is ready for release.

Although interruptions are a BadThing(tm), if you are asked to switch from one task to another, all you need to do is commit your changes and then create a new feature branch for your new task. When that task is done, just checkout your original feature branch and you can continue where you left off.

#### Collaboration

Feature branches also make it easier for two or more developers to collaborate on the same feature, because each feature branch is a sandbox where the only changes are the changes necessary to get the new feature working. That makes it very easy to see and follow what each collaborator is doing.

#### Release Staging Area

As new development is completed, it gets merged back into the **develop branch**, which is a staging area for all completed features that haven’t yet been released. So when the next release is branched off of **develop**, it will automatically contain all of the new stuff that has been finished.

#### Support For Emergency Fixes

GitFlow supports **hotfix branches** - branches made from a tagged release. You can use these to make an emergency change, safe in the knowledge that the hotfix will only contain your emergency fix. There’s no risk that you’ll accidentally merge in new development at the same time.

[Source](https://datasift.github.io/gitflow/IntroducingGitFlow.html)

# Environment Setup

## Create a new project

![](/img/gitflow-azuredvops/New-Project.PNG)

First thing let's create a new project on Azure DevOps.
Of course, you have to make sure the version control is set to Git. The other options can be set to your preferences.

![](/img/gitflow-azuredvops/Create-New-Project.PNG)

Welcome to your newly created project.

![](/img/gitflow-azuredvops/Newly-Created.PNG)

## Connect GitKraken to Azure Devops

First thing is to connect GitKraken to your Azure Devops. For that, you are going to need to create a Token

When opening GitKraken you should see Azure Devops option available (_Pro Version_)

![](/img/gitflow-azuredvops/open-gitkraken.png)

![](/img/gitflow-azuredvops/connect-to-azure-devops.PNG)

Enter your devops url and click "Generate a token on Azure DevOps".
![](/img/gitflow-azuredvops/enter-url-devops.png)

You will be redirected to your AzureDevOps personal setting and will be invited to create a new Token

Give it a name and depending on your preferences you can set a maximum of one year validity.

Then switch to a full access scope.

![](/img/gitflow-azuredvops/create-new-token.png)

Once you click on create Azure DevOps will give you a Token to copy.

![](/img/gitflow-azuredvops/success-token.PNG)

Copy that token and return to GitKraken to past it.
![](/img/gitflow-azuredvops/paste-token.png)

Once you click on Connect you should see your token

![](/img/gitflow-azuredvops/connected-success.png)

You can then make sure SSH Key has been correctly added to your DevOps SSH public keys

Now your GitKraken is successfully connected to your Azure DevOps

[Official GitKraken Doc](https://support.gitkraken.com/integrations/visual-studio-team-services/)

## Clone your Git Repo from GitKraken

Now you are connected to your DevOps organization you can clone your newly created project.

![](/img/gitflow-azuredvops/clone-repo.png)

GitKraken will clone to the location you indicated and invite you to do an initial commit to initialize the repo.

![](/img/gitflow-azuredvops/init-repo.PNG)

Once the initial commit is done you should see the following screen
![](/img/gitflow-azuredvops/initial-screen.png)

To confirm that you repo was correctly initialize. You can navigate to the Repos tab of your project on DevOps and you should see a master branch with a readme file in it.

![](/img/gitflow-azuredvops/devops-first-commit.PNG)

## Initialize Git Flow branches from GitKraken.

We are now going to initialize the Git Flow branching strategy with the help of GitKraken. It will give you a quick way to create new branches (develop, features, releases or hotfixes.)

From GitKraken open the Preferences

![](/img/gitflow-azuredvops/preferences.PNG)

And then reach the Git Flow menu

![](/img/gitflow-azuredvops/git-flow.png)

Then click on Initialize Git Flow

You will see now that new menu appeared on your GitKraken main screen but also `develop` branch was created locally.

As mentioned earlier Git is a distributed source code repository

For now, `develop` is only on your local machine. That's why we can't see it on the remote yet. It needs to be pushed.

On GitKraken you can see what is on remote and what is on local by checking little icon. Little computer is where local is and the DevOps team logo is where remote is.

On the screenshot bellow, I need to push my local to remote if I want to init the `develop` branch.

And that's the beauty of Git. You can do as many checking you want locally before sharing it with the rest of the team.

![](/img/gitflow-azuredvops/local-vs-remote.PNG)

First, you need to `checkout` the development for Git to point to this branch.

Normally with command line, it would be done by

```
git checkout develop
```

Within GitKraken you can simply double click on the develop from Main area or left panel.

Now develop should be focused.
![](/img/gitflow-azuredvops/dev-focus.PNG)

Now you can click push to push all the `develop` changes from `local` to `origin`. This will create the branch on the server.

Unless you want to rename anything or have multiple remote you can confirm by clicking submit.

![](/img/gitflow-azuredvops/whatbranch.PNG)

If everything went well you should be able to see the `develop` branch on `remote`and logo from team should be also beside `develop`.

![](/img/gitflow-azuredvops/dev-now-remote.PNG)

## Setting Branch Policies and Pull Request

As mentioned earlier we want to block people from pushing directly to the `develop` branch forcing them to create pull request and also setting some rules for a pull request to be approved. (like can't be approved by yourself and so on.)

Go on Repo-> Branches menu of Azure Devops

You should see the two branches `master` and `develop`

![](/img/gitflow-azuredvops/reposbranches.PNG)

First, little thing to do (optional) is setting the `develop` branch as the Compare one. Then all the features branch will take the `develop` branch as a comparation reference and show how many commits behind or ahead it is.

Click on the 3 dots and then `Set as compare branch`

![](/img/gitflow-azuredvops/setascomparebranch.PNG)

Then we want to setup Branch Policies by again clicking the 3 dots and then `Branch policies`

You can now set the rules as you wish.

- Having Reviewers
- Linked work items
- Resolved Comments
- Merge type
- Build validation (we will do a tutorial on this topic as well)
- etc

As mention in the disclaimer of that page setting rules will automatically apply the following.
![](/img/gitflow-azuredvops/protectthisbranch.PNG)

For the purpose of this tutorial I'm going to activate only a reviewer and comment being set to resolve. (_I can approve my own pull request but it is for this tutorial purpose_)

Here is option example:

![](/img/gitflow-azuredvops/optionexample.PNG)

**Congratulations!: Your environment is now ready to use and setup correctly.**

# WorkFlow in Action

## Starting a feature

Now we are starting a new project which will be a small API made with node.js.

Let say you have all your user stories setup with tasks on DevOps

![](/img/gitflow-azuredvops/project-plan.PNG)

The first feature I'm going to work on is `project setup`. (note here the project is a sample one very small but normal features are a group of one or multiple tasks and not user storied like this example.)

Just to confirm my setting applied. I'm trying to commit my initial files to the `develop` branch

![](/img/gitflow-azuredvops/trycommittodev.PNG)

I am able to push against dev locally but when trying to push on remote I have the following message

![](/img/gitflow-azuredvops/can.tpushondev.PNG)

## Creating a feature from GitKraken

Click on Open GitFlow panel on the left panel of GitKraken

![](/img/gitflow-azuredvops/opengitflowPNG.PNG)

Select Start New Feature

![](/img/gitflow-azuredvops/newfeature.PNG)

Then type the name of the feature and click start feature

![](/img/gitflow-azuredvops/projectsetupfeature.png)

Now we can see that we have a local feature folder created with a project-setup branch in it (only locally for now). I can now push my changes to that local `feature` branch.

Notice that Gitkraken has a nice code comparison tool with different types of view including side by side view.

![](/img/gitflow-azuredvops/side-by-side-view.PNG)

We can now as many`commit` we want on our local branch.
When a feature is done or when we want to share progression we can push all the changes to remote

## Create Pull Request with GitKraken

Now it is time to ask for the feature to be merged with `develop` branch.

Of course, pull request can be created on dev ops directly, command line etc.

Here we are going to create a pull request via GitKraken.

Two ways of doing it.

Click Create pull request menu

![](/img/gitflow-azuredvops/create pull request.PNG)

Or Drag and Dropping the `feature` branch to `develop`

![](/img/gitflow-azuredvops/dragdrop.gif)

We can enter the information we want and then create the pull request.

![](/img/gitflow-azuredvops/pullrequestcreation.PNG)

You can now view your pull request on azure. It needs now to be approved to be merged on `develop`

## Pull Request on Azure Devops

### General View

![](/img/gitflow-azuredvops/generalview.PNG)

### Adding Work Items

You can now add work items related to the pull request (they can be automatically close when pull request is approved )

![](/img/gitflow-azuredvops/assignworkitemPNG.PNG)

### Adding Reviewers

Reviewers can be set and they will receive a notification via email automatically

![](/img/gitflow-azuredvops/reviewers.PNG)

### Set auto-complete

One nice feature is you can set some rules whenever the PR is approved like

- Deleting feature branch automatically

- Set related work items to be resolved, completed, closed ...

- Merge Type

![](/img/gitflow-azuredvops/autocompletion.PNG)

Now Pull Request is fully setup and is waiting to be approved

## Pull Request Approval and Code Review

As a reviewer, you will have all you need to see what was done for that feature.

Azure devops provide a nice and easy way to review and give feedback on your peers' code.

Indeed in one view only you can scroll through all the changes at once.

![](/img/gitflow-azuredvops/CodeChanges.PNG)

### Feedback on code

As mentioned reviewers and any people can leave a comment on a specific line of code or an entire file.

Entire file

![](/img/gitflow-azuredvops/comment-on-file.PNG)

Specific line

![](/img/gitflow-azuredvops/commentonline.PNG)

A nice feature is the fact that comments can be rich and including many formatting/tagging/images/Pull Request or items reference and much more.

![](/img/gitflow-azuredvops/comment example.PNG)

Now a comment is posted we can see on the PR timeline a policy that it doesn't comply to rules of having `all comments resolved`

![](/img/gitflow-azuredvops/timeline.PNG)

The developer will be notified about the comment and make the required changes or reply to the comment

He can push his new changes and reply to the comment by tagging the reviewer for example.

The new commit will appear in the Pull Request timeline

![](/img/gitflow-azuredvops/newcommit500.PNG)

If change is good then the reviewer can now resolve the comment

![](/img/gitflow-azuredvops/resolvecomment.PNG)

Now Pull Request is ready to approve. The reviewer can click on Approve.

![](/img/gitflow-azuredvops/readytoaprove.PNG)

The PR will now indicate that the changes will be merged into `develop`.
![](/img/gitflow-azuredvops/mergeintodev.PNG)

Once Merge being completed the Pull Request will be set to `completed`

![](/img/gitflow-azuredvops/pullcompleted.PNG)

We can also notice the Tasks and User Story being closed automatically

![](/img/gitflow-azuredvops/taskclosed.PNG)

Finally, we can visually see the merge happened in GitKraken

![](/img/gitflow-azuredvops/gitmerge.PNG)

Notice also that feature branch was deleted from remote.
To keep things clean it is better to delete it also locally

![](/img/gitflow-azuredvops/branchdeleted.PNG)

## Multiple Features / Conflicts

Now any developers can start there one feature without affecting the develop branch

In the following example, we can see 2 features going on `products` and `orders`

Following the previous pull request creation sequence each feature will have its pull request once completed.

![](/img/gitflow-azuredvops/multiplefeature.PNG)
We can see that `develop` now is behind and can be tested with the previous request being approved

We will end with pull request for each feature

![](/img/gitflow-azuredvops/2pulls.PNG)

It can happen that the order of Pull Request being approved and changes may trigger conflicts.

For example, while working on orders feature (product and many others were already done.)
Two developers changed the application variable name.

![](/img/gitflow-azuredvops/bothchaningapp.PNG)

Result being Pull Request indicating that there is a conflict

![](/img/gitflow-azuredvops/conflicts.PNG)

### Merging and Resolving Conflicts using GitKraken

To have pull request completed and conflicts resolved. The developer needs to merge all the `develop` changed into its feature.

In that case, we are going to merge `develop` into `feature\order`

It can be done by drag and dropping `develop` on the `feature` branch

![](/img/gitflow-azuredvops/dragdropmeege.gif)

Then the conflict will be detected

![](/img/gitflow-azuredvops/conflictsdeteted.PNG)

Clicking view conflicts will show all the files that cause the conflicts

![](/img/gitflow-azuredvops/conflictsfilesdetails.PNG)

You can click on each file and have access to a very user friendly editor where you can select or exclude any line or even edit the output as needed

![](/img/gitflow-azuredvops/editconflict.PNG)

Once conflicts edited click on save
Now Merge is ready to Commit and Merge

![](/img/gitflow-azuredvops/commitandmerge.PNG)

Once commit is pushed. The Pull Request will be ready to be completed.

![](/img/gitflow-azuredvops/readytoaproveaftermerge.PNG)

Once completed you can see how dev once merge before feature being merged itself in `develop`

![](/img/gitflow-azuredvops/finalresult.PNG)

# Conclusion

In conclusion, we did a retrospective on this project and all the team members agreed by saying this workflow really help the project and all its participants. All dev have a different level of experiences and different preferences but everyone agreed this was the way to go to work together.

**GitKraken** really simplifies everything when it comes to deal with all the Git concepts without using a console any single time. This is definitely a tool we want to keep in our work and it will be hard to go back on other code source repositories like TFS or SVN.

Having **Git Flow** and Pull Request policies in place was a bit challenging at first but in the end, we were always able to provide nice and smooth feedback on each other code which ended with much more consistent and solid code without enforcing strict coding style policy.

**Azure Devops** is a must-have for us now. Everything is very user friendly and the amount of things we can do with this tool is amazing. One of the policies we had for pull request was the application being able to build (.net core api + angular). We didn't have last-minute bad surprise we an application not able to build for production and not being able to deploy.
