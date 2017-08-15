---
title: "Migrating from Bing Ads API Version 9 to Version 10"
ms.custom: na
ms.date: "08/08/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: e20c8a1b-78b6-431f-bb68-61ec4dc93c74
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
robots: noindex,nofollow
---
# Migrating from Bing Ads API Version 9 to Version 10
You should use version 10 of the [Ad Insight](http://msdn.microsoft.com/library/d8263375-08db-4c6d-adb8-feeef5332669), [Bulk](http://msdn.microsoft.com/library/893b4696-c081-473c-b726-08f9ccce4cf7), and [Campaign Management](http://msdn.microsoft.com/library/5f50ed8a-6bca-4d30-8340-7290bc074f0e) services. The Ad Intelligence, Bulk, Campaign Management, and Optimizer Version 9 services were sunset [!INCLUDE[v9_sunset](../guides/includes/v9_sunset.md)].

You should use version 9 of the [Customer Billing](https://msdn.microsoft.com/library/bing-ads-customer-billing-api-reference(v=msads.90).aspx), [Customer Management](https://msdn.microsoft.com/library/bing-ads-customer-management-api-reference(v=msads.90).aspx), and [Reporting](https://msdn.microsoft.com/library/bing-ads-reporting-service-reference(v=msads.90).aspx) services.

For information about what’s changed from version 9 to version 10, see the following sections.

-   [Ad Insight (Ad Intelligence and Optimizer Merged)](#adinsight)

-   [Bulk](#bulk)

-   [Campaign Management](#campaign)

## <a name="adinsight"></a>Ad Insight (Ad Intelligence and Optimizer Merged)
> [!IMPORTANT]
> The Ad Intelligence and Optimizer services that were available in [!INCLUDE[brand](../guides/includes/brand.md)] API Version 9 are merged together and named  Ad Insight in [!INCLUDE[brand](../guides/includes/brand.md)] API Version 10.

### Breaking Changes

#### Proxy Client
The Ad Intelligence and Optimizer services that were available in [!INCLUDE[brand](../guides/includes/brand.md)] API Version 9 are merged together and named  Ad Insight [!INCLUDE[brand](../guides/includes/brand.md)] API Version 10.

Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/AdInsight/v10`.

The production endpoint is [https://adinsight.api.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc](https://adinsight.api.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc).

The sandbox endpoint is [https://adinsight.api.sandbox.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc](https://adinsight.api.sandbox.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc).

#### Moved to Ad Insight from the Optimizer Service
These service operations have been moved from the version 9 Optimizer service to the new Ad Insight service.

-   [GetBidOpportunities](http://msdn.microsoft.com/library/eb61e4cc-4f38-4442-995a-e5ce0663e56d)

-   [GetBudgetOpportunities](http://msdn.microsoft.com/library/1cad7317-7f04-4d8e-8584-99fc245c184d)

-   [GetKeywordOpportunities](http://msdn.microsoft.com/library/b6ef9a22-d068-46d0-b9ca-34cc83bbc216)

These data objects have been moved to the new Ad Insight service.

-   [BidOpportunity](http://msdn.microsoft.com/library/618912fc-8288-448c-a530-9adce1f662ff)

    **Note:** The `CampaignId` element is added to [BidOpportunity](http://msdn.microsoft.com/library/618912fc-8288-448c-a530-9adce1f662ff) so you can map each opportunity to the ad group's campaign.

-   [BroadMatchKeywordOpportunity](http://msdn.microsoft.com/library/f78e2f02-12eb-47d1-8708-eeadd8b53909)

-   [BroadMatchSearchQueryKPI](http://msdn.microsoft.com/library/f330d946-efac-4729-bbab-d57917a939ab)

-   [BudgetOpportunity](http://msdn.microsoft.com/library/71378754-9fe7-4baa-be66-7a2c2005ec62)

-   [BudgetPoint](http://msdn.microsoft.com/library/acc6ba96-72db-4727-9c22-0c6099dd5590)

-   [KeywordOpportunity](http://msdn.microsoft.com/library/7843acf6-03af-471f-89e5-477556133b67)

-   [Opportunity](http://msdn.microsoft.com/library/62cbb136-f435-43f9-ba76-ae2aee57d17b)

These value sets have been moved to the new Ad Insight service.

-   [BidOpportunityType](http://msdn.microsoft.com/library/f8c8bfc4-9937-4a7a-9446-0aa0e6fab643)

-   [BudgetLimitType](http://msdn.microsoft.com/library/80f6136f-038f-428d-8bd8-c21d0ff77371)

-   [BudgetPointType](http://msdn.microsoft.com/library/77f02cbe-fcb5-47de-a351-90402e055b88)

-   [KeywordOpportunityType](http://msdn.microsoft.com/library/d1eabe94-4667-4079-9856-1850c076bb6b)

#### Optimizer Features Sunset
These service operations will sunset with version 9 of the Optimizer service.

-   `ApplyOpportunities`

    **Note:** To apply the suggested bid, budget, and keyword opportunities, you can use the update operations provided with the [Bulk](http://msdn.microsoft.com/library/893b4696-c081-473c-b726-08f9ccce4cf7) or [Campaign Management](http://msdn.microsoft.com/library/5f50ed8a-6bca-4d30-8340-7290bc074f0e) services.

-   `GetBudgetLandscape`

    **Note:** Budget landscape data is available in the new [Ad Insight](http://msdn.microsoft.com/library/d8263375-08db-4c6d-adb8-feeef5332669) service. The response for [GetBudgetOpportunities](http://msdn.microsoft.com/library/1cad7317-7f04-4d8e-8584-99fc245c184d) now includes a list of [BudgetPoint](http://msdn.microsoft.com/library/acc6ba96-72db-4727-9c22-0c6099dd5590) objects.

These data objects will sunset with version 9 of the Optimizer service.

-   `BidOpportunityModifier`

-   `BroadMatchOpportunityModifier`

-   `BudgetLandscapePoint`

-   `BudgetOpportunityModifier`

-   `CampaignBudgetLandscape`

-   `KeywordOpportunityModifier`

-   `OpportunityModifier`

#### Budget Landscape
The `GetBudgetLandscape` operation is not carried forward with Ad Insight version 10, and will be sunset with version 9 of the Optimizer service.

With Ad Insight version 10, you can get budget landscape data using the [GetBudgetOpportunities](http://msdn.microsoft.com/library/1cad7317-7f04-4d8e-8584-99fc245c184d) operation. Each returned [BudgetOpportunity](http://msdn.microsoft.com/library/71378754-9fe7-4baa-be66-7a2c2005ec62) now includes `BudgetPoints`, which is a list of [BudgetPoint](http://msdn.microsoft.com/library/acc6ba96-72db-4727-9c22-0c6099dd5590) objects representing the budget landscape.

In version 10, each [BudgetPoint](http://msdn.microsoft.com/library/acc6ba96-72db-4727-9c22-0c6099dd5590) includes weekly impressions, clicks, and cost estimates instead of the daily estimates provided in version 9.

#### Opportunity Expiration Date
The `ExpirationDate` element is removed from the [Opportunity](http://msdn.microsoft.com/library/62cbb136-f435-43f9-ba76-ae2aee57d17b) object. Expired opportunities will not be returned by the Ad Insight service.

#### Bid Opportunity Type
The `IncreaseTraffic` value is removed from the [BidOpportunityType](http://msdn.microsoft.com/library/f8c8bfc4-9937-4a7a-9446-0aa0e6fab643) value set.

#### Opportunities by Account
The `AccountId` request element is removed from the [GetBidOpportunities](http://msdn.microsoft.com/library/eb61e4cc-4f38-4442-995a-e5ce0663e56d), [GetBudgetOpportunities](http://msdn.microsoft.com/library/1cad7317-7f04-4d8e-8584-99fc245c184d), and  [GetKeywordOpportunities](http://msdn.microsoft.com/library/b6ef9a22-d068-46d0-b9ca-34cc83bbc216) operations.

In Ad Insight version 10, the `CustomerAccountId` request header element determines the account used for the provided opportunities.

#### Keyword Data by Device
The `Device` element is added to the following objects.

-   [KeywordDemographic](http://msdn.microsoft.com/library/7b9e9c87-7c95-4798-9e9b-6d67b87492d4)

-   [KeywordKPI](http://msdn.microsoft.com/library/78beb008-ca91-4d19-801b-5be05cc76f64)

-   [KeywordLocation](http://msdn.microsoft.com/library/b62c334b-75a1-436d-965f-746e48a44df8)

Given the above update, the `Device` element is removed from the following objects.

-   [KeywordDemographicResult](http://msdn.microsoft.com/library/8302bf12-d2df-4401-bfd1-513a6fbbc1c8)

-   [KeywordHistoricalPerformance](http://msdn.microsoft.com/library/23696dd5-bf2e-4e21-b39c-3f2179e05bb3)

-   [KeywordLocationResult](http://msdn.microsoft.com/library/5b5bd2d7-20e3-43fb-9432-f51197ebe4d0)

The `Device` and `HistoricalSearchCounts` elements are removed from the [KeywordSearchCount](http://msdn.microsoft.com/library/1b2aef24-b5bf-43a1-a40b-832d2b599975) object. They are replaced by the `SearchCountsByAttributes` element, which is a list of [SearchCountsByAttributes](http://msdn.microsoft.com/library/25b1a22b-c130-4187-a2dc-5fddd6c990e2). Each [SearchCountsByAttributes](http://msdn.microsoft.com/library/25b1a22b-c130-4187-a2dc-5fddd6c990e2) object contains a list of keyword historical search counts for the corresponding device.

#### Ad Group Estimated Bid
The data type of the `AdGroupEstimatedBid` response element of the [GetEstimatedBidByKeywords](http://msdn.microsoft.com/library/9fcf4632-445c-4d10-aa50-ad87ddd1a2f9) operation is changed from `AdGroupEstimatedBid` to [EstimatedBidAndTraffic](http://msdn.microsoft.com/library/35d32ae9-4d74-4484-81ff-97590ddfe986).

The name and data type of the request property used by [GetEstimatedBidByKeywords](http://msdn.microsoft.com/library/9fcf4632-445c-4d10-aa50-ad87ddd1a2f9) to determine the bid level is changed from GetBidsAtLevel (`int`) to EntityLevelBid (`string`). You can now specify either Keyword, AdGroup, or AllEntities.

#### <a name="adinsight_bmkeyword"></a>Broad Match Keyword Opportunity
The following elements are moved from the [KeywordOpportunity](http://msdn.microsoft.com/library/7843acf6-03af-471f-89e5-477556133b67) to [BroadMatchKeywordOpportunity](http://msdn.microsoft.com/library/f78e2f02-12eb-47d1-8708-eeadd8b53909) data object.

-   `AverageCPC`

-   `AverageCTR`

-   `ClickShare`

Previously the [BroadMatchKeywordOpportunity](http://msdn.microsoft.com/library/f78e2f02-12eb-47d1-8708-eeadd8b53909) object inherited those elements from [KeywordOpportunity](http://msdn.microsoft.com/library/7843acf6-03af-471f-89e5-477556133b67).

#### <a name="adinsight_budgetlandscape"></a>Budget Landscape
The response for [GetBudgetOpportunities](http://msdn.microsoft.com/library/1cad7317-7f04-4d8e-8584-99fc245c184d) now includes a list of [BudgetPoint](http://msdn.microsoft.com/library/acc6ba96-72db-4727-9c22-0c6099dd5590) objects.

#### <a name="adinsight_timeinterval"></a>Time Interval
The [TimeInterval value set](http://msdn.microsoft.com/library/b02381b5-98a6-48dc-8b62-54f8562136bf) is updated to reflect the true intervals.

-   `Last30Days` is updated to `LastMonth`.

-   `Last7Days` is updated to `LastWeek`.

## <a name="bulk"></a>Bulk

### Breaking Changes

#### Proxy Client
Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/CampaignManagement/v10`.

The production endpoint is [https://bulk.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc](https://bulk.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc).

The sandbox endpoint is [https://bulk.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc](https://bulk.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc).

#### Format Version 4.0
Support for Bulk file format version 3.0 is removed. [!INCLUDE[brand](../guides/includes/brand.md)] API Version 10 now only supports format version 4.0. When calling the [DownloadCampaignsByAccountIds](http://msdn.microsoft.com/library/82a5b6e6-97e0-4746-9880-566fadad21d9) and [DownloadCampaignsByCampaignIds](http://msdn.microsoft.com/library/24e0dc96-4438-415b-8cbb-072466d031a0) operations you must specify 4.0 in the `FormatVersion` request element. When uploading a bulk file, you must specify 4.0 in the `Name` field of the [Format Version](https://msdn.microsoft.com/library/bing-ads-bulk-format-version-record.aspx) record. The following records have changed between format version 3.0 and 4.0.

-   The `Mobile Ad` record is removed. [!INCLUDE[brand](../guides/includes/brand.md)] no longer supports WAP mobile ads.

-   The `Product Ad Extension`, `Campaign Product Ad Extension`, and  `Ad Group Product Target` records are removed. Product ad extensions are not supported in [!INCLUDE[brand](../guides/includes/brand.md)] Version 10. For product ads you should use [Bing Shopping Campaigns](../Topic/Bing%20Shopping%20Campaigns.md) instead.

-   The `COUNTRY_CODE` column is renamed to `Country Code`. This impacts the following existing record types: [Call Ad Extension](http://msdn.microsoft.com/library/d1f47324-03fc-4d50-93d7-8b5d292de2ab), [Campaign](http://msdn.microsoft.com/library/16416f5f-2a3b-47e6-bf3a-524ceed4d578), and [Location Ad Extension](http://msdn.microsoft.com/library/49d9c862-4052-4dfc-af22-d8a8311985df).

-   In the [Ad Group](http://msdn.microsoft.com/library/7dff0d14-3738-4a05-bc91-622374d22467) record, the `Search Broad Bid` column is renamed `Search Bid` and corresponds to the new `SearchBid` element of the [AdGroup](http://msdn.microsoft.com/library/c4efdb80-f856-47f1-a08d-966082661263) object in the [Campaign Management](http://msdn.microsoft.com/library/5f50ed8a-6bca-4d30-8340-7290bc074f0e) service.

-   The `Campaign Type` field is now required when adding a new campaign using the [Campaign](http://msdn.microsoft.com/library/16416f5f-2a3b-47e6-bf3a-524ceed4d578) record. In previous format versions SearchAndContent was used as the default value if `Campaign Type` was not specified.

-   For the [Image Ad Extension](http://msdn.microsoft.com/library/e5d12b8f-eaa2-42b7-9851-cf61eb58b3e5) record, the `Media Id` column is renamed `Media Ids` and accepts multiple media identifiers which must be semicolon delimited.

#### Bulk Status Operations Renamed
The `GetDetailedBulkUploadStatus` operation is renamed [GetBulkUploadStatus](http://msdn.microsoft.com/library/e3db8105-9373-440c-952a-609f655454c4), which replaces the version 9 `GetBulkUploadStatus` operation.

The `GetDetailedBulkDownloadStatus` operation is renamed [GetBulkDownloadStatus](http://msdn.microsoft.com/library/b13f42f7-e8ad-4dfe-8ea7-7eb1e08074c1), which replaces the version 9 `GetDownloadStatus` operation.

#### Download Compression Type
You can now specify either the GZip or ZIP [CompressionType](http://msdn.microsoft.com/library/9dec0902-4d30-4f67-9d43-cd1ae8f139eb) when calling the [DownloadCampaignsByAccountIds](http://msdn.microsoft.com/library/82a5b6e6-97e0-4746-9880-566fadad21d9) and [DownloadCampaignsByCampaignIds](http://msdn.microsoft.com/library/24e0dc96-4438-415b-8cbb-072466d031a0) operations.

#### Location Target Version
The `LocationTargetVersion` element is removed from the [DownloadCampaignsByAccountIds](http://msdn.microsoft.com/library/82a5b6e6-97e0-4746-9880-566fadad21d9) and [DownloadCampaignsByCampaignIds](http://msdn.microsoft.com/library/24e0dc96-4438-415b-8cbb-072466d031a0) operations. The service will always return locations according to Nielsen DMA® codes. For more information, see [Geographical Location Codes](../guides/geographical-location-codes.md).

#### Upgrade to Final URLs
Final URLs will eventually replace Destination URLs that are specified today for your ads and keywords. Version 9 will not support Final URLs, so you'll need to use Version 10. For more information, see [Tracking Templates for Landing Page URLs](../Topic/Tracking%20Templates%20for%20Landing%20Page%20URLs.md).

These are the [!INCLUDE[brand](../guides/includes/brand.md)] entities with properties for managing URLs that can be accessed using the [Bulk](http://msdn.microsoft.com/library/893b4696-c081-473c-b726-08f9ccce4cf7) service.

-   [Campaign](http://msdn.microsoft.com/library/16416f5f-2a3b-47e6-bf3a-524ceed4d578)

-   [Ad Group](http://msdn.microsoft.com/library/7dff0d14-3738-4a05-bc91-622374d22467)

-   [Ad Group Product Partition](http://msdn.microsoft.com/library/5053d872-cb6e-419d-b43a-3f2171379999)

-   [Text Ad](http://msdn.microsoft.com/library/646f438f-72cc-481d-b98c-fd2d0ffcb078)

-   [Keyword](http://msdn.microsoft.com/library/acadbada-e9a6-464f-897d-ad1c64ea4f85)

-   [Sitelink Ad Extension](http://msdn.microsoft.com/library/b8041ddc-0902-40db-90a0-f14f33954d8f)


#### Tracking Templates and Custom Parameters
Tracking templates and custom parameters are added to provide more flexibility and simplify management of [Tracking Templates for Landing Page URLs](../Topic/Tracking%20Templates%20for%20Landing%20Page%20URLs.md).

These are the [!INCLUDE[brand](../guides/includes/brand.md)] entities with properties for managing tracking templates that can be accessed using the [Bulk](http://msdn.microsoft.com/library/893b4696-c081-473c-b726-08f9ccce4cf7) service.

-   [Campaign](http://msdn.microsoft.com/library/16416f5f-2a3b-47e6-bf3a-524ceed4d578)

-   [Ad Group](http://msdn.microsoft.com/library/7dff0d14-3738-4a05-bc91-622374d22467)

-   [Text Ad](http://msdn.microsoft.com/library/646f438f-72cc-481d-b98c-fd2d0ffcb078)

-   [Keyword](http://msdn.microsoft.com/library/acadbada-e9a6-464f-897d-ad1c64ea4f85)

-   [Sitelink Ad Extension](http://msdn.microsoft.com/library/b8041ddc-0902-40db-90a0-f14f33954d8f)

> [!NOTE]
> Custom Parameters and Tracking Templates are not yet supported for [Product Ad](http://msdn.microsoft.com/library/b5e1cac7-593d-4bfa-9959-921851e62d5f) or [Ad Group Product Partition](http://msdn.microsoft.com/library/5053d872-cb6e-419d-b43a-3f2171379999). Support will be added soon.

## <a name="campaign"></a>Campaign Management

### Breaking Changes

#### Proxy Client
Update your proxy client to use the new endpoint address and namespace.

The namespace is `https://bingads.microsoft.com/CampaignManagement/v10`.

The production endpoint is [https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc).

The sandbox endpoint is [https://campaign.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc](https://campaign.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc).

#### Target2 renamed as Target
In [!INCLUDE[brand](../guides/includes/brand.md)] API version 9, the "Target2" object model was introduced to avoid breaking changes, instead of adding new elements to the version 9 `Target`. The following objects and operations are renamed in version 10.

|Version 9|Version 10|
|-------------|--------------|
|`Target2`|[Target](http://msdn.microsoft.com/library/800bab2c-7d1d-4f05-9ec2-e1f799667a88)|
|`LocationTarget2`|[LocationTarget](http://msdn.microsoft.com/library/4349d964-0553-4d68-a53e-5011ff51a8f9)|
|`RadiusTarget2`|[RadiusTarget](http://msdn.microsoft.com/library/69810673-38a6-4f96-9dba-2351a6d49266)|
|`RadiusTargetBid2`|[RadiusTargetBid](http://msdn.microsoft.com/library/2f15a842-4266-463f-b8ec-dff27adf733f)|
|`AddTargetsToLibrary2`|[AddTargetsToLibrary](http://msdn.microsoft.com/library/6e709477-2b67-420e-b865-8df78cb8f388)|
|`GetTargetsByAdGroupIds2`|[GetTargetsByAdGroupIds](http://msdn.microsoft.com/library/98af7172-f2ac-4972-b4bb-8b87e7debc26)|
|`GetTargetsByCampaignIds2`|[GetTargetsByCampaignIds](http://msdn.microsoft.com/library/379faa2e-6f20-4674-9fc2-466b4b3d6ac5)|
|`GetTargetsByIds2`|[GetTargetsByIds](http://msdn.microsoft.com/library/96f88bfa-f850-47b4-a788-51a54a390a94)|
|`UpdateTargetsInLibrary2`|[UpdateTargetsInLibrary](http://msdn.microsoft.com/library/52b6e364-48ff-4c42-a308-f311b6093dcf)|
The following objects and value sets related to the legacy version 9 target model are also removed.

-   `DayTarget Data Object`

-   `DayTargetBid Data Object`

-   `HourTarget Data Object`

-   `HourTargetBid Data Object`

-   `NetworkTarget Data Object`

-   `NetworkTargetBid Data Object`

-   `HourRange Value Set`

-   `NetworkType Value Set`

#### Negative Keyword Legacy Operations Removed
The `SetNegativeKeywordsToCampaigns` and `SetNegativeKeywordsToAdGroups` operations are removed.[AddNegativeKeywordsToEntities](http://msdn.microsoft.com/library/25da735e-4979-4bf4-8ab7-d72609359b0c) and [DeleteNegativeKeywordsFromEntities](http://msdn.microsoft.com/library/25da735e-4979-4bf4-8ab7-d72609359b0c) should be used instead of the `SetNegativeKeywordsToCampaigns` and `SetNegativeKeywordsToAdGroups` operations.

The `GetNegativeKeywordsByCampaignIds` and `GetNegativeKeywordsByAdGroupIds` operations are removed. [GetNegativeKeywordsByEntityIds](http://msdn.microsoft.com/library/146aa287-d649-4e52-93a9-d9c6c7cc8c32) should be used instead of the `GetNegativeKeywordsByCampaignIds` and `GetNegativeKeywordsByAdGroupIds` operations.

In turn the `AdGroupNegativeKeywords Data Object``CampaignNegativeKeywords Data Object` are also removed.

#### Ad Group Status
The `Expired` value is added to the [AdGroupStatus value set](http://msdn.microsoft.com/library/5de54e64-f20c-4282-a6e7-d1a7b9092a62). Previously expired ad groups were returned with a `Deleted` status, although the true status has always been expired. The `Deleted` value is retained in version 10, but is now reserved for internal use.

The `Draft` value is removed from the [AdGroupStatus value set](http://msdn.microsoft.com/library/5de54e64-f20c-4282-a6e7-d1a7b9092a62). In turn, the `SubmitAdGroupForApproval` operation is also removed. To pause and resume ad groups, use the [UpdateAdGroups](http://msdn.microsoft.com/library/222be3c0-da10-448f-984c-55d4a1deeca1) operation.

#### Partial Success and Partial Errors
Partial success means that when adding, updating, or deleting entities in batches of one or more, the operation may succeed for some and fail for part of the batch. For each list index where an entity was not added, the corresponding element will be null. The `PartialErrors` element represents an array of [BatchError](http://msdn.microsoft.com/library/76474f9b-3725-4018-b75d-276098599c1a) objects that contain details for any entities that were not successfully added, updated, or deleted. The list only includes a [BatchError](http://msdn.microsoft.com/library/76474f9b-3725-4018-b75d-276098599c1a) for unsuccessful attempts, and does not include null elements at the index of each successfully added entity. Similarly some operations return `NestedPartialErrors` as a list of [BatchErrorCollection](http://msdn.microsoft.com/library/e752de9e-198f-45d1-8743-7675e8e46f75), or a two dimensional [BatchError](http://msdn.microsoft.com/library/76474f9b-3725-4018-b75d-276098599c1a).

The following operations now include `PartialErrors` in the response.

-   [AddAdGroups](http://msdn.microsoft.com/library/10bbda9a-f0e2-41b8-b5cc-14c75e638633)

-   [AddCampaigns](http://msdn.microsoft.com/library/3ad2e776-3129-4fcd-b196-390fc2fd7e7f)

-   [AppealEditorialRejections](http://msdn.microsoft.com/library/ba87645c-f131-4a6a-addc-53e459f633a2)

-   [DeleteAdGroupCriterions](http://msdn.microsoft.com/library/a9d9af83-ceef-4092-bfa9-b6bcc3d87456)

-   [DeleteAdGroups](http://msdn.microsoft.com/library/c419088d-3c86-4edd-9368-d77ff4fe2fa8)

-   [DeleteCampaigns](http://msdn.microsoft.com/library/d48f22a6-60e8-46a3-a9cb-475e4318a78c)

-   [GetAdExtensionsAssociations](http://msdn.microsoft.com/library/9c972e9c-688a-4c72-8d19-41aeffaec383)

-   [GetAdGroupsByIds](http://msdn.microsoft.com/library/e84ee993-e005-4fd2-a0df-ed8a277b71ef)

-   [GetCampaignsByIds](http://msdn.microsoft.com/library/a5b47421-e856-4c94-8648-65eb226b7676)

-   [GetEditorialReasonsByIds](http://msdn.microsoft.com/library/c6c8b301-c2d3-4f50-82a6-47fa74f59e22)

-   [GetNegativeSitesByAdGroupIds](http://msdn.microsoft.com/library/9e268244-40fa-4711-b034-3b3d70d06750)

-   [GetNegativeSitesByCampaignIds](http://msdn.microsoft.com/library/dd00f6de-4d55-4ffd-90d0-cd5eac4f9ea2)

-   [GetTargetsByAdGroupIds](http://msdn.microsoft.com/library/98af7172-f2ac-4972-b4bb-8b87e7debc26)

-   [GetTargetsByCampaignIds](http://msdn.microsoft.com/library/379faa2e-6f20-4674-9fc2-466b4b3d6ac5)

-   [SetAdExtensionsAssociations](http://msdn.microsoft.com/library/111646e5-3d5a-455b-9b6d-e7cc24c4da3f)

-   [SetNegativeSitesToAdGroups](http://msdn.microsoft.com/library/b0e5125a-f4be-4bda-bc60-15a0c1847222)

-   [SetNegativeSitesToCampaigns](http://msdn.microsoft.com/library/d1b7a5ff-ea9f-4432-86e6-888559435e1f)

-   [UpdateAdGroups](http://msdn.microsoft.com/library/222be3c0-da10-448f-984c-55d4a1deeca1)

-   [UpdateCampaigns](http://msdn.microsoft.com/library/2ec8e857-9273-49d1-8097-9253348fabda)

The following operations now include `NestedPartialErrors` in the response.

-   [AddAdGroupCriterions](http://msdn.microsoft.com/library/7a7d6c77-e6af-47de-aceb-e0d9b9547292)

-   [UpdateAdGroupCriterions](http://msdn.microsoft.com/library/3b97047c-47fc-461f-922a-8a79b8390ce2)

For more information and a complete list of operations that support partial success, see [Partial Success using the Campaign Management Service](../guides/handling-service-errors-and-exceptions.md#partialsuccess).

#### Editorial Operations Require Ad Group Identifiers
The [AppealEditorialRejections](http://msdn.microsoft.com/library/ba87645c-f131-4a6a-addc-53e459f633a2) and [GetEditorialReasonsByIds](http://msdn.microsoft.com/library/c6c8b301-c2d3-4f50-82a6-47fa74f59e22) operations now require the ad group identifier in addition to ad or keyword ID. The `EntityIds` element is removed from both operations and replaced by `EntityIdToParentIdAssociations`, which is a list of [EntityIdToParentIdAssociation](http://msdn.microsoft.com/library/5355f77f-08f1-4f28-a7db-55ba8f28e4bb). Each [EntityIdToParentIdAssociation](http://msdn.microsoft.com/library/5355f77f-08f1-4f28-a7db-55ba8f28e4bb) contains the unique system identifier of an entity such as ad or keyword, and the identifier of its parent. An ad group is the parent of an ad or keyword.

Additionally, an `AdGroupId` element is added to the [EditorialReasonCollection data object](http://msdn.microsoft.com/library/ab58a13a-3e7c-4f55-81b0-d60d7854b261).

#### Get Criterions
The `GetAdGroupCriterionsByAdGroupId` operation is removed. To get all ad group criterions for an ad group, you can leave `AdGroupCriterionIds` null in the request to [GetAdGroupCriterionsByIds](http://msdn.microsoft.com/library/357a3026-ab8c-431c-b73c-7167a007dfeb).

The `GetCampaignCriterionsByCampaignId` operation is removed. To get all campaign criterions for a campaign, you can leave `CampaignCriterionIds` null in the request to [GetCampaignCriterionsByIds](http://msdn.microsoft.com/library/8da2b953-82f4-4bb4-b8e5-d072e493dad6).

#### Get Campaigns
The `CampaignType` element is now required when calling [GetCampaignsByAccountId](http://msdn.microsoft.com/library/2cd78bd9-0397-4fcc-8ebb-40f72b987a96) and [GetCampaignsByIds](http://msdn.microsoft.com/library/a5b47421-e856-4c94-8648-65eb226b7676).

#### Ad Group Search Bid
The `SearchBid` element is added to the [AdGroup](http://msdn.microsoft.com/library/c4efdb80-f856-47f1-a08d-966082661263) object, and replaces the `BroadMatchBid`, `ExactMatchBid`, and `PhraseMatchBid` elements. You can set a default bid for all search match types (broad, exact, and phrase) using this new element. You can no longer set different ad group level bids for broad, exact, and phrase match types. You can still override the bids for each distinct [Keyword](http://msdn.microsoft.com/library/916e6bc1-10b6-4954-b676-dd19aecbabb2) match type.

#### Mobile Ads
[!INCLUDE[brand](../guides/includes/brand.md)] no longer supports WAP mobile ads. The `MobileAd` Data Object is not available in [!INCLUDE[brand](../guides/includes/brand.md)] Version 10.

#### Product Ads
Product ad extensions are not supported in [!INCLUDE[brand](../guides/includes/brand.md)] Version 10. For product ads you should use [Bing Shopping Campaigns](../Topic/Bing%20Shopping%20Campaigns.md) instead. The following programming elements are not available in [!INCLUDE[brand](../guides/includes/brand.md)] Version 10.

-   `Product Data Object`

-   `ProductAdExtension Data Object`

> [!NOTE]
> The [AddAdGroupCriterions](http://msdn.microsoft.com/library/7a7d6c77-e6af-47de-aceb-e0d9b9547292), [DeleteAdGroupCriterions](http://msdn.microsoft.com/library/a9d9af83-ceef-4092-bfa9-b6bcc3d87456), and [UpdateAdGroupCriterions](http://msdn.microsoft.com/library/3b97047c-47fc-461f-922a-8a79b8390ce2) operations remain in the interface and are reserved for future use. Currently there are no ad group criterions that can be used with those operations.

#### Location Target Version
The `LocationTargetVersion` element is removed from the [GetTargetsByAdGroupIds](http://msdn.microsoft.com/library/98af7172-f2ac-4972-b4bb-8b87e7debc26), [GetTargetsByCampaignIds](http://msdn.microsoft.com/library/379faa2e-6f20-4674-9fc2-466b4b3d6ac5), and [GetTargetsByIds](http://msdn.microsoft.com/library/96f88bfa-f850-47b4-a788-51a54a390a94) operations. The service will always return locations according to Nielsen DMA® codes. For more information, see [Geographical Location Codes](../guides/geographical-location-codes.md).

#### Native Ads
To avoid breaking changes in [!INCLUDE[brand](../guides/includes/brand.md)] version 9, some optional request elements were added to the following service operations. The elements have been removed in [!INCLUDE[brand](../guides/includes/brand.md)] version 10.

-   The `IncludeNativeBidAdjustment` element is removed from the [GetAdGroupsByCampaignId](http://msdn.microsoft.com/library/75b19dfe-6e48-40d4-bd5b-5d0cc7ae15fc), [GetAdGroupsByIds](http://msdn.microsoft.com/library/e84ee993-e005-4fd2-a0df-ed8a277b71ef), [GetCampaignsByCampaignId](http://msdn.microsoft.com/library/2cd78bd9-0397-4fcc-8ebb-40f72b987a96), and [GetCampaignsByIds](http://msdn.microsoft.com/library/a5b47421-e856-4c94-8648-65eb226b7676),operations. The `NativeBidAdjustment` element is always returned in both the [AdGroup](http://msdn.microsoft.com/library/c4efdb80-f856-47f1-a08d-966082661263) and [Campaign](http://msdn.microsoft.com/library/ebd3b33c-8368-49f0-9ba4-b5f71c411c91) objects.

-   The `UpdateNativeBidAdjustment` element is removed from the [UpdateCampaigns](http://msdn.microsoft.com/library/2ec8e857-9273-49d1-8097-9253348fabda) operation. The operation will always update the `NativeBidAdjustment` element of each specified [Campaign](http://msdn.microsoft.com/library/ebd3b33c-8368-49f0-9ba4-b5f71c411c91) object.

#### Campaign Level Conversion Tracking
The `ConversionTrackingEnabled` element is removed from the [Campaign](http://msdn.microsoft.com/library/ebd3b33c-8368-49f0-9ba4-b5f71c411c91) object. Campaign-level conversion tracking has already sunset, and this element is no longer used even in [!INCLUDE[brand](../guides/includes/brand.md)] version 9.

#### Upgrade to Final URLs
Final URLs will eventually replace Destination URLs that are specified today for your ads and keywords. Version 9 will not support Final URLs, so you'll need to use Version 10. For more information, see [Tracking Templates for Landing Page URLs](../Topic/Tracking%20Templates%20for%20Landing%20Page%20URLs.md).

The `FinalMobileUrls` and `FinalUrls` elements are added to the following objects.

-   [Ad](http://msdn.microsoft.com/library/c3150088-32b0-41d0-b91d-5e65e072eb26)
-   [BiddableAdGroupCriterion](http://msdn.microsoft.com/library/5f7752d5-234f-4668-bc4e-ae2026dd41e1)
-   [Keyword](http://msdn.microsoft.com/library/916e6bc1-10b6-4954-b676-dd19aecbabb2)
-   [SiteLink](http://msdn.microsoft.com/library/5b7b2aff-9ddb-405f-a3ef-495a39aa525a)


#### Tracking Templates and Custom Parameters
Tracking templates and custom parameters are added to provide more flexibility and simplify management of [Tracking Templates for Landing Page URLs](../Topic/Tracking%20Templates%20for%20Landing%20Page%20URLs.md).

The `TrackingUrlTemplate` and `UrlCustomParameters` elements are added to the following objects.

-   [Ad](http://msdn.microsoft.com/library/c3150088-32b0-41d0-b91d-5e65e072eb26)
-   [AdGroup](http://msdn.microsoft.com/library/c4efdb80-f856-47f1-a08d-966082661263)
-   [BiddableAdGroupCriterion](http://msdn.microsoft.com/library/5f7752d5-234f-4668-bc4e-ae2026dd41e1)
-   [Campaign](http://msdn.microsoft.com/library/ebd3b33c-8368-49f0-9ba4-b5f71c411c91)
-   [Keyword](http://msdn.microsoft.com/library/916e6bc1-10b6-4954-b676-dd19aecbabb2)
-   [SiteLink](http://msdn.microsoft.com/library/5b7b2aff-9ddb-405f-a3ef-495a39aa525a)


## Additional Resources
[Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md)

[Release Notes](../guides/release-notes.md)

