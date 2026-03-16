---
title: Work with Multiple Git Repositories
description: Instead of directly working with Cloud Manager's Git repository, learn how you can work with your own Git repository or multiple Git repositories.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a

---
# Work with multiple source Git repositories {#working-with-multiple-source-git-repos} 

Instead of directly working with Cloud Manager's Git repository, learn how you can work with your own Git repository or multiple Git repositories.

## Sync customer-managed Git repositories {#syncing-customer-managed-git-repositories}

To keep Cloud Manager's Git repository up-to-date, set up an automated synchronization process if you are using your own repository or repositories.

Depending on where your Git repository is hosted, a GitHub action or a continuous integration solution like Jenkins could be used to set up the automation. With an automation in place, every push to your own repository can be automatically forwarded to Cloud Manager's Git repository.

While such an automation for a single customer-owned Git repository is straightforward, configuring it for multiple repositories requires a more involved initial setup. The contents from multiple Git repositories need to be mapped to different directories within a single Cloud Manager's Git repository. Cloud Manager's Git repository needs to be provisioned with a root Maven `pom.xml`, listing the different sub projects in the modules section 

Below is a sample `pom.xml` for two customer-owned Git repositories. The first project is put into the directory named `project-a`, and the second project is put into the directory named `project-b`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
  
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
  
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
  
</project>
```

Such a root `pom.xml` is pushed to a branch in Cloud Manager's Git repository. Then the two projects must be set up to forward changes to Cloud Manager's Git repository automatically. 

For example, a push to a branch in project A can trigger a GitHub action. The action checks out project A and the Cloud Manager Git repository. It copies all contents from project A into the `project-a` directory of Cloud Manager's Git repository. Then it commits and pushes the change.

For example, a change on the `main` branch in project A is automatically pushed to the `main` branch in Cloud Manager's Git repository. Of course, there could be a mapping between branches like a push to a branch named `dev` in project A is pushed to a branch named `development` in Cloud Manager's Git repository. Similar steps are required for Project B.

Depending on the branching strategy and workflows, the syncing can be configured for different branches. If the used Git repository does not provide a concept similar to GitHub actions, an integration by way of Jenkins (or similar) is possible as well. In this case, a webhook triggers a Jenkins job that does the work.

Do the following to add a new (third) source or repository:

1. Add a new GitHub action to the new repository that pushes changes from that repository to Cloud Manager's Git repository.
1. Perform that action at least once to ensure that project code is in Cloud Manager's Git repository.
1. Add a reference to the new directory in the root Maven `pom.xml` of the Cloud Manager Git repository.

## Sample GitHub action {#sample-github-action}

A push to the `main` branch triggers this sample GitHub action, which then pushes into a subdirectory of Cloud Manager's Git repository. The GitHub actions need to be provided with two secrets, `MAIN_USER` and `MAIN_PASSWORD`, to be able to connect and push to Cloud Manager's Git repository.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

As shown above, using a GitHub action is flexible. Any mapping between branches of the Git repositories can be performed and any mapping of the separate Git projects into the directory layout of the main project.

>[!NOTE]
>
>The above script uses `git add` to update the repository, which assumes that removals are included. Depending on the default configuration of Git, this requirement may need to be replaced with `git add --all`.

## Sample Jenkins job {#sample-jenkins-job}

This script is a sample that can be used in a Jenkins job or similar. A change in a Git repository triggers it. The Jenkins job checks out the latest state of that project or branch and then triggers this script.

This script in turn checks out Cloud Manager's Git repository and commits the project code to a subdirectory.

The Jenkins job needs to be provided with two secrets, `MAIN_USER` and `MAIN_PASSWORD`, to be able to connect and push to Cloud Manager's Git repository.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

As shown above, using a Jenkins job is very flexible. Any mapping between branches of the Git repositories can be performed and any mapping of the separate Git projects into the directory layout of the main project.

>[!NOTE]
>
>The above script uses `git add` to update the repository, which assumes that removals are included. Depending on the default configuration of Git, `git add` may need to be replaced with `git add --all`.
