---
title: "Keyword"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: acadbada-e9a6-464f-897d-ad1c64ea4f85
caps.latest.revision: 18
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Keyword
Defines a keyword that can be downloaded and uploaded in a bulk file.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Keyword* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Bid](#bid)
- [Bid Strategy Type](#bidstrategytype)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Custom Parameter](#customparameter)
- [Destination Url](#destinationurl)
- [Editorial Appeal Status](#editorialappealstatus)
- [Editorial Location](#editoriallocation)
- [Editorial Reason Code](#editorialreasoncode)
- [Editorial Status](#editorialstatus)
- [Editorial Term](#editorialterm)
- [Final Url](#finalurl)
- [Id](#id)
- [Inherited Bid Strategy Type](#inheritedbidstrategytype)
- [Keyword](#keyword)
- [Match Type](#matchtype)
- [Mobile Final Url](#mobilefinalurl)
- [Modified Time](#modifiedtime)
- [Param1](#param1)
- [Param2](#param2)
- [Param3](#param3)
- [Parent Id](#parentid)
- [Publisher Countries](#publishercountries)
- [Status](#status)
- [Tracking Template](#trackingtemplate)

You can download all fields of the *Keyword* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *Keywords* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new keyword given a valid ad group ID (*Parent Id*). 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Keyword,Match Type,Bid,Param1,Param2,Param3,Name,Final Url,Mobile Final Url,Tracking Template,Custom Parameter,Bid Strategy Type
Format Version,,,,,,,,,,,,,,5,,,,,
Keyword,Active,,-1111,ParentCampaignNameGoesHere,AdGroupNameHere,ClientIdGoesHere,,red shoes,Broad,0.5,,,,,http://www.contoso.com/womenshoesale,http://mobile.contoso.com/womenshoesale,,{_promoCode}=PROMO1; {_season}=summer,ManualCpc
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkKeyword* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkKeyword
var bulkKeyword = new BulkKeyword
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
    // Keyword object of the Campaign Management service.
    Keyword = new Keyword
    {
        // 'Bid' column header in the Bulk file
        Bid = new Bid
        {
            Amount = 0.50,
        },
        // 'Bid Strategy Type' column header in the Bulk file
        BiddingScheme = new ManualCpcBiddingScheme { },
        // 'Destination Url' column header in the Bulk file
        DestinationUrl = null,
        // 'Mobile Final Url' column header in the Bulk file
        FinalMobileUrls = new[] {
            // Each Url is delimited by a semicolon (;) in the Bulk file
            "http://mobile.contoso.com/womenshoesale"
        },
        // 'Final Url' column header in the Bulk file
        FinalUrls = new[] {
            // Each Url is delimited by a semicolon (;) in the Bulk file
            "http://www.contoso.com/womenshoesale"
        },
        // 'Id' column header in the Bulk file
        Id = null,
        // 'Match Type' column header in the Bulk file
        MatchType = MatchType.Broad,
        // 'Param 1 column header in the Bulk file
        Param1 = null,
        // 'Param 2' column header in the Bulk file
        Param2 = null,
        // 'Param 3' column header in the Bulk file
        Param3 = null,
        // 'Status' column header in the Bulk file
        Status = KeywordStatus.Active,
        // 'Text' column header in the Bulk file
        Text = "red shoes",
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

uploadEntities.Add(bulkKeyword);

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
The name of the ad group that contains the keyword.

**Add:** Read-only and Required  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="bid"></a>Bid
The bid to use when the user's search term and the keyword match.

**Add:** Optional. If you do not specify a keyword level bid, the [Ad Group](../bulk-api/ad-group.md) bid for the corresponding search or content match type will be used. For more information, see [Budget and Bid Strategies](~/concepts/budget-and-bid-strategies.md).  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]  
**Delete:** Read-only  

### <a name="bidstrategytype"></a>Bid Strategy Type
The bid strategy type for how you want to manage your bids. For keywords you can use either of the *InheritFromParent* or *ManualCpc* bid strategy types. If you do not set this field, then *InheritFromParent* is used by default.

[!INCLUDE[autobid_alert](../bulk-api/includes/autobid-alert.md)]

[!INCLUDE[tip_biddingscheme](../bulk-api/includes/tip-biddingscheme.md)]

> [!NOTE]
> The *Bid Strategy Type* field is not supported for Bing Shopping campaigns.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="campaign"></a>Campaign
The name of the campaign that contains the keyword.

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
The URL of the webpage to take the user to when they click the ad. The keyword's destination URL is used if specified; otherwise, the ad's destination URL is used.

> [!IMPORTANT]
> If you are currently using Destination URLs, you must eventually replace them with Final URLs. For more information, see [URL Tracking with Upgraded URLs](~/concepts/url-tracking-with-upgraded-urls.md).

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]     
**Delete:** Read-only  

### <a name="editorialappealstatus"></a>Editorial Appeal Status
Determines whether you can appeal the issues found by the editorial review.

Possible values include *Appealable*, *AppealPending*, and *NotAppealable*. For more details, see [AppealStatus Value Set](~/campaign-api/appealstatus-value-set.md).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editoriallocation"></a>Editorial Location
The component or property of the keyword that failed editorial review. 

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialreasoncode"></a>Editorial Reason Code
A code that identifies the reason for the failure. For a list of possible reason codes, see [Editorial Failure Reason Codes](~/concepts/bing-ads-editorial-failure-reason-codes.md). 

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialstatus"></a>Editorial Status
The editorial status of the keyword.

Possible values include *Active*, *ActiveLimited*, *Disapproved*, and *Inactive*. For more details, see [KeywordEditorialStatus Value Set](~/campaign-api/keywordeditorialstatus-value-set.md).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="editorialterm"></a>Editorial Term
The term that failed editorial review.

This field will not be set if a combination of terms caused the failure or if the failure was based on a policy violation.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="finalurl"></a>Final Url
The landing page URL. The keyword's final URL is used if specified; otherwise, the ad's final URL is used.

[!INCLUDE[validationrules_finalurls_bulk](../bulk-api/includes/validationrules-finalurls-bulk.md)] 

Also note that  if the *Tracking Template* or *Custom Parameter* fields are set, then the *Final Url* field is required.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the keyword.

**Add:** Read-only  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="inheritedbidstrategytype"></a>Inherited Bid Strategy Type
The bid strategy type that is inherited from the parent campaign or ad group. This value is equal to the parent campaign or ad group's *Bid Strategy Type* field. Possible values are *EnhancedCpc*, *ManualCpc*, *MaxClicks*, *MaxConversions*, and *TargetCpa*.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="keyword"></a>Keyword
The keyword text.

The text can contain a maximum of 100 characters.

You should specify the keyword in the locale of the Language value that you specified for the ad group to which the keyword belongs.

If the *Match Type* is Broad, your application should handle broad match modifiers. Broad match modified keywords can be modified or prefixed with a plus sign (+), to require that specific terms in your keyword be present in the search query. In the download file, broad match modified terms are preceded by an extra space character. For example if the keyword text is "+Hawaii +hotel", the text included in the bulk download file is " +Hawaii +hotel". For bulk upload you may specify the keyword with or without the preceding space. For more information about broad match modifiers, see [Budget and Bid Strategies](~/concepts/budget-and-bid-strategies.md).

**Add:** Required  
**Update:** Optional    
**Delete:** Read-only

### <a name="matchtype"></a>Match Type
The type of match to compare the keyword and the user's search term.

The supported match type values for a keyword are *Broad*, *Exact* and *Phrase*.

**Add:** Required  
**Update:** Read-only    
**Delete:** Read-only  

### <a name="mobilefinalurl"></a>Mobile Final Url
The mobile landing page URL. The keyword's final mobile URL is used if specified; otherwise, the ad's final mobile URL is used.

[!INCLUDE[validationrules_finalurls_bulk](../bulk-api/includes/validationrules-finalurls-bulk.md)] 

Also note that if the TrackingUrlTemplate or UrlCustomParameters element are set, then at least one final URL is required.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
**Delete:** Read-only  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="param1"></a>Param1
The string to use as the substitution value in an ad if the ad's title, text, display URL, or destination URL contains the {Param1} dynamic substitution string.

> [!NOTE]
> Although you can use {Param1} to specify an ad's destination URL, you are encouraged not to. Instead, you should set the keyword's DestinationUrl element.

The string can contain a maximum of 1,022 characters. The actual limit depends on the length of the element that references the substitution string. For example, the length of a text ad's title can contain a maximum of 25 characters.

When implementing dynamic text in your ad copy you should provide a default string e.g. {Param1:default} that the system will use if Param1 for a keyword is null or empty, or if including the Param1 substitution value will cause the expanded string to exceed the element's limit; otherwise the ad will not serve with this keyword. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](https://help.bingads.microsoft.com/#apex/3/en/50811/1).

Also note that if the ad group only has one ad, and if that ad uses {Param1} but does not provide a default string e.g. {Param1:default}, then you must supply a valid Param1 value for that substitution. Otherwise this keyword cannot be added or updated.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
**Delete:** Read-only  

### <a name="param2"></a>Param2
The string to use as the substitution value in an ad if the title, text, display URL, or destination URL contains the {Param2} dynamic substitution string.

Typically, you use the {Param2} substitution string in the title or text (ad copy description) elements of an ad.

The string can contain a maximum of 70 characters. The actual limit depends on the length of the element that references the substitution string. For example, the length of a text ad's title can contain a maximum of 25 characters.

When implementing dynamic text in your ad copy you should provide a default string e.g. {Param2:default} that the system will use if Param2 for a keyword is null or empty, or if including the Param2 substitution value will cause the expanded string to exceed the element's limit; otherwise the ad will not serve with this keyword. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](https://help.bingads.microsoft.com/#apex/3/en/50811/1).

Also note that if the ad group only has one ad, and if that ad uses {Param2} but does not provide a default string e.g. {Param2:default}, then you must supply a valid *Param2* value for that substitution. Otherwise this keyword cannot be added or updated. 

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
**Delete:** Read-only  

### <a name="param3"></a>Param3
The string to use as the substitution value in an ad if the title, text, display URL, or destination URL contains the {Param3} dynamic substitution string.

Typically, you use the {Param3} substitution string in the title or text (ad copy description) elements of an ad.

The string can contain a maximum of 70 characters. The actual limit depends on the length of the element that references the substitution string. For example, the length of a text ad's title can contain a maximum of 25 characters.

When implementing dynamic text in your ad copy you should provide a default string e.g. {Param3:default} that the system will use if Param3 for a keyword is null or empty, or if including the Param3 substitution value will cause the expanded string to exceed the element's limit; otherwise the ad will not serve with this keyword. For more information, see the Bing Ads help article [Automatically customize your ads with dynamic text parameters](https://help.bingads.microsoft.com/#apex/3/en/50811/1).

Also note that if the ad group only has one ad, and if that ad uses {Param3} but does not provide a default string e.g. {Param3:default}, then you must supply a valid *Param3* value for that substitution. Otherwise this keyword cannot be added or updated. 

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the ad group that contains the keyword.

This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record.

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are adding new keywords to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only  
**Delete:** Read-only  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="publishercountries"></a>Publisher Countries
The list of publisher countries whose editorial guidelines do not allow the specified [term](#editorialterm).

In a bulk file, the list of publisher countries are delimited with a semicolon (;).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="status"></a>Status
The status of the keyword.

Possible values are *Active*, *Paused*, *Inactive*, or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Required. The Status must be set to *Deleted*.

### <a name="trackingtemplate"></a>Tracking Template
The tracking template to use as a default for the URL specified with FinalUrls.

[!INCLUDE[validationrules_trackingurltemplate](../bulk-api/includes/validationrules-trackingurltemplate.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_delete_all](../bulk-api/includes/update-optional-delete-all.md)]    
**Delete:** Read-only  

## <a name="bidsuggestionsdata"></a>Bid Suggestions Data Fields in the Bulk File
If the requested download [DataScope Value Set](../bulk-api/datascope-value-set.md) includes *BidSuggestionsData*, the download file will also include the following record types for each corresponding keyword.
* [Keyword Best Position Bid](../bulk-api/keyword-best-position-bid.md)
* [Keyword Main Line Bid](../bulk-api/keyword-main-line-bid.md)
* [Keyword First Page Bid](../bulk-api/keyword-first-page-bid.md)

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

## <a name="qualityscore"></a>Quality Score Fields in the Bulk File
If the [DataScope Value Set](../bulk-api/datascope-value-set.md) element of the download request includes *QualityScore*, the download file will also include the following fields in this record.

|Column Header|Description|
|-----------------|---------------|
|*Quality Score*|[!INCLUDE[reportcolumn_qualityscore](../bulk-api/includes/reportcolumn-qualityscore.md)]|
|*Keyword Relevance*|[!INCLUDE[reportcolumn_keywordrelevance](../bulk-api/includes/reportcolumn-keywordrelevance.md)]|
|*Landing Page Relevance*|[!INCLUDE[reportcolumn_landingpagerelevance](../bulk-api/includes/reportcolumn-landingpagerelevance.md)]|
|*Landing Page User Experience*|[!INCLUDE[reportcolumn_landingpageuserexperience](../bulk-api/includes/reportcolumn-landingpageuserexperience.md)]|
