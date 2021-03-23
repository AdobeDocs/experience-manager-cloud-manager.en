---
title: Configure your Release Branches
seo-title: Configure your Release Branches
description: Configure release branches in Git for AEM Cloud Manager
seo-description: Follow this page to learn on how to configure your release branches in git.
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6

feature: Git Repositories
---

# Configure your Release Branches {#configure-your-release-branches}

## Setting Up Your First Branch in Git {#setting-up-your-first-branch-in-git}

A single, initially empty, **Git Repository** is provisioned for each program on-boarded in Cloud Manager. This repository can contain as many (or as few) branches as your development process follows, but there must be at least one branch which is used by the CI/CD pipeline to deploy application code to stage and production. The best practice is to use `master` as the name of this branch. Conveniently, this is the default behavior of Git clients when setting up new projects.

For example, when setting up a new project, you will run a set of commands like this:

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>Its not a requirement to use the command-line client. There are a variety of graphical Git clients available either as standalone applications or as part of an Integrated Development Environment (IDE) such as Eclipse or IntelliJ. As long as the client application supports the Git using HTTPS, it should be compatible with [!UICONTROL Cloud Manager].

## Pushing Your First Branch {#pushing-your-first-branch}

Once you have commited at least one revision, you can add the [!UICONTROL Cloud Manager] repository as a **remote** and then push your commits to it:

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      master -> master
```

>[!NOTE]
>
>The specific URL, along with your credentials, will be provided to your by your Customer Success Engineering during [!UICONTROL Cloud Manager] onboarding.

## Additional Branches {#additional-branches}

A single `master` branch may suffice for very simple projects, but in most cases, a more complex branching strategy will be required. Many customers follow a process where day-to-day development activities are performed on a branch called `develop` and the develop branch is merged into the `master` branch when it is time for a deployment.

>[!NOTE]
>
>To view the common git commands, see the [Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
