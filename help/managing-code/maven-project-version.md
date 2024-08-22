---
title: Maven Project Version Handling
description: Learn how Maven handles project versioning in Cloud Manager.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
---

# Maven project version handling {#project-version}

Learn how Maven handles project versioning in Cloud Manager.

## How Maven handles project versions {#how-maven}

For staging and production deployments, Cloud Manager generates a unique, incrementing version. 

This version is seen on the pipeline execution details page and the activity page. When a build is run, the Maven project is updated to use this version. A tag is created in the Git repository with that version as its name. 

If the original project version meets certain criteria, the updated Maven project version merges both the original project version and the Cloud Manager generated version. The tag, however, always uses the generated version. For this merging to occur, the original project version must be formed with exactly three version segments, for example, `1.0.0` or `1.2.3`, but not `1.0` or `1`, and the original version must not end in `-SNAPSHOT`. 

>[!NOTE]
>
>This original project version value must be statically set in the `<version>` element of the top-level `pom.xml` file in the Git repository branch.

If the original version meets these criteria, then the generated version is appended to the original version as a new version segment. The generated version is also slightly modified to include proper sorting and version handling. For example, assuming a generated version of `2019.926.121356.0000020490`:

| Version | Version in `pom.xml` | Comment |
| --- | --- | --- |
| `1.0.0` |  `1.0.0.2019_0926_121356_0000020490` |  Properly formed original version |
| `1.0.0-SNAPSHOT` |  `2019.926.121356.0000020490`  |  Snapshot version, overwritten | 
| `1` |  `2019.926.121356.0000020490` |  Incomplete version, overwritten | 

>[!NOTE]
>
>Whether or not the original version was integrated into the Cloud Manager-initialized version, it is still accessible as a Maven property named `cloudManagerOriginalVersion`.
