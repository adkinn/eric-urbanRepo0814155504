---
title: "Migrating to Bing Ads API Version 11"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 904537a4-2b00-4ff9-a7b0-f4aed63cb7a7
caps.latest.revision: 59
---
# Migrating to Bing Ads API Version 11
All Bing Ads API SOAP web services will be available with Version 11.   

[!INCLUDE[v10_sunset](../concepts/includes/v10-sunset.md)]

The sections below describe changes from version 10 to version 11 of the [Ad Insight](https://msdn.microsoft.com/library/bing-ads-ad-insight-service-reference(v=msads.110).aspx), [Bulk](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference(v=msads.110).aspx), and [Campaign Management](https://msdn.microsoft.com/library/bing-ads-campaign-management-service-reference(v=msads.110).aspx) services, and changes from version 9 to version 11 of the [Customer Billing](https://msdn.microsoft.com/library/bing-ads-customer-billing-api-service-reference(v=msads.110).aspx), [Customer Management](https://msdn.microsoft.com/library/bing-ads-customer-management-api-service-reference(v=msads.110).aspx), and [Reporting](https://msdn.microsoft.com/library/bing-ads-reporting-service-reference(v=msads.110).aspx) services.

-   [Ad Insight](#adinsight)
-   [Bulk](#bulk)
-   [Campaign Management](#campaign)
-   [Customer Billing](#billing)
-   [Customer Management](#customer)
-   [Reporting](#reporting)

## <a name="adinsight"></a>Ad Insight

### Breaking Changes

#### Proxy Client

Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/AdInsight/v11`.

The production endpoint is [https://adinsight.api.bingads.microsoft.com/Api/Advertiser/AdInsight/v11/AdInsightService.svc](https://adinsight.api.bingads.microsoft.com/Api/Advertiser/AdInsight/v11/AdInsightService.svc).

The sandbox endpoint is [https://adinsight.api.sandbox.bingads.microsoft.com/Api/Advertiser/AdInsight/v11/AdInsightService.svc](https://adinsight.api.sandbox.bingads.microsoft.com/Api/Advertiser/AdInsight/v11/AdInsightService.svc).

#### <a name="adinsight_monthlybudget"></a>Campaign Monthly Budget
The *MonthlyBudgetSpendUntilDepleted* value is removed from the the [BudgetLimitType](https://msdn.microsoft.com/library/bing-ads-ad-insight-budgetlimittype(v=msads.110).aspx) value set. Previously the [GetBudgetOpportunities](https://msdn.microsoft.com/library/bing-ads-ad-insight-getbudgetopportunities(v=msads.110).aspx) operation would return monthly budget opportunities for campaigns using monthly budgets. Monthly budgets are no longer supported in Bing Ads. 


## <a name="bulk"></a>Bulk

### Breaking Changes

#### Proxy Client

Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/CampaignManagement/v11`.

The production endpoint is [https://bulk.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/BulkService.svc](https://bulk.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/BulkService.svc).

The sandbox endpoint is [https://bulk.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/BulkService.svc](https://bulk.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/BulkService.svc).

#### <a name="bulk_downloadentities"></a>Download Entities
The *DownloadEntities* request element replaces the *Entities* request element for the [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbyaccountids(v=msads.110).aspx) and [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbycampaignids(v=msads.110).aspx) operations. The *DownloadEntities* element accepts a list of [DownloadEntity](https://msdn.microsoft.com/library/bing-ads-bulk-downloadentity(v=msads.110).aspx) values instead of a flag set used in Bing Ads API version 10. The *BulkDownloadEntity* value set is removed. 

#### <a name="bulk_formatversion5"></a>Format Version 5.0

Support for Bulk file format version 4.0 is removed. [!INCLUDE[brand](../concepts/includes/brand.md)] API Version 11 only supports format version 5.0. When calling the [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbyaccountids(v=msads.110).aspx) and [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/bing-ads-bulk-downloadcampaignsbycampaignids(v=msads.110).aspx) operations you must specify *5.0* in the *FormatVersion* request element. When uploading a bulk file, you must specify 5.0 in the *Name* field of the [Format Version](https://msdn.microsoft.com/library/bing-ads-bulk-format-version-record(v=msads.110).aspx) record. Changes to records between format version 4.0 and 5.0 are described in more detail in the following sections.

#### <a name="bulk_targetcriterions"></a>Upgrade from Targets to Criterions
Instead of using targets to show your ads based on age, day and time, device, gender, and location, starting with Bing Ads API version 11 you must use criterions. Partial update of target criterions is supported in Bing Ads API version 11. The following changes are required to upgrade from targets to criterions. For more details please see the [Upgrade Targets to Criterions](../concepts/upgrade-targets-to-criterions.md) guide.
  * Replaced all target records with criterion records. For example the *Ad Group Age Target* record is replaced with the [Ad Group Age Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-age-criterion-record(v=msads.110).aspx) record. You can download the new criterion records using the *AdGroupTargetCriterions* and *CampaignTargetCriterions* values of the [DownloadEntity](https://msdn.microsoft.com/library/bing-ads-bulk-downloadentity(v=msads.110).aspx) value set. 
  * The [Ad Group Age Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-age-criterion-record(v=msads.110).aspx) and [Campaign Age Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-age-criterion-record(v=msads.110).aspx) records support new values in the *Target* field: *EighteenToTwentyFour*, *TwentyFiveToThirtyFour*, *ThirtyFiveToFortyNine*, *FiftyToSixtyFour*, and *SixtyFiveAndAbove*. The upper bound of each range previously supported in format version 4.0 were not inclusive, for example *EighteenToTwentyFive* would only target ages eighteen through twenty-four. The values in format version 5.0 match the effective target range that remains unchanged. 
  * If an ad group or campaign has any device criterion, then it must have bids for all three device types. Please note this change when adding and updating [Ad Group DeviceOS Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-deviceos-criterion-record(v=msads.110).aspx) and [Campaign DeviceOS Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-deviceos-criterion-record(v=msads.110).aspx) records. For example you cannot have a campaign that only has one [Campaign DeviceOS Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-deviceos-criterion-record(v=msads.110).aspx) record. If the campaign has any device criterion then it must have three [Campaign DeviceOS Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-deviceos-criterion-record(v=msads.110).aspx) records, each with corresponding supported bids for *Computers*, *Smartphones*, and *Tablets*. Previously in format version 4.0 the missing records were added automatically with bids set to '0' (zero).  
  * The [Ad Group Location Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-location-criterion-record(v=msads.110).aspx) and [Campaign Location Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-location-criterion-record(v=msads.110).aspx) records support location identifiers in the *Target* field, instead of the location codes that were accepted by the corresponding format version 4.0 target records. The location identifier corresponds to the *ID* field of the geographical locations file. For more information, see [Geographical Location Codes](https://msdn.microsoft.com/library/bing-ads-geographical-location-codes(v=msads.110).aspx) and [GetGeoLocationsFileUrl](https://msdn.microsoft.com/library/bing-ads-campaign-management-getgeolocationsfileurl(v=msads.110).aspx).
  * The *Sub Type* field for [Ad Group Location Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-location-criterion-record(v=msads.110).aspx) and [Campaign Location Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-location-criterion-record(v=msads.110).aspx) records can include these values: *City*, *Country*, *MetroArea*, *PostalCode*, and *State*. The *Sub Type* field in the Bulk file format version 4.0 target records included these values (with spaces between words): *City*, *Country*, *Metro Area*, *Postal Code*, and *State*. 
  * The *Physical Intent* field is not available in the [Ad Group Location Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-location-criterion-record(v=msads.110).aspx), [Campaign Location Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-location-criterion-record(v=msads.110).aspx), [Ad Group Radius Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-radius-criterion-record(v=msads.110).aspx), and [Campaign Radius Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-radius-criterion-record(v=msads.110).aspx) records, as it had been in the corresponding format version 4.0 target records. To determine the intent option for all location and radius criterions of a given ad group or campaign, you can use the new [Ad Group Location Intent Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-location-intent-criterion-record(v=msads.110).aspx) and [Campaign Location Intent Criterion](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-location-intent-criterion-record(v=msads.110).aspx) records. 
  * You cannot delete all criterions by sending one bulk record having *Status* set to *Deleted*. Previously using version 10 targets, you could have sent one row to delete all city targets for example. With criterions, each record must be updated and deleted individually with its unique identifier.

#### <a name="bulk_remarketinglist"></a>Remarketing Lists
For the remarketing list name in the [Remarketing List](https://msdn.microsoft.com/library/bing-ads-bulk-remarketing-list-record(v=msads.110).aspx) and [Ad Group Remarketing List Association](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-remarketing-list-association-record(v=msads.110).aspx) records, use the *Audience* field instead of the *Remarketing List* field. For the remarketing list identifier in the same records, use the *Audience Id* field instead of the *Remarketing List Id* field.

Bing Ads API version 11 also supports custom and in-market [audiences](#bulk_audience), in addition to remarketing lists. 

#### <a name="bulk_invalidcriterionstatus"></a>Invalid Criterion Status
An error will be returned if you attempt to set the *Status* of the [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record(v=msads.110).aspx) or [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record(v=msads.110).aspx) to an invalid value e.g. *Paused*. In Bing Ads API version 10, the invalid status update would not succeed but would not result in an error.

#### <a name="bulk_sunset_cpm"></a>Cpm Pricing Model
The CPM pricing model is not supported in Bing Ads, and the *Pricing Model* field of an [Ad Group](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-record(v=msads.110).aspx) is now deprecated. The *Pricing Model* field is now optional, defaults to *Cpc*, and can only be set to *Cpc*. 

### New Features

#### <a name="bulk_audience"></a>Audience Associations and Exclusions
Bing Ads API version 11 now supports custom audiences and in-market audiences, in addition to [remarketing lists](#bulk_remarketinglist). The following audience, association, and exclusion records are supported.

*  [Remarketing List](https://msdn.microsoft.com/library/bing-ads-bulk-remarketing-list-record(v=msads.110).aspx)  
*  [Ad Group Remarketing List Association](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-remarketing-list-association-record(v=msads.110).aspx)  
*  [Ad Group Negative Remarketing List Association](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-remarketing-list-association-record(v=msads.110).aspx)  
*  [Custom Audience](https://msdn.microsoft.com/library/bing-ads-bulk-custom-audience-record(v=msads.110).aspx)  
*  [Ad Group Custom Audience Association](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-custom-audience-association-record(v=msads.110).aspx)  
*  [Ad Group Negative Custom Audience Association](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-custom-audience-association-record(v=msads.110).aspx)  
*  [In Market Audience](https://msdn.microsoft.com/library/bing-ads-bulk-in-market-audience-record(v=msads.110).aspx)  
*  [Ad Group In Market Audience Association](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-in-market-audience-association-record(v=msads.110).aspx)  
*  [Ad Group Negative In Market Audience Association](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-in-market-audience-association-record(v=msads.110).aspx)  

To download these record types individually you can include the following values from the [DownloadEntity](https://msdn.microsoft.com/library/bing-ads-bulk-downloadentity(v=msads.110).aspx) value set: *RemarketingLists*, *AdGroupRemarketingListAssociations*, *AdGroupNegativeRemarketingListAssociations*, *CustomAudiences*, *AdGroupCustomAudienceAssociations*, *AdGroupNegativeCustomAudienceAssociations*, *InMarketAudiences*, *AdGroupInMarketAudienceAssociations*, *AdGroupNegativeInMarketAudienceAssociations*. You can get all three types of audiences, associations, or exclusions by including the *Audiences*, *AdGroupAudienceAssociations*, and *AdGroupNegativeAudienceAssociations* values.

#### <a name="bulk_accountextensions"></a>Associate Ad Extensions with an Account
Support is added for associating ad extensions at the account level. In Bing Ads API version 10 you could only associate ad extensions with campaigns and ad groups.

> [!NOTE]
> Call ad extensions cannot be associated with an account.
>
> In addition the deprecated sitelink ad extensions cannot be associated with an account. You must first [Upgrade from Multiple Sitelinks to One Sitelink Per Extension](../concepts/upgrade-from-multiple-sitelinks-to-one-sitelink-per-extension.md). 

To get and set account level associations, use the following account level association records. 
*   [Account App Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-app-ad-extension-record(v=msads.110).aspx)   
*   [Account Callout Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-callout-ad-extension-record(v=msads.110).aspx)  
*   [Account Image Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-image-ad-extension-record(v=msads.110).aspx)  
*   [Account Location Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-location-ad-extension-record(v=msads.110).aspx)  
*   [Account Price Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-price-ad-extension-record(v=msads.110).aspx)  
*   [Account Review Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-review-ad-extension-record(v=msads.110).aspx)  
*   [Account Sitelink2 Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-sitelink2-ad-extension-record(v=msads.110).aspx)  
*   [Account Structured Snippet Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-structuredsnippet-ad-extension-record(v=msads.110).aspx)  

To download these record types individually you can include the following values from the [DownloadEntity](https://msdn.microsoft.com/library/bing-ads-bulk-downloadentity(v=msads.110).aspx) value set: *AccountAppAdExtensions*, *AccountCalloutAdExtensions*, *AccountImageAdExtensions*, *AccountLocationAdExtensions*, *AccountPriceAdExtensions*, *AccountReviewAdExtensions*, *AccountSitelink2AdExtensions*, *AccountStructuredSnippetAdExtensions*. 

#### <a name="bulk_priceextensions"></a>Price Ad Extensions
Support for price ad extensions is added. You can upload and download these price ad extension records.
*  [Price Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-price-ad-extension-record(v=msads.110).aspx)  
*  [Account Price Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-account-price-ad-extension-record(v=msads.110).aspx)  
*  [Ad Group Price Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-price-ad-extension-record(v=msads.110).aspx)  
*  [Campaign Price Ad Extension](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-price-ad-extension-record(v=msads.110).aspx) 

To download these record types individually you can include the following values from the [DownloadEntity](https://msdn.microsoft.com/library/bing-ads-bulk-downloadentity(v=msads.110).aspx) value set: *PriceAdExtensions*, *AdGroupPriceAdExtensions*, *CampaignPriceAdExtensions*, *AccountPriceAdExtensions*. 

## <a name="campaign"></a>Campaign Management

### Breaking Changes

#### Proxy Client
Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/CampaignManagement/v11`.

The production endpoint is [https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/CampaignManagementService.svc](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/CampaignManagementService.svc).

The sandbox endpoint is [https://campaign.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/CampaignManagementService.svc](https://campaign.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v11/CampaignManagementService.svc).

#### <a name="campaign_targetcriterions"></a>Upgrade from Targets to Criterions
Instead of using targets to show your ads based on age, day and time, device, gender, and location, starting with Bing Ads API version 11 you must use criterions. Partial update of target criterions is supported in Bing Ads API version 11. The following changes are required to upgrade from targets to criterions. For more details please see the [Upgrade Targets to Criterions](../concepts/upgrade-targets-to-criterions.md) guide.
  * Removed all *Target* objects and service operations. For example the *AgeTarget* and *AgeTargetBid* are replaced with the [AgeCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-agecriterion(v=msads.110).aspx) object. To add an age criterion you embed the [AgeCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-agecriterion(v=msads.110).aspx) in either the [BiddableCampaignCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-biddablecampaigncriterion(v=msads.110).aspx) or [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-biddableadgroupcriterion(v=msads.110).aspx) and then call the respective [AddCampaignCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addcampaigncriterions(v=msads.110).aspx) or [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions(v=msads.110).aspx) service operation. 
  * The [AgeRange](https://msdn.microsoft.com/library/bing-ads-campaign-management-agerange(v=msads.110).aspx) values are updated: *EighteenToTwentyFour*, *TwentyFiveToThirtyFour*, *ThirtyFiveToFortyNine*, *FiftyToSixtyFour*, and *SixtyFiveAndAbove*. The upper bound of each range previously supported in Bing Ads API Version 10 were not inclusive, for example *EighteenToTwentyFive* would only target ages eighteen through twenty-four. The values in Bing Ads API Version 11 match the effective target range that remains unchanged. 
  * If an ad group or campaign has any device criterion, then it must have bids for all three device types. Please note this change when adding and updating [DeviceCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-devicecriterion(v=msads.110).aspx). For example you cannot have a campaign that only has one [DeviceCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-devicecriterion(v=msads.110).aspx). If the campaign has any device criterion then it must have three [DeviceCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-devicecriterion(v=msads.110).aspx), each with corresponding supported bids for *Computers*, *Smartphones*, and *Tablets*. Previously in Bing Ads API Version 10 the missing bids were added automatically with bids set to '0' (zero).  
  * The [LocationCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-locationcriterion(v=msads.110).aspx) supports location identifiers in its *LocationId* element, instead of the location codes that were accepted for sub location targets e.g. *CityTargetBid* in Bing Ads API Version 10. The location identifier corresponds to the *ID* field of the geographical locations file. For more information, see [Geographical Location Codes](https://msdn.microsoft.com/library/bing-ads-geographical-location-codes(v=msads.110).aspx) and [GetGeoLocationsFileUrl](https://msdn.microsoft.com/library/bing-ads-campaign-management-getgeolocationsfileurl(v=msads.110).aspx).
  * The [LocationIntentCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-locationintentcriterion(v=msads.110).aspx) is added in Bing Ads API Version 11. Previously in Bing Ads API Version 10 you would have set the intent option in the *LocationTarget*, which has been removed. One location intent criterion determines the intent option for all location and radius criterions of a given ad group or campaign. 
  * Use the [BidMultiplier](https://msdn.microsoft.com/library/bing-ads-campaign-management-bidmultiplier(v=msads.110).aspx) object to adjust the bid for the target criterion. 
  
#### <a name="campaign_biddablecampaigncriterion"></a>Biddable Campaign Criterion
The [BiddableCampaignCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-biddablecampaigncriterion(v=msads.110).aspx) is added, and derives properties from the [CampaignCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaigncriterion(v=msads.110).aspx), which is now an abstract base class. You must use [BiddableCampaignCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-biddablecampaigncriterion(v=msads.110).aspx) instead of [CampaignCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaigncriterion(v=msads.110).aspx) in add, get, and update campaign criterion operations.
  
#### <a name="campaign_fixedbid"></a>Fixed Bid
Within the [FixedBid](https://msdn.microsoft.com/library/bing-ads-campaign-management-fixedbid(v=msads.110).aspx) object, the *Bid* element of type [Bid](https://msdn.microsoft.com/library/bing-ads-campaign-management-bid(v=msads.110).aspx) is replaced by the *Amount* element of type *double*. 

#### <a name="campaign_adgroupcriteriontype"></a>Ad Group Criterion Type
The *AccountId* element is removed from the request message of the [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions(v=msads.110).aspx), [DeleteAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadgroupcriterions(v=msads.110).aspx), [GetAdGroupCriterionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupcriterionsbyids(v=msads.110).aspx), and [UpdateAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateadgroupcriterions(v=msads.110).aspx) operations. You must set the *CustomerAccountId* header element instead.

#### <a name="campaign_adgroupcriteriontype"></a>Shared Target to Criterion Migration
The *IsMigrated* element is added to the response message of the [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions(v=msads.110).aspx), [DeleteAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadgroupcriterions(v=msads.110).aspx), [UpdateAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateadgroupcriterions(v=msads.110).aspx), [AddCampaignCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addcampaigncriterions(v=msads.110).aspx), [DeleteCampaignCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-deletecampaigncriterions(v=msads.110).aspx), and [UpdateCampaignCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-updatecampaigncriterions(v=msads.110).aspx) operations. The *IsMigrated* element indicates whether or not the campaign or ad group where you added, deleted, or updated target criterions previously shared target criterions with another campaign or ad group. If *IsMigrated* is set to *true*, it indicates that the service migrated the shared target associations and assigned new criterion IDs. If you already have criterion IDs for targets such as age, day and time, device, gender, and location, then you should replace those IDs with all of the new IDs returned by the [GetAdGroupCriterionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupcriterionsbyids(v=msads.110).aspx) or [GetCampaignCriterionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getcampaigncriterionsbyids(v=msads.110).aspx) operation (specify *TargetCriterions* as the *CriterionType*). You only need to sync target criterion IDs, as other criterion types such as webpage criterions are not migrated. For more details please see the [Upgrade Targets to Criterions](../concepts/upgrade-targets-to-criterions.md) guide.

#### <a name="campaign_criterionaccount"></a>Account Id for Criterions
The *CriterionType* value set is renamed [AdGroupCriterionType](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroupcriteriontype(v=msads.110).aspx). You'll need to make code changes if you call the [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions(v=msads.110).aspx), [DeleteAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadgroupcriterions(v=msads.110).aspx), [GetAdGroupCriterionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupcriterionsbyids(v=msads.110).aspx), or [UpdateAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateadgroupcriterions(v=msads.110).aspx) operations.

#### <a name="campaign_remarketinglist"></a>Remarketing Lists
The [RemarketingList](https://msdn.microsoft.com/library/bing-ads-campaign-management-remarketinglist(v=msads.110).aspx) now derives from the [Audience](https://msdn.microsoft.com/library/bing-ads-campaign-management-audience(v=msads.110).aspx) base class. The *Description*, *ForwardCompatibilityMap*, *Id*, *MembershipDuration*, *Name*, *ParentId*, and *Scope* elements are moved from [RemarketingList](https://msdn.microsoft.com/library/bing-ads-campaign-management-remarketinglist(v=msads.110).aspx) to the [Audience](https://msdn.microsoft.com/library/bing-ads-campaign-management-audience(v=msads.110).aspx) base class. The *AddRemarketingLists*, *DeleteRemarketingLists*, *GetRemarketingLists*, and *UpdateRemarketingLists* operations are replaced with the [AddAudiences](https://msdn.microsoft.com/library/bing-ads-campaign-management-addaudiences(v=msads.110).aspx), [DeleteAudiences](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteaudiences(v=msads.110).aspx), [GetAudiencesByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getaudiencesbyids(v=msads.110).aspx), and [UpdateAudiences](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateaudiences(v=msads.110).aspx) operations. Bing Ads API version 11 also supports custom and in-market [audiences](#campaign_audience), in addition to remarketing lists. 

The *AdGroupRemarketingListAssociation* object and *AddAdGroupRemarketingListAssociations*, *DeleteAdGroupRemarketingListAssociations*, *GetAdGroupRemarketingListAssociations*, and *UpdateAdGroupRemarketingListAssociations* operations are removed. To associate remarketing lists and other audience types with ad groups, use the new [AudienceCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-audiencecriterion(v=msads.110).aspx) object with the [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions(v=msads.110).aspx), [DeleteAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadgroupcriterions(v=msads.110).aspx), [GetAdGroupCriterionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupcriterionsbyids(v=msads.110).aspx), and [UpdateAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateadgroupcriterions(v=msads.110).aspx) operations.

#### <a name="campaign_monthlybudget"></a>Campaign Monthly Budget
Monthly budgets are no longer supported for Bing Ads campaigns. The *MonthlyBudget* element is removed from the [Campaign](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaign(v=msads.110).aspx) object. The *MonthlyBudgetSpendUntilDepleted* value is removed from the [BudgetLimitType](https://msdn.microsoft.com/library/bing-ads-campaign-management-budgetlimittype(v=msads.110).aspx) value set.  

#### <a name="campaign_extensionpartialsuccess"></a>Ad Extensions Partial Success
The [AddAdExtensions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadextensions(v=msads.110).aspx), [DeleteAdExtensions](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadextensions(v=msads.110).aspx), [DeleteAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadextensionsassociations(v=msads.110).aspx), [GetAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsassociations(v=msads.110).aspx),  [GetAdExtensionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsbyids(v=msads.110).aspx), [GetAdExtensionsEditorialReasons](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionseditorialreasons(v=msads.110).aspx), and [UpdateAdExtensions](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateadextensions(v=msads.110).aspx) operations now support partial success. Either the *PartialErrors* or *NestedPartialErrors* element is added to each operation's response message. Note that the [SetAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-setadextensionsassociations(v=msads.110).aspx) operation already supported partial success.

#### <a name="campaign_extensiondevicepreference"></a>Ad Extensions Device Preference
The *DevicePreference* element is added to the [AdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-adextension(v=msads.110).aspx) base class, and *DevicePreference* is removed from the [AppAdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-appadextension(v=msads.110).aspx), [CallAdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-calladextension(v=msads.110).aspx), and [Sitelink2AdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-sitelink2adextension(v=msads.110).aspx) objects. Device preference is currently only supported for app, sitelink, and sitelink2 ad extensions. 

#### <a name="campaign_migrationtype"></a>Required Migration Type Filter
The *MigrationType* element of the [GetAccountMigrationStatuses](https://msdn.microsoft.com/library/bing-ads-campaign-management-getaccountmigrationstatuses(v=msads.110).aspx) service operation is now required. In version 10 if you did not specify any migration type value, by default the *SiteLinkAdExtension* migration status would be returned. 

#### <a name="campaign_requiredadtypes"></a>Required Ad Types
When calling the [GetAdsByAdGroupId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadsbyadgroupid(v=msads.110).aspx), [GetAdsByEditorialStatus](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadsbyeditorialstatus(v=msads.110).aspx), and [GetAdsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadsbyids(v=msads.110).aspx) operations the *AdTypes* element is now required. In version 10 these operations returned text and product ads if *AdTypes* was left nil.

#### <a name="campaign_addads"></a>Add Ads Duplicate Error
If you attempt to create an ad with duplicate ad copy, the [AddAds](https://msdn.microsoft.com/library/bing-ads-campaign-management-addads(v=msads.110).aspx) operation will now consistently return a duplicate ad error. In Version 10, the operation would return an error if the duplicate ad copy exists in the same batch request. However, if duplicate ad copy was provided in a subsequent call the operation appeared to succed but returned the existing ad identifier.

#### <a name="campaign_idcollection"></a>IdCollection Ids Data Type
The *Ids* element of the [IdCollection](https://msdn.microsoft.com/library/bing-ads-campaign-management-idcollection(v=msads.110).aspx) object is updated from *ArrayOflong* to *ArrayOfNullableOflong*. The response for [AddNegativeKeywordsToEntities](https://msdn.microsoft.com/library/bing-ads-campaign-management-addnegativekeywordstoentities(v=msads.110).aspx) can now contain a list item that is nil if a negative keyword was not successfully added. In Version 10 if a negative keyword was not added the operation returned *0* as a list item within *Ids* instead of nil. 

#### <a name="campaign_siteplacements"></a>Site Placements Sunset
Site placements were sunset during calendar year 2016, and the following programming elements are removed from the Campaign Management API: *SitePlacement*, *AddSitePlacements*, *DeleteSitePlacements*, *GetSitePlacementsByAdGroupId*, *GetSitePlacementsByIds*, *UpdateSitePlacements*, and *GetPlacementDetailsForUrls*.

#### <a name="campaign_adgroup_biddingmodel"></a>Ad Group Bidding Model
The *BiddingModel* value set is removed and the *BiddingModel* element is removed from the [AdGroup](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroup(v=msads.110).aspx) object. The bidding model is effectively determined by the Campaign type e.g. you can bid on keywords in Search and Content campaigns, product groups in Shopping campaigns, or webpage criterion in Dynamic Search Ad campaigns.

#### <a name="campaign_daylightsaving"></a>Campaign Daylight Saving
The *DaylightSaving* element is removed from the [Campaign](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaign(v=msads.110).aspx) object. Bing Ads will continue to adjust the delivery only on time zones where DST adjustment applies. This setting was only used to interpret the start and end date of your ad groups relative to your campaign's time zone. It has never been used for day and time scheduling.

#### <a name="campaign_biddingschemestartingbid"></a>Bidding Scheme Starting Bid
The *StartingBid* element is removed from the [MaxConversionsBiddingScheme](https://msdn.microsoft.com/library/bing-ads-campaign-management-maxconversionsbiddingscheme(v=msads.110).aspx) and [TargetCpaBiddingScheme](https://msdn.microsoft.com/library/bing-ads-campaign-management-targetcpabiddingscheme(v=msads.110).aspx) objects. The starting bid was never implemented, and is removed from the Campaign Management API contract. 

#### <a name="campaign_invalidcriterionstatus"></a>Invalid Criterion Status
An error will be returned if you attempt to set the *Status* of the [NegativeAdGroupCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-negativeadgroupcriterion(v=msads.110).aspx) or [NegativeCampaignCriterion](https://msdn.microsoft.com/library/bing-ads-campaign-management-negativecampaigncriterion(v=msads.110).aspx) to an invalid value e.g. *Paused*. In Bing Ads API version 10, the invalid status update would not succeed but would not result in an error.

#### <a name="campaign_adformatpreference"></a>Ad Format Preference for Native Ads
The Ad Format Preference is used to indicate whether or not you prefer the ad copy to be shown to users as a search or native ad. Search ads tend to be written as a call to action, whereas native ads should be written in more of an informational style.

The *NativePreference* key is removed from the ad's *ForwardCompatibilityMap*. In its place, the *AdFormatPreference* element of type *string* is added to the [Ad](https://msdn.microsoft.com/library/bing-ads-campaign-management-ad(v=msads.110).aspx) object. All ad types inherit this element, and currently it is only applicable for the [ExpandedTextAd](https://msdn.microsoft.com/library/bing-ads-campaign-management-expandedtextad(v=msads.110).aspx) and [TextAd](https://msdn.microsoft.com/library/bing-ads-campaign-management-textad(v=msads.110).aspx) objects. 

Possible values are *Native* and *All*. If set to *All*, the ad will be eligible for both search and native ad formats. If set to *Native*, the ad will only be eligible for the native ad format.

#### <a name="campaign_returnadditionalfields"></a>Return Additional Fields
The *ReturnAdditionalFields* element is removed from the [GetCampaignsByAccountId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getcampaignsbyaccountid(v=msads.110).aspx), [GetCampaignsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getcampaignsbyids(v=msads.110).aspx), [GetAdGroupsByCampaignId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupsbycampaignid(v=msads.110).aspx),[GetAdGroupsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupsbyids(v=msads.110).aspx), [GetKeywordsByAdGroupId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getkeywordsbyadgroupid(v=msads.110).aspx), [GetKeywordsByEditorialStatus](https://msdn.microsoft.com/library/bing-ads-campaign-management-getkeywordsbyeditorialstatus(v=msads.110).aspx), [GetKeywordsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getkeywordsbyids(v=msads.110).aspx), [GetAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsassociations(v=msads.110).aspx),[GetAdExtensionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsbyids(v=msads.110).aspx), and [GetRemarketingLists](https://msdn.microsoft.com/library/bing-ads-campaign-management-getremarketinglists(v=msads.110).aspx) request messages, and the corresponding elements of each [Campaign](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaign(v=msads.110).aspx), [AdGroup](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroup(v=msads.110).aspx), [Keyword](https://msdn.microsoft.com/library/bing-ads-campaign-management-keyword(v=msads.110).aspx), [AdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-adextension(v=msads.110).aspx), and [RemarketingList](https://msdn.microsoft.com/library/bing-ads-campaign-management-remarketinglist(v=msads.110).aspx) are returned by default.

#### <a name="campaign_sunset_cpm"></a>Cpm Pricing Model
The CPM pricing model is not supported in Bing Ads, and the *PricingModel* element of an [AdGroup](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroup(v=msads.110).aspx) is now deprecated. The *PricingModel* element is now optional, defaults to *Cpc*, and can only be set to *Cpc*. 

### New Features

#### <a name="campaign_audience"></a>Audience Associations and Exclusions
Bing Ads API version 11 now supports custom audiences and in-market audiences, in addition to [remarketing lists](#campaign_remarketinglist). 

The [CustomAudience](https://msdn.microsoft.com/library/bing-ads-campaign-management-customaudience(v=msads.110).aspx), [InMarketAudience](https://msdn.microsoft.com/library/bing-ads-campaign-management-inmarketaudience(v=msads.110).aspx), and [RemarketingList](https://msdn.microsoft.com/library/bing-ads-campaign-management-remarketinglist(v=msads.110).aspx) derive from the [Audience](https://msdn.microsoft.com/library/bing-ads-campaign-management-audience(v=msads.110).aspx) base class. You can manage audiences with the [AddAudiences](https://msdn.microsoft.com/library/bing-ads-campaign-management-addaudiences(v=msads.110).aspx), [DeleteAudiences](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteaudiences(v=msads.110).aspx), [GetAudiencesByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getaudiencesbyids(v=msads.110).aspx), and [UpdateAudiences](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateaudiences(v=msads.110).aspx) operations.
 
#### <a name="campaign_accountextensions"></a>Associate Ad Extensions with an Account
Support is added for associating ad extensions at the account level. In Bing Ads API version 10 you could only associate ad extensions with campaigns and ad groups.

> [!NOTE]
> Call ad extensions cannot be associated with an account.
>
> In addition the deprecated sitelink ad extensions cannot be associated with an account. You must first [Upgrade from Multiple Sitelinks to One Sitelink Per Extension](../concepts/upgrade-from-multiple-sitelinks-to-one-sitelink-per-extension.md). 

To get and set account level associations, use the *Account* value of the [AssociationType](https://msdn.microsoft.com/library/bing-ads-campaign-management-associationtype(v=msads.110).aspx) value set. 

#### <a name="campaign_priceextensions"></a>Price Ad Extensions
Support for price ad extensions is added. You can manage the new [PriceAdExtension](https://msdn.microsoft.com/library/bing-ads-campaign-management-priceadextension(v=msads.110).aspx) object with the [AddAdExtensions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadextensions(v=msads.110).aspx), [DeleteAdExtensions](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadextensions(v=msads.110).aspx), [DeleteAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadextensionsassociations(v=msads.110).aspx), [GetAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsassociations(v=msads.110).aspx),  [GetAdExtensionsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionsbyids(v=msads.110).aspx), [GetAdExtensionsEditorialReasons](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadextensionseditorialreasons(v=msads.110).aspx), [SetAdExtensionsAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-setadextensionsassociations(v=msads.110).aspx), and [UpdateAdExtensions](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateadextensions(v=msads.110).aspx) operations. 

## <a name="billing"></a>Customer Billing

### Breaking Changes

#### Proxy Client
Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/Billing/v11`.

The production endpoint is [https://clientcenter.api.bingads.microsoft.com/Api/Billing/v11/CustomerBillingService.svc](https://clientcenter.api.bingads.microsoft.com/Api/Billing/v11/CustomerBillingService.svc).

#### <a name="billing_insertionorderstatus"></a>Insertion Order Status
For parity with the insertion order status values that you'll already find in the Bing Ads web application, the *Exhausted* and *Pending* values are added to the [InsertionOrderStatus](https://msdn.microsoft.com/library/bing-ads-billing-insertionorderstatus(v=msads.110).aspx) value set. 

> [!NOTE]
> If the insertion order start date is in the future, the Bing Ads API Version 9 status would be Active; However in the Bing Ads web application and Bing Ads API Version 11 the status is Pending.

In addition the *ChangePendingReview* element is added to the [InsertionOrder](https://msdn.microsoft.com/library/bing-ads-billing-insertionorder(v=msads.110).aspx) object. If this element is true, an update to the insertion order is pending user review. 

## <a name="customer"></a>Customer Management

### Breaking Changes

#### Proxy Client
Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/Customer/v11`.

The production endpoint is [https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v11/CustomerManagementService.svc](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v11/CustomerManagementService.svc).

The sandbox endpoint is [https://clientcenter.api.sandbox.bingads.microsoft.com/Api/CustomerManagement/v11/CustomerManagementService.svc](https://clientcenter.api.sandbox.bingads.microsoft.com/Api/CustomerManagement/v11/CustomerManagementService.svc).

#### <a name="customer_taxdetails"></a>Tax Details
The *TaxId* is moved as a key and value pair to the *TaxInformation* element of the [AdvertiserAccount](https://msdn.microsoft.com/library/bing-ads-customer-management-advertiseraccount(v=msads.110).aspx) object. Additional keys include the *TaxType* and *VatNumber*.
 
The *BusinessAddress* element of an [AdvertiserAccount](https://msdn.microsoft.com/library/bing-ads-customer-management-advertiseraccount(v=msads.110).aspx) is now required when adding accounts. 

The *IncludeTaxDetails* element is removed from the [GetAccount](https://msdn.microsoft.com/library/bing-ads-customer-management-getaccount(v=msads.110).aspx) and [SearchAccounts](https://msdn.microsoft.com/library/bing-ads-customer-management-searchaccounts(v=msads.110).aspx) request messages, so the *BusinessAddress* element is now returned by default when retrieving accounts. With this update the *TaxId* and *TaxIdStatus* elements and corresponding value set is also removed.

The *IncludeTaxInformation* element is removed from the [GetAccount](https://msdn.microsoft.com/library/bing-ads-customer-management-getaccount(v=msads.110).aspx) and [SearchAccounts](https://msdn.microsoft.com/library/bing-ads-customer-management-searchaccounts(v=msads.110).aspx) request messages, so the *TaxInformation* element is now returned by default when retrieving accounts. 

#### <a name="customer_standarduser"></a>Standard User Role
To represent the Standard user role, the *StandardUser* value is added to the [UserRole](https://msdn.microsoft.com/library/bing-ads-customer-management-userrole(v=msads.110).aspx) value set. With Customer Management API Version 9 you could not get or set the Standard user role. In version 9 the Advertiser Campaign Manager role value was returned instead.

#### <a name="customer_linkedagencies"></a>Linked Agencies
The *LinkedAgencies* element is added to the [AdvertiserAccount](https://msdn.microsoft.com/library/bing-ads-customer-management-advertiseraccount(v=msads.110).aspx) object. This array of [CustomerInfo](https://msdn.microsoft.com/library/bing-ads-customer-management-customerinfo(v=msads.110).aspx) represents the list of agencies linked to the account. This element is reserved for future use.

The *AgencyContactName* and *AgencyCustomerId* elements are removed from the [AdvertiserAccount](https://msdn.microsoft.com/library/bing-ads-customer-management-advertiseraccount(v=msads.110).aspx) object. Instead you will be able to get those values in the *LinkedAgencies* element.

## <a name="reporting"></a>Reporting

### Breaking Changes

#### Proxy Client
Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/Reporting/v11`.

The production endpoint is [https://reporting.api.bingads.microsoft.com/Api/Advertiser/Reporting/v11/ReportingService.svc](https://reporting.api.bingads.microsoft.com/Api/Advertiser/Reporting/v11/ReportingService.svc).

The sandbox endpoint is [https://reporting.api.sandbox.bingads.microsoft.com/Api/Advertiser/Reporting/v11/ReportingService.svc](https://reporting.api.sandbox.bingads.microsoft.com/Api/Advertiser/Reporting/v11/ReportingService.svc).

#### <a name="reporting_downloadedcolumns"></a>Consistency Between WSDL Contract and Downloaded Report Columns
Previously there were some discrepancies between the report column value set names and the names of the columns in the downloaded reports. In Reporting API Version 11 most of the downloaded column names match the requested value. For example now when you submit a [KeywordPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportrequest(v=msads.110).aspx) with the *BidMatchType* value from the [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportcolumn(v=msads.110).aspx) value set, the column name in the downloaded report is also *BidMatchType* in Reporting API Version 11. Previously in version 9, the column name in the downloaded report was *BiddedMatchType*.

> [!NOTE]
> Some download column names in version 11 do not match the version 11 contract. These will be updated in version 12. For more details see each column description in [Report Attributes and Performance Statistics](../concepts/report-attributes-and-performance-statistics.md).

The following column names have changed in the downloaded reports from version 9 to 11.

Version 9|Version 11  
---------|---------
Ad group item Id|AdGroupCriterionId
BiddedMatchType|BidMatchType
MatchType|DeliveredMatchType
Device type|DeviceType
Path 1|Path1
Path 2|Path2
Title Part 1|TitlePart1
Title Part 2|TitlePart2
Search query|SearchQuery

#### <a name="reporting_percentcolumns"></a>Percent Appended to Downloaded Data
A percent symbol (%) is appended to the downloaded report data for the following columns. 

*ClickSharePercent*  
*Ctr*  
*EstimatedClickPercent*  
*EstimatedConversionRate*  
*EstimatedCtr*  
*EstimatedImpressionPercent*  
*ImpressionLostToAdRelevancePercent*  
*ImpressionLostToBidPercent*  
*ImpressionLostToBudgetPercent*  
*ImpressionLostToRankPercent*  
*ImpressionLostToExpectedCtrPercent*  
*ImpressionSharePercent*  
*LowQualityClicksPercent*  
*LowQualityImpressionsPercent*  
*ReturnOnAdSpend*  

The data is still a percentage and has not changed from version 9 to version 11. The only change is the percent symbol. For example in version 9 the download data for *Ctr* might have been *2.13*, and in version 11 it would be *2.13%*.

#### <a name="reporting_timeperiod"></a>TimePeriod Data Format
The date in the *TimePeriod* column download data is now formatted as YYYY-MM-DD. For example May 1, 2017 would be formatted as 2017-05-01. Previously the date was localized e.g. for English report downloads the date was formatted as m/d/yyyy. 


#### <a name="reporting_qualityscoresov"></a>Rename Quality Score and Share of Voice Subscore
Previously some of the Reporting API quality score and share of voice report column value set names did not match the Bing Ads web application. In Reporting API Version 11 the [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-accountperformancereportcolumn(v=msads.110).aspx), [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportcolumn(v=msads.110).aspx), [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportcolumn(v=msads.110).aspx), [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportcolumn(v=msads.110).aspx), and [ShareOfVoicePerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-shareofvoiceperformancereportcolumn(v=msads.110).aspx) value sets are each updated with one or more of the new values, and the new names are also reflected in the downloaded report data i.e. new column header names. 

The following report column values have changed from version 9 to 11.

Version 9|Version 11  
---------|---------
HistoricKeywordRelevance|HistoricExpectedCtr
HistoricLandingPageRelevance|HistoricAdRelevance
HistoricLandingPageUserExperience|HistoricLandingPageExperience
ImpressionLostToKeywordRelevancePercent|ImpressionLostToExpectedCtrPercent
ImpressionLostToLandingPageRelevancePercent|ImpressionLostToAdRelevancePercent
KeywordRelevance|ExpectedCtr
LandingPageRelevance|AdRelevance
LandingPageUserExperience|LandingPageExperience

#### <a name="reporting_renamegeoreports"></a>Rename Geographic and User Location Reports
The following geographic and user location reports have been renamed to clarify their usage and match the Bing Ads web application.

In version 11, the [GeographicPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-geographicperformancereportrequest(v=msads.110).aspx) with corresponding columns and filter replaces the *GeoLocationPerformanceReportRequest*.The geographic performance report shows impressions, clicks, spend, and average cost-per-click for each ad group, organized into columns that show the location used to serve ads. You can see where your traffic is coming from: the physical location of the people searching for your ad or the locations people are searching for. You can then validate whether your location targeting strategy is successful and identify opportunities to improve.

In version 11, the [UserLocationPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-userlocationperformancereportrequest(v=msads.110).aspx) with corresponding columns and filter replaces the *GeographicalLocationReportRequest*. The user location performance report shows impressions, clicks, spend, and average cost-per-click for each ad group, organized by city, country, metro area, radius, state, and account. You can see where your traffic is coming from broken out by the physical location and the location people are searching for. You can then validate whether your location targeting strategy is successful, and identify opportunities to improve.

|Report Request|Report Filter|Report Column|
|-------------|-----------------|-----------------|
|[GeographicPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-geographicperformancereportrequest(v=msads.110).aspx)|[GeographicPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-geographicperformancereportfilter(v=msads.110).aspx)|[GeographicPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-geographicperformancereportcolumn(v=msads.110).aspx)|
|[UserLocationPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-userlocationperformancereportrequest(v=msads.110).aspx)|[UserLocationPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-userlocationperformancereportfilter(v=msads.110).aspx)|[UserLocationPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-userlocationperformancereportcolumn(v=msads.110).aspx)|


#### <a name="reporting_reportdownloadurl"></a>Report Download URL and Empty Reports
Even when the *Status* of the [ReportRequestStatus](https://msdn.microsoft.com/library/bing-ads-reporting-reportrequeststatus(v=msads.110).aspx) object is set to *Success*, the *ReportDownloadUrl* element will be nil if no performance data is available for the submitted report parameters (whether or not header and footer metadata were requested). Previously in version 9 a file that only included header and footer metadata would be returned.


#### <a name="reporting_sunset_bsc_reports"></a>Sunset Product Offer and Product Target Reports
The *ProductOfferPerformanceReportRequest* and *ProductTargetPerformanceReportRequest* with corresponding columns and filters are removed. For Bing Shopping campaigns you should use the [ProductDimensionPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productdimensionperformancereportrequest(v=msads.110).aspx), [ProductPartitionPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportrequest(v=msads.110).aspx), and [ProductPartitionUnitPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionunitperformancereportrequest(v=msads.110).aspx). 

Additionally, the *ProductTarget* column is removed from the [SearchQueryPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-searchqueryperformancereportcolumn(v=msads.110).aspx) value set. 

#### <a name="reporting_sunset_extensiondimension"></a>Sunset Ad Extension Dimension Report
The *AdExtensionDimensionReportRequest* with corresponding columns and filters is removed. Previously in Reporting API Version 9 attempting to submit this report request would throw an exception.

#### <a name="reporting_sunset_analytics"></a>Sunset Campaign Analytics Reports
The *TacticChannelReportRequest* and *TrafficSourcesReportRequest* with corresponding columns and filters are removed. Campaign Analytics was deprecated in October 2016, and data processing ended February 2017. If you are using [Universal Event Tracking](../concepts/universal-event-tracking.md) you can get conversion data with several other reports, for example the [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-accountperformancereportcolumn(v=msads.110).aspx), [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportcolumn(v=msads.110).aspx), [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportcolumn(v=msads.110).aspx), and [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportcolumn(v=msads.110).aspx). 

Additionally the *ExtendedCost*, *FunnelConversionRate*, *Step1*, *Step2*, *Step3*, *Step4*, and *Step5* columns are removed from all related value sets.

#### <a name="reporting_sunset_visits"></a>Sunset Visits and Spend Columns
Based on customer feedback about reporting priorities, the *AverageDurationPerVisit*, *AveragePagesPerVisit*, *BounceRate*, and *TotalVisits* columns are removed from the [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-accountperformancereportcolumn(v=msads.110).aspx), [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportcolumn(v=msads.110).aspx), [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportcolumn(v=msads.110).aspx), and [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportcolumn(v=msads.110).aspx) value sets. 

Additionally the *ReturnOnAdSpend* and *Spend* columns are removed from the [GoalAndFunnelsReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-goalsandfunnelsreportcolumn(v=msads.110).aspx) value set.

#### <a name="reporting_sunset_phonespend"></a>Sunset Phone Spend Columns
There is no charge for call forwarding numbers using Skype, so the *PhoneSpend* and *TotalCostPhoneAndClicks* columns are removed from the [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-accountperformancereportcolumn(v=msads.110).aspx), [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportcolumn(v=msads.110).aspx), [CallDetailReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-calldetailreportcolumn(v=msads.110).aspx), and [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportcolumn(v=msads.110).aspx) value sets. 

#### <a name="reporting_sunset_draft"></a>Sunset Draft Status Filter
The *Draft* status for ad groups was previously sunset in Bing Ads Campaign Management API (draft status removed from ad group status). In turn, the *Draft* value is removed removed from the [AdGroupStatusReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupstatusreportfilter(v=msads.110).aspx) value set.

#### <a name="reporting_sunset_submitted"></a>Sunset Submitted Filter
The *Submitted* status has the same meaning as *Active*, so the *Submitted* value is removed removed from the [AdStatusReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-adstatusreportfilter(v=msads.110).aspx), [AdGroupStatusReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupstatusreportfilter(v=msads.110).aspx), [CampaignStatusReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-campaignstatusreportfilter(v=msads.110).aspx) value sets.  

#### <a name="reporting_sunset_richads"></a>Sunset Rich Ads Report
The rich ads in search feature was already sunset in Bing Ads, and now the *RichAdComponentPerformanceReportRequest* with corresponding columns and filters is removed from the Reporting API. 

Additionally the *Image*, *Mobile*, *RichAd*, *RichMedia*, and *ThirdPartyCreative* values are removed from the [AdTypeReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-adtypereportfilter(v=msads.110).aspx) value set.

#### <a name="reporting_sunset_siteplacements"></a>Sunset Site Performance Report
Site placements are already sunset in Bing Ads, and now the *SitePerformanceReportRequest* with corresponding columns and filters is removed from the Reporting API. 

#### <a name="reporting_sunset_cpm"></a>Cpm Pricing Model
The CPM pricing model is not supported in Bing Ads, so the *AverageCpm* column is removed from the report column value sets. 

The [PricingModelReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-pricingmodelreportfilter(v=msads.110).aspx) value set is removed from the Reporting API and the *PricingModel* element is removed from the the [PublisherUsagePerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-publisherusageperformancereportfilter(v=msads.110).aspx). 


#### <a name="reporting_sunset_keywordmatchtypeid"></a>Sunset KeywordMatchTypeId Column
The keyword by match type migration was completed October 2013. Since Bing Ads does not return data prior to this date, the KeywordMatchTypeId is removed from the [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportcolumn(v=msads.110).aspx) value set. 

### New Features

#### <a name="reporting_excludemetadata"></a>Exclude Report Columns and Metadata
Bing Ads API version 11 now lets you choose whether or not the downloaded report should contain header, column, and footer metadata. You can optionally set any of the *ExcludeColumnHeaders*, *ExcludeReportFooter*, or *ExcludeReportHeader* properties of the [ReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-reportrequest(v=msads.110).aspx) to *true* if you want the corresponding metadata excluded from the downloaded report.
 
