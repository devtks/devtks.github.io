---
layout: post
comments: true
title: Process - Using Retrospective Extension in Azure DevOps
gh-repo: devtks/devtks.github.io
gh-badge: [star, fork, follow]
tags: [tuto, tutorial, process, azure-devops]
---

Project Retrospective. you know the thing we rarely do and we do it gets quickly lost in the nature within a Word Doc or other type of one time used never read again type of doc. 
Because we are trying to use the full potential of Azure Devops here and TKS by using features like Boards, Pipeline and so on we thought it would be nice to have retrospective that sit within the project artifacts and be accessible by anyone at any time.

This guide will help you to use a plugin available in Azure Devops that will allow you to gather feedback from your team, your clients. Vote, plan and create actionable items.


- [Installation](#installation)
- [Create a Retrospective](#create-a-retrospective)
  - [Choose you audience](#choose-you-audience)
  - [Create a new Board](#create-a-new-board)
- [Collect Feedback](#collect-feedback)
- [Group Feedback](#group-feedback)
- [Vote for feedbacks](#vote-for-feedbacks)
- [Act](#act)
- [Track your progress](#track-your-progress)
- [Conclusion](#conclusion)


# Installation

Very easy step. On the right top corner of your Azure Devops page you can click on the extension icon and `Browse marketplace`

![](/img/retrospective/browsemarketplace.PNG)

Then search for Retrospective (in my case it is on the homepage because it is one of the featured extensions)

![](/img/retrospective/store.PNG)

You should land on this page https://marketplace.visualstudio.com/items?itemName=ms-devlabs.team-retrospectives



Click on `Get it Free`

![](/img/retrospective/getitfree.PNG)

Select your company or if you have a server download the plugin


![](/img/retrospective/selectcompany.png)

Now when you navigate to one of your project you should see a retrospective menu under Boards.


![](/img/retrospective/myproject.PNG)

![](/img/retrospective/newmeny.PNG)

# Create a Retrospective

## Choose you audience

You might want to do your retrospectives internally, or with your client. Some information might be sensitive or you might want to clean the feedback before involving your client or external people for example.

That is why the first thing to do is to select your team. It will determine who can see you retrospective.

Example:

![](/img/retrospective/choosingteam.PNG)



## Create a new Board

You can create a new board by choosing several options. Giving the opportunity for people to give their feedback anonymously or add a maximum of 4 columns.

![](/img/retrospective/newboard.PNG)

In my example I'm doing a mid project retrospective. Keeping the 2 default columns but adding a 3rd one "What should we start"

![](/img/retrospective/newmidprojectboard.PNG)

Welcome to your new board !! It should look like this.

![](/img/retrospective/firstboard.PNG)

# Collect Feedback

Now that is time to tell your team, client or whoever to give their feedback. It will had cards under each categories.


![](/img/retrospective/cards.PNG)

# Group Feedback

You might end with similar or identical feedback from multiple team member. The extension give you the ability to group them.

Example:


![](/img/retrospective/toomanyemails.PNG)

Click on the 3 dots and Group Feedback


![](/img/retrospective/group.PNG)

Then search for the ticket you want to group with


![](/img/retrospective/search.PNG)

Once you click on it you will see your card with `items`


![](/img/retrospective/2items.PNG)

You can expand it and see the other feedback related.

![](/img/retrospective/2itemsextended.PNG)

# Vote for feedbacks

Now your items are grouped and your board is now clean and organize. You can ask your team or client to vote for the items they agree with or think are more important.

Each member can give any number of vote per item they want.

It should give a good idea of what items are consider important

![](/img/retrospective/votes.PNG)

At any time a feedback can be delete.

That is your choice to let say for example remove all the feedbacks that didn't have any vote.

# Act

Everything described previously led to this important moment.

Everything described above can be done without any meeting which is a big gain of time and productivity.

Now that is time to gather everyone (or not). But this is the phase were you can review, create items or action items base on feedbacks.

You have 2 possible views for this

**Board view**

![](/img/retrospective/boardview.PNG)

**Focus view**
it allows to go through the feedbacks one by one which can be convenient for your final retrospective meeting to stay `focus`.

![](/img/retrospective/focus.PNG)

You can notice the text speak for itself.

Time to create actionable work items.

ex: 
stack was fun?

![](/img/retrospective/createtask.PNG)

then a task can be created on creating a reusable template.

![](/img/retrospective/createnewtemplate.PNG)

# Track your progress

Once you are done you can come back anytime at your retrospective and check if any actions items was created. Who was assigned to them, are they completed or not etc
![](/img/retrospective/resume.PNG)

![](/img/retrospective/progress.PNG)

# Conclusion

This plugin can be very useful to archive and follow up on project retrospective. If your are using Azure DevOps is it a nice way to keep those precious feedback along your project artifact.