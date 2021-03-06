---
title: "Ad Group Dynamic Search Ad Target"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb32fd26-1513-45a5-b303-f3ecc81ab99b
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Group Dynamic Search Ad Target
Defines an Ad Group Dynamic Search Ad Target that can be uploaded and downloaded in a bulk file.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group Dynamic Search Ad Target* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Bid](#bid)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Custom Parameter](#customparameter)
- [Dynamic Ad Target Condition 1](#dynamicadtargetcondition1)
- [Dynamic Ad Target Condition 2](#dynamicadtargetcondition2)
- [Dynamic Ad Target Condition 3](#dynamicadtargetcondition3)
- [Dynamic Ad Target Value 1](#dynamicadtargetvalue1)
- [Dynamic Ad Target Value 2](#dynamicadtargetvalue2)
- [Dynamic Ad Target Value 3](#dynamicadtargetvalue3)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Name](#name)
- [Parent Id](#parentid)
- [Status](#status)
- [Tracking Template](#trackingtemplate)

You can download all fields of the *Ad Group Dynamic Search Ad Target* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroupDynamicSearchAdTargets* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new ad group dynamic search ad target given a valid ad group ID (*Parent Id*). 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Bid,Name,Tracking Template,Custom Parameter,Dynamic Ad Target Condition 1,Dynamic Ad Target Condition 2,Dynamic Ad Target Condition 3,Dynamic Ad Target Value 1,Dynamic Ad Target Value 2,Dynamic Ad Target Value 3
Format Version,,,,,,,,,5,,,,,,,,
Ad Group Dynamic Search Ad Target,Paused,,-1113,,,ClientIdGoesHere,,0.5,Bulk Ad Group Dynamic Search Ad Target,,{_promoCode}=PROMO1; {_season}=summer,Url,Category,PageContent,contoso.com,US/CA/SFO,flowers
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroupDynamicSearchAdTarget* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAdGroupDynamicSearchAdTarget
var bulkAdGroupDynamicSearchAdTarget = new BulkAdGroupDynamicSearchAdTarget
{
    // Map properties in the Bulk file to the 
    // BiddableAdGroupCriterion object of the Campaign Management service.
    AdGroupCriterion = new BiddableAdGroupCriterion
    {
        // 'Parent Id' column header in the Bulk file
        AdGroupId = adGroupIdKey,
        Criterion = new Webpage
        {
            Parameter = new WebpageParameter
            {
                // Set Conditions null if you want to target all webpages
                Conditions = new []
                {
                    new WebpageCondition
                    {
                        // 'Dynamic Ad Target Value 1' column header in the Bulk file
                        Argument = "contoso.com",
                        // 'Dynamic Ad Target Condition 1' column header in the Bulk file
                        Operand = WebpageConditionOperand.Url
                    },
                    new WebpageCondition
                    {
                        // 'Dynamic Ad Target Value 2' column header in the Bulk file
                        Argument = "US/CA/SFO",
                        // 'Dynamic Ad Target Condition 2' column header in the Bulk file
                        Operand = WebpageConditionOperand.Category
                    },
                    new WebpageCondition
                    {
                        // 'Dynamic Ad Target Value 3' column header in the Bulk file
                        Argument = "flowers",
                        // 'Dynamic Ad Target Condition 3' column header in the Bulk file
                        Operand = WebpageConditionOperand.PageContent
                    },
                },
                // 'Name' column header in the Bulk file
                CriterionName = "Bulk Ad Group Dynamic Search Ad Target"
            }
        },
        CriterionBid = new FixedBid
        {
            // 'Bid' column header in the Bulk file
            Bid = new Bid
            {
                Amount = 0.50
            }
        },
        // 'Id' column header in the Bulk file
        Id = null,
        // 'Status' column header in the Bulk file
        Status = AdGroupCriterionStatus.Paused,
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
    // 'Ad Group' column header in the Bulk file
    AdGroupName = null,
    // 'Campaign' column header in the Bulk file
    CampaignName = null,
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",
};

uploadEntities.Add(bulkAdGroupDynamicSearchAdTarget);

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
The name of the ad group that contains the dynamic ad target (webpage criterion).

**Add:** Read-only and Required  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="bid"></a>Bid
The amount to bid in the auction.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="campaign"></a>Campaign
The name of the campaign that contains the ad group and dynamic ad target (webpage criterion).

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

### <a name="dynamicadtargetcondition1"></a>Dynamic Ad Target Condition 1
The first of up to 3 webpage condition operands. The condition is met if the webpage property that is referenced by this field contains or equals the *Dynamic Ad Target Value 1* value.

Possible values include *Category*, *PageContent*, *PageTitle*, and *Url*.

**Add:** Optional. If you do not set any of the dynamic ad target condition or value fields, then you are effectively targeting all webpages. You can only have one dynamic ad target per ad group for all webpages.  
**Update:** Not allowed. You cannot update the dynamic ad target condition or value fields. To update the webpage conditions you must delete the dynamic ad target and add a new one.    
**Delete:** Read-only  

### <a name="dynamicadtargetcondition2"></a>Dynamic Ad Target Condition 2
The second of up to 3 webpage condition operands. The condition is met if the webpage property that is referenced by this field contains or equals the *Dynamic Ad Target Value 2* value.

Possible values include *Category*, *PageContent*, *PageTitle*, and *Url*.

**Add:** Optional. If you do not set any of the dynamic ad target condition or value fields, then you are effectively targeting all webpages. You can only have one dynamic ad target per ad group for all webpages.  
**Update:** Not allowed. You cannot update the dynamic ad target condition or value fields. To update the webpage conditions you must delete the dynamic ad target and add a new one.    
**Delete:** Read-only  

### <a name="dynamicadtargetcondition3"></a>Dynamic Ad Target Condition 3
The third of up to 3 webpage condition operands. The condition is met if the webpage property that is referenced by this field contains or equals the *Dynamic Ad Target Value 1* value.

Possible values include *Category*, *PageContent*, *PageTitle*, and *Url*.

**Add:** Optional. If you do not set any of the dynamic ad target condition or value fields, then you are effectively targeting all webpages. You can only have one dynamic ad target per ad group for all webpages.  
**Update:** Not allowed. You cannot update the dynamic ad target condition or value fields. To update the webpage conditions you must delete the dynamic ad target and add a new one.    
**Delete:** Read-only  

### <a name="dynamicadtargetvalue1"></a>Dynamic Ad Target Value 1
The first of up to 3 webpage condition or criterion arguments.

You can set this string to the URL, category, page title, or page content for your site. For example if the *Dynamic Ad Target Condition 1* field is set to *Url*, then you might set this field to *contoso.com/flowers*.

**Add:** Optional. If you do not set any of the dynamic ad target condition or value fields, then you are effectively targeting all webpages. You can only have one dynamic ad target per ad group for all webpages.  
**Update:** Not allowed. You cannot update the dynamic ad target condition or value fields. To update the webpage conditions you must delete the dynamic ad target and add a new one.    
**Delete:** Read-only  

### <a name="dynamicadtargetvalue2"></a>Dynamic Ad Target Value 2
The second of up to 3 webpage condition or criterion arguments.

You can set this string to the URL, category, page title, or page content for your site. For example if the *Dynamic Ad Target Condition 2* field is set to *Url*, then you might set this field to *contoso.com/flowers*.

**Add:** Optional. If you do not set any of the dynamic ad target condition or value fields, then you are effectively targeting all webpages. You can only have one dynamic ad target per ad group for all webpages.  
**Update:** Not allowed. You cannot update the dynamic ad target condition or value fields. To update the webpage conditions you must delete the dynamic ad target and add a new one.    
**Delete:** Read-only  

### <a name="dynamicadtargetvalue3"></a>Dynamic Ad Target Value 3
The third of up to 3 webpage condition or criterion arguments.

You can set this string to the URL, category, page title, or page content for your site. For example if the *Dynamic Ad Target Condition 3* field is set to *Url*, then you might set this field to *contoso.com/flowers*.

**Add:** Optional. If you do not set any of the dynamic ad target condition or value fields, then you are effectively targeting all webpages. You can only have one dynamic ad target per ad group for all webpages.  
**Update:** Not allowed. You cannot update the dynamic ad target condition or value fields. To update the webpage conditions you must delete the dynamic ad target and add a new one.    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the dynamic ad target (webpage criterion).

**Add:** Read-only  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="name"></a>Name
The criterion name that you can use to identify the criteria, for example you can filter or sort alphabetically.

The criterion name length must be between 1 to 2048, inclusive.

**Add:** Optional. If you do not specify any name, by default the name will be set to a concatenated list of conditions. Each condition will be delimited by the *and* keyword. For example if the conditions are a) *Url contains flower* , b) *Url contains book* , and c) *PageContent contains seattle*, then the default criterion name will be *Url contains flower and Url contains book and PageContent contains seattle*. If all condition and value fields are empty, then you are effectively targeting all webpages and the name will be set to *All Webpages*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] If you specify the *delete_value* keyword, then the criterion name will be updated to the default value i.e. either *All Webpages* or a concatenated list of criterions.  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the ad group that contains the dynamic ad target (webpage criterion).

This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record.

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are adding new dynamic ad targets to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only  
**Delete:** Read-only  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="status"></a>Status
The status of the dynamic ad target (webpage criterion).

Possible values are *Active*, *Paused*, or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Required. The Status must be set to *Deleted*.

### <a name="trackingtemplate"></a>Tracking Template
Tracking templates can be used in tandem with the landing page URL that is generated dynamically from the domain that you specified for your Dynamic Search Ads campaign. By combining the domain with the tracking template, the landing page URL is assembled where a user is directed after clicking the ad. 

[!INCLUDE[validationrules_trackingtemplate_dsa](../bulk-api/includes/validationrules-trackingtemplate-dsa.md)]

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

