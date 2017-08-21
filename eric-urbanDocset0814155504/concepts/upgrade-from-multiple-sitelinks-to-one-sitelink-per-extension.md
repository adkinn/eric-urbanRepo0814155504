---
title: "Upgrade from Multiple Sitelinks to One Sitelink Per Extension"
ms.custom: ""
ms.date: "08/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af48f101-f2d9-44a5-892a-378d1bd593f0
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Upgrade from Multiple Sitelinks to One Sitelink Per Extension
> [!IMPORTANT]
> [!INCLUDE[sitelinks_migration_eta](../concepts/includes/sitelinks-migration-eta.md)]

Use this guide to prepare for migration from multiple sitelinks to one sitelink per ad extension. The sections below describe what you can expect before, during, and after migration.

The pre-migration ad extension ID will be deleted and new sitelink ad extensions will be created with new IDs. Reporting data for pre-migration sitelinks will be rolled up with the new IDs.

During migration the existing campaigns, ads, and extensions will continue to run. The editorial status of the pre-migrated ad extension will be copied to the new ad extensions, so that post-migration there will be no change in status or delays to delivery.   

**Note:** It is not possible to have a "mixed mode" with both the deprecated sitelink extension type and new sitelink2 extension type in the same account. Each account will either have the deprecated type or the new type.

## <a name="getmigrationstatus"></a> Checking for Migration Status
You should use the [GetAccountMigrationStatuses](~/campaign-api/getaccountmigrationstatuses-service-operation.md) operation to determine which sitelink data model is in effect for each account. The operation will return one of the [MigrationStatus](~/campaign-api/migrationstatus-value-set.md) values listed in the table below. The sitelink data types that you can manage depend upon the migration status. Please see [Before Migration](#beforemigration), [During Migration](#migrationinprogress), and [After Migration](#migrationcompleted) for details.  

Migration Status|Bulk Records|Campaign Management Objects  
---------|---------|---------
NotInPilot, NotStarted|[Sitelink Ad Extension](~/bulk-api/sitelink-ad-extension.md)<br/>[AdGroup Sitelink Ad Extension](~/bulk-api/adgroup-sitelink-ad-extension.md)<br/>[Campaign Sitelink Ad Extension](~/bulk-api/campaign-sitelink-ad-extension.md) |[SiteLinksAdExtension](~/campaign-api/sitelinksadextension-data-object.md)<br/>[SiteLink](~/campaign-api/sitelink-data-object.md)         
InProgress|None|None         
Completed|[Sitelink2 Ad Extension](~/bulk-api/sitelink2-ad-extension.md)<br/>[Ad Group Sitelink2 Ad Extension](~/bulk-api/ad-group-sitelink2-ad-extension.md)<br/>[Campaign Sitelink2 Ad Extension](~/bulk-api/campaign-sitelink2-ad-extension.md) |[Sitelink2AdExtension](~/campaign-api/sitelink2adextension-data-object.md) 

## <a name="beforemigration"></a>Before Migration
Before migration the [GetAccountMigrationStatuses](~/campaign-api/getaccountmigrationstatuses-service-operation.md) operation will return the [MigrationStatus](~/campaign-api/migrationstatus-value-set.md) value of either *NotInPilot* or *NotStarted*, and you can continue to add, delete, get, and update multiple sitelinks per ad extension. 

For example, when using the [Campaign Management](~/campaign-api/campaign-management-service-reference.md) service to retrieve [SiteLinksAdExtension](~/campaign-api/sitelinksadextension-data-object.md) objects you should continue to use the *SiteLinksAdExtension* value of the [AdExtensionsTypeFilter](~/campaign-api/adextensionstypefilter-value-set.md) value set when calling the [GetAdExtensionIdsByAccountId](~/campaign-api/getadextensionidsbyaccountid-service-operation.md), [GetAdExtensionsAssociations](~/campaign-api/getadextensionsassociations-service-operation.md), and [GetAdExtensionsByIds](~/campaign-api/getadextensionsbyids-service-operation.md) operations. If you attempt to use the *Sitelink2AdExtension* filter, the *AdExtensionPilotNotEnabledForCustomer* error will be returned.

When using the [Bulk](~/bulk-api/bulk-service-reference.md) service you should continue to use the *SiteLinksAdExtensions*, *AdGroupSiteLinksAdExtensions*, and *CampaignSiteLinksAdExtensions* values of the [DownloadEntity](~/bulk-api/downloadentity-value-set.md) value set to download the corresponding [Sitelink Ad Extension](~/bulk-api/sitelink-ad-extension.md), [AdGroup Sitelink Ad Extension](~/bulk-api/adgroup-sitelink-ad-extension.md), and [Campaign Sitelink Ad Extension](~/bulk-api/campaign-sitelink-ad-extension.md) records in a Bulk file.  

> [!NOTE]
> After migration to sitelink2 ad extensions if you request a delta download where *LastSyncTimeInUTC* is set prior to the migration, and if you request *SiteLinksAdExtensions* in the download, the result file will include [Sitelink Ad Extension](~/bulk-api/sitelink-ad-extension.md) with *Status* set to *Deleted*. 

## <a name="migrationinprogress"></a>During Migration
During migration the [GetAccountMigrationStatuses](~/campaign-api/getaccountmigrationstatuses-service-operation.md) operation will return the [MigrationStatus](~/campaign-api/migrationstatus-value-set.md) value of *InProgress*, and you will be unable to make changes to Sitelink Extensions of any data type until this is completed. From this point forward the service will not accept or return the pre-migration data types. 

## <a name="migrationcompleted"></a>After Migration
After migration the [GetAccountMigrationStatuses](~/campaign-api/getaccountmigrationstatuses-service-operation.md) operation will return the [MigrationStatus](~/campaign-api/migrationstatus-value-set.md) value of *Completed*, and from this point forward you must use the new data model with one sitelink per ad extension. After migration the service will not accept or return the pre-migration data types. 

For example, when using the [Campaign Management](~/campaign-api/campaign-management-service-reference.md) service to retrieve [Sitelink2AdExtension](~/campaign-api/sitelink2adextension-data-object.md) objects you must use the *Sitelink2AdExtension* value of the [AdExtensionsTypeFilter](~/campaign-api/adextensionstypefilter-value-set.md) value set when calling the [GetAdExtensionIdsByAccountId](~/campaign-api/getadextensionidsbyaccountid-service-operation.md), [GetAdExtensionsAssociations](~/campaign-api/getadextensionsassociations-service-operation.md), and [GetAdExtensionsByIds](~/campaign-api/getadextensionsbyids-service-operation.md) operations. If you attempt to use the *SiteLinksAdExtensions* filter, the *CampaignServiceInvalidAdExtensionType* error will be returned.

When using the [Bulk](~/bulk-api/bulk-service-reference.md) service you must use the *Sitelink2AdExtensions*, *AdGroupSitelink2AdExtensions*, and *CampaignSitelink2AdExtensions* values of the [DownloadEntity](~/bulk-api/downloadentity-value-set.md) value set to download the corresponding [Sitelink2 Ad Extension](~/bulk-api/sitelink2-ad-extension.md), [Ad Group Sitelink2 Ad Extension](~/bulk-api/ad-group-sitelink2-ad-extension.md), and [Campaign Sitelink2 Ad Extension](~/bulk-api/campaign-sitelink2-ad-extension.md) records in a Bulk file.  


## See Also
[Bing Ads Web Service Addresses](../concepts/bing-ads-web-service-addresses.md)  

