---
title: "Upgrade from Multiple Sitelinks to One Sitelink Per Extension"
ms.custom: na
ms.date: "08/12/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: af48f101-f2d9-44a5-892a-378d1bd593f0
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Upgrade from Multiple Sitelinks to One Sitelink Per Extension
> [!IMPORTANT]
> [!INCLUDE[sitelinks_migration_eta](../../concepts/includes/sitelinks_migration_eta.md)]

Use this guide to prepare for migration from multiple sitelinks to one sitelink per ad extension. The sections below describe what you can expect before, during, and after migration.

The pre-migration ad extension ID will be deleted and new sitelink ad extensions will be created with new IDs. Reporting data for pre-migration sitelinks will be rolled up with the new IDs.

During migration the existing campaigns, ads, and extensions will continue to run. The editorial status of the pre-migrated ad extension will be copied to the new ad extensions, so that post-migration there will be no change in status or delays to delivery.   

**Note:** It is not possible to have a "mixed mode" with both the deprecated sitelink extension type and new sitelink2 extension type in the same account. Each account will either have the deprecated type or the new type.

## <a name="getmigrationstatus"></a> Checking for Migration Status
You should use the [GetAccountMigrationStatuses](https://msdn.microsoft.com/library/bing-ads-campaign-management-getaccountmigrationstatuses.aspx) operation to determine which sitelink data model is in effect for each account. The operation will return one of the [MigrationStatus](https://msdn.microsoft.com/library/bing-ads-campaign-management-migrationstatus.aspx) values listed in the table below. The sitelink data types that you can manage depend upon the migration status. Please see [Before Migration](#beforemigration), [During Migration](#migrationinprogress), and [After Migration](#migrationcompleted) for details.  

Migration Status|Bulk Records|Campaign Management Objects  
---------|---------|---------
NotInPilot, NotStarted|[Sitelink Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-sitelink-ad-extension-record.aspx)<br/>[AdGroup Sitelink Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-sitelink-ad-extension-record.aspx)<br/>[Campaign Sitelink Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-sitelink-ad-extension-record.aspx) |[SiteLinksAdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-sitelinksadextension.aspx)<br/>[SiteLink](https://msdn.microsoft.com/library/bing-ads-campaign-management-sitelink.aspx)         
InProgress|None|None         
Completed|[Sitelink2 Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-sitelink2-ad-extension-record.aspx)<br/>[Ad Group Sitelink2 Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-sitelink2-ad-extension-record.aspx)<br/>[Campaign Sitelink2 Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-sitelink2-ad-extension-record.aspx) |[Sitelink2AdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-sitelink2adextension.aspx) 

## <a name="beforemigration"></a>Before Migration
Before migration the [GetAccountMigrationStatuses](https://msdn.microsoft.com/library/bing-ads-campaign-management-getaccountmigrationstatuses.aspx) operation will return the [MigrationStatus](https://msdn.microsoft.com/library/bing-ads-campaign-management-migrationstatus.aspx) value of either *NotInPilot* or *NotStarted*, and you can continue to add, delete, get, and update multiple sitelinks per ad extension. 

For example, when using the [Campaign Management](https://msdn.microsoft.com/library/bing-ads-campaign-management-service-reference.aspx) service to retrieve [SiteLinksAdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-sitelinksadextension.aspx) objects you should continue to use the *SiteLinksAdExtension* value of the [AdExtensionsTypeFilter](https://msdn.microsoft.com/library/bing-ads-campaign-management-adextensionstypefilter.aspx) value set when calling the [GetAdExtensionIdsByAccountId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionidsbyaccountid.aspx), [GetAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsassociations.aspx), and [GetAdExtensionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsbyids.aspx) operations. If you attempt to use the *Sitelink2AdExtension* filter, the *AdExtensionPilotNotEnabledForCustomer* error will be returned.

When using the [Bulk](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx) service you should continue to use the *SiteLinksAdExtensions*, *AdGroupSiteLinksAdExtensions*, and *CampaignSiteLinksAdExtensions* values of the [DownloadEntity](https://msdn.microsoft.com/library/bing-ads-bulk-downloadentity.aspx) value set to download the corresponding [Sitelink Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-sitelink-ad-extension-record.aspx), [AdGroup Sitelink Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-sitelink-ad-extension-record.aspx), and [Campaign Sitelink Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-sitelink-ad-extension-record.aspx) records in a Bulk file.  

> [!NOTE]
> After migration to sitelink2 ad extensions if you request a delta download where *LastSyncTimeInUTC* is set prior to the migration, and if you request *SiteLinksAdExtensions* in the download, the result file will include [Sitelink Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-sitelink-ad-extension-record.aspx) with *Status* set to *Deleted*. 

## <a name="migrationinprogress"></a>During Migration
During migration the [GetAccountMigrationStatuses](https://msdn.microsoft.com/library/bing-ads-campaign-management-getaccountmigrationstatuses.aspx) operation will return the [MigrationStatus](https://msdn.microsoft.com/library/bing-ads-campaign-management-migrationstatus.aspx) value of *InProgress*, and you will be unable to make changes to Sitelink Extensions of any data type until this is completed. From this point forward the service will not accept or return the pre-migration data types. 

## <a name="migrationcompleted"></a>After Migration
After migration the [GetAccountMigrationStatuses](https://msdn.microsoft.com/library/bing-ads-campaign-management-getaccountmigrationstatuses.aspx) operation will return the [MigrationStatus](https://msdn.microsoft.com/library/bing-ads-campaign-management-migrationstatus.aspx) value of *Completed*, and from this point forward you must use the new data model with one sitelink per ad extension. After migration the service will not accept or return the pre-migration data types. 

For example, when using the [Campaign Management](https://msdn.microsoft.com/library/bing-ads-campaign-management-service-reference.aspx) service to retrieve [Sitelink2AdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-sitelink2adextension.aspx) objects you must use the *Sitelink2AdExtension* value of the [AdExtensionsTypeFilter](https://msdn.microsoft.com/library/bing-ads-campaign-management-adextensionstypefilter.aspx) value set when calling the [GetAdExtensionIdsByAccountId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionidsbyaccountid.aspx), [GetAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsassociations.aspx), and [GetAdExtensionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsbyids.aspx) operations. If you attempt to use the *SiteLinksAdExtensions* filter, the *CampaignServiceInvalidAdExtensionType* error will be returned.

When using the [Bulk](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx) service you must use the *Sitelink2AdExtensions*, *AdGroupSitelink2AdExtensions*, and *CampaignSitelink2AdExtensions* values of the [DownloadEntity](https://msdn.microsoft.com/library/bing-ads-bulk-downloadentity.aspx) value set to download the corresponding [Sitelink2 Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-sitelink2-ad-extension-record.aspx), [Ad Group Sitelink2 Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-sitelink2-ad-extension-record.aspx), and [Campaign Sitelink2 Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-sitelink2-ad-extension-record.aspx) records in a Bulk file.  


## See Also
[Bing Ads Web Service Addresses](../../concepts/bing-ads-web-service-addresses.md)  

