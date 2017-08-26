---
title: "Ad Group"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7dff0d14-3738-4a05-bc91-622374d22467
caps.latest.revision: 36
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Group
Defines an ad group that can be uploaded and downloaded in a bulk file.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Ad Rotation](#adrotation)
- [Bid Adjustment](#bidadjustment)
- [Bid Strategy Type](#bidstrategytype)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Content Bid](#contentbid)
- [Content Network](#contentnetwork)
- [Custom Parameter](#customparameter)
- [End Date](#enddate)
- [Id](#id)
- [Inherited Bid Strategy Type](#inheritedbidstrategytype)
- [Language](#language)
- [Modified Time](#modifiedtime)
- [Network Distribution](#networkdistribution)
- [Parent Id](#parentid)
- [Pricing Model](#pricingmodel)
- [Remarketing Targeting Setting](#remarketingtargetingsetting)
- [Search Bid](#searchbid)
- [Search Network](#searchnetwork)
- [Start Date](#startdate)
- [Status](#status)
- [Tracking Template](#trackingtemplate)

You can download all fields of the *Ad Group* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroups* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new ad group if the correct campaign Id would be provided. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Start Date,End Date,Network Distribution,Pricing Model,Ad Rotation,Search Network,Search Bid,Content Network,Content Bid,Language,Bid Adjustment,Name,Tracking Template,Custom Parameter,Bid Strategy Type,Remarketing Targeting Setting
Format Version,,,,,,,,,,,,,,,,,,,5,,,,
Ad Group,Active,,-111,ParentCampaignNameGoesHere,Women's Red Shoe Sale,ClientIdGoesHere,,11/5/2017,12/31/2018,OwnedAndOperatedAndSyndicatedSearch,,RotateAdsEvenly,On,0.1,Off,,English,10,,http://tracker.example.com/?season={_season}&promocode={_promocode}&u={lpurl},{_promoCode}=PROMO1; {_season}=summer,ManualCpc,TargetAndBid
```


If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroup* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAdGroup
var bulkAdGroup = new BulkAdGroup
{
    // 'Campaign' column header in the Bulk file
    CampaignName = "ParentCampaignNameGoesHere",
    // 'Parent Id' column header in the Bulk file
    CampaignId = campaignIdKey,
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",
                  
    // Map properties in the Bulk file to the 
    // AdGroup object of the Campaign Management service.
    AdGroup = new AdGroup
    {
        // 'Search Network' or 'Content Network' column header in the Bulk file
        AdDistribution = AdDistribution.Search,
        // 'Ad Rotation' column header in the Bulk file
        AdRotation = new AdRotation
        {
            Type = AdRotationType.RotateAdsEvenly
        },
        // The AdGroup.BiddingModel property is not supported in the Bulk file.
        BiddingModel = BiddingModel.Keyword,
        // 'Bid Strategy Type' column header in the Bulk file
        BiddingScheme = new ManualCpcBiddingScheme { },
        // 'Content Bid' column header in the Bulk file
        ContentMatchBid = null,
        // 'End Date' column header in the Bulk file
        EndDate = new Microsoft.BingAds.V11.CampaignManagement.Date
        {
            Month = 12,
            Day = 31,
            Year = DateTime.UtcNow.Year + 1
        },
        // 'Id' column header in the Bulk file
        Id = null,
        // 'Language' column header in the Bulk file
        Language = "English",
        // 'Ad Group' column header in the Bulk file
        Name = "Women's Red Shoe Sale",
        // 'Bid Adjustment' column header in the Bulk file
        NativeBidAdjustment = 10,
        // 'Network Distribution' column header in the Bulk file
        Network = Network.OwnedAndOperatedAndSyndicatedSearch,
        // 'Pricing Model' column header in the Bulk file
        PricingModel = null,
        // 'Remarketing Targeting Setting' column header in the Bulk file
        RemarketingTargetingSetting = RemarketingTargetingSetting.TargetAndBid,
        // 'Search Bid' column header in the Bulk file
        SearchBid = new Bid
        {
            Amount = 0.10
        },
        // 'Start Date' column header in the Bulk file
        StartDate = new Microsoft.BingAds.V11.CampaignManagement.Date
        {
            Month = DateTime.UtcNow.Month,
            Day = DateTime.UtcNow.Day,
            Year = DateTime.UtcNow.Year
        },
        // 'Status' column header in the Bulk file
        Status = AdGroupStatus.Paused,
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

uploadEntities.Add(bulkAdGroup);

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
The name of the ad group.

The name must be unique among all active ad groups within the campaign. The name can contain a maximum of 128 characters.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="adrotation"></a>Ad Rotation
Determines how often you'd like the ads in your ad group to show in relation to one another. If you have multiple ads within an ad group, your ads will rotate because no more than one ad from your account can show at a time.

> [!NOTE]
> This feature is not supported for ad groups in Bing Shopping campaigns.

Possible values are *OptimizeForClicks* and *RotateAdsEvenly*.

If set to *OptimizeForClicks*, [!INCLUDE[brand](../bulk-api/includes/brand.md)] will predominantly show ads that have the highest click-through rate (CTR).

If set to *RotateAdsEvenly*, [!INCLUDE[brand](../bulk-api/includes/brand.md)] will rotate between your ads on an equal basis. That is, each ad in a particular ad group has an equal chance of being displayed in response to a searcher's query. Sometimes the ads that get the highest CTR are not the ads that get the highest conversions. Using *RotateAdsEvenly*, you can help ensure that ads with a higher CTR don't unintentionally get precedence over ads with a higher conversion rate. Also if you want to test new ad copy, using *RotateAdsEvenly* can help ensure that those new ads get an opportunity to be displayed, even if you have other ads within the same ad group that have an established and higher CTR performance history.

**Add:** Optional. The default value is *OptimizeForClicks*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="bidadjustment"></a>Bid Adjustment
The percent amount by which to adjust your bid for native ads above or below the base ad group or keyword bid.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

Supported values are negative one hundred (-100) through positive nine hundred (900). Setting the bid adjustment to -100 percent will prevent native ads from showing for this ad group.

Set this field to zero (0) if you do not want any bid adjustment for native ads. If this field is empty you will inherit the *Bid Adjustment* setting of the ad group's [Campaign](../bulk-api/campaign.md).

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] If the ad group already has a native bid adjustment, and you want to remove it to effectively inherit the *Bid Adjustment* setting of the ad group's [Campaign](../bulk-api/campaign.md), set this field to *delete_value*. The *delete_value* keyword removes the previous setting.   
**Delete:** Read-only  

### <a name="bidstrategytype"></a>Bid Strategy Type
The bid strategy type for how you want to manage your bids. For ad groups you can use either of the *InheritFromParent* or *ManualCpc* bid strategy types. 

[!INCLUDE[autobid_alert](../bulk-api/includes/autobid-alert.md)]

[!INCLUDE[tip_biddingscheme](../bulk-api/includes/tip-biddingscheme.md)]

> [!NOTE]
> For campaigns of type *Shopping* the product partitions inherit the ad group *Bid Strategy Type*, and you must be in the Bing Shopping Enhanced CPC pilot. The pilot ID is 340.

**Add:** Optional. If you do not set this field, then *InheritFromParent* is used by default.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="campaign"></a>Campaign
The name of the campaign that contains the ad group.

**Add:** Read-only and Required  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Campaign* field.

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Read-only  

### <a name="contentbid"></a>Content Bid
The bid to use when the keywords that the service extracts from the content page and the ad group's keywords match by using an exact match comparison. An exact match results when all of the words in the keyword exactly match the user's query.
    
> [!NOTE]
> This feature is not supported for ad groups in Bing Shopping campaigns or Dynamic Search Ads campaigns.

The minimum and maximum bid range depends on the account's currency. For more information, see [Currencies](~/concepts/currencies.md)

You can set a content bid if the *Content Network* ad distribution channel is set to *On*.

Specifying a content match bid at the keyword level overrides the ad group's content match bid value.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="contentnetwork"></a>Content Network
Determines whether the ads within this ad group will be displayed on the content distribution channel.

> [!NOTE]
> The content ad distribution channel is not supported for ad groups in Bing Shopping campaigns or Dynamic Search Ads campaigns.

> [!IMPORTANT]
> Bing Ads no longer serves ads on the content network. Starting July 30th, 2017 you won't be able to set the Content ad distribution either. If you try to add or update an ad group with ad distribution set only to Content, the *CampaignServiceAdGroupMediumNotAllowedForDistributionChannel* error will be returned.  If you try to add or update an ad group with ad distribution set to both Search and Content, the operation will succeed, however the ad distribution will be stored as Search only. By end of Q3 calendar 2017, Bing Ads will migrate the remaining Content ad groups to Search only. Then when you retrieve the ad groups which were previously set to Search and Content or Content
only, the ad distribution will be Search only.  

Set the value *On* for ad distribution on the content network, and otherwise set the value *Off*.

The *Content Network* and *Search Network* fields each partially map to the *AdDistribution* element of the [AdGroup](~/campaign-api/adgroup-data-object.md) object. The *AdDistribution* element can contain one or both network values, whereas in the Bulk file schema there are two seperate fields for determining the network.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="customparameter"></a>Custom Parameter
Your custom collection of key and value parameters for URL tracking.

[!INCLUDE[validationrules_customparameters_bulk](../bulk-api/includes/validationrules-customparameters-bulk.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] To remove all custom parameters, set this field to *delete_value*. The *delete_value* keyword removes the previous setting. To remove a subset of custom parameters, specify the custom parameters that you want to keep and omit any that you do not want to keep. The new set of custom parameters will replace any previous custom parameter set.    
**Delete:** Read-only  

### <a name="enddate"></a>End Date
The date that the ads in the ad group will expire.

If you do not specify an end date, the ads will not expire. The end date can be extended to make an ad group's ads eligible for delivery, even after the ad group expires.

The end date is inclusive. For example, if you set *End Date* to 12/31/2020, the ads in the ad group will expire at 11:59 PM on 12/31/2020. The time is based on the time zone that you specify at the campaign level.

**Add:** Optional. To set no end date when adding an ad group, do not set this field.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] To delete the existing end date setting, and effectively set no end date when updating an ad group, set this field to a date equal to or later than January 2, 2050. When you retrieve the ad group next time, this field will be empty i.e. it will not be set to January 2, 2050.    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the ad group.

**Add:** Optional. You must either leave this field empty, or specify a negative identifier. A negative identifier set for the ad group can then be referenced in the *Parent Id* field of dependent record types such as ads, keywords, or criterion. This is recommended if you are adding new ad groups and new dependent records in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="inheritedbidstrategytype"></a>Inherited Bid Strategy Type
The bid strategy type that is inherited from the parent campaign. This value is equal to the parent campaign's *Bid Strategy Type* field. Possible values are *EnhancedCpc*, *ManualCpc*, *MaxClicks*, *MaxConversions*, and *TargetCpa*.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="language"></a>Language
The ad group language.

For possible values, see the Language column within [Ad Languages](~/concepts/ad-languages.md)

> [!IMPORTANT]
> Support for multiple languages at the campaign level is in pilot. If languages are set at both the ad group and campaign level, the ad group-level language will override the campaign-level language. The customer is enabled for the pilot if the [GetCustomerPilotFeatures](~/customer-api/getcustomerpilotfeatures-service-operation.md) response includes pilot number *310*. Pilot participants will be able to set multiple languages at the campaign level, and will be able to delete the ad group level language by setting this field to *delete_value*. The *delete_value* keyword removes the previous setting. If you leave this field nil, then the ad group language will not be updated. If your application depends on ad group language being set, then you must prepare for the possibility that ad group language will be nil. More specific dates and implementation details will be provided later through the [Bing Ads API Blog](https://blogs.msdn.microsoft.com/bing_ads_api/), and in the meantime you should update your application right away to support the change. 

**Add:** Optional if the campaign has one or more languages set, and otherwise language is required.  
**Update:** Optional if the customer is in the *Campaign Languages* pilot, and otherwise update is not allowed. If you are not in the pilot and try to change the language during update, no error will be returned and the setting will not be changed.  
**Delete:** Read-only  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="networkdistribution"></a>Network Distribution
The search networks where you want your ads to display.

Possible values are *OwnedAndOperatedAndSyndicatedSearch*, *OwnedAndOperatedOnly*, and *SyndicatedSearchOnly*. The default is *OwnedAndOperatedAndSyndicatedSearch*.

You must not set *Network Distribution* if the *Content Network* ad distribution channel is set to *On*, otherwise an error will be returned.

If you select one of the syndicated search options, you can call the [SetNegativeSitesToAdGroups](~/campaign-api/setnegativesitestoadgroups-service-operation.md) or [SetNegativeSitesToCampaigns](~/campaign-api/setnegativesitestocampaigns-service-operation.md) operation to prevent the ads from displaying on specific syndicated search websites.

**Add:** Optional. The default is *OwnedAndOperatedAndSyndicatedSearch*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the campaign that contains the ad group.

This bulk field maps to the *Id* field of the [Camnpaign](../bulk-api/campaign.md) record.

**Add:** Read-only and Required. You must either specify an existing campaign identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Campaign](../bulk-api/campaign.md) record. This is recommended if you are adding new ad groups to a new campaign in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Campaign* field.
  
### <a name="pricingmodel"></a>Pricing Model
The only supported pricing model in [!INCLUDE[brand](../bulk-api/includes/brand.md)] is based on cost per click (CPC).

With *CPC*, each time the user clicks your ad, the service charges your account based on your bid. The actual charge is based on the auction results and may be less than your bid value.

> [!NOTE]
> This field is deprecated and will be removed in a future version of the Bing Ads API.

**Add:** Optional. The pricing model will be set to *CPC* by default.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]  
**Delete:** Read-only  

### <a name="remarketingtargetingsetting"></a>Remarketing Targeting Setting
The targeting setting that is applicable for all audiences e.g., custom audiences and remarketing lists that are associated with this ad group. Each audience can be associated with multiple ad groups, and each ad group's remarketing targeting setting is applied independently for delivery.

Possible values are *TargetAndBid* and *BidOnly*. 

Set this field to *TargetAndBid* if you want to show ads only to people included in the audience, with the option to change the bid amount. Ads in this ad group will only show to people included in the audience.

Set this field to *BidOnly* if you want to show ads to people searching for your ad, with the option to change the bid amount for people included in the audience. Ads in this ad group can show to everyone but the bid adjustment will apply to people included in the audience.

**Add:** Optional. The default value is *BidOnly*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="searchbid"></a>Search Bid
The default bid to use when the user's query and the ad group's keywords match by using either a broad, exact, or phrase match comparison.

The minimum and maximum bid range depends on the account's currency. For more information, see [Currencies](~/concepts/currencies.md).

You can set a search bid if the *Search Network* ad distribution channel is set to *On*.

Specifying a broad, exact, or phrase match bid at the keyword level overrides the ad group's search bid value for the corresponding match type.

**Add:** Optional. If you do not set a bid, it will be set to the minimum depending on your account's currency.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="searchnetwork"></a>Search Network
Determines whether the ads within this ad group will be displayed on the search distribution channel.

Set the value *On* for ad distribution on the search network, and otherwise set the value *Off*.

The *Content Network* and *Search Network* fields each partially map to the *AdDistribution* element of the [AdGroup](~/campaign-api/adgroup-data-object.md) object. The *AdDistribution* element can contain one or both network values, whereas in the Bulk file schema there are two seperate fields for determining the network.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="startdate"></a>Start Date
The date that the ads in the ad group can begin serving; otherwise, the service can begin serving the ads in the ad group the day that the ad group becomes active.

The start date cannot be updated after the ad group is submitted.

The start date is inclusive. For example, if you set *Start Date* to 11/5/2017, the ads in the ad group will start at 12:00 AM on 11/5/2017. The time is based on the time zone that you specify at the campaign level.

**Add:** Optional. If you do not set the start date, then it will default to today's date and the service can begin serving the ads in the ad group as soon as the ad group status is active.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="status"></a>Status
The status of the ad group.

Possible values are *Active*, *Deleted*, *Expired*, and *Paused*. The *Expired* status is read-only.

**Add:** Optional. The default value is *Paused*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Required. The Status must be set to Deleted.

### <a name="trackingtemplate"></a>Tracking Template
The tracking template to use as a default for all URLs in your ad group.

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

## <a name="qualityscore"></a>Quality Score Fields in the Bulk File
If the [DataScope Value Set](../bulk-api/datascope-value-set.md) element of the download request includes *QualityScore*, the download file will also include the following fields in this record.

|Column Header|Description|
|-----------------|---------------|
|*Quality Score*|[!INCLUDE[reportcolumn_qualityscore](../bulk-api/includes/reportcolumn-qualityscore.md)]|
|*Keyword Relevance*|[!INCLUDE[reportcolumn_keywordrelevance](../bulk-api/includes/reportcolumn-keywordrelevance.md)]|
|*Landing Page Relevance*|[!INCLUDE[reportcolumn_landingpagerelevance](../bulk-api/includes/reportcolumn-landingpagerelevance.md)]|
|*Landing Page User Experience*|[!INCLUDE[reportcolumn_landingpageuserexperience](../bulk-api/includes/reportcolumn-landingpageuserexperience.md)]|
