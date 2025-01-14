---
ms.date: 08/11/2023
title: "Overview: Migrate Google Workspace to Microsoft 365 with Migration Manager"
ms.reviewer: 
ms.author: jhendr
author: JoanneHendrickson
manager: jtremper
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.service: microsoft-365-migration
ms.localizationpriority: high
ms.collection: 
- m365solution-migratetom365
- m365solution-scenario
- M365-collaboration
- SPMigration
- highpri
- m365initiative-migratetom365
ms.custom: admindeeplinkSPO
search.appverid: MET150
description: Overview of how to migrate from Google Workspace to Microsoft 365 with Migration Manager.
---

# Migrate Google Workspace to Microsoft 365 with Migration Manager

Collaborate all in one place by migrating your Google Workspace documents, data, and users to OneDrive, SharePoint, and Teams in Microsoft 365. 


## How does it work?

- **Step 1:** [Connect to Google](mm-google-step1-connect.md).   Sign in to your Google account and add the Microsoft 365 migration app to your Google Workspace account custom apps. 
- **Step 2:** [Scan and assess](mm-google-step2-scan-assess.md). Google Drive accounts are scanned automatically for you. Once the scans are complete, download the generated reports and logs to investigate any possible issues that might block your migration.
- **Step 3:** [Copy to Migrations list](mm-google-step3-copy-to-migrations.md). After a Google Drive has been scanned and determined ready, add them to your migration list.
- **Step 4:** [Review destination paths](mm-google-step4-review-destinations.md).  We automatically map source paths to any exactly matching destination paths. Ensure content is being copied to the right place by reviewing and modifying as needed for each destination path.
- **Step 5:** [Map identities](mm-google-step5-map-identities.md).   Map your groups and users in Google Drive to an account in Microsoft 365 to migrate your Google Drive permission settings.
- **Step 6:** [Migrate and Monitor](mm-google-step6-migrate-monitor.md). After reviewing your migration setup, migrate your Google accounts and monitor the progress.

>[!Tip]
>Watch this video to help get started:  [Migrate Google files to Microsoft 365 with Migration Manager](https://youtu.be/GZ4kTX31U-A)


## Get started

To get started:

Go to the Migration overview page in the **Microsoft Admin Center** or Migration Manager in the **SharePoint Admin center.** Sign in with an account that has [admin permissions](/sharepoint/sharepoint-admin-role) for your organization.

Make sure that you have:

- **Access to the destination**: You must either be a global admin or OneDrive/SharePoint admin to the Microsoft 365 tenant where you want to migrate your content. 

- **Access to the source**: Have Google account credentials that have read access to any Google user account you plan to migrate.

- **Prerequisites installed:** Make sure you have the necessary prerequisites installed.

## Google Shared Drives

Google Shared drives can now be discovered and migrated normally. Google Shared Drive permissions are migrated according to what you have set in Project settings, under [general permission setting](/sharepointmigration/mm-project-settings-permissions#migrate-permissions). 

Folder permissions are migrated by default. File permissions are migrated on demand. 

We recommend the following steps when migrating permissions in your shared drive:

- Recreate a Microsoft 365 group with the same memberships as the Google Drive group. You can either create a new group or edit the group linked to the Team site designated as the migration destination for the Google Shared Drive.
- In the 'Map Identities' setting, map the original Google Drive group of the shared drive to the Microsoft 365 group.


## What isn't migrated

Google doesn't allow us to export these items from Drive:

- Google Drawings
- Google Sites
- Google Maps
- Google Forms

### Docs, Slides, and Sheets

Google's proprietary formats aren't compatible with anything other than a Google Workspace Drive. When migrating from Google Workspace, Google export API converts to the Microsoft Office format from Google's format.

|Google format|Office format|
|:-----|:-----|
|.gsheet|.xlsx|
|.gdoc|.docx|
|.gslide|.pptx|


> [!Note]
> The only way to migrate/download a Google format file is to request that they [Google] facilitate it. Microsoft does not control the conversion process, and the forced limitations are strictly on Google's end.
### File size of Google proprietary files

Google only started calculating the size of its proprietary files, including Google Docs, Sheets, Forms, and Slides, on May 2, 2022. Any Google proprietary files created and modified **before** May 2, 2022 won't include file size in the metadata info we get from the API calls. As a result, all Google proprietary files created before May 2, 2022 default to a scanned size of 1 byte and are reported as such in our *ScanSummary report*.

### Files marked as restricted

Google Workspace/Drive lets owners disable the ability for users to copy, download, or print a file on a per-file basis. To work properly, this feature must be disabled on each file for which it has been enabled. If not disabled, this error will appear:

`Permissions issue: File marked as restricted or not copyable`

To disable this feature:

1. See the **Sharing** settings for a file, and select **Advanced**. 
2. Select the checkbox for the owner of the file to **Disable options to download, print, and copy for commenters and viewers.**
    
### What happens to Google Drive shortcuts?

Shortcut files aren't supported for migration and therefore not migrated.

## File size migration limit

We support files up to 15 GB in size for Google to Microsoft 365 migrations.


>[!NOTE]
>
>Migration Manager Google isn't available for users of Office 365 operated by 21Vianet in China.
>
>Google migration is not available for users of the Government Cloud, including GCC, Consumer, GCC High, or DoD.

