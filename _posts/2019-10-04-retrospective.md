---
layout: post
comments: true
title: Process - Using Retrospective Extension in Azure DevOps
gh-repo: devtks/devtks.github.io
gh-badge: [star, fork, follow]
tags: [tuto, tutorial, process, azure-devops]
---

Project Retrospective... You know the thing we rarely do but when we do it gets lost in nature in a Word Document or some other type of one time, never read again type of document. 
At TKS we are trying to use the full potential of Azure Devops by using features like Boards, Pipeline among several others. We thought it would be nice to have a retrospective that sits within the project artifacts and is accessible by anyone at any time.

This guide will help you to use a plugin available in Azure Devops, that will allow you to gather feedback from your team, your clients in order to vote, plan and create actionable items.


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

Very easy step. On the top right corner of your Azure Devops page, you can click on the extension icon and `Browse marketplace`

![](/img/retrospective/browsemarketplace.PNG)

Then search for Retrospective (in my case it is on the homepage because it is one of the featured extensions)

![](/img/retrospective/store.PNG)

You should land on this page https://marketplace.visualstudio.com/items?itemName=ms-devlabs.team-retrospectives



Click on `Get it Free`

![](/img/retrospective/getitfree.PNG)

Select your company or if you have a server, download the plugin.


![](/img/retrospective/selectcompany.png)

When you navigate to one of your projects you should see a retrospective menu under "Boards".


![](/img/retrospective/myproject.PNG)

![](/img/retrospective/newmeny.PNG)

# Create a Retrospective

## Choose you audience

You may want to do your retrospectives internally, or with your client. Some information may be sensitive so it could be valuable to you clean the feedback before involving your client or external parties. 

This is why the first thing you do is to select your team. It will determine who can see you retrospective.

Example:

![](/img/retrospective/choosingteam.PNG)



## Create a new Board

You can create a new board by choosing several options. Giving the opportunity to people to give their feedback anonymously or adding a maximum of 4 columns.

![](/img/retrospective/newboard.PNG)

In my example, I am doing a mid project retrospective. Keeping the 2 default columns but adding a 3rd one "What should we start"

![](/img/retrospective/newmidprojectboard.PNG)

Welcome to your new board !! It should look like this.

![](/img/retrospective/firstboard.PNG)

# Collect Feedback

It is now time to tell your team, client or whoever's feedback you want. It will show cards under each categories.


![](/img/retrospective/cards.PNG)

# Group Feedback

You might end with similar or identical feedback from multiple team members. The extension gives you the ability to group them.

Example:


![](/img/retrospective/toomanyemails.PNG)

Click on the 3 dots -> Group Feedback


![](/img/retrospective/group.PNG)

Then search the ticket you want to group with


![](/img/retrospective/search.PNG)

Once you click on it you will see your card with `items`


![](/img/retrospective/2items.PNG)

You can expand it and see the other related feedback.

![](/img/retrospective/2itemsextended.PNG)

# Vote for feedback

Now your items are grouped and your board is clean and organized. You can ask your team or client to vote for the items they agree with or think are most important.

Each member can give any number of votes per item they want.

It would give a good understanding of what items are considered important

![](/img/retrospective/votes.PNG)

At any time feedback can be deleted. 

That is your choice... removing feedback that didn't have any votes for example.

# Act

Everything mentioned above has led to this important moment, as now this can be done without a meeting which is time and productivity win.

Now that it is time to gather everyone (or not), this is the phase were you can review, create items or action items base on feedback.

You have 2 possible views for this

**Board view**

![](/img/retrospective/boardview.PNG)

**Focus view**
it allows to go through the feedback one by one, which can be convenient for your final retrospective meeting to stay `focus`.

![](/img/retrospective/focus.PNG)

You will notice the text speaks for itself.

Time to create actionable work items.

ex: 
stack was fun?

![](/img/retrospective/createtask.PNG)

Then a task can be created to make a reusable template.

![](/img/retrospective/createnewtemplate.PNG)

# Track your progress

Once you are done, you can come back anytime  and check if any actions items were created, who was assigned to them and are they completed etc.
![](/img/retrospective/resume.PNG)

![](/img/retrospective/progress.PNG)

# Conclusion

This plugin can be very useful to archive and follow up on project retrospective. If your are using Azure DevOps is it a nice way to keep precious feedback along your project artifact. If you wish to learn more or have any questions for our development team here at TKS please don't hesitate to visit TKS.ca or email info@tks.ca anytime. 