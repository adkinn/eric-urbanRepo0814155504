---
title: "Release Notes"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92fa50dd-e2a6-490d-aaa1-2e02bf108b63
caps.latest.revision: 77
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Release Notes
For information about the changes to the Bing Ads services for each release, see the following sections.

-   [August 2017](#august2017)  
-   [July 2017](#july2017) 
-   [May 2017](#may2017) 
-   [April 2017](#april2017)  
-   [February 2017](#february2017)  
-   [January 2017](#january2017)  
-   [December 2016](#december2016)  
-   [November 2016](#november2016)  
-   [October 2016](#october2016)  
-   [September 2016](#september2016)  

## <a name="august2017"></a>August 2017
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bing Ads Software Development Kit (SDK) Updates](#sdk_august2017)  
-   [Increase in subdomain limit for website exclusions](#negativesites_august2017)

### <a name="sdk_august2017"></a>Bing Ads Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for the following features. Unless otherwise noted the changes only apply to Bing Ads API version 11. Some objects are reserved for future use, so please refer to the service reference documentation for availability details.

* The [Campaign Management](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#inheritedbidstrategytype_july2017) service proxies are updated to support inherited bid strategy type.  
* The [Reporting](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#reporting_bsc_july2017) service proxies are updated to support new columns for Bing Shopping campaigns.
* New version 11 bulk labels objects are added i.e., *BulkLabel*, *BulkCampaignLabel*, *BulkAdGroupLabel*, *BulkKeywordLabel*, *BulkAppInstallAdLabel*, *BulkDynamicSearchAdLabel*, *BulkExpandedTextAdLabel*, *BulkProductAdLabel*, and *BulkTextAdLabel* objects are added to the SDK for reading and writing the corresponding [Bulk file records](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#bulk_v11_labels_july2017).
* A new version 11 bulk offline conversion object is added i.e., the *BulkOfflineConversion* object is added to the SDK for writing and uploading the corresponding [Bulk file record](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#bulk_v11_offline_conversions_july2017).  
* For the Bing Ads .NET SDK - Fixed the mapping for expired ad groups in the *BulkAdGroup* object. Previously if the ad group status in the bulk file was *Expired*, the SDK mapped and returned the value as *Deleted*.  Prior to Bing Ads API version 10, expired ad groups were returned with a deleted status by design for backwards compatibility. 


### <a name="negativesites_august2017"></a>Increase in subdomain limit for website exclusions
The limit of subdomains allowed in a website exclusion increased from two to three, based on customer requests. This will enable you to exclude URLs based on two-part top-level domains (TLDs) such as *.co.uk*. The number of allowed subdirectories remains unchanged at two. 

For example, the following are valid URLs,
*  one.two.three.contoso.com/1/2  
*  www.two.three.contoso.com/1/2  
*  one.two.contoso.co.uk/1/2

The following are invalid URLs:
*  one.two.three.contoso.co.uk/1/2 (too many subdomains)  
*  one.two.three.contoso.com/1/2/3 (too many subdirectories)  

For reference documentation, please see [CampaignNegativeSites](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaignnegativesites.aspx) and [AdGroupNegativeSites](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroupnegativesites.aspx).

## <a name="july2017"></a>July 2017
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Keyword Planner](#keyword_planner_july2017)  
-   [Labels](#labels_july2017)  
-   [Offline Conversion Import](#offline_conversions_july2017)  
-   [New Reporting Columns for Bing Shopping Campaigns](#reporting_bsc_july2017)  
-   [Inherited Bid Strategy Type](#inheritedbidstrategytype_july2017)
-   [Bing Ads Software Development Kit (SDK) Updates](#sdk_july2017)  

### <a name="keyword_planner_july2017"></a>Keyword Planner
Support for keyword planner operations is added. The Keyword Planner was already available in the Bing Ads web application, and now support is added for Bing Ads API version 11.

> [!NOTE]
> Keyword Planner features are currently available to customers in the United States, United Kingdom, Canada, Australia, France, and Germany.

Given a list of existing keywords, the [GetKeywordIdeas](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordideas.aspx) operation suggests new ad groups and keywords based on your existing keywords, website, and product category. You can also request historical statistics for keywords e.g., monthly searches, competition, average CPC, and ad impression share. You can use the returned suggested keyword bids as input to the [GetKeywordTrafficEstimates](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordtrafficestimates.aspx) operation.

The result is a [KeywordIdea](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordidea.aspx) list. Each keyword idea includes historical statistics for keywords e.g., monthly searches, competition, average CPC, and ad impression share. Whereas the Bing Ads web application returns a 12 month average of the historical monthly search counts, each [KeywordIdea](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordidea.aspx) includes a list of monthly search counts. You can use each count individually or average them for parity with the Bing Ads web application's calculation.

Once you have already settled on an initial set of keywords, the [GetKeywordTrafficEstimates](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordtrafficestimates.aspx) operation provides traffic estimates for keywords e.g., average CPC, average position, clicks, CTR, impressions, and total cost. As input you provide the keyword, bid, language, location, and network, with optional campaign budget and negative keyword filters.

The result is a [KeywordEstimate](https://msdn.microsoft.com/library/bing-ads-ad-insight-keywordestimate.aspx) list for each [AdGroupEstimate](https://msdn.microsoft.com/library/bing-ads-ad-insight-adgroupestimate.aspx), which are all nested within one [CampaignEstimate](https://msdn.microsoft.com/library/bing-ads-ad-insight-campaignestimate.aspx). Each keyword estimate includes a minimum and maximum [TrafficEstimate](https://msdn.microsoft.com/library/bing-ads-ad-insight-trafficestimate.aspx). As previously mentioned, the traffic estimates for keywords include average CPC, average position, clicks, CTR, impressions, and total cost.

For more details see the [Keyword Ideas and Traffic Estimates](../concepts/keyword-ideas-and-traffic-estimates.md) technical guide.

### <a name="labels_july2017"></a>Labels
Support for labels is added. Labels let you organize campaigns, ad groups, ads, and keywords into groups based on whatever is important to you. You can then filter and run reports on your labels to get the data that is most meaningful to you.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]

#### <a name="bulk_v11_labels_july2017"></a>Bulk API Version 11 for Labels  
You can use the following Bulk record types to manage labels with the Bulk API.
-   [Label](https://msdn.microsoft.com/library/bing-ads-bulk-label-record.aspx)
-   [Campaign Label](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-label-record.aspx)
-   [Ad Group Label](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-label-record.aspx)
-   [Keyword Label](https://msdn.microsoft.com/library/bing-ads-bulk-keyword-label-record.aspx)
-   [App Install Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-app-install-ad-label-record.aspx)
-   [Dynamic Search Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-dynamic-search-ad-label-record.aspx)
-   [Expanded Text Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-expanded-text-ad-label-record.aspx)
-   [Product Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-product-ad-label-record.aspx)
-   [Text Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-text-ad-label-record.aspx)

#### <a name="campaign_v11_labels_july2017"></a>Campaign Management API Version 11 for Labels  
You can add, delete, get, and update labels ([Label](https://msdn.microsoft.com/library/bing-ads-campaign-management-label.aspx) objects) with the corresponding operations.
-  [AddLabels](https://msdn.microsoft.com/library/bing-ads-campaign-management-addlabels.aspx)  
-  [DeleteLabels](https://msdn.microsoft.com/library/bing-ads-campaign-management-deletelabels.aspx)  
-  [GetLabelsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getlabelsbyids.aspx)  
-  [UpdateLabels](https://msdn.microsoft.com/library/bing-ads-campaign-management-updatelabels.aspx)  

You can set, get, and delete label associations ([LabelAssociation](https://msdn.microsoft.com/library/bing-ads-campaign-management-labelassociation.aspx) objects) with the corresponding operations.
-  [DeleteLabelAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-deletelabelassociations.aspx)  
-  [GetLabelAssociationsByEntityIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getlabelassociationsbyentityids.aspx)  
-  [GetLabelAssociationsByLabelIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getlabelassociationsbylabelids.aspx)  
-  [SetLabelAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-setlabelassociations.aspx)  

### <a name="offline_conversions_july2017"></a>Offline Conversion Import
Support for Offline Conversion Import is added. Use offline conversions to track the full impact and benefit of your search ads. It allows you to import offline conversions derived from a search click back into Bing Ads. 

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]

To set up offine conversion tracking, create an offline conversion goal with the [Campaign Management](#campaign_v11_offline_conversions_july2017) service or via the Bing Ads web application, wait two hours, and then send Bing Ads the offline conversion data with either the [Campaign Management](#campaign_v11_offline_conversions_july2017) service or [Bulk](#bulk_v11_offline_conversions_july2017) service.

You must also enable MSCLKID Auto Tagging. Every time you create a new [OfflineConversionGoal](https://msdn.microsoft.com/library/bing-ads-campaign-management-offlineconversiongoal.aspx) via either the Bing Ads web application or Campaign Management API, the MSCLKID Auto Tagging is enabled automatically. You can enable or disable auto tagging using either the [Campaign Management](#campaign_v11_offline_conversions_july2017) service or [Bulk](#bulk_v11_offline_conversions_july2017) service. 

For more information, see [Tracking offline conversions](https://help.bingads.microsoft.com/#apex/3/en/help:app54554/1/en-US/#ext:ConversionTracking_Load).

#### <a name="bulk_v11_offline_conversions_july2017"></a>Bulk API Version 11 for Offline Conversions  
You can send Bing Ads the offline conversion data by uploading one or more [Offline Conversion](https://msdn.microsoft.com/library/bing-ads-bulk-offline-conversion-record.aspx) Bulk records.

To manage the MSCLKID Auto Tagging, use the *MSCLKID Auto Tagging Enabled* field of the [Account](https://msdn.microsoft.com/library/bing-ads-bulk-account-record.aspx) Bulk record.

#### <a name="campaign_v11_offline_conversions_july2017"></a>Campaign Management API Version 11 for Offline Conversions  

You can manage [OfflineConversionGoal](https://msdn.microsoft.com/library/bing-ads-campaign-management-offlineconversiongoal.aspx) objects with the previously shipped conversion goal service operations e.g. [AddConversionGoals](https://msdn.microsoft.com/library/bing-ads-campaign-management-addconversiongoals.aspx).

You can send Bing Ads the offline conversion data by submitting [OfflineConversion](https://msdn.microsoft.com/library/bing-ads-campaign-management-offlineconversion.aspx) data via the [ApplyOfflineConversions](https://msdn.microsoft.com/library/bing-ads-campaign-management-applyofflineconversions.aspx) operation.

To manage the MSCLKID Auto Tagging, use the corresponding [AccountProperty](https://msdn.microsoft.com/library/bing-ads-campaign-management-accountproperty.aspx) (*MSCLKIDAutoTaggingEnabled*) via the [GetAccountProperties](https://msdn.microsoft.com/library/bing-ads-campaign-management-getaccountproperties.aspx) and [SetAccountProperties](https://msdn.microsoft.com/library/bing-ads-campaign-management-setaccountproperties.aspx) operations. 

### <a name="reporting_bsc_july2017"></a>New Reporting Columns for Bing Shopping Campaigns
The *ReturnOnAdSpend*, *BidStrategyType*, *LocalStoreCode*, and *StoreId* columns have been added to the [ProductDimensionPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productdimensionperformancereportcolumn.aspx) value set.

The *ReturnOnAdSpend*, *BidStrategyType*, and *LocalStoreCode* columns have been added to the [ProductPartitionPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportcolumn.aspx) value set.

The *ReturnOnAdSpend*, *BidStrategyType*, and *LocalStoreCode* columns have been added to the [ProductPartitionUnitPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionunitperformancereportcolumn.aspx) value set.

### <a name="inheritedbidstrategytype_july2017"></a>Inherited Bid Strategy Type
You can get the bid strategy type that is inherited from each ad group or keyword's parent campaign or ad group. This value is equal to the parent campaign or ad group's *Bid Strategy Type* field. Possible values are *EnhancedCpc*, *ManualCpc*, *MaxClicks*, *MaxConversions*, and *TargetCpa*.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]

#### <a name="bulk_v11_inheritedbidstrategytype_july2017"></a>Bulk API Version 11 for Inherited Bid Strategy Type  
The *Inherited Bid Strategy Type* field is added to the [Ad Group](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-record.aspx) and [Keyword](https://msdn.microsoft.com/library/bing-ads-bulk-keyword-record.aspx) records. 

#### <a name="campaign_v11_inheritedbidstrategytype_july2017"></a>Campaign Management API Version 11 for Inherited Bid Strategy Type  
The *InheritedBidStrategyType* element is added to the  [InheritFromParentBiddingScheme](https://msdn.microsoft.com/library/bing-ads-campaign-management-inheritfromparentbiddingscheme.aspx) object. This element is not returned by default. You must include *InheritedBidStrategyType* in the *ReturnAdditionalFields* optional request element when calling [GetAdGroupsByCampaignId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupsbycampaignid.aspx), [GetAdGroupsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupsbyids.aspx), [GetKeywordsByAdGroupId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getkeywordsbyadgroupid.aspx), [GetKeywordsByEditorialStatus](https://msdn.microsoft.com/library/bing-ads-campaign-management-getkeywordsbyeditorialstatus.aspx), and [GetKeywordsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getkeywordsbyids.aspx).


### <a name="sdk_july2017"></a>Bing Ads Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for the following features. Unless otherwise noted the changes only apply to Bing Ads API version 11. Some objects are reserved for future use, so please refer to the service reference documentation for availability details.

#### <a name="sdk_breaking_changes_july2017"></a>Breaking Changes
> [!IMPORTANT]
> Before you upgrade to the latest SDK please note the following breaking changes.
* The *Status* property of the *BulkCampaignProductScope* object is removed. The Bulk file *Status* field is now mapped to the *Status* element of the *BiddableCampaignCriterion* of the *BulkCampaignProductScope*. 
* All BulkEntity derived SDK objects (except *BulkAdGroupProductPartition*) which previously contained the *AdGroupCriterion* or *CampaignCriterion* property are updated as either Biddable or Negative. Both the type and the name are updated e.g. *BulkAdGroupAgeCriterion* has property name *BiddableAdGroupCriterion* and data type *BiddableAdGroupCriterion*. The purpose is to be clear about the supported data type per bulk entity up front, rather than causing friction later i.e., runtime errors due to mismatch of BulkEntity to concrete criterion type. Several bulk entities were updated during the May 2017 release; and the remaining mappings are fixed with this release.

#### <a name="sdk_non_breaking_changes_july2017"></a>Non Breaking Changes
* The [Ad Insight](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#keyword_planner_july2017) service proxies are updated to support the keyword planner. 
* The [Bulk](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#bulk_v11_labels_july2017) service proxies are updated to support labels.
* The [Campaign Management](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#campaign_v11_labels_july2017) service proxies are updated to support labels.  
* The [Bulk](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#bulk_v11_offline_conversions_july2017) service proxies are updated to support offline conversions.
* The [Campaign Management](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#campaign_v11_offline_conversions_july2017) service proxies are updated to support offline conversions.  
* Support is added for Bulk entity mapping of [multiple campaign languages](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#campaign_languages_february2017) i.e., updated mapping of the *Language* field in the Bulk file to the *BulkCampaign* and *BulkAdGroup*. **Note:** Support is added for Bing Ads API version 10 and 11.
* Support is added for Bulk entity mapping of MaxConversions, MaxCpc, and TargetCpa bid strategy types i.e., mapping of the *Bid Strategy Type*, *Bid Strategy MaxCpc*, and *Bid Strategy TargetCpa* fields in the Bulk file to the *BulkCampaign*. **Note:** Support is added for Bing Ads API version 10 and 11.
* Support is added for Bulk entity mapping of LocalInventoryAdsEnabled for Bing Shopping campaigns i.e., mapping of the *LocalInventoryAdsEnabled* field in the Bulk file to the *BulkCampaign*.
* Performance data mapping is added to the *BulkAdGroupRemarketingListAssociation* object.
* New version 11 bulk audience objects are added i.e., *BulkAdGroupNegativeRemarketingListAssociation*, *BulkCustomAudience*, *BulkAdGroupCustomAudience*, *BulkAdGroupNegativeCustomAudience*, *BulkInMarketAudience*, *BulkAdGroupInMarketAudience*, and *BulkAdGroupNegativeInMarketAudience* objects are added to the SDK for reading and writing the corresponding Bulk file records.
* New version 11 bulk price ad extension objects are added i.e., *BulkPriceAdExtension*, *BulkCampaignPriceAdExtension*, and *BulkAdGroupPriceAdExtension* objects are added to the SDK for reading and writing the corresponding Bulk file records.
* New version 11 bulk account level ad extension objects are added i.e., *BulkAccountAppAdExtension*, *BulkAccountCalloutAdExtension*, *BulkAccountImageAdExtension*, *BulkAccountLocationAdExtension*, *BulkAccountPriceAdExtension*, *BulkAccountReviewAdExtension*, and *BulkAccountSitelink2AdExtension* objects are added to the SDK for reading and writing the corresponding Bulk file records.

## <a name="may2017"></a>May 2017
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bing Ads API Version 11 General Availability](#v11_ga_may2017)  
-   [Bing Ads Software Development Kit (SDK) Updates](#sdk_may2017)  
-   [Dynamic Search Ads Reports](#reporting_v11_dsa_may2017)  

### <a name="v11_ga_may2017"></a>Bing Ads API Version 11 General Availability
Bing Ads API Version 11 is released to production. For more details, see [Migrating to Bing Ads API Version 11](../concepts/migrating-to-bing-ads-api-version-11.md) and [Version 11 API Reference](../concepts/version-11-api-reference.md).

[!INCLUDE[v10_sunset](../concepts/includes/v10-sunset.md)]

### <a name="sdk_may2017"></a>Bing Ads PHP Software Development Kit (SDK)
The Bing Ads .NET, Java, and PHP SDKs are updated with support for Bing Ads API Version 11 [web service addresses](../concepts/bing-ads-web-service-addresses.md). This release enables you to [upgrade](../concepts/migrating-to-bing-ads-api-version-11.md) existing features from version 9 and 10 to version 11. 

Bulk entity support for new version 11 features e.g. *BulkPriceAdExtension* will be added to the .NET, Java, and Python SDKs in a future release.

### <a name="reporting_v11_dsa_may2017"></a>Dynamic Search Ads Reports
The the following reports are added for Dynamic Search Ads.

|Report Request|Report Filter|Report Column|
|-------------|-----------------|-----------------|
|[DSAAutoTargetPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-dsaautotargetperformancereportrequest.aspx)|[DSAAutoTargetPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-dsaautotargetperformancereportfilter.aspx)|[DSAAutoTargetPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-dsaautotargetperformancereportcolumn.aspx)|
|[DSACategoryPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-dsacategoryperformancereportrequest.aspx)|[DSACategoryPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-dsacategoryperformancereportfilter.aspx)|[DSACategoryPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-dsacategoryperformancereportcolumn.aspx)|
|[DSASearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-dsasearchqueryperformancereportrequest.aspx)|[DSASearchQueryPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-dsasearchqueryperformancereportfilter.aspx)|[DSASearchQueryPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-dsasearchqueryperformancereportcolumn.aspx)|


## <a name="april2017"></a>April 2017
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bing Ads API Version 11 Preview](#v11_preview_april2017)  
-   [Bing Ads PHP Software Development Kit (SDK)](#php_sdk_april2017)  
-   [Bing Shopping Product Search Query Performance Report](#productsearchqueryperformancereport_april2017)  

### <a name="v11_preview_april2017"></a>Bing Ads API Version 11 Preview
A preview of the Bing Ads API Version 11 is released to sandbox. For more details, see [Migrating to Bing Ads API Version 11](../concepts/migrating-to-bing-ads-api-version-11.md) and [Version 11 API Reference](../concepts/version-11-api-reference.md).

### <a name="php_sdk_april2017"></a>Bing Ads PHP Software Development Kit (SDK)
The Bing Ads PHP SDK is now available. 

For details please see the [blog post](https://blogs.msdn.microsoft.com/bing_ads_api/2017/04/05/announcing-bing-ads-php-sdk/) and [Getting Started Using PHP with Bing Ads Services](../concepts/getting-started-using-php-with-bing-ads-services.md).

### <a name="productsearchqueryperformancereport_april2017"></a>Bing Shopping Product Search Query Performance Report
The Product Search Query performance report is now available for Bing Shopping Campaigns. Submit the [ProductPartitionPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportrequest.aspx) to see what your audience is searching for when your product ads are shown.

## <a name="february2017"></a>February 2017
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Campaign and Ad Group Languages](#campaign_languages_february2017)
-   [New Reporting Columns for Bing Shopping Campaigns](#reporting_v9_bsc_february2017)
-   [Software Development Kit (SDK) Updates](#sdk_february2017)

### <a name="campaign_languages_february2017"></a>Campaign and Ad Group Languages

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]

Starting in late Q1 or early Q2 calendar year 2017, Bing Ads will begin piloting a new feature to support multiple languages at the campaign level. If languages are set at both the ad group and campaign level, the ad group-level language will override the campaign-level language. The customer is enabled for the pilot if the [GetCustomerPilotFeatures](https://msdn.microsoft.com/library/bing-ads-customer-management-getcustomerpilotfeatures.aspx) response includes pilot number *310*. 

**IMPORTANT:** Pilot participants will be able to set multiple languages at the campaign level, and will be able to delete the ad group level language. If your application depends on ad group language being set, then you must prepare for the possibility that ad group language will be empty. More specific dates and implementation details will be provided later through the [Bing Ads API Blog](https://blogs.msdn.microsoft.com/bing_ads_api/), and in the meantime you should update your application right away to support the change. 

Also note that as a one time migration when the customer is added to pilot, campaign languages are set to the union of all individual ad group languages. For example if you have three ad groups with language set to *English*, *German*, and *French*, then at the time of pilot enablement this campaign's languages will be set to a list including *English*, *German*, and *French*.

#### <a name="bulk_v10_february2017"></a>Bulk Version 10
For details about how to add and update campaign and ad group languages using the Bulk API, see the [Campaign](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-record.aspx) and [Ad Group](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-record.aspx) reference documentation.  

#### <a name="campaign_v10_february2017"></a>Campaign Management Version 10
For details about how to add and update campaign and ad group languages using the Campaign Management API, see the [Campaign](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaign.aspx) and [AdGroup](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroup.aspx) reference documentation.  

### <a name="reporting_v9_bsc_february2017"></a>New Reporting Columns for Bing Shopping Campaigns
The *AdDistribution* and *TopVsOther* columns have been added to the [ProductDimensionPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productdimensionperformancereportcolumn.aspx) value set. The *AdDistribution* column has been added to the [ProductPartitionPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportcolumn.aspx) value set.

### <a name="sdk_february2017"></a>Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for bulk upload of remarketing lists using the *BulkRemarketingList* class. Upload is [already supported by the Bulk service](#bulk_v10_remarketing_december2016), and now the SDK is also enabled.

## <a name="january2017"></a>January 2017
For information about the changes to the Bing Ads services included in this release, see the following sections.
-   [Remarketing List Exclusions](#remarketing_january2017)

### <a name="remarketing_january2017"></a>Remarketing List Exclusions
Remarketing in Paid Search lets you improve your return on investment by optimizing your campaigns for specific audiences, which are the people who have visited your website before. In a previous release we only supported ad group remarketing list associations. Support is now added to the Campaign Management API for ad group remarketing list exclusions. For example you might want to include all users who visited a page within the last 60 days but not those who visited last week. For more information about Remarketing APIs, see the [UET and Remarketing Guide](https://msdn.microsoft.com/library/bing-ads-universal-event-tracking-guide.aspx#remarketing). 

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]

> [!NOTE]
> Remarketing list exclusions are not supported with the Bulk API. You can use the Campaign Management API to set exclusions.

#### <a name="campaign_v10_remarketing_january2017"></a>Campaign Management API for Remarketing List Exclusions
The *IsExcluded* element of the [AdGroupRemarketingListAssociation](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroupremarketinglistassociation.aspx) object is now supported. If this element is set to *True*, then the [AdGroupRemarketingListAssociation](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroupremarketinglistassociation.aspx) is an exclusion, and otherwise the audience is included. 

To add, get, update, or delete the [AdGroupRemarketingListAssociation](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroupremarketinglistassociation.aspx) between your remarketing list and ad group (whether associations or exclusions), use the respective [AddAdGroupRemarketingListAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupremarketinglistassociations.aspx), [GetAdGroupRemarketingListAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupremarketinglistassociations.aspx), [UpdateAdGroupRemarketingListAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateadgroupremarketinglistassociations.aspx), and [DeleteAdGroupRemarketingListAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteadgroupremarketinglistassociations.aspx) operations. 

> [!NOTE]
> With [GetAdGroupRemarketingListAssociations](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupremarketinglistassociations.aspx), the inclusive ad group remarketing list associations will always be returned. If you set the *ReturnExclusions* request element to *True* then ad group remarketing list exclusions will also be returned in the list of results.

## <a name="december2016"></a>December 2016
For information about the changes to the Bing Ads services included in this release, see the following sections.
-   [Add and Modify Remarketing Lists](#remarketing_december2016)
-   [Dynamic Search Ads](#dsa_december2016)
-   [Geographical Location Codes Breaking Changes](#geolocationsbreakingchanges_december2016)
-   [Get Geographical Location Codes for Targeting](#campaign_v10_geolocations_december2016)
-   [New Reporting Columns for Bing Shopping Campaigns](#reporting_v9_bsc_december2016)
-   [Software Development Kit (SDK) Updates](#sdk_december2016)

### <a name="remarketing_december2016"></a>Add and Modify Remarketing  Lists
Remarketing in Paid Search lets you improve your return on investment by optimizing your campaigns for specific audiences, which are the people who have visited your website before. In a previous release we only supported adding and modifying the ad group remarketing list associations. Support is now added to the Campaign Management and Bulk APIs for adding, updating, and deleting remarketing lists. For more information about Remarketing APIs, see the [UET and Remarketing Guide](https://msdn.microsoft.com/library/bing-ads-universal-event-tracking-guide.aspx#remarketing). 

#### <a name="bulk_v10_remarketing_december2016"></a>Bulk API for Remarketing Lists
Upload support is added for the [Remarketing List](https://msdn.microsoft.com/library/bing-ads-bulk-remarketing-list-record.aspx) Bulk record. 

The *Template* field is added for both Bulk download and upload. Previously the *Template* field was not included in the downloaded [Remarketing List](https://msdn.microsoft.com/library/bing-ads-bulk-remarketing-list-record.aspx) record. You can use the *Template* field to set the remarketing rule with conditions used to determine who to add to your remarketing list. For example you can set custom events or page visitors rules. 

#### <a name="campaign_v10_remarketing_december2016"></a>Campaign Management API for Remarketing Lists
The respective [AddRemarketingLists](https://msdn.microsoft.com/library/bing-ads-campaign-management-addremarketinglists(MSADS.100).aspx), [UpdateRemarketingLists](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateremarketinglists(MSADS.100).aspx), and [DeleteRemarketingLists ](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteremarketinglists(MSADS.100).aspx) operations are supported for adding, updating, and deleting [RemarketingList](https://msdn.microsoft.com/library/bing-ads-campaign-management-remarketinglist(MSADS.100).aspx) objects.

The *Rule* element is added to the [RemarketingList](https://msdn.microsoft.com/library/bing-ads-campaign-management-remarketinglist(MSADS.100).aspx) object. A rule includes conditions used to determine who to add to your remarketing list. You can choose one of the four types of rules to target different audiences: [CustomEventsRule](https://msdn.microsoft.com/library/bing-ads-campaign-management-customeventsrule(MSADS.100).aspx), [PageVisitorsRule](https://msdn.microsoft.com/library/bing-ads-campaign-management-pagevisitorsrule(MSADS.100).aspx), [PageVisitorsWhoDidNotVisitAnotherPageRule](https://msdn.microsoft.com/library/bing-ads-campaign-management-pagevisitorswhodidnotvisitanotherpagerule(MSADS.100).aspx), and [PageVisitorsWhoVisitedAnotherPageRule](https://msdn.microsoft.com/library/bing-ads-campaign-management-pagevisitorswhovisitedanotherpagerule(MSADS.100).aspx). The *Rule* element is not returned in the [RemarketingList](https://msdn.microsoft.com/library/bing-ads-campaign-management-remarketinglist(MSADS.100).aspx) object by default. You must include *Rule* in the optional *ReturnAdditionalFields* flags when calling the [GetRemarketingLists](https://msdn.microsoft.com/library/bing-ads-campaign-management-getremarketinglists(MSADS.100).aspx) operation. 

### <a name="dsa_december2016"></a>Dynamic Search Ads 
Dynamic Search Ads are coming to Bing Ads. You will be able to create a new type of campaign where the ad copy is automatically generated from the content on your website. A preview of the Bulk APIs are now available as described in the next section. A preview of the Campaign Management APIs for DSA was released in [September](#dsa_september2016).

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]
> 
> Before you can use dynamic search ads, you must upgrade to Final Urls. For more information, see [URL Tracking with Upgraded URLs](https://msdn.microsoft.com/library/bing-ads-tracking-template-urls-guide.aspx).

#### <a name="bulk_v10_dsa_december2016"></a>Bulk API for Dynamic Search Ads  
The following Bulk records are added for managing dynamic search ads campaigns.
* [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record.aspx)
* [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record.aspx)
* [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record.aspx)
* [Dynamic Search Ad](https://msdn.microsoft.com/library/bing-ads-bulk-dynamic-search-ad-record.aspx)
 
To get started with dynamic search ads, first you'll need to define a [Campaign](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-record.aspx) record with the *Campaign Type* field set to *DynamicSearchAds*. When you create the campaign, you'll also need to specify the *Domain Language* and *Website* fields.  

Next, define an [Ad Group](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-record.aspx) within the dynamic search ads campaign. You can add one or more [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record.aspx) records for the parent ad group that helps determine whether or not to serve dynamic search ads. 

If you want to exclude certain portions of your website, you can add negative targets at the campaign and/or ad group level using the respective [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record.aspx) and [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record.aspx) records. The [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record.aspx) at the campaign level applies to all ad groups within the campaign; however, if you define ad group level [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record.aspx), the campaign target is ignored for that ad group. 

For any of the [Ad Group Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-dynamic-search-ad-target-record.aspx), [Ad Group Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-negative-dynamic-search-ad-target-record.aspx), and [Campaign Negative Dynamic Search Ad Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-negative-dynamic-search-ad-target-record.aspx) records, you can choose whether you want the target argument to match partial URLs, page content, page title, or categories that Bing thinks applies to your website. To discover the categories that you can use for targets (positive or negative), call the [GetDomainCategories](https://msdn.microsoft.com/library/bing-ads-ad-insight-getdomaincategories.aspx) operation with the Ad Insight service.

Finally you can define a [Dynamic Search Ad](https://msdn.microsoft.com/library/bing-ads-bulk-dynamic-search-ad-record.aspx) record assigned to the ad group. The ad title and display URL are generated automatically based on the website domain and language that you want to target.

### <a name="geolocationsbreakingchanges_december2016"></a>Geographical Location Codes Breaking Changes
Starting Monday December 19th, we require updated target codes for the US postal codes listed below. If you have targets defined in one or more of these locations, please make sure to update them in your application so that your ads may serve correctly in these locations. If you attempt to add or update targets with the deprecated codes, the operation will return an error. When you retrieve targets the new target code will be returned.

Postal Code  |Deprecated Target Code  |New Target Code  
---------|---------|---------
03804	|03804, ME US	|03804, NH US
20389	|20389, MD US	|20389, DC US
20310	|20310, VA US	|20310, DC US
20406	|20406, VA US	|20406, DC US
20207	|20207, MD US	|20207, DC US
20330	|20330, VA US	|20330, DC US
45298	|45298, KY US	|45298, OH US
45277	|45277, KY US	|45277, OH US
20069	|20069, VA US	|20069, DC US
20041	|20041, VA US	|20041, DC US
20599	|20599, MD US	|20599, DC US
20453	|20453, VA US	|20453, DC US
20070	|20070, VA US	|20070, DC US
20206	|20206, VA US	|20206, DC US
20301	|20301, VA US	|20301, DC US
20350	|20350, VA US	|20350, DC US
20233	|20233, MD US	|20233, DC US
40843	|40843, KY US	|40843, VA US
20058	|20058, MD US	|20058, DC US

Please reach out to [support](https://advertise.bingads.microsoft.com/bing-ads-support), the [Bing Ads API Development Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=BingAds), or your account manager if you have any questions or concerns.

### <a name="campaign_v10_geolocations_december2016"></a>Get Geographical Location Codes for Targeting
The [GetGeoLocationsFileUrl](https://msdn.microsoft.com/library/bing-ads-campaign-management-getgeolocationsfileurl.aspx) operation is now available with the Campaign Management service. The operation returns a temporary URL that you can use to download a file that contains the supported geographical location targeting codes.

### <a name="reporting_v9_bsc_december2016"></a>New Reporting Columns for Bing Shopping Campaigns
The *BenchmarkBid*, *BenchmarkCtr*, *ImpressionLostToBudgetPercent*, *ImpressionLostToRankPercent*, and *ImpressionSharePercent* columns have been added to the [ProductDimensionPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productdimensionperformancereportcolumn.aspx) and [ProductPartitionPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportcolumn.aspx) value sets.

### <a name="sdk_december2016"></a>Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for the following features.
* The [Campaign Management](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#campaign_v10_remarketing_december2016) service proxies are updated to support adding and updating remarketing lists.
* The [Campaign Management](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#campaign_v10_geolocations_december2016) service proxies are updated to support the [GetGeoLocationsFileUrl](https://msdn.microsoft.com/library/bing-ads-campaign-management-getgeolocationsfileurl.aspx) operation. 
* The [Reporting](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#reporting_v9_bsc_december2016) service proxies are updated to support new columns for Bing Shopping campaigns. 
* The *BulkAdGroupDynamicSearchAdTarget*, *BulkAdGroupNegativeDynamicSearchAdTarget*, *BulkCampaignNegativeDynamicSearchAdTarget*, and *BulkDynamicSearchAd* objects are added to the SDK for reading and writing the corresponding [Dynamic Search Ads](#bulk_v10_dsa_december2016) Bulk file records.
* The Java and Python SDKs are updated to support encoded redirection URI per the Github community [pull request](https://github.com/BingAds/BingAds-Python-SDK/pull/42). 

## <a name="november2016"></a>November 2016
For information about the changes to the Bing Ads services included in this release, see the following sections.
-   [New Reporting Columns for Low Quality Clicks](#reporting_v9_lowqualityclicks_november2016)

### <a name="reporting_v9_lowqualityclicks_november2016"></a>New Reporting Columns for Low Quality Clicks
The *LowQualityGeneralClicks* and *LowQualitySophisticatedClicks* columns have been added to the [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-accountperformancereportcolumn.aspx) and [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportcolumn.aspx) value sets.

## <a name="october2016"></a>October 2016
For information about the changes to the Bing Ads services included in this release, see the following sections.
-   [Expanded Device Targeting](#devicetarget_october2016)

### <a name="devicetarget_october2016"></a>Expanded Device Targeting 
We are now giving you more control in setting bid adjustments by device, so you can more effectively manage your campaigns across each device type. Most significantly, you will be able to target tablets separately from PC with different bid adjustments. We are expanding the range to +900% for each device type – PC, Tablet, and Mobile, as well as adding the ability to completely opt out (set to -100%) from displaying ads on Tablet and Mobile. 

#### <a name="bulk_v10_devicetarget_october2016"></a>Bulk API for Expanded Device Targeting
You can use the *Bid Adjustment* field within the following Bulk record types to manage device targeting with the Bulk API.
-   [Ad Group DeviceOS Target](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-deviceos-target-record.aspx)
-   [Campaign DeviceOS Target](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-deviceos-target-record.aspx)

#### <a name="campaign_v10_devicetarget_october2016"></a>Campaign Management API for Expanded Device Targeting 
You can use *BidAdjustment* element of the [DeviceOSTargetBid](https://msdn.microsoft.com/library/bing-ads-campaign-management-deviceostargetbid.aspx) object to manage device targeting with the Campaign Management API.

## <a name="september2016"></a>September 2016
For information about the changes to the Bing Ads services included in this release, see the following sections.
-   [Dynamic Search Ads](#dsa_september2016)
-   [Software Development Kit (SDK) Updates](#sdk_september2016)

### <a name="dsa_september2016"></a>Dynamic Search Ads 
Dynamic Search Ads are coming to Bing Ads. You will be able to create a new type of campaign where the ad copy is automatically generated from the content on your website. A preview of the Campaign Management APIs are now available.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]
> 
> Before you can use dynamic search ads, you must upgrade to Final Urls. For more information, see [URL Tracking with Upgraded URLs](https://msdn.microsoft.com/library/bing-ads-tracking-template-urls-guide.aspx).

#### <a name="campaign_v10_dsa_september2016"></a>Campaign Management API for Dynamic Search Ads  

To get started with dynamic search ads, first you'll need to [add](https://msdn.microsoft.com/library/bing-ads-campaign-management-addcampaigns.aspx) a new [Campaign](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaign.aspx) with its type set to *DynamicSearchAds*. When you create the campaign, you'll need to include a [DynamicSearchAdsSetting](https://msdn.microsoft.com/library/bing-ads-campaign-management-dynamicsearchadssetting.aspx) that specifies the target website domain and language. The new *DynamicSearchAds* value is added to the [CampaignType](https://msdn.microsoft.com/library/bing-ads-campaign-management-campaigntype.aspx) value set. 

Next, [create](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroups.aspx) a new [AdGroup](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroup.aspx) within the dynamic search ads campaign. You can add one or more [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion to each ad group that helps determine whether or not to serve dynamic search ads, by calling the [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions.aspx) operation. 

If you want to exclude certain portions of your website, you can add negative [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion at the campaign and/or ad group level using the respective [AddCampaignCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addcampaigncriterions.aspx) and [AddAdGroupCriterions](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroupcriterions.aspx) service operations. The negative [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion at the campaign level applies to all ad groups within the campaign; however, if you define ad group level negative [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion, the campaign criterion is ignored for that ad group. 

Whether the criterion is positive or negative, you can choose whether you want the criterion argument to match partial URLs, page content, page title, or categories that Bing thinks applies to your website. To discover the categories that you can use for [Webpage](https://msdn.microsoft.com/library/bing-ads-campaign-management-webpage.aspx) criterion (positive or negative), use the [GetDomainCategories](https://msdn.microsoft.com/library/bing-ads-ad-insight-getdomaincategories.aspx) operation with the Ad Insight service.

Finally you can [add](https://msdn.microsoft.com/library/bing-ads-campaign-management-addads.aspx) a [DynamicSearchAd](https://msdn.microsoft.com/library/bing-ads-campaign-management-dynamicsearchad.aspx) into the ad group. The ad title and display URL are generated automatically based on the website domain and language that you want to target.

### <a name="sdk_september2016"></a>Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for the following features.
* Service proxies are added to the [Campaign Management](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#campaign_v10_dsa_september2016) API for managing Dynamic Search Ads campaigns. 

	
