---
date: 2024-12-03
authors: [jonasbirkelof]
categories:
  - Development
---

# Workflows for Git branches

There are no rules for how to use branches, it's up for you to decide based on your needs and preferences. There are however some ways the industry use branches that makes development easier. 

<!-- more -->

## The permanent development branch

Before we visit the better practises, let's first discuss a practise that is not that great. It is common for developers to have a permanent **development** branch where all development for a new version of the project is pushed to. When the work in the development branch is finished it is merged with the **master** branch but is not deleted afterwards. All the developers will then pull the development branch and continue from there.

The problem with this approach is that when the development branch is merged with the master branch, a commit for the merge is created on the master branch (but not on the development branch). This means that the master branch will always be one commit ahead of the development branch which will make them out of sync. There are ways to solve this but it's not really worth the effort when there are better solutions.

## Temporary development branches

The solution is to use temporary development branches that the developer will push code to when working on a specific feature or issue. When the work is done, the development branch is merged into an upcomming version branch and is then deleted. The upcomming version branch will then be merged into the major version branch or master branch (depending on the use case) and is also then deleted. Any new feature or issue is then developed using new branches that are cloned or forked from the major or upcoming version branch.

If you don't want to share the progress to the public, you can `fork` the branch you want to develop, push to that copy and then make a pull request to the upcomming or major version branch when you are done.

## Option 1: Version branches

Let's say you have an application that is version **2.0.0** that has an older version (**1.1.0**) that still needs to be maintained with bug fixes. Version 1.x might be needed for older operating systems for instance. This means that you must keep the source code for that version somehow so that you can clone or fork it.

By having a branch for every major version of the application called **1.x** and **2.x** you can clone or fork the version you want to develop at any time without messing with the other version. One developer can work on bug fixes for version 1.x and another can work on a new feature for version 2.x.

You do not push anything to the master branch but do not delete it. Do not make changes directly to the upcomming version branch!

This kind of workflow can look something like this:

<div class="steps" markdown>

1. Create a branch called **2.0.1** based on the **2.x** branch. This is the upcomming version branch.

1. Create a branch for the new feature or issue you will be working on. Name it **feature**, **issue-001** or something descriptive (not just "feature"...).

1. When the feature development is finished, merge the **feature** branch with the upcomming version branch **2.0.1** and delete the feature branch. 

1. When the version 2.0.1 development is finished and is ready to be released, merge the **2.0.1** branch with the **2.x** branch and delete the upcomming version branch.

1. Make a new release based on the **2.x** branch. 

1. The **2.x** branch will now contain the latest version of your application and there will be a release for the latest version (2.0.1) where the source code can be downloaded as a zip file.

1. When a new version **2.0.2** is being developed, repeat this process.

</div>

An example of a project that uses this workflow is [Font Awesome](https://github.com/FortAwesome/Font-Awesome).

| Branch name | Description                                                                        |
| ----------- | ---------------------------------------------------------------------------------- |
| master      | Not in use, do not delete!                                                         |
| 2.x         | The latest version of the code (set to default branch).                            |
| 1.x         | The latest legacy version of the code.                                             |
| 2.0.1       | Upcomming version. Push changes to it, then merge with 2.x, then delete.           |
| issue-001   | Development for issue 001. Push changes to it, then merge with 2.0.1, then delete. |

The branch that your visitors will see by default when they visit you repository is the **master** branch. You will probably want to change this to the latest version branch (**2.x**). You do that by going to **Settings > General > Default branch** and select the branch you want to set as default.

## Option 2: Master branch

Let's say you have a website that only has one version which is the one in production. You do not have to maintain legacy versions of the code. In this case you store the production code in the **master** branch and just like the approach with major version branches, you use temporary branches for the development. 

You can still use semantic versioning for the code to keep track of progress if you like. On smaller projects, or if you work alone, you can skip the upcomming version branch and create a temporary development branch directly from the master branch and then merge back into the master branch when you are done.

Do not make changes directly to the master branch or upcomming version branch!

This kind of workflow can look something like this:

<div class="steps" markdown>

1. Create a branch called **2.0.1** based on the **master** branch. This is the upcomming version branch.

1. Create a branch for the new feature or issue you will be working on. Name it **feature**, **issue-001** or something descriptive (not just "feature"...).

1. When the feature development is finished, merge the **feature** branch with the upcomming version branch **2.0.1** and delete the feature branch. 

1. When the version 2.0.1 development is finished, merge the **2.0.1** branch with the **master** branch and delete the upcomming version branch.

1. The **master** branch will now contain the latest version of your website.

1. When a new version is being developed, repeat this process.

</div>

!!! tip

	On smaller projects, or if you work alone, you can skip the upcomming version branch and create a temporary development branch directly from the master branch and then merge back into the master branch when you are done.

An example of a project that uses this workflow is [Bootstrap](https://github.com/twbs/bootstrap).

| Branch name | Description                                                                        |
| ----------- | ---------------------------------------------------------------------------------- |
| master      | Not in use, do not delete!                                                         |
| 2.0.1       | Upcomming version. Push changes to it, then merge with 2.x, then delete.           |
| issue-001   | Development for issue 001. Push changes to it, then merge with 2.0.1, then delete. |