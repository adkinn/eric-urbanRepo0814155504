---
title: "Campaign"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16416f5f-2a3b-47e6-bf3a-524ceed4d578
caps.latest.revision: 39
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Campaign
Defines a campaign that can be uploaded and downloaded in a bulk file. 

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Campaign* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

|Column Header|Supported Campaign Types|
|-----------------|---------------|
|[Bid Adjustment](#bidadjustment)|All|
|[Bid Strategy MaxCpc](#bidstrategymaxcpc)|SearchAndContent<br>DynamicSearchAds|
|[Bid Strategy TargetCpa](#bidstrategytargetcpa)|SearchAndContent<br>DynamicSearchAds|
|[Bid Strategy Type](#bidstrategytype)|All|
|[Budget](#budget)|All|
|[Budget Id](#budgetid)|All|
|[Budget Name](#budgetname)|All|
|[Budget Type](#budgettype)|All|
|[Campaign](#campaign)|All|
|[Campaign Type](#campaigntype)|All|
|[Client Id](#clientid)|All|
|[Country Code](#countrycode)|Shopping|
|[Domain Language](#domainlanguage)|DynamicSearchAds|
|[Id](#id)|All|
|[Language](#language)|All|
|[LocalInventoryAdsEnabled](#language)|Shopping|
|[Modified Time](#modifiedtime)|All|
|[Parent Id](#parentid)|All|
|[Priority](#priority)|Shopping|
|[Status](#status)|All|
|[Store Id](#storeid)|Shopping|
|[Time Zone](#timezone)|All|
|[Tracking Template](#trackingtemplate)|All|
|[Website](#website)|DynamicSearchAds|

You can download all fields of the *Campaign* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *Campaigns* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would add one campaign of each type i.e. Search and Content, Shopping, and Dynamic Search Ads campaign. 

```csv
Type,Status,Id,Parent Id,Campaign,Website,Client Id,Modified Time,Time Zone,Budget Id,Budget Name,Budget,Budget Type,Bid Adjustment,Name,Country Code,Store Id,Campaign Type,Priority,Tracking Template,Custom Parameter,Bid Strategy Type,Domain Language
Format Version,,,,,,,,,,,,,,5,,,,,,,,
Campaign,Active,-111,0,SearchAndContent 2/6/2017 4:11:11 PM,,ClientIdGoesHere,,PacificTimeUSCanadaTijuana,,,50,DailyBudgetStandard,10,,,,SearchAndContent,,,{_promoCode}=PROMO1; {_season}=summer,EnhancedCpc,
Campaign,Active,-111,0,Shopping 2/6/2017 4:11:11 PM,,ClientIdGoesHere,,PacificTimeUSCanadaTijuana,,,50,DailyBudgetStandard,10,,US,39807,Shopping,0,,{_promoCode}=PROMO1; {_season}=summer,,
Campaign,Active,-111,0,DynamicSearchAds 2/6/2017 4:11:11 PM,contoso.com,ClientIdGoesHere,,PacificTimeUSCanadaTijuana,,,50,DailyBudgetStandard,10,,,,DynamicSearchAds,,,{_promoCode}=PROMO1; {_season}=summer,EnhancedCpc,EN
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkCampaign* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

for(int i = 0; i < 3; i++)
{
    // Map properties in the Bulk file to the BulkCampaign
    var bulkCampaign = new BulkCampaign
    {
        // 'Parent Id' column header in the Bulk file
        AccountId = 0,
        // 'Client Id' column header in the Bulk file
        ClientId = "ClientIdGoesHere",
        // 'Modified Time' column header in the Bulk file is read-only
        // LastModifiedTime cannot be set in the Bulk entity

        // Map properties in the Bulk file to the 
        // Campaign object of the Campaign Management service.
        Campaign = new Campaign
        {
            // 'Bid Strategy Type' column header in the Bulk file
            BiddingScheme = new EnhancedCpcBiddingScheme { },
            // 'Budget Id' column header in the Bulk file
            BudgetId = null,
            // 'Budget Type' column header in the Bulk file
            BudgetType = BudgetLimitType.DailyBudgetStandard,
            // 'Campaign Type' column header in the Bulk file
            CampaignType = null,
            // 'Budget' column header in the Bulk file
            DailyBudget = 50,
            // 'Description' column header in the Bulk file
            Description = "Red shoes line.",
            // 'Id' column header in the Bulk file
            Id = campaignIdKey,
            // 'Language' column header in the Bulk file
            Languages = null,
            // 'Campaign' column header in the Bulk file
            Name = "Women's Shoes " + DateTime.UtcNow,
            // 'Bid Adjustment' column header in the Bulk file
            NativeBidAdjustment = 10,
            // 'Settings are not applicable for the SearchAndContent campaign type
            Settings = null,
            // 'Status' column header in the Bulk file
            Status = CampaignStatus.Active,
            // 'Time Zone' column header in the Bulk file
            TimeZone = "PacificTimeUSCanadaTijuana",
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

    uploadEntities.Add(bulkCampaign);
}

// Set properties specific to the SearchAndContent campaign type
((BulkCampaign)uploadEntities[0]).Campaign.Name = "SearchAndContent " + DateTime.UtcNow;
((BulkCampaign)uploadEntities[0]).Campaign.CampaignType = CampaignType.SearchAndContent;

// Set properties specific to the Shopping campaign type
((BulkCampaign)uploadEntities[1]).Campaign.Name = "Shopping " + DateTime.UtcNow;
// EnhancedCpcBiddingScheme is not supported for shopping campaigns.
// 'Bid Strategy Type' column header in the Bulk file
((BulkCampaign)uploadEntities[1]).Campaign.BiddingScheme = null;
((BulkCampaign)uploadEntities[1]).Campaign.CampaignType = CampaignType.Shopping;
((BulkCampaign)uploadEntities[1]).Campaign.Settings = new[] {
    new ShoppingSetting {
        // 'Priority' column header in the Bulk file
        Priority = 0,
        // 'Country Code' column header in the Bulk file
        SalesCountryCode = "US",
        // 'Store Id' column header in the Bulk file
        StoreId = 39807 // TBD
    }
};
            
// Set properties specific to the DynamicSearchAds campaign type
((BulkCampaign)uploadEntities[2]).Campaign.Name = "DynamicSearchAds " + DateTime.UtcNow;
((BulkCampaign)uploadEntities[2]).Campaign.CampaignType = CampaignType.DynamicSearchAds;
((BulkCampaign)uploadEntities[2]).Campaign.Settings = new[] {
    new DynamicSearchAdsSetting {
        // 'Website' column header in the Bulk file
        DomainName = "contoso.com",
        // 'Domain Language' column header in the Bulk file
        Language = "EN"
    }
};

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

### <a name="bidadjustment"></a>Bid Adjustment
The percent amount by which to adjust your bid for native ads above or below the base ad group or keyword bid.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

Supported values are negative one hundred (-100) through positive nine hundred (900). Setting the bid adjustment to -100 percent will prevent native ads from showing for this campaign.

Set this field to zero (0) if you do not want any bid adjustment for native ads.

**Add:** Optional. If you do not set this field the system default bid adjustment will be used. The system default bid adjustment is currently zero (0), and is subject to change.   
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] If you set this field to *delete_value* the system default bid adjustment will be used. The *delete_value* keyword removes the previous setting. The system default bid adjustment is currently zero (0), and is subject to change. If you do not specify any value this field will be ignored.    
**Delete:** Read-only  

### <a name="bidstrategymaxcpc"></a>Bid Strategy MaxCpc
The maximum cost per click that you want to spend with the corresponding bid strategy type. 

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]
> 
> The *Bid Strategy MaxCpc* field is only used if the *Bid Strategy Type* field is set to *MaxClicks*, *MaxConversions*, or *TargetCpa*, and otherwise this field is ignored.
> 
> The *MaxClicks* bid strategy is available only to advertisers from the following countries: Australia, Canada, France, Germany, India, Italy, Netherlands, Spain, Sweden, Switzerland, United Kingdom, and United States.
> 
> The *MaxConversions* bid strategy is available only to advertisers from the following countries: Australia, Canada, France, Germany, United Kingdom, and United States.
> 
> The *TargetCpa* bid strategy is available only to advertisers from the following countries: Australia, Canada, France, Germany, United Kingdom, and United States.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="bidstrategytargetcpa"></a>Bid Strategy TargetCpa
The target cost per acquisition (CPA) that you want used by Bing Ads to maximize conversions. 

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]
> 
> The *Bid Strategy TargetCpa* field is only used if the *Bid Strategy Type* field is set to *TargetCpa*, and otherwise this field is ignored.
> 
> The *TargetCpa* bid strategy is available only to advertisers from the following countries: Australia, Canada, France, Germany, United Kingdom, and United States.

**Add:** Required if the *Bid Strategy Type* field is set to *TargetCpa*, and otherwise this field is ignored.   
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="bidstrategytype"></a>Bid Strategy Type
The bid strategy type for how you want to manage your bids. 

A bid strategy type set at the [Ad Group](../bulk-api/ad-group.md) or [Keyword](../bulk-api/keyword.md) level will take precedence over the campaign level bid strategy type. 

For campaigns you can use any of the following bid strategy types. 
*  *EnhancedCpc* - Use the enhanced CPC bid strategy type to set your ad group and keyword bids, and Bing Ads will automatically adjust your bids in real time so that you bid up to 30% higher on users that are more likely to convert and up to 100% less on users less likely to convert. Bing Ads will still respect your campaign budget limit.  
*  *ManualCpc* - This is the default bid strategy type for your campaigns. Use the manual CPC bid strategy type if you will set your [Ad Group](../bulk-api/ad-group.md) or [Keyword](../bulk-api/keyword.md) bids, and Bing Ads will use these bids every time.  

If you are signed up to pilot one or more of the auto bid strategy types, then you can also use the corresponding bid strategy type value:  

*  *MaxClicks* - Defines an automated bidding strategy to maximize clicks given your maximum allowed budget.  
*  *MaxConversions* - Defines an automated bidding strategy to maximize conversions given your maximum allowed budget.    
*  *TargetCpa* - Defines an automated bidding strategy to maximize conversions at the target cost per acquisition (CPA). If you use this strategy type then you must also include the *Bid Strategy TargetCpa* field.    

For campaigns of type *Shopping* only the *EnhancedCpc* or *ManualCpc* bid strategy values can be used, and you must be in the Bing Shopping Enhanced CPC pilot. The pilot ID is 340.

[!INCLUDE[autobid_alert](../bulk-api/includes/autobid-alert.md)]

[!INCLUDE[tip_biddingscheme](../bulk-api/includes/tip-biddingscheme.md)]

**Add:** Optional. If you do not set this field, then *ManualCpc* is used by default.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]  If you update the bid strategy type, then any existing values in the *Bid Strategy MaxCpc* and *Bid Strategy TargetCpa* fields will be deleted.       
**Delete:** Read-only  

### <a name="budget"></a>Budget
The campaign's budget amount.

In the context of shared budgets, the budget amount is a read-only property that is always returned regardless of whether or not the campaign uses a shared budget. When a campaign is associated to a shared budget the amount returned is that of the shared budget. To determine whether the campaign uses a shared budget, check the value of the *Budget Id* field.

*Shared budget:*  
**Add:** Read-only  
**Update:** Not allowed. If you try to update the budget amount of a campaign that has a shared budget, the service will return the *CampaignServiceCannotUpdateSharedBudget* error code.    
**Delete:** Read-only  

*Unshared budget:*  
**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="budgetid"></a>Budget Id
The system generated identifier of the [Budget](../bulk-api/budget.md) that this campaign shares with other campaigns in the account.

If the field is empty, then the campaign is not using a shared budget. If the field is not empty and the value is greater than zero, then the campaign is using a shared budget. If the campaign is using a shared budget, and you prefer that it use its own budget amount, set this element to '0' (zero) and set the *Budget* field to a valid budget amount.

> [!NOTE]
> This value corresponds to the *Id* column of the [Budget](../bulk-api/budget.md) record.
	
**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="budgetname"></a>Budget Name
The name of the shared budget.

This value corresponds to the *Budget Name* column of the [Budget](../bulk-api/budget.md) record. You can only set this value using the [Budget](../bulk-api/budget.md) record.

**Add:** Read-only  
**Update:** Read-only    
**Delete:** Read-only  

### <a name="budgettype"></a>Budget Type
The budget type determines how the budget is spent. The possible values are *DailyBudgetAccelerated* and *DailyBudgetStandard*.

In the context of shared budgets, the budget type is a read-only property that is always returned regardless of whether or not the campaign uses a shared budget. To determine whether the campaign uses a shared budget, check the value of the *Budget Id* field. 

*Shared budget:*  
**Add:** Read-only  
**Update:** Not allowed. If you try to update the budget type of a campaign that has a shared budget, the service will return the *CampaignServiceCannotUpdateSharedBudget* error code.    
**Delete:** Read-only  

*Unshared budget:*  
**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="campaign"></a>Campaign
The name of the campaign.

**Add:** Required  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For update and delete, you must specify either the *Id* or *Campaign* field.

### <a name="campaigntype"></a>Campaign Type
The type of the campaign.

The campaign type determines whether the campaign is a Bing Shopping campaign, Dynamic Search Ads campaign, or Search &amp; Content campaign. Possible values include *Shopping*, *DynamicSearchAds*, and *SearchAndContent*.

**Add:** Optional. If not specified, then default value of *SearchAndContent* is used and you cannot set Bing Shopping or Dynamic Search Ads campaign settings.  If the campaign type is *Shopping* then you must also include the *Country Code*, *Priority*, and *Store Id* fields. If the campaign type is *DynamicSearchAds* then you must also include the *Domain Language* and *Website* fields.  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Read-only  

### <a name="countrycode"></a>Country Code
The country code for the [!INCLUDE[storebrand](../bulk-api/includes/storebrand.md)] store.

For example, the following country code values are supported.
* *AU* - Australia
* *GB* - United Kingdom
* *DE* - Germany
* *FR* - France
* *US* - United States

To get the current list of supported country codes use the [GetBSCCountries](https://msdn.microsoft.com/library/bing-ads-campaign-management-getbsccountries.aspx) operation via the Campaign Management service.

**Add:** Required if the *Campaign Type* field is set to *Shopping*. You cannot include this column for other campaign types.  
**Update:** Read-only    
**Delete:** Read-only  

### <a name="customparameter"></a>Custom Parameter
Your custom collection of key and value parameters for URL tracking.

[!INCLUDE[validationrules_customparameters_bulk](../bulk-api/includes/validationrules-customparameters-bulk.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] To remove all custom parameters, set this field to *delete_value*. The *delete_value* keyword removes the previous setting. To remove a subset of custom parameters, specify the custom parameters that you want to keep and omit any that you do not want to keep. The new set of custom parameters will replace any previous custom parameter set.    
**Delete:** Read-only  


### <a name="domainlanguage"></a>Domain Language
The language of the website pages that you want to target for dynamic search ads.

Currently the only supported language code is *EN*.

**Add:** Required if the *Campaign Type* field is set to *DynamicSearchAds*. You cannot include this column for other campaign types.  
**Update:** Read-only. You cannot update the language.      
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the campaign.

**Add:** Optional. You must either leave this field empty, or specify a negative identifier. A negative identifier set for the campaign can then be referenced in the *Parent Id* field of dependent record types such as ad groups or criterion. This is recommended if you are adding new campaigns and new dependent records in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For update and delete, you must specify either the *Id* or *Campaign* field.

### <a name="language"></a>Language
The campaign languages.

For possible values, see the Language column within [Ad Languages](https://msdn.microsoft.com/library/bing-ads-ad-languages.aspx). Each language in the bulk field is delimited by a semicolon and space ("; "), for example *English; French; German*. You can specify multiple languages individually in the list, or only include one string in this field set to *All* if you want to target all languages.

> [!IMPORTANT]
> Support for multiple languages at the campaign level is in pilot. If languages are set at both the ad group and campaign level, the ad group-level language will override the campaign-level language. The customer is enabled for the pilot if the [GetCustomerPilotFeatures](https://msdn.microsoft.com/library/bing-ads-customer-management-getcustomerpilotfeatures.aspx) response includes pilot number *310*. Pilot participants will be able to set multiple languages at the campaign level, and will be able to delete the ad group level language. If your application depends on ad group language being set, then you must prepare for the possibility that ad group language will be nil. More specific dates and implementation details will be provided later through the [Bing Ads API Blog](https://blogs.msdn.microsoft.com/bing_ads_api/), and in the meantime you should update your application right away to support the change. Also note that as a one time migration when the customer is added to pilot, campaign languages are set to the union of all individual ad group languages. For example if you have three ad groups with language set to *English*, *German*, and *French*, then at the time of pilot enablement this campaign's languages will be set to a list including *English*, *German*, and *French*. 

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] Once campaign languages are set, you cannot delete all of them. The list of languages that you specify during update replaces the previous settings i.e. does not append to the existing set of languages.  
**Delete:** Read-only  

### <a name="localinventoryadsenabled"></a>LocalInventoryAdsEnabled
Determines whether local inventory ads are enabled for the [!INCLUDE[storebrand](../bulk-api/includes/storebrand.md)] store.

[!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

Set this property to *TRUE* if you want to enable local inventory ads, and otherwise set it to *FALSE*.

**Add:** Optional. If you do not specify this field or leave it empty, the default value of *FALSE* will be set and local inventory ads will not be enabled.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the account that contains the campaign.

This bulk field maps to the *Id* field of the [Account](../bulk-api/account.md) record.

**Add:** Read-only and Required  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  
  
### <a name="priority"></a>Priority
Helps determine which [!INCLUDE[brand_bsc](../bulk-api/includes/brand-bsc.md)] campaign serves ads, in the event that two or more campaigns use the product catalog feed from the same [!INCLUDE[storebrand](../bulk-api/includes/storebrand.md)] store.

You must specify one of the supported values: 0, 1, or 2. The higher numbers are given higher priority.

If two shopping campaigns use the product catalog feed from same [!INCLUDE[storebrand](../bulk-api/includes/storebrand.md)] store, then  ads will be delivered for the [Ad Group Product Partition](../bulk-api/ad-group-product-partition.md) with the highest bid.

> [!NOTE]
> If you create a [!INCLUDE[brand_bsc](../bulk-api/includes/brand-bsc.md)] campaign in the [!INCLUDE[brand](../bulk-api/includes/brand.md)] web application, the default priority selected is "Low" which is the equivalent of '0'.

**Add:** Required if the *Campaign Type* field is set to *Shopping*. You cannot include this column for other campaign types.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]  
**Delete:** Read-only  

### <a name="status"></a>Status
The status of the campaign.

Possible values are *Active*, *Paused*, and *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Required. The Status must be set to Deleted.

### <a name="storeid"></a>Store Id
The unique identifier for the [!INCLUDE[storebrand](../bulk-api/includes/storebrand.md)] store that your product catalog feed belongs to.

To get your store identifiers, call the [GetBMCStoresByCustomerId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getbmcstoresbycustomerid.aspx) operation.

**Add:** Required if the *Campaign Type* field is set to *Shopping*. You cannot include this column for other campaign types.  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="timezone"></a>Time Zone
The time zone where the campaign operates.

The time zone is used for reporting and applying the start and end date of an ad group.

For possible values, see [Common Market Values](http://go.microsoft.com/fwlink/?LinkId=691345).

**Add:** Required.   
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] You may not update the time zone if the campaign contains or has ever contained ad groups in the *Active* or *Paused* state.    
**Delete:** Read-only  

### <a name="trackingtemplate"></a>Tracking Template
The tracking template to use as a default for all URLs in your campaign.

[!INCLUDE[validationrules_trackingurltemplate](../bulk-api/includes/validationrules-trackingurltemplate.md)]

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="website"></a>Website
The domain name of the website that you want to target for dynamic search ads.

The length of the string is limited to 2,048 characters. If the domain name includes *www* it will be trimmed and not used.

**Add:** Required if the *Campaign Type* field is set to *DynamicSearchAds*. You cannot include this column for other campaign types.  
**Update:** Read-only. You cannot update the domain name.      
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
