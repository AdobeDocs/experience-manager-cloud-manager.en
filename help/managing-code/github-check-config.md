---
title: Pull Request Checks for Private Repositories
description: Learn how to control the pipelines that are created automatically to validate each pull request to a private repository.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
---
# Pull request checks for private repositories {#github-check-config}

<!--OLD TITLE THAT I THOUGHT WAS BETTER Check configuration for private repositories -->

Learn how to control the pipelines that are created automatically to validate each pull request to a private repository.

## Configuration of private repository checks {#configuration}

When using [private repositories](private-repositories.md#using), a [full stack code quality pipeline](/help/overview/ci-cd-pipelines.md) is created automatically. This pipeline is started at each pull request update. 

You can control these checks by creating a `.cloudmanager/pr_pipelines.yml` file in the default branch of the private repository.

```yaml
pullRequest:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR
    importantMetricsFailureBehavior: CONTINUE
```

| Parameter | Possible Values | Default | Description |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` or `false` | `false` | Whether to keep only the last comment with the code scanning results on this GitHub pull request or keep all. |
| `type` | `CI_CD` | n/a | Defines the behavior of a CI/CD pipeline. |
| `template.programID` | Integer | No pipeline variables are reused | You can reuse the [pipeline variables](/help/getting-started/build-environment.md#pipeline-variables) set on an existing pipeline, which each PR creates automatically. |
| `template.pipelineID` | Integer | No pipeline variables are reused | You can reuse the [pipeline variables](/help/getting-started/build-environment.md#pipeline-variables) set on an existing pipeline, which each PR creates automatically. |
| `namePrefix` | String |`Full Stack Code Quality Pipeline for PR` | Used to set the name of the pipeline that is created automatically. |
| `importantMetricsFailureBehavior` | `CONTINUE` or `FAIL` or `PAUSE` | `CONTINUE` | Sets the important metric behavior of the pipeline<br>`CONTINUE` = If an important metric fails, the pipeline moves forward automatically<br>`FAIL` = The pipeline finishes with a FAILED status if an important metric fails<br>`PAUSE` = The code scanning step receives a WAITING status when an important metric fails and must be manually resumed. |
