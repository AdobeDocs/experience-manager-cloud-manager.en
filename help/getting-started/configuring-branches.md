---
title: Configuring Branches
description: Learn how to set up your first branch in Git and how it is used by the CI/CD pipeline to deploy your application code.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
---

# Configure branches {#configuring-branches}

Learn how to set up your first branch in Git and how it is used by the CI/CD pipeline to deploy your application code.

## Set up your first branch in Git {#setting-up-your-first-branch-in-git}

A single, initially empty, git repository [is provisioned](/help/requirements/environment-provisioning.md) for each program onboarded in Cloud Manager. This repository can contain as many branches as your development process requires, but there must be at least one branch that is used by the CI/CD pipeline to deploy application code to stage and production. The best practice is to use `main` as the name of this branch. Conveniently, this approach is the default behavior of Git clients when setting up new projects.

For example, when setting up a new project, you run a set of commands similar to the following.

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
>It is not a requirement to use the command-line client. There are a variety of graphical Git clients available either as standalone applications or as part of an integrated development environment (IDE) such as Eclipse or IntelliJ. As long as the client application supports git using HTTPS, it should be compatible with [!UICONTROL Cloud Manager].

## Push your first branch {#pushing-your-first-branch}

When you have committed at least one revision, you can add the [!UICONTROL Cloud Manager] repository as a remote, and then push your commits to it.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>The specific URL, along with your credentials, is provided by your Adobe CSE (Customer Success Engineer) during [!UICONTROL Cloud Manager] onboarding.

## Additional branches {#additional-branches}

A single `main` branch may suffice for very simple projects, but in most cases, a more complex branching strategy is required. Many customers follow a process where day-to-day development activities are performed on a branch called `develop`. The develop branch is then merged into the `main` branch when it is time for a deployment.

>[!TIP]
>
>To view common Git commands, see the [Git Cheat Sheet](https://training.github.com/downloads/github-git-cheat-sheet).
