---
title: "Dynamic Search Ad"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c878cc92-455f-4e77-8f2e-2739ee06668b
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Dynamic Search Ad
Defines a dynamic search ad that can be downloaded and uploaded in a bulk file.

With a dynamic search ads campaign, the ad title and display URL are generated automatically based on the website domain and language that you want to target.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Dynamic Search Ad* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Custom Parameter](#customparameter)
- [Editorial Appeal Status](#editorialappealstatus)
- [Editorial Location](#editoriallocation)
- [Editorial Reason Code](#editorialreasoncode)
- [Editorial Status](#editorialstatus)
- [Editorial Term](#editorialterm)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Path 1](#path1)
- [Path2](#path2)
- [Publisher Countries](#publishercountries)
- [Status](#status)
- [Text](#text)
- [Tracking Template](#trackingtemplate)

You can download all fields of the *Dynamic Search Ad* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *DynamicSearchAds* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would add a new dynamic search ad given a valid ad group ID (*Parent Id*). 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Title,Text,Display Url,Destination Url,Promotion,Device Preference,Name,App Platform,App Id,Final Url,Mobile Final Url,Tracking Template,Custom Parameter,Title Part 1,Title Part 2,Path 1,Path 2
Format Version,,,,,,,,,,,,,,5,,,,,,,,,,
Dynamic Search Ad,Active,,-1113,ParentCampaignNameGoesHere,AdGroupNameHere,ClientIdGoesHere,,,Find New Customers & Increase Sales! Start Advertising on Contoso Today.,,,,,,,,,,,{_promoCode}=PROMO1; {_season}=summer,,,seattle,shoe sale
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkDynamicSearchAd* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkDynamicSearchAd
var bulkDynamicSearchAd = new BulkDynamicSearchAd
{
    // 'Parent Id' column header in the Bulk file
    AdGroupId = adGroupIdKey,
    // 'Ad Group' column header in the Bulk file
    AdGroupName = "AdGroupNameHere",
    // 'Campaign' column header in the Bulk file
    CampaignName = "ParentCampaignNameGoesHere",
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",

    // Map properties in the Bulk file to the 
    // DynamicSearchAd object of the Campaign Management service.
    DynamicSearchAd = new DynamicSearchAd
    {
        // 'Id' column header in the Bulk file
        Id = null,
        // 'Path 1' column header in the Bulk file
        Path1 = "seattle",
        // 'Path 2' column header in the Bulk file
        Path2 = "shoe sale",
        // 'Status' column header in the Bulk file
        Status = AdStatus.Active,
        // 'Text' column header in the Bulk file
        Text = "Find New Customers & Increase Sales! Start Advertising on Contoso Today.",
        // 'Tracking Template' column header in the Bulk file
        TrackingUrlTemplate = null,
        // 'Custom Parameter' column header in the Bulk file
        UrlCustomParameters = new CustomParameters
        {
            // Each custom parameter is delimited by a semicolon (;) in the Bulk file
            Parameters = new[] {
                new CustomParameter(){
                    Key = "promoCode",
                    Value = "PROMO1"
                },
                new CustomParameter(){
                    Key = "season",
                    Value = "summer"
                },
            }
        },
    },
};

uploadEntities.Add(bulkDynamicSearchAd);

var entityUploadParameters = new EntityUploadParameters
{
    Entities = uploadEntities,
    ResponseMode = ResponseMode.ErrorsAndResults,
    ResultFileDirectory = FileDirectory,
    ResultFileName = DownloadFileName,
    OverwriteResultFile = true,
};

var uploadResultEntities = (await BulkService.UploadEntitiesAsync(entityUploadParameters)).ToList();
```

### <a name="adgroup"></a>Ad Group
The name of the ad group that contains the ad.

**Add:** Read-only and Required  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="campaign"></a>Campaign
The name of the campaign that contains the ad group and ad.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Read-only  

### <a name="customparameter"></a>Custom Parameter
Your custom collection of key and value parameters for URL tracking.

[!INCLUDE[validationrules_customparameters_bulk](../bulk-api/includes/validationrules-customparameters-bulk.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] To remove all custom parameters, set this field to *delete_value*. The *delete_value* keyword removes the previous setting. To remove a subset of custom parameters, specify the custom parameters that you want to keep and omit any that you do not want to keep. The new set of custom parameters will replace any previous custom parameter set.    
**Delete:** Read-only  

### <a name="editorialappealstatus"></a>Editorial Appeal Status
Determines whether you can appeal the issues found by the editorial review.

Possible values include *Appealable*, *AppealPending*, and *NotAppealable*. For more details, see [AppealStatus Value Set](https://msdn.microsoft.com/library/bing-ads-campaign-management-appealstatus.aspx).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editoriallocation"></a>Editorial Location
The component or property of the ad that failed editorial review. 

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialreasoncode"></a>Editorial Reason Code
A code that identifies the reason for the failure. For a list of possible reason codes, see [Editorial Failure Reason Codes](https://msdn.microsoft.com/library/bing-ads-editorialfailurereasoncodes.aspx). 

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialstatus"></a>Editorial Status
The editorial status of the ad.

Possible values include *Active*, *ActiveLimited*, *Disapproved*, and *Inactive*. For more details, see [AdEditorialStatus Value Set](https://msdn.microsoft.com/library/bing-ads-campaign-management-adeditorialstatus.aspx).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialterm"></a>Editorial Term
The term that failed editorial review.

This field will not be set if a combination of terms caused the failure or if the failure was based on a policy violation.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the ad.

**Add:** Read-only  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the ad group that contains the ad.

This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record.

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are adding new ads to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Update:** Read-only  
**Delete:** Read-only  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="path1"></a>Path 1
The first part of the optional path that will be appended to the domain portion of your display URL. The display URL e.g. *www.contoso.com* will be generated from the domain of your display URL. Then if you have specified a value for *Path 1* it will be appended to the display URL. If you have also specified a value for *Path 2*, then it will also be appended to the display URL after *Path 1*. For example if your domain is *contoso.com*, *Path 1* is set to *subdirectory1*, and *Path 2* is set to *subdirectory2*, then the URL displayed will be *www.contoso.com/subdirectory1/subdirectory2*.

The maximum input length of the path is 15 characters. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of the path is 7 characters. Although dynamic text substitution is supported for other ad types like Expanded Text ads, it is not supported for dynamic search ads.

The path cannot contain the forward slash (/) or newline (\n) characters.

If the path includes a space, it will be replaced with an underscore (_) when the ad is shown.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="path2"></a>Path 2
The second part of the optional path that will be appended to the domain portion of your display URL. The display URL e.g. *www.contoso.com* will be generated from the domain of your dynamic search ads campaign level settings. Then if you have specified a value for *Path 1* it will be appended to the display URL. If you have also specified a value for *Path 2*, then it will also be appended to the display URL after *Path 1*. For example if your domain is *contoso.com*, *Path 1* is set to *subdirectory1*, and *Path 2* is set to *subdirectory2*, then the URL displayed will be *www.contoso.com/subdirectory1/subdirectory2*.

You can only specify *Path 2* if *Path 1* is also set.

The maximum input length of the path is 15 characters. Note that for languages with double-width characters e.g. Traditional Chinese the maximum input length of the path is 7 characters. Although dynamic text substitution is supported for other ad types like Expanded Text ads, it is not supported for dynamic search ads.

The path cannot contain the forward slash (/) or newline (\n) characters. If the path includes a space, it will be replaced with an underscore (_) when the ad is shown.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="publishercountries"></a>Publisher Countries
The list of publisher countries whose editorial guidelines do not allow the specified [term](#editorialterm).

In a bulk file, the list of publisher countries are delimited with a semicolon (;).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="status"></a>Status
The status of the ad.

Possible values are *Active*, *Paused*, or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Required. The Status must be set to *Deleted*.

### <a name="text"></a>Text
The ad copy.

The text must contain at least one word.

The maximum input length of the copy is 80 characters. Note that for ad groups that use Traditional Chinese the maximum input length of the copy is 40 characters. Although dynamic text substitution is supported for other ad types like expanded text ads, it is not supported for dynamic search ads.

The text cannot contain the newline (\n) character.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="trackingtemplate"></a>Tracking Template
The tracking template to use as a default for the URL specified with FinalUrls.

[!INCLUDE[validationrules_trackingurltemplate](../bulk-api/includes/validationrules-trackingurltemplate.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  


## <a name="entityperformancedata"></a>Performance Data Fields in the Bulk File
If the [DataScope Value Set](../bulk-api/datascope-value-set.md) element of the download request includes *EntityPerformanceData*, the download file will also include the following fields in this record.

|Column Header|Description|
|-----------------|---------------|
|*Spend*|[!INCLUDE[reportcolumn_spend](../bulk-api/includes/reportcolumn-spend.md)]|
|*Impressions*|[!INCLUDE[reportcolumn_impressions](../bulk-api/includes/reportcolumn-impressions.md)]|
|*Clicks*|[!INCLUDE[reportcolumn_clicks](../bulk-api/includes/reportcolumn-clicks.md)]|
|*CTR*|[!INCLUDE[reportcolumn_ctr](../bulk-api/includes/reportcolumn-ctr.md)]|
|*Avg CPC*|[!INCLUDE[reportcolumn_averagecpc](../bulk-api/includes/reportcolumn-averagecpc.md)]|
|*Avg CPM*|[!INCLUDE[reportcolumn_averagecpm](../bulk-api/includes/reportcolumn-averagecpm.md)]|
|*Avg position*|[!INCLUDE[reportcolumn_averageposition](../bulk-api/includes/reportcolumn-averageposition.md)]|
|*Conversions*|[!INCLUDE[reportcolumn_conversions](../bulk-api/includes/reportcolumn-conversions.md)]|
|*CPA*|[!INCLUDE[reportcolumn_costperconversion](../bulk-api/includes/reportcolumn-costperconversion.md)]|


