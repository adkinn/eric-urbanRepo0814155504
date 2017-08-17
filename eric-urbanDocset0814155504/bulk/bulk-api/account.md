---
title: "Account"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f14ec426-086e-47ae-8c5b-a22f468d2cdf
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Account
Defines an account that can be uploaded and downloaded in a bulk file.   

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Account* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Id](#id)
- [MSCLKID Auto Tagging Enabled](#msclkidautotaggingenabled)
- [Parent Id](#parentid)
- [Sync Time](#synctime)
- [Tracking Template](#trackingtemplate)

The *Account* record is included in the Bulk download file automatically everytime you call the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. 

### <a name="id"></a>Id
The system generated identifier of the account.

> [!IMPORTANT]
> The Bing Ads Bulk API only supports one account per file. This field is ignored during upload, and effectively set to the account ID that is specified in the [GetBulkUploadUrl](https://msdn.microsoft.com/library/bing-ads-bulk-getbulkuploadurl.aspx) service request.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="msclkidautotaggingenabled"></a>MSCLKID Auto Tagging Enabled
You might want to enable auto-tagging of MSCLKID for tracking leads via offline conversion goals. If auto-tagging of MSCLKID is enabled, the MSCLKID is automatically appended to the landing page URL when a customer clicks on your ad. For example, *www.contoso.com/?msclkid={msclkid}*. The click ID is unique for each ad click and multiple clicks on the same ad from the same user will result in multiple click IDs.

If the value is *True*, then the MSCLKID auto tagging feature is enabled. Otherwise the MSCLKID auto tagging feature is not enabled.

> [!IMPORTANT]
> Every time you create a new [OfflineConversionGoal](https://msdn.microsoft.com/library/bing-ads-campaign-management-offlineconversiongoal.aspx) via either the Bing Ads web application or Campaign Management API, the *MSCLKID Auto Tagging Enabled* field is set to *True* automatically. For more information, see [Tracking offline conversions](https://help.bingads.microsoft.com/#apex/3/en/help:app54554/1/en-US/#ext:ConversionTracking_Load).

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the customer that contains the account.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  
 

### <a name="synctime"></a>Sync Time
Where the Account row intersects with the Sync Time column, the field value is represented as **MM/DD/YYYY HH:MM**, or month, day, year, hour, and minute relative to the UTC time zone. Save this value and use it with the bulk service to only get the changes between the current and the next download.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  


### <a name="trackingtemplate"></a>Tracking Template
The tracking template to use as a default for all URLs in your account.

[!INCLUDE[validationrules_trackingurltemplate](../bulk-api/includes/validationrules-trackingurltemplate.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  



