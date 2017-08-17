---
title: "Ad Group Product Partition"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5053d872-cb6e-419d-b43a-3f2171379999
caps.latest.revision: 17
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Group Product Partition
Defines an ad group product partition that can be uploaded and downloaded in a bulk file.

You can upload *Ad Group Product Partition* records for multiple ad groups in the same bulk file, as long as the validation rules are satisfied as described in [Create a Bing Shopping Campaign with the Bulk Service](https://msdn.microsoft.com/library/bing-ads-campaign-management-bing-shopping-campaigns.aspx#bingshopping_bulkservice). For example if you are creating or modifying the tree structure, parent product partition tree nodes must be ordered ahead of the child product partition tree nodes; however, the order does not matter for non-structural changes such as updating the bid. For example if you want to update the bids without adding, deleting, or updating the tree structure, then you only need to upload the *Id*, *Parent Id*, and *Bid* fields.   

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group Product Partition* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Bid](#bid)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Custom Parameter](#customparameter)
- [Destination Url](#destinationurl)
- [Id](#id)
- [Is Excluded](#isexcluded)
- [Modified Time](#modifiedtime)
- [Parent Criterion Id](#parentcriterionid)
- [Parent Id](#parentid)
- [Product Condition 1](#productcondition1)
- [Product Value 1](#productvalue1)
- [Status](#status)
- [Sub Type](#subtype)
- [Tracking Template](#trackingtemplate)

You can download all fields of the *Ad Group Product Partition* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroupProductPartitions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would add a new ad group product partition given a valid ad group ID (*Parent Id*). 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Ad Group,Client Id,Modified Time,Bid,Name,Product Condition 1,Product Value 1,Is Excluded,Parent Criterion Id,Tracking Template,Custom Parameter
Format Version,,,,,,,,,,5,,,,,,
Ad Group Product Partition,Paused,,-1112,,,,ClientIdGoesHere,,0.5,,All,,FALSE,,,{_promoCode}=PROMO1; {_season}=summer
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroupProductPartition* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAdGroupProductPartition
var bulkAdGroupProductPartition = new BulkAdGroupProductPartition
{
    // Map properties in the Bulk file to the BiddableAdGroupCriterion or
    // NegativeAdGroupCriterion object of the Campaign Management service.
    // Use the BiddableAdGroupCriterion to set the 'Is Excluded' field in the Bulk file to True,
    // and otherwise use the NegativeAdGroupCriterion to set the 'Is Excluded' field to False.
    AdGroupCriterion = new BiddableAdGroupCriterion
    {
        // 'Parent Id' column header in the Bulk file
        AdGroupId = adGroupIdKey,
        Criterion = new ProductPartition { 
            Condition = new ProductCondition
            {
                // 'Product Value 1' column header in the Bulk file
                Attribute = null,
                // 'Product Condition 1' column header in the Bulk file
                Operand = "All",
            },
            // 'Parent Criterion Id' column header in the Bulk file
            ParentCriterionId = null
        },
        CriterionBid = new FixedBid
        {
            // 'Bid' column header in the Bulk file is only applicable for BiddableAdGroupCriterion
            Bid = new Bid
            {
                Amount = 0.50
            },
        },
        // 'Destination Url' column header in the Bulk file is only applicable for BiddableAdGroupCriterion
        DestinationUrl = null,
        // 'Id' column header in the Bulk file
        Id = null,
        // 'Status' column header in the Bulk file
        Status = AdGroupCriterionStatus.Paused,
        // 'Tracking Template' column header in the Bulk file is only applicable for BiddableAdGroupCriterion
        TrackingUrlTemplate = null,
        // 'Custom Parameter' column header in the Bulk file is only applicable for BiddableAdGroupCriterion
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

uploadEntities.Add(bulkAdGroupProductPartition);

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
The name of the ad group that contains the product partition.

**Add:** Read-only and Required  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="bid"></a>Bid
The amount to bid in the auction.

**Add:** Required if *Is Excluded* is *FALSE* and the *Sub Type* is *Unit*, and otherwise the bid is not allowed.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="campaign"></a>Campaign
The name of the campaign that contains the ad group and product partition.

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

### <a name="destinationurl"></a>Destination Url
The URL of the webpage that the user is taken to when they click the ad.

If you are currently using Destination URLs, you must eventually replace them with Tracking Templates. For more information, see [URL Tracking with Upgraded URLs](https://msdn.microsoft.com/library/bing-ads-tracking-template-urls-guide.aspx).

The URL can contain dynamic parameters such as {MatchType}. For a list of supported parameters, see the Bing Ads help article [What tracking or URL parameters can I use?](https://help.bingads.microsoft.com/#apex/3/en/56799/2).

The URL can contain a maximum of 1,024 characters. If the URL does not specify a protocol, the system uses the HTTP protocol when a user clicks the ad. If the URL specifies the HTTP protocol when you add an ad, the service will remove the http:// protocol string (the HTTP protocol string does not count against the 1,024 character limit); however, the service will not remove an HTTPS protocol string (https://) from the URL.

> [!NOTE]
> This destination URL is used if specified; otherwise, the destination URL is determined by the corresponding value of the 'Link' that you specified for the product offer in your Bing Merchant Center catalog.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] To remove the destination URL, set this field to *delete_value*. The *delete_value* keyword removes the previous setting.    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the product partition.

**Add:** Read-only  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="isexcluded"></a>Is Excluded
Determines whether the product partition represents a biddable or negative criterion. 

If set to *TRUE* it is a negative criterion, and otherwise if *FALSE* it is a biddable criterion.

**Add:** Required  
**Update:** Read-only    
**Delete:** Read-only  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentcriterionid"></a>Parent Criterion Id
The criterion identifier of the parent product partition.

> [!NOTE]
> This field is not applicable for the tree root product partition node, which has no parent.

**Add:** Read-only and Required  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the ad group that contains the product partition.

This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record.

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are adding new product partitions to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="productcondition1"></a>Product Condition 1
The condition’s operand. The operands implicitly include the equal operator. For example, you can read *Brand* as *Brand=*.

**Add:** Required  
**Update:** Read-only. You cannot update the condition or value fields. To update the conditions you must delete the product partition and add a new one.    
**Delete:** Read-only  

### <a name="productvalue1"></a>Product Value 1
The condition’s attribute value.

An attribute’s value must exactly match the value specified in the customer’s Bing Merchant Center catalog file.

For available condition and value settings, see [Bing Shopping Product Conditions](https://msdn.microsoft.com/library/bing-ads-campaign-management-bing-shopping-campaigns.aspx#conditions).

**Add:** Required  
**Update:** Read-only. You cannot update the condition or value fields. To update the conditions you must delete the product partition and add a new one.    
**Delete:** Read-only  

### <a name="status"></a>Status
The status of the product partition.

Possible values are *Active* or *Deleted*. 

**Add:** Optional. The only possible status is *Active*. If you set the status to *Deleted* it will be ignored and the returned record will have status set to *Active*.  
**Update:** Optional    
**Delete:** Required. The Status must be set to *Deleted*.

### <a name="subtype"></a>Sub Type
The type of product partition.

Possible values are *Subdivision* and *Unit*.

**Add:** Required  
**Update:** Read-only    
**Delete:** Read-only  

### <a name="trackingtemplate"></a>Tracking Template
The tracking templates can be used in tandem with the URL specified in the 'Link' field for the product offer that you submitted via the [Content API](https://msdn.microsoft.com/library/bing-ads-content-api.aspx). By combining the feed URL with the tracking template, the landing page URL is assembled where a user is directed after clicking the ad. When you use the *Tracking Template* field to update the URL parameters instead of updating them in the feed URL, the feed URL doesn't need to go through editorial review and your ads will continue to serve uninterrupted. For example if your product offer URL in the catalog feed is *http://contoso.com/*, you could specify the following tracking template: *{lpurl}?matchtype={matchtype}&device={device}*.

[!INCLUDE[validationrules_trackingurltemplate_bsc](../bulk-api/includes/validationrules-trackingurltemplate-bsc.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  


## <a name="entityperformancedata"></a>Performance Data Fields in the Bulk File
If the [DataScope Value Set](../bulk-api/datascope-value-set.md) element of the download request includes *EntityPerformanceData*, the download file will also include the following fields in this record.

The tree root *Ad Group Product Partition* record contains performance statistics for the entire tree, the *Ad Group Product Partition* record corresponding to each subdivision contains the performance statistics of all leaf nodes under it, and the *Ad Group Product Partition* record corresponding to each unit contains performance statistics only for that specific node.

> [!NOTE]
> Performance statistics returned by the Bulk and Reporting services lags behind the performance statistics that you see in the [!INCLUDE[brand](../bulk-api/includes/brand.md)] web application  by up to an hour. Please note the following differences between the [Bulk service](../bulk-api/bulk-service-reference.md) and [Reporting service](https://msdn.microsoft.com/library/bing-ads-reporting-service-reference.aspx) with respect to the freshness of the tree structure and performance statistics.
> 
> -   If you have modified your product partition tree structure within the last hour, the tree structure of your product partitions will always be up to date in the [Bulk](../bulk-api/bulk-service-reference.md) download. However, the [Bulk](../bulk-api/bulk-service-reference.md) download performance statistics may lag behind the performance statistics that you see in the [!INCLUDE[brand](../bulk-api/includes/brand.md)] web application by up to an hour. **Note:** If you have modified your product partition tree structure within the last hour, only the *Ad Group Product Partition* record for the tree root node will contain performance statistics fields such as impressions and clicks. 
> -   If you have modified your product partition tree structure within the last hour, both the performance statistics and the tree structure of your product partitions returned in a report through the [Reporting service](https://msdn.microsoft.com/library/bing-ads-reporting-service-reference.aspx) may lag behind the data that you see in the [!INCLUDE[brand](../bulk-api/includes/brand.md)] web application by up to an hour.

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
