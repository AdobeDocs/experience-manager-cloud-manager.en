---
title: Evaluation Phase
seo-title: Evaluation Phase
description: Learn how the Product Update wizard's evaluation phase assesses the upgrade complexity with the pattern detector.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
---

# Evaluation phase {#evaluation}

The first phase of the Product Update wizard is the **[!UICONTROL Evaluation]** phase. It runs the pattern detector within the wizard to assess upgrade complexity. At the end of this step, you can view the evaluation report.

The report checks the author instance for upgrade readiness by detecting patterns for the following:

* Rule violations in areas impacted or overwritten by the upgrade.
* It uses AEM 6.x features or APIs that are not backwards compatible and may break after the upgrade.

This report helps estimate the development effort required to upgrade to Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>To learn more about the pattern detector, see [Assessing the Upgrade Complexity with the Pattern Detector](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Run the evaluation report {#running}

The pattern detector can run in any environment. However, to increase the detection rate and avoid any slowdowns on business critical instances, Cloud Manager runs it on the staging environment of the author instance.

**To run the evaluation report:**

1. Start the wizard as described in the document [Product Update Wizard](/help/product-update-wizard/overview.md).

1. Click **[!UICONTROL Run Evaluation]**.

   ![Run evaluation](/help/assets/Run-Evaluation.png)

1. The wizard informs you of the status of your action. Notice **In progress** or **completed** as applicable when the evaluation report is being generated.

1. After the report is generated, you can click **[!UICONTROL Download report]** to save a copy.

   ![Report created](/help/assets/Evaluation-1.png)

The current Product Update wizard in Cloud Manager supports the **Evaluation** phase only. The other four phases namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon.
