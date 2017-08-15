---
title: "Release Notes ARCHIVE"
ms.custom: na
ms.date: "08/12/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: c249f89b-7265-467c-91d2-0cd0bfaa1cb1
caps.latest.revision: 2
---
# Release Notes ARCHIVE
For information about the changes to the Bing Ads services for each release, see the following sections.

-   [May 2016](#may2016)

-   [April 2016](#april2016)

-   [March 2016](#march2016)

-   [February 2016](#february2016)

-   [October 2015](#october2015)

-   [July 2015](#july2015)

-   [June 2015](#june2015)

-   [April 2015](#april2015)

-   [January 2015](#january2015)

-   [October 2014](#october2014)

-   [September 2014](#september2014)

-   [August 2014](#august2014)

-   [July 2014](#july2014)

-   [June 2014](#june2014)

-   [May 2014](#may2014)

-   [April 2014](#april2014)

-   [March 2014](#march2014)

-   [February 2014](#february2014)

-   [January 2014](#january2014)

-   [December 2013](#december2013)

-   [November 2013](#november2013)

-   [October 2013](#october2013)

-   [September 2013](#september2013)

-   [August 2013](#august2013)

-   [July 2013](#july2013)

-   [June 2013](#v9)


## <a name="may2016"></a>May 2016
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Reporting Version 9](#reporting_v9_may2016)

-   [Software Development Kit (SDK) Updates](#sdk_may2016)

### <a name="reporting_v9_may2016"></a>Reporting Version 9
#### <a name="reporting_status_filters_may2016"></a>Reporting Status Filters
You can filter the negative keyword conflict report by the status of your account, campaign, ad group, or keyword. The [NegativeKeywordConflictReportFilter](https://msdn.microsoft.com/library/mt706469(v=msads.90).aspx) is added to the [NegativeKeywordConflictReportRequest](https://msdn.microsoft.com/library/hh560534(v=msads.90).aspx) data object. 

### <a name="sdk_may2016"></a>Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for the following features.
-   [Reporting](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#reporting_v9_may2016) API interface updates for the month of May.
-   Added support to download and upload the Bulk record type [App Install Ad](https://msdn.microsoft.com/library/mt718317.aspx) by reading and writing the new *BulkAppInstallAd* SDK object.
-   Added support for setting the 'state' parameter in *OAuthAuthorization* subclasses to help prevent cross site request forgery (CSRF).
-   Added support for constructing *OAuthAuthorization* subclasses using an existing access token. 

Additionally the Java SDK added Bulk format version verification. The *BulkFileReader* will now return *UnsupportedOperationException* if the Bulk format version in the given CSV file is not supported by the corresponding version of Bulk API. For example, Bulk API V10 only supports Bulk format version 4.0, and Bulk API V9 only supports Bulk format version 3.0.

## <a name="april2016"></a>April 2016
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Campaign Management Version 10](#campaign_v10_april2016)

-   [Reporting Version 9](#reporting_v9_april2016)

-   [Site Placements Sunset in Campaign Management Versions 9 and 10](#siteplacement_sunset_april2016)

-   [Software Development Kit (SDK) Updates](#sdk_april2016)

### <a name="campaign_v10_april2016"></a>Campaign Management Version 10
#### <a name="campaign_adtype_april2016"></a>Ad Type for Get Ads Operations
Once app install ads are available, you can set the *AdTypes* request element of the following operations to retrieve the [AppInstallAd](https://msdn.microsoft.com/library/mt712576(v=msads.100).aspx) objects.
* [GetAdsByAdGroupId](https://msdn.microsoft.com/library/dn277534(v=msads.100).aspx)
* [GetAdsByEditorialStatus](https://msdn.microsoft.com/library/dn277538(v=msads.100).aspx)
* [GetAdsByIds](https://msdn.microsoft.com/library/dn236296(v=msads.100).aspx)

> [!IMPORTANT]
> In [March](#campaign_v10_march2016_appinstallad) the [GetAdsByAdGroupId](https://msdn.microsoft.com/library/dn277534(v=msads.100).aspx), [GetAdsByEditorialStatus](https://msdn.microsoft.com/library/dn277538(v=msads.100).aspx), and [GetAdsByIds](https://msdn.microsoft.com/library/dn236296(v=msads.100).aspx) operations were released with a single *AdType* request element. This service bug was fixed in the April release, and in order to retrieve [AppInstallAd](https://msdn.microsoft.com/library/mt712576(v=msads.100).aspx) objects, you must specify the *AdTypes* element as an array of [AdType](https://msdn.microsoft.com/library/bb671537(v=msads.100).aspx). The *AdTypes* element is still optional, and if not specified the get ads operations return [TextAd](https://msdn.microsoft.com/library/bb672081(v=msads.100).aspx) and [ProductAd](https://msdn.microsoft.com/library/jj738612(v=msads.100).aspx) objects by default.

### <a name="reporting_v9_april2016"></a>Reporting Version 9
#### <a name="reporting_campaign_type_april2016"></a>Search Term Campaign Type
The `CampaignType` column is added to the [SearchQueryPerformanceReportColumn](https://msdn.microsoft.com/library/ee703958(v=msads.90).aspx) value set. When you include this column in your [SearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/ee703962(v=msads.90).aspx), the report data will include a CampaignType column with possible values of *Shopping* and *Search & content*.
**Note:** The [AudiencePerformanceReportFilter](https://msdn.microsoft.com/library/mt489833(v=msads.90).aspx) and [CallDetailReportFilter](https://msdn.microsoft.com/library/mt489831(v=msads.90).aspx) data objects are also new. They come with the new status filters as described in the table below. 

#### <a name="reporting_status_filters_april2016"></a>Reporting Status Filters
One or more of the `AccountStatus`, `AdGroupStatus`, `AdStatus`, `CampaignStatus`, and `KeywordStatus` status filters have been added to the following reports.
**Note:** The [AudiencePerformanceReportFilter](https://msdn.microsoft.com/library/mt489833(v=msads.90).aspx) and [CallDetailReportFilter](https://msdn.microsoft.com/library/mt489831(v=msads.90).aspx) data objects are also new. They come with the new status filters as described in the table below. 

|Report Request|Report Filter|Status Filters Added|
|-------------|-----------------|-----------------|
|[AccountPerformanceReportRequest](https://msdn.microsoft.com/library/bb671927(v=msads.90).aspx)|[AccountPerformanceReportFilter](https://msdn.microsoft.com/library/bb671671(v=msads.90).aspx)|AccountStatus|
|[AdDynamicTextPerformanceReportRequest](https://msdn.microsoft.com/library/bb671950(v=msads.90).aspx)|[AdDynamicTextPerformanceReportFilter](https://msdn.microsoft.com/library/bb672086(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />KeywordStatus|
|[AdExtensionByAdReportRequest](https://msdn.microsoft.com/library/jj713606(v=msads.90).aspx)|[AdExtensionByAdReportFilter](https://msdn.microsoft.com/library/dn393942(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[AdExtensionByKeywordReportRequest](https://msdn.microsoft.com/library/jj713605(v=msads.90).aspx)|[AdExtensionByKeywordReportFilter](https://msdn.microsoft.com/library/dn393943(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[AdExtensionDetailReportRequest](https://msdn.microsoft.com/library/dn610364(v=msads.90).aspx)|[AdExtensionDetailReportFilter](https://msdn.microsoft.com/library/dn610806(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[AdGroupPerformanceReportRequest](https://msdn.microsoft.com/library/bb671686(v=msads.90).aspx)|[AdGroupPerformanceReportFilter ](https://msdn.microsoft.com/library/bb671729(v=msads.90).aspx)|AccountStatus<br /><br />CampaignStatus|
|[AdPerformanceReportRequest](https://msdn.microsoft.com/library/bb672006(v=msads.90).aspx)|[AdPerformanceReportFilter](https://msdn.microsoft.com/library/bb671609(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[AgeGenderDemographicReportRequest](https://msdn.microsoft.com/library/bb671917(v=msads.90).aspx)|[AgeGenderDemographicReportFilter](https://msdn.microsoft.com/library/bb671580(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[AudiencePerformanceReportRequest](https://msdn.microsoft.com/library/mt604702(v=msads.90).aspx)|[AudiencePerformanceReportFilter](https://msdn.microsoft.com/library/mt489833(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[CallDetailReportRequest](https://msdn.microsoft.com/library/dn195845(v=msads.90).aspx)|[CallDetailReportFilter](https://msdn.microsoft.com/library/mt489831(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[CampaignPerformanceReportRequest](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)|[CampaignPerformanceReportFilter](https://msdn.microsoft.com/library/bb671808(v=msads.90).aspx)|AccountStatus|
|[ConversionPerformanceReportRequest](https://msdn.microsoft.com/library/gg262843(v=msads.90).aspx)|[ConversionPerformanceReportFilter](https://msdn.microsoft.com/library/gg262849(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[DestinationUrlPerformanceReportRequest](https://msdn.microsoft.com/library/bb671480(v=msads.90).aspx)|[DestinationUrlPerformanceReportFilter](https://msdn.microsoft.com/library/bb671544(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[GeoLocationPerformanceReportRequest](https://msdn.microsoft.com/library/dn743772(v=msads.90).aspx)|[GeoLocationPerformanceReportFilter](https://msdn.microsoft.com/library/dn743754(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[GoalsAndFunnelsReportRequest](https://msdn.microsoft.com/library/gg262840(v=msads.90).aspx)|[GoalsAndFunnelsReportFilter](https://msdn.microsoft.com/library/gg262854(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[KeywordPerformanceReportRequest](https://msdn.microsoft.com/library/bb671816(v=msads.90).aspx)|[KeywordPerformanceReportFilter](https://msdn.microsoft.com/library/bb672082(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[ProductDimensioPerformanceReportRequest](https://msdn.microsoft.com/library/dn913141(v=msads.90).aspx)|[ProductDimensionPerformanceReportFilter](https://msdn.microsoft.com/library/dn913139(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[ProductOfferPerformanceReportRequest](https://msdn.microsoft.com/library/dn743719(v=msads.90).aspx)|[ProductOfferPerformanceReportFilter](https://msdn.microsoft.com/library/dn743718(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[ProductPartitionPerformanceReportRequest](https://msdn.microsoft.com/library/dn913138(v=msads.90).aspx)|[ProductPartitionPerformanceReportFilter](https://msdn.microsoft.com/library/dn913143(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[ProductPartitionUnitPerformanceReportRequest](https://msdn.microsoft.com/library/mt592960(v=msads.90).aspx)|[ProductPartitionUnitPerformanceReportFilter](https://msdn.microsoft.com/library/mt592961(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[ProductTargetPerformanceReportRequest](https://msdn.microsoft.com/library/dn195846(v=msads.90).aspx)|[ProductTargetPerformanceReportFilter](https://msdn.microsoft.com/library/dn195847(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[PublisherUsagePerformanceReportRequest](https://msdn.microsoft.com/library/dd797229(v=msads.90).aspx)|[PublisherUsagePerformanceReportFilter](https://msdn.microsoft.com/library/dd796865(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[RichAdComponentPerformanceReportRequest](https://msdn.microsoft.com/library/hh180150(v=msads.90).aspx)|[RichAdComponentPerformanceReportFilter](https://msdn.microsoft.com/library/hh180147(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[SearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/ee703962(v=msads.90).aspx)|[SearchQueryPerformanceReportFilter](https://msdn.microsoft.com/library/ee703961(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />KeywordStatus|
|[ShareOfVoiceReportRequest](https://msdn.microsoft.com/library/jj592909(v=msads.90).aspx)|[ShareOfVoiceReportFilter](https://msdn.microsoft.com/library/jj592908(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[SitePerformanceReportRequest](https://msdn.microsoft.com/library/dd797220(v=msads.90).aspx)|[SitePerformanceReportFilter](https://msdn.microsoft.com/library/dd796955(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[TacticChannelReportRequest](https://msdn.microsoft.com/library/gg262842(v=msads.90).aspx)|[TacticChannelReportFilter](https://msdn.microsoft.com/library/gg262855(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[TrafficSourcesReportRequest](https://msdn.microsoft.com/library/gg262853(v=msads.90).aspx)|[TrafficSourcesReportFilter](https://msdn.microsoft.com/library/gg262844(v=msads.90).aspx)|AccountStatus|

The [AccountStatusReportFilter](https://msdn.microsoft.com/library/mt489832(v=msads.90).aspx) value set is added with possible values of *Active*, *Paused*, and *Inactive*.
The [KeywordStatusReportFilter](https://msdn.microsoft.com/library/mt489834(v=msads.90).aspx) value set is added with possible values of *Active*, *Paused*, and *Deleted*.
The *Paused* value is added to the [AdStatusReportFilter](https://msdn.microsoft.com/library/hh560533(v=msads.90).aspx) value set.
The *Suspended* value is added to the [CampaignStatusReportFilter](https://msdn.microsoft.com/library/bb672004(v=msads.90).aspx) value set.

One or more of the `AccountStatus`, `AdGroupStatus`, `AdStatus`, `CampaignStatus`, and `KeywordStatus` status columns have been added to the following report column value sets.

Report Request|Report Column Set|Status Columns Added|
|-------------|-----------------|-----------------|
|[AccountPerformanceReportRequest](https://msdn.microsoft.com/library/bb671927(v=msads.90).aspx)|[AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bb671947(v=msads.90).aspx)|AccountStatus|
|[AdDynamicTextPerformanceReportRequest](https://msdn.microsoft.com/library/bb671950(v=msads.90).aspx)|[AdDynamicTextPerformanceReportColumn](https://msdn.microsoft.com/library/bb671878(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />KeywordStatus|
|[AdExtensionByAdReportRequest](https://msdn.microsoft.com/library/jj713606(v=msads.90).aspx)|[AdExtensionByAdReportColumn](https://msdn.microsoft.com/library/jj713608(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[AdExtensionByKeywordReportRequest](https://msdn.microsoft.com/library/jj713605(v=msads.90).aspx)|[AdExtensionByKeywordReportColumn](https://msdn.microsoft.com/library/jj713610(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[AdExtensionDetailReportRequest](https://msdn.microsoft.com/library/dn610364(v=msads.90).aspx)|[AdExtensionDetailReportColumn](https://msdn.microsoft.com/library/dn610365(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[AdGroupPerformanceReportRequest](https://msdn.microsoft.com/library/bb671686(v=msads.90).aspx)|[AdGroupPerformanceReportColumn ](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)|AccountStatus<br /><br />CampaignStatus|
|[AdPerformanceReportRequest](https://msdn.microsoft.com/library/bb672006(v=msads.90).aspx)|[AdPerformanceReportColumn](https://msdn.microsoft.com/library/bb671923(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[AgeGenderDemographicReportRequest](https://msdn.microsoft.com/library/bb671917(v=msads.90).aspx)|[AgeGenderDemographicReportColumn](https://msdn.microsoft.com/library/bb671786(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[AudiencePerformanceReportRequest](https://msdn.microsoft.com/library/mt604702(v=msads.90).aspx)|[AudiencePerformanceReportColumn](https://msdn.microsoft.com/library/mt604701(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[CallDetailReportRequest](https://msdn.microsoft.com/library/dn195845(v=msads.90).aspx)|[CallDetailReportColumn](https://msdn.microsoft.com/library/dn195843(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[CampaignPerformanceReportRequest](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)|[CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bb671614(v=msads.90).aspx)|AccountStatus|
|[ConversionPerformanceReportRequest](https://msdn.microsoft.com/library/gg262843(v=msads.90).aspx)|[ConversionPerformanceReportColumn](https://msdn.microsoft.com/library/gg262852(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[DestinationUrlPerformanceReportRequest](https://msdn.microsoft.com/library/bb671480(v=msads.90).aspx)|[DestinationUrlPerformanceReportColumn](https://msdn.microsoft.com/library/bb671820(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[GeoLocationPerformanceReportRequest](https://msdn.microsoft.com/library/dn743772(v=msads.90).aspx)|[GeoLocationPerformanceReportColumn](https://msdn.microsoft.com/library/dn743762(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[GoalsAndFunnelsReportRequest](https://msdn.microsoft.com/library/gg262840(v=msads.90).aspx)|[GoalsAndFunnelsReportColumn](https://msdn.microsoft.com/library/gg262845(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[ProductDimensioPerformanceReportRequest](https://msdn.microsoft.com/library/dn913141(v=msads.90).aspx)|[ProductDimensionPerformanceReportColumn](https://msdn.microsoft.com/library/dn913140(v=msads.90).aspx)|AdStatus|
|[ProductOfferPerformanceReportRequest](https://msdn.microsoft.com/library/dn743719(v=msads.90).aspx)|[ProductOfferPerformanceReportColumn](https://msdn.microsoft.com/library/dn743720(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[ProductPartitionPerformanceReportRequest](https://msdn.microsoft.com/library/dn913138(v=msads.90).aspx)|[ProductPartitionPerformanceReportColumn](https://msdn.microsoft.com/library/dn913142(v=msads.90).aspx)|AdStatus|
|[ProductPartitionUnitPerformanceReportRequest](https://msdn.microsoft.com/library/mt592960(v=msads.90).aspx)|[ProductPartitionUnitPerformanceReportColumn](https://msdn.microsoft.com/library/mt592967(v=msads.90).aspx)|AdStatus|
|[ProductTargetPerformanceReportRequest](https://msdn.microsoft.com/library/dn195846(v=msads.90).aspx)|[ProductTargetPerformanceReportColumn](https://msdn.microsoft.com/library/dn195844(v=msads.90).aspx)|AdStatus|
|[PublisherUsagePerformanceReportRequest](https://msdn.microsoft.com/library/dd797229(v=msads.90).aspx)|[PublisherUsagePerformanceReportColumn](https://msdn.microsoft.com/library/dd797159(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus|
|[RichAdComponentPerformanceReportRequest](https://msdn.microsoft.com/library/hh180150(v=msads.90).aspx)|[RichAdComponentPerformanceReportColumn](https://msdn.microsoft.com/library/hh180149(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[SearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/ee703962(v=msads.90).aspx)|[SearchQueryPerformanceReportColumn](https://msdn.microsoft.com/library/ee703958(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />KeywordStatus|
|[ShareOfVoiceReportRequest](https://msdn.microsoft.com/library/jj592909(v=msads.90).aspx)|[ShareOfVoiceReportColumn](https://msdn.microsoft.com/library/jj592910(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[SitePerformanceReportRequest](https://msdn.microsoft.com/library/dd797220(v=msads.90).aspx)|[SitePerformanceReportColumn](https://msdn.microsoft.com/library/dd797115(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />AdStatus<br /><br />CampaignStatus|
|[TacticChannelReportRequest](https://msdn.microsoft.com/library/gg262842(v=msads.90).aspx)|[TacticChannelReportColumn](https://msdn.microsoft.com/library/gg262851(v=msads.90).aspx)|AccountStatus<br /><br />AdGroupStatus<br /><br />CampaignStatus<br /><br />KeywordStatus|
|[TrafficSourcesReportRequest](https://msdn.microsoft.com/library/gg262853(v=msads.90).aspx)|[TrafficSourcesReportColumn](https://msdn.microsoft.com/library/gg262847(v=msads.90).aspx)|AccountStatus|

### <a name="siteplacement_sunset_april2016"></a>Site Placements Sunset in Campaign Management Versions 9 and 10
Site placement features are now sunset. This completes the content ads deprecation, which we announced last summer in the blog article [Changes coming to Bing Ads due to Content Ads Deprecation](http://advertise.bingads.microsoft.com/blog/34580/changes-coming-to-bing-ads-due-to-content-ads-deprecation). 

The site placement ad groups in your account have been removed from Bing Ads, and new errors will be thrown for the following operations:
-	If you try to add or update an [AdGroup](https://msdn.microsoft.com/library/bing-ads-campaign-management-adgroup.aspx) with BiddingModel set to SitePlacement via [AddAdGroups](https://msdn.microsoft.com/library/bing-ads-campaign-management-addadgroups.aspx) or [UpdateAdGroups](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateadgroups.aspx), the operation will return the *CampaignServiceInvalidBiddingModel*  or *CampaignServiceCannotUpdateBiddingModel* error respectively.
-	The [GetAdGroupsByCampaignId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupsbycampaignid.aspx) operation will no longer return site placement ad groups, since they will have been deleted. The operation will continue to return ad groups that use the keyword bidding model. 
-	If you try to retrieve a deleted site placement AdGroup via [GetAdGroupsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getadgroupsbyids.aspx), the operation will return the *CampaignServiceInvalidAdGroupId* error. The experience will be no different than when you specify any invalid ad group ID.
-	If you try to add, update, retrieve, or delete a [SitePlacement](https://msdn.microsoft.com/library/bing-ads-campaign-management-siteplacement.aspx) via [AddSitePlacements](https://msdn.microsoft.com/library/bing-ads-campaign-management-addsiteplacements.aspx), [DeleteSitePlacements](https://msdn.microsoft.com/library/bing-ads-campaign-management-deletesiteplacements.aspx), [GetSitePlacementsByAdGroupId](https://msdn.microsoft.com/library/bing-ads-campaign-management-getsiteplacementsbyadgroupid.aspx), [GetSitePlacementsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-getsiteplacementsbyids.aspx), [UpdateSitePlacements](https://msdn.microsoft.com/library/bing-ads-campaign-management-updatesiteplacements.aspx), or [GetPlacementDetailsForUrls](https://msdn.microsoft.com/library/bing-ads-campaign-management-getplacementdetailsforurls.aspx), the operation will return the *CampaignServiceSitePlacementOperationNotAllowedForPilot* error.

### <a name="sdk_april2016"></a>Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for the [Campaign Management](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#campaign_v10_april2016) API and [Reporting](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#reporting_v9_april2016) API interface changes in April.

The Bing Ads Python SDK is updated with the following bug fixes. 
-	Fixed the bug where the BulkFileReader failed to parse the 'Sitelink Ad Extension' record type if 'Sitelink Extension Order' column is empty.
-	Fixed the bug that setting any other supported key value pair except of 'location' to the suds_option parameter does not take effect in BulkServiceManager and ReportingServiceManger methods.
-	Fixed the bug where 'BulkKeyword.Bid' is defaulted to deleting the keyword bid. With this fix, keyword bids are unchanged by default. If you want to delete the keyword level bid, and inherit from the ad group level bid, you can explicitly set the 'Bid' to 'None'. It is also important to note that previously if you had explicitly set the 'Bid' to 'None', the keyword bid would not have been updated. For more information, see the [BulkKeywordsAds.py](https://github.com/BingAds/BingAds-Python-SDK/blob/master/examples/BingAdsPythonConsoleExamples/BingAdsPythonConsoleExamples/v10/BulkKeywordsAds.py) code example on GitHub.


## <a name="march2016"></a>March 2016
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bulk Version 10](#bulk_v10_march2016)

-   [Campaign Management Version 10](#campaign_v10_march2016)

-   [Customer Management Version 9](#customer_v9_march2016)

-   [Software Development Kit (SDK) Updates](#sdk_march2016)

### <a name="bulk_v10_march2016"></a>Bulk Version 10
The following bulk records are added for managing callout and review extensions.

* [Callout Ad Extension](https://msdn.microsoft.com/library/mt691503(v=msads.100).aspx)
* [Ad Group Callout Ad Extension](https://msdn.microsoft.com/library/mt691505(v=msads.100).aspx)
* [Campaign Callout Ad Extension](https://msdn.microsoft.com/library/mt691507(v=msads.100).aspx)

* [Review Ad Extension](https://msdn.microsoft.com/library/mt691502(v=msads.100).aspx)
* [Ad Group Review Ad Extension](https://msdn.microsoft.com/library/mt691506(v=msads.100).aspx)
* [Campaign Review Ad Extension](https://msdn.microsoft.com/library/mt691504(v=msads.100).aspx)

### <a name="campaign_v10_march2016"></a>Campaign Management Version 10

#### <a name="campaign_v10_march2016_adextensions"></a>Callout and Review Extensions
The following objects are added for managing callout and review extensions.

* [CalloutAdExtension](https://msdn.microsoft.com/library/mt691508(v=msads.100).aspx)
* [ReviewAdExtension](https://msdn.microsoft.com/library/mt691509(v=msads.100).aspx)

#### <a name="campaign_v10_march2016_appinstallad"></a>App Install Ads
The [AppInstallAd](https://msdn.microsoft.com/library/mt712576(v=msads.100).aspx) object is added and reserved for future use.

When app install ads are available, you can set the *AdType* request element of the following operations to retrieve the [AppInstallAd](https://msdn.microsoft.com/library/mt712576(v=msads.100).aspx) objects.
* [GetAdsByAdGroupId](https://msdn.microsoft.com/library/dn277534(v=msads.100).aspx)
* [GetAdsByEditorialStatus](https://msdn.microsoft.com/library/dn277538(v=msads.100).aspx)
* [GetAdsByIds](https://msdn.microsoft.com/library/dn236296(v=msads.100).aspx)

> [!IMPORTANT]
> In March the [GetAdsByAdGroupId](https://msdn.microsoft.com/library/dn277534(v=msads.100).aspx), [GetAdsByEditorialStatus](https://msdn.microsoft.com/library/dn277538(v=msads.100).aspx), and [GetAdsByIds](https://msdn.microsoft.com/library/dn236296(v=msads.100).aspx) operations were released with a single *AdType* request element. This service bug was fixed in the [April](#campaign_adtype_april2016) release, and in order to retrieve [AppInstallAd](https://msdn.microsoft.com/library/mt712576(v=msads.100).aspx) objects, you must specify the *AdTypes* element as an array of [AdType](https://msdn.microsoft.com/library/bb671537(v=msads.100).aspx). The *AdTypes* element is still optional, and if not specified the get ads operations return [TextAd](https://msdn.microsoft.com/library/bb672081(v=msads.100).aspx) and [ProductAd](https://msdn.microsoft.com/library/jj738612(v=msads.100).aspx) objects by default.

> [!NOTE]
> Not everyone has this feature yet. If you don’t, don’t worry. It’s coming soon.

### <a name="customer_v9_march2016"></a>Customer Management Version 9
The `BusinessAddress`, `TaxId`, and `TaxIdStatus` elements are added to the [AdvertiserAccount Data Object](https://msdn.microsoft.com/library/ee704163(v=msads.90).aspx).

> [!NOTE]
> Not everyone has this feature yet. If you don’t, don’t worry. It’s coming soon.

The new `BusinessAddress`, `TaxId`, and `TaxIdStatus` elements are not returned by default when calling the [GetAccount](https://msdn.microsoft.com/library/ee704163(v=msads.90).aspx) and [SearchAccounts](https://msdn.microsoft.com/library/ee704163(v=msads.90).aspx) operations. The `IncludeTaxDetails` element is added as optional for the [GetAccount](https://msdn.microsoft.com/library/ee704163(v=msads.90).aspx) and [SearchAccounts](https://msdn.microsoft.com/library/ee704163(v=msads.90).aspx) request messages, and is used to gate the new elements for forward compatibility. To include the `BusinessAddress`, `TaxId`, and `TaxIdStatus` elements, set the value of `IncludeTaxDetails` to True.

### <a name="sdk_march2016"></a>Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for the following new features.
* Added proxy support for Bulk, Campaign Management, Customer Management, and Reporting service updates from [February](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#february2016) through [March](https://msdn.microsoft.com/library/bing-ads-overview-release-notes.aspx#march2016). 
* Added retry and timeout processing in BulkServiceManager and ReportingServiceManager. The retry feature is an internal implementation. For information on getting started with using the new timeout feature, see Using BulkServiceManager ([C#](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-csharp-visual-basic-with-web-services.aspx#bulkservicemanager) | [Java](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-java-with-web-services.aspx#bulkservicemanager) | [Python](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-python-with-web-services.aspx#bulkservicemanager)) and Using ReportingServiceManager ([C#](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-csharp-visual-basic-with-web-services.aspx#reportingservicemanager) | [Java](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-java-with-web-services.aspx#reportingservicemanager) | [Python](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-python-with-web-services.aspx#reportingservicemanager)).
* Added more exception handling for both download and upload methods in BulkServiceManager and ReportingServiceManager.
* Added support for using the SDK with either the Sandbox or Production environment by specifying the Bing Ads environment parameter in BulkServiceManager/ReportingServiceManager and BulkOperation/ReportingDownloadOperation. Previously you could only set the environment globally or through the ServiceClient, so this option provides additional flexibility. For more information, see Configuring Sandbox ([C#](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-csharp-visual-basic-with-web-services.aspx#sandbox) | [Java](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-java-with-web-services.aspx#sandbox) | [Python](https://msdn.microsoft.com/library/bing-ads-overview-getting-started-python-with-web-services.aspx#sandbox)).

For a full list of March updates, please see the release notes on GitHub ([.NET](https://github.com/BingAds/BingAds-dotNet-SDK/releases) | [Java](https://github.com/BingAds/BingAds-Java-SDK/releases) | [Python](https://github.com/BingAds/BingAds-Python-SDK/releases)). 

For more information on getting started with the SDKs, reference, and samples, please see [Bing Ads Client Libraries](../guides/bing-ads-client-libraries.md).


## <a name="february2016"></a>February 2016
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Reporting Version 9](#reporting_v9_february2016)

### <a name="reporting_v9_february2016"></a>Reporting Version 9
New columns are added to the following reports.

The following columns are added to the [AgeGenderDemographicReportColumn Value Set](https://msdn.microsoft.com/library/bb671786(v=msads.90).aspx).

-   `EstimatedClicks`

-   `EstimatedConversions`

-   `EstimatedConversionRate`

-   `EstimatedImpressions`

The following columns are added to the [ProductDimensionPerformanceReportColumn Value Set](https://msdn.microsoft.com/library/dn913140(v=msads.90).aspx).

-   `SellerName`

-   `OfferLanguage`

-   `CountryOfSale`

The following columns are added to the [ProductPartitionPerformanceReportColumn Value Set](https://msdn.microsoft.com/library/dn913142(v=msads.90).aspx).

-   `OfferLanguage`

-   `CountryOfSale`

## <a name="october2015"></a>October 2015
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bing Ads API Version 10](#v10_october2015)

-   [Campaign Management Version 10](#campaign_v10_october2015)

-   [Software Development Kit (SDK) Updates](#sdk_october2015)

### <a name="v10_october2015"></a>Bing Ads API Version 10
Bing Ads API Version 10 Ad Insight, Bulk, and Campaign Management services are now generally available in production and sandbox.

> [!NOTE]
> The Ad Intelligence, Bulk, Campaign Management, and Optimizer Version 9 services are deprecated and are scheduled to be sunset [!INCLUDE[v9_sunset](../guides/includes/v9_sunset.md)]. You must migrate to the Ad Insight, Bulk, and Campaign Management Version 10 services.
> 
> For more information, see [Migrating from Bing Ads API Version 9 to Version 10](../guides/migrating-from-bing-ads-api-version-9-to-version-10.md).

|Web Service Name|Production|Sandbox|
|--------------------|--------------|-----------|
|Ad Insight|[https://adinsight.api.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc](https://adinsight.api.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc)|[https://adinsight.api.sandbox.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc](https://adinsight.api.sandbox.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc)|
|Bulk|[https://bulk.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc](https://bulk.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc)|[https://bulk.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc](https://bulk.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc)|
|Campaign Management|[https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc](https://campaign.api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc)|[https://campaign.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc](https://campaign.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc)|

### <a name="campaign_v10_october2015"></a>Campaign Management Version 10
The `CampaignType` element is now required when calling [GetCampaignsByAccountId](https://msdn.microsoft.com/library/dn236299(v=msads.100).aspx) and [GetCampaignsByIds](https://msdn.microsoft.com/library/dn236303(v=msads.100).aspx).

### <a name="sdk_october2015"></a>Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for [Bing Ads API Version 10](#v10_october2015). For more information, see [Bing Ads Client Libraries](../guides/bing-ads-client-libraries.md).

## <a name="july2015"></a>July 2015
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bulk Version 10](#bulk_july2015)

-   [Campaign Management Version 10](#campaign_july2015)

-   [Reporting Version 9](#reporting_july2015)

-   [Software Development Kit (SDK) Updates](#sdk_july2015)

### <a name="bulk_july2015"></a>Bulk  Version 10

#### Format Version 4.0
Support for Bulk file format version 3.0 is removed. Bing Ads API Version 10 now only supports format version 4.0. The following records have changed between format version 3.0 and 4.0.

-   The `Mobile Ad` record is removed. Bing Ads no longer supports WAP mobile ads.

-   The `Product Ad Extension`, `Campaign Product Ad Extension`, and  `Ad Group Product Target` records are removed. Product ad extensions are not supported in Bing Ads Version 10. For product ads you should use [Bing Shopping Campaigns](../Topic/Bing%20Shopping%20Campaigns.md) instead.

-   The `COUNTRY_CODE` column is renamed to `Country Code`. This impacts the following existing record types: [Call Ad Extension](https://msdn.microsoft.com/library/dn764743(v=msads.100).aspx), [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx), and [Location Ad Extension](https://msdn.microsoft.com/library/dn764759(v=msads.100).aspx).

-   In the [Ad Group](https://msdn.microsoft.com/library/dn764731(v=msads.100).aspx) record, the `Search Broad Bid` column is renamed `Search Bid` and corresponds to the new `SearchBid` element of the [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.100).aspx) object in the [Campaign Management](https://msdn.microsoft.com/library/bb671719(v=msads.100).aspx) service.

-   The `Campaign Type` field is now required when adding a new campaign using the [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx) record. In previous format versions SearchAndContent was used as the default value if `Campaign Type` was not specified.

-   For the [Image Ad Extension](https://msdn.microsoft.com/library/dn764742(v=msads.100).aspx) record, the `Media Id` column is renamed `Media Ids` and accepts multiple media identifiers which must be semicolon delimited.

#### Location Target Version
The `LocationTargetVersion` element is removed from the [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/jj885755(v=msads.100).aspx) and [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/jj885756(v=msads.100).aspx) operations. The service will always return locations according to Nielsen DMA® codes. For more information, see [Geographical Location Codes](../guides/geographical-location-codes.md).

#### Error Field Path
The `Field Path` field in the Bulk file now returns the name of the record's field where the error occurred. The name is formatted without spaces according to the element of the corresponding [Campaign Management](https://msdn.microsoft.com/library/bb671719(v=msads.100).aspx) data object.   For example if the `Tracking Template` field of a [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx) record contains invalid text, the value of this `Field Path` is TrackingUrlTemplate, which corresponds to the `TrackingUrlTemplate` element of the [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx) object.

> [!NOTE]
> This field is only supported for `Mobile Final Url`, `Final Url`, `Tracking Template`, and `Custom Parameter` fields of the respective [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx), [Ad Group](https://msdn.microsoft.com/library/dn764731(v=msads.100).aspx), [Campaign](https://msdn.microsoft.com/library/dn764756(v=msads.100).aspx), [Product Ad](https://msdn.microsoft.com/library/dn764755(v=msads.100).aspx), [Ad Group Product Partition](https://msdn.microsoft.com/library/cc540184(v=msads.100).aspx), [Keyword](https://msdn.microsoft.com/library/dn764751(v=msads.100).aspx), and [Sitelink Ad Extension](https://msdn.microsoft.com/library/dn764770(v=msads.100).aspx) records.

### <a name="campaign_july2015"></a>Campaign Management Version 10

#### Ad Group Search Bid
The `SearchBid` element is added to the [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.100).aspx) object, and replaces the `BroadMatchBid`, `ExactMatchBid`, and `PhraseMatchBid` elements. You can set a default bid for all search match types (broad, exact, and phrase) using this new element. You can no longer set different ad group level bids for broad, exact, and phrase match types. You can still override the bids for each distinct [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.100).aspx) match type.

#### Mobile Ads
Bing Ads no longer supports WAP mobile ads. The `MobileAd` Data Object is not available in Bing Ads Version 10.

#### Product Ads
Product ad extensions are not supported in Bing Ads Version 10. For product ads you should use [Bing Shopping Campaigns](../Topic/Bing%20Shopping%20Campaigns.md) instead. The following programming elements are not available in Bing Ads Version 10.

-   `Product Data Object`

-   `ProductAdExtension Data Object`

> [!NOTE]
> The [AddAdGroupCriterions](https://msdn.microsoft.com/library/dn277499(v=msads.100).aspx), [DeleteAdGroupCriterions](https://msdn.microsoft.com/library/dn236302(v=msads.100).aspx), and [UpdateAdGroupCriterions](https://msdn.microsoft.com/library/dn277527(v=msads.100).aspx) operations remain in the interface and are reserved for future use. Currently there are no ad group criterions that can be used with those operations.

#### Location Target Version
The `LocationTargetVersion` element is removed from the [GetTargetsByAdGroupIds](https://msdn.microsoft.com/library/dn236297(v=msads.100).aspx), [GetTargetsByCampaignIds](https://msdn.microsoft.com/library/dn236300(v=msads.100).aspx), and [GetTargetsByIds](https://msdn.microsoft.com/library/dn236304(v=msads.100).aspx) operations. The service will always return locations according to Nielsen DMA® codes. For more information, see [Geographical Location Codes](../guides/geographical-location-codes.md).

#### Native Ads
To avoid breaking changes in Bing Ads version 9, some optional request elements were added to the following service operations. The elements have been removed in Bing Ads version 10.

-   The `IncludeNativeBidAdjustment` element is removed from the [GetAdGroupsByCampaignId](https://msdn.microsoft.com/library/dn277524(v=msads.100).aspx), [GetAdGroupsByIds](https://msdn.microsoft.com/library/dn277529(v=msads.100).aspx), [GetCampaignsByCampaignId](https://msdn.microsoft.com/library/dn236299(v=msads.100).aspx), and [GetCampaignsByIds](https://msdn.microsoft.com/library/dn236303(v=msads.100).aspx),operations. The `NativeBidAdjustment` element is always returned in both the [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.100).aspx) and [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx) objects.

-   The `UpdateNativeBidAdjustment` element is removed from the [UpdateCampaigns](https://msdn.microsoft.com/library/dn277536(v=msads.100).aspx) operation. The operation will always update the `NativeBidAdjustment` element of each specified [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx) object.

#### Campaign Level Conversion Tracking
The `ConversionTrackingEnabled` element is removed from the [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx) object. Campaign-level conversion tracking has already sunset, and this element is no longer used even in Bing Ads version 9.

#### BatchError FieldPath
The `FieldPath` element of a [BatchError](https://msdn.microsoft.com/library/bb671765.aspx(v=msads.100).aspx) now returns the name of the data object's element where the error occurred. For example if the `TrackingUrlTemplate` of a [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx) contains invalid text, the value of this `FieldPath` element is TrackingUrlTemplate.

> [!NOTE]
> This element is only supported for `FinalAppUrls`, `FinalMobileUrls`, `FinalUrls`, `TrackingUrlTemplate`, and `UrlCustomParameters` elements of the respective [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx), [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.100).aspx), [TextAd](https://msdn.microsoft.com/library/bb672081(v=msads.100).aspx), [ProductAd](https://msdn.microsoft.com/library/jj738612(v=msads.100).aspx), [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538(v=msads.100).aspx), [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.100).aspx), and [SiteLink](https://msdn.microsoft.com/library/jj134381(v=msads.100).aspx) objects.

### <a name="reporting_july2015"></a>Reporting Version 9
The [ProductDimensionPerformanceReportColumn Value Set](https://msdn.microsoft.com/library/dn913140(v=msads.90).aspx) has been changed. The following elements have been removed.

-   `AdStatus`

-   `SellerName`

-   `AverageCPM`

### <a name="sdk_july2015"></a>Software Development Kit (SDK) Updates
The Bing Ads .NET, Java, and Python SDKs are updated with support for Native Ads and Bing Shopping Campaign Bulk operations. For more information, see [Bing Ads Client Libraries](../guides/bing-ads-client-libraries.md).

## <a name="june2015"></a>June 2015
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Ad Insight Version 10](#adinsight_june2015)

-   [Bulk Version 10](#bulk_june2015)

-   [Campaign Management Version 10](#campaign_june2015)

-   [Reporting](#reporting_june2015)

-   [Updated Length of Download Request ID](#change_DownloadRequestID)

### <a name="adinsight_june2015"></a>Ad Insight Version 10

#### Merged Ad Intelligence and Optimizer
Version 10 of the [Ad Insight](https://msdn.microsoft.com/library/mt219281(v=msads.100).aspx) service is available for preview in sandbox.

The Ad Intelligence and Optimizer services that were available in Bing Ads API Version 9 are merged together and named Ad Insight.

The namespace is `https://bingads.microsoft.com/AdInsight/v10`.

The sandbox endpoint is [https://adinsight.api.sandbox.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc](https://adinsight.api.sandbox.bingads.microsoft.com/Api/Advertiser/AdInsight/V10/AdInsightService.svc).

#### Moved to Ad Insight from the Optimizer Service
These service operations have been moved from the version 9 Optimizer service to the new Ad Insight service.

-   [GetBidOpportunities](https://msdn.microsoft.com/library/mt219287(v=msads.100).aspx)

-   [GetBudgetOpportunities](https://msdn.microsoft.com/library/mt219289(v=msads.100).aspx)

-   [GetKeywordOpportunities](https://msdn.microsoft.com/library/mt219321(v=msads.100).aspx)

These data objects have been moved to the new Ad Insight service.

-   [BidOpportunity](https://msdn.microsoft.com/library/mt219336(v=msads.100).aspx)

    > [!NOTE]
    > The `CampaignId` element is added to [BidOpportunity](https://msdn.microsoft.com/library/mt219336(v=msads.100).aspx) so you can map each opportunity to the ad group's campaign.

-   [BroadMatchKeywordOpportunity](https://msdn.microsoft.com/library/mt219315(v=msads.100).aspx)

-   [BroadMatchSearchQueryKPI](https://msdn.microsoft.com/library/mt219329(v=msads.100).aspx)

-   [BudgetOpportunity](https://msdn.microsoft.com/library/mt219334(v=msads.100).aspx)

-   [BudgetPoint](https://msdn.microsoft.com/library/mt219337(v=msads.100).aspx)

-   [KeywordOpportunity](https://msdn.microsoft.com/library/mt219316(v=msads.100).aspx)

-   [Opportunity](https://msdn.microsoft.com/library/mt219304(v=msads.100).aspx)

These value sets have been moved to the new Ad Insight service.

-   [BidOpportunityType](https://msdn.microsoft.com/library/mt219343(v=msads.100).aspx)

-   [BudgetLimitType](https://msdn.microsoft.com/library/mt219344(v=msads.100).aspx)

-   [BudgetPointType](https://msdn.microsoft.com/library/mt219327(v=msads.100).aspx)

-   [KeywordOpportunityType](https://msdn.microsoft.com/library/mt219346(v=msads.100).aspx)

#### Optimizer Features Sunset
These service operations will sunset with version 9 of the Optimizer service.

-   `ApplyOpportunities`

    > [!NOTE]
    > To apply the suggested bid, budget, and keyword opportunities, you can use the update operations provided with the [Bulk](https://msdn.microsoft.com/library/jj134984(v=msads.10).aspx) or [Campaign Management](https://msdn.microsoft.com/library/bb671719(v=msads.100).aspx) services.

-   `GetBudgetLandscape`

    > [!NOTE]
    > Budget landscape data is available in the new [Ad Insight](https://msdn.microsoft.com/library/mt219281(v=msads.100).aspx) service. The response for [GetBudgetOpportunities](https://msdn.microsoft.com/library/mt219289(v=msads.100).aspx) now includes a list of [BudgetPoint](https://msdn.microsoft.com/library/mt219337(v=msads.100).aspx) objects.

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

With Ad Insight version 10, you can get budget landscape data using the [GetBudgetOpportunities](https://msdn.microsoft.com/library/mt219289(v=msads.100).aspx) operation. Each returned [BudgetOpportunity](https://msdn.microsoft.com/library/mt219334(v=msads.100).aspx) now includes `BudgetPoints`, which is a list of [BudgetPoint](https://msdn.microsoft.com/library/mt219337(v=msads.100).aspx) objects representing the budget landscape.

In version 10, each [BudgetPoint](https://msdn.microsoft.com/library/mt219337(v=msads.100).aspx) includes weekly impressions, clicks, and cost estimates instead of the daily estimates provided in version 9.

#### Opportunity Expiration Date
The `ExpirationDate` element is removed from the [Opportunity](https://msdn.microsoft.com/library/mt219304(v=msads.100).aspx) object. Expired opportunities will not be returned by the Ad Insight service.

#### Bid Opportunity Type
The `IncreaseTraffic` value is removed from the [BidOpportunityType](https://msdn.microsoft.com/library/mt219343(v=msads.100).aspx) value set.

#### Opportunities by Account
The `AccountId` request element is removed from the [GetBidOpportunities](https://msdn.microsoft.com/library/mt219287(v=msads.100).aspx), [GetBudgetOpportunities](https://msdn.microsoft.com/library/mt219289(v=msads.100).aspx), and  [GetKeywordOpportunities](https://msdn.microsoft.com/library/mt219321(v=msads.100).aspx) operations.

In Ad Insight version 10, the `CustomerAccountId` request header element determines the account used for the provided opportunities.

#### Keyword Data by Device
The `Device` element is added to the following objects.

-   [KeywordDemographic](https://msdn.microsoft.com/library/mt219283(v=msads.100).aspx)

-   [KeywordKPI](https://msdn.microsoft.com/library/mt219293(v=msads.100).aspx)

-   [KeywordLocation](https://msdn.microsoft.com/library/mt219301(v=msads.100).aspx)

Given the above update, the `Device` element is removed from the following objects.

-   [KeywordDemographicResult](https://msdn.microsoft.com/library/mt219288(v=msads.100).aspx)

-   [KeywordHistoricalPerformance](https://msdn.microsoft.com/library/mt219292(v=msads.100).aspx)

-   [KeywordLocationResult](https://msdn.microsoft.com/library/mt219299(v=msads.100).aspx)

The `Device` and `HistoricalSearchCounts` elements are removed from the [KeywordSearchCount](https://msdn.microsoft.com/library/mt219303(v=msads.100).aspx) object. They are replaced by the `SearchCountsByAttributes` element, which is a list of [SearchCountsByAttributes](https://msdn.microsoft.com/library/mt179362(v=msads.100).aspx). Each [SearchCountsByAttributes](https://msdn.microsoft.com/library/mt179362(v=msads.100).aspx) object contains a list of keyword historical search counts for the corresponding device.

#### Ad Group Estimated Bid
The data type of the `AdGroupEstimatedBid` response element of the [GetEstimatedBidByKeywords](https://msdn.microsoft.com/library/mt219297(v=msads.100).aspx) operation is changed from `AdGroupEstimatedBid` to [EstimatedBidAndTraffic](https://msdn.microsoft.com/library/mt219348(v=msads.100).aspx).

The name and data type of the request property used by [GetEstimatedBidByKeywords](https://msdn.microsoft.com/library/mt219297(v=msads.100).aspx) to determine the bid level is changed from GetBidsAtLevel (`int`) to EntityLevelBid (`string`). You can now specify either Keyword, AdGroup, or AllEntities.

#### Broad Match Keyword Opportunity
The following elements are moved from the [KeywordOpportunity](https://msdn.microsoft.com/library/mt219316(v=msads.100).aspx) to [BroadMatchKeywordOpportunity](https://msdn.microsoft.com/library/mt219315(v=msads.100).aspx) data object.

-   `AverageCPC`

-   `AverageCTR`

-   `ClickShare`

Previously the [BroadMatchKeywordOpportunity](https://msdn.microsoft.com/library/mt219315(v=msads.100).aspx) object inherited those elements from [KeywordOpportunity](https://msdn.microsoft.com/library/mt219316(v=msads.100).aspx).

#### Budget Landscape
The response for [GetBudgetOpportunities](https://msdn.microsoft.com/library/mt219289(v=msads.100).aspx) now includes a list of [BudgetPoint](https://msdn.microsoft.com/library/mt219337(v=msads.100).aspx) objects.

#### Time Interval
The [TimeInterval value set](https://msdn.microsoft.com/library/mt219339(v=msads.100).aspx) is updated to reflect the true intervals.

-   `Last30Days` is updated to `LastMonth`.

-   `Last7Days` is updated to `LastWeek`.

### <a name="bulk_june2015"></a>Bulk Version 10

#### Updated the Version Number
Version 10 of the [Bulk](https://msdn.microsoft.com/library/jj134984(v=msads.100).aspx) service is available for preview in sandbox.

The namespace has been changed to reflect the new version number of this release; The namespace is `https://bingads.microsoft.com/CampaignManagement/v10`.

The sandbox endpoint is [https://bulk.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc](https://bulk.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/BulkService.svc).

#### Bulk Status Operations Renamed
The `GetDetailedBulkUploadStatus` operation is renamed [GetBulkUploadStatus](https://msdn.microsoft.com/library/dn249979(v=msads.100).aspx), which replaces the version 9 `GetBulkUploadStatus` operation.

The `GetDetailedBulkDownloadStatus` operation is renamed [GetBulkDownloadStatus](https://msdn.microsoft.com/library/jj885754(v=msads.100).aspx), which replaces the version 9 `GetDownloadStatus` operation.

#### Download Compression Type
You can now specify either the GZip or ZIP [CompressionType](https://msdn.microsoft.com/library/mt179363(v=msads.100).aspx) when calling the [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/jj885755(v=msads.100).aspx) and [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/jj885756(v=msads.100).aspx) operations.

### <a name="campaign_june2015"></a>Campaign Management Version 10

#### Updated the Version Number
Version 10 of the [Campaign Management](https://msdn.microsoft.com/library/bb671719(v=msads.100).aspx) service is available for preview in sandbox.

The namespace has been changed to reflect the new version number for this release. The new namespace name is https://bingads.microsoft.com/CampaignManagement/v10. For the production and sandbox endpoints, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

The namespace has been changed to reflect the new version number for this release.; The namespace is `https://bingads.microsoft.com/CampaignManagement/v10`.

The sandbox endpoint is [https://campaign.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc](https://campaign.api.sandbox.bingads.microsoft.com/Api/Advertiser/CampaignManagement/V10/CampaignManagementService.svc).

#### Target2 renamed as Target
In Bing Ads API version 9, the "Target2" object model was introduced to avoid breaking changes, instead of adding new elements to the version 9 `Target`. The following objects and operations are renamed in version 10.

|Version 9|Version 10|
|-------------|--------------|
|`Target2`|[Target](https://msdn.microsoft.com/library/bb671789(v=msads.100).aspx)|
|`LocationTarget2`|[LocationTarget](https://msdn.microsoft.com/library/bb671646(v=msads.100).aspx)|
|`RadiusTarget2`|[RadiusTarget](https://msdn.microsoft.com/library/dd796953(v=msads.100).aspx)|
|`RadiusTargetBid2`|[RadiusTargetBid](https://msdn.microsoft.com/library/dd796863(v=msads.100).aspx)|
|`AddTargetsToLibrary2`|[AddTargetsToLibrary](https://msdn.microsoft.com/library/dn277526(v=msads.100).aspx)|
|`GetTargetsByAdGroupIds2`|[GetTargetsByAdGroupIds](https://msdn.microsoft.com/library/dn236297(v=msads.100).aspx)|
|`GetTargetsByCampaignIds2`|[GetTargetsByCampaignIds](https://msdn.microsoft.com/library/dn236300(v=msads.100).aspx)|
|`GetTargetsByIds2`|[GetTargetsByIds](https://msdn.microsoft.com/library/dn236304(v=msads.100).aspx)|
|`UpdateTargetsInLibrary2`|[UpdateTargetsInLibrary](https://msdn.microsoft.com/library/dn236301(v=msads.100).aspx)|
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
The `SetNegativeKeywordsToCampaigns` and `SetNegativeKeywordsToAdGroups` operations are removed. [AddNegativeKeywordsToEntities](https://msdn.microsoft.com/library/dn743724(v=msads.100).aspx) and [DeleteNegativeKeywordsFromEntities](https://msdn.microsoft.com/library/dn743725(v=msads.100).aspx) should be used instead of the `SetNegativeKeywordsToCampaigns` and `SetNegativeKeywordsToAdGroups` operations.

The `GetNegativeKeywordsByCampaignIds` and `GetNegativeKeywordsByAdGroupIds` operations are removed. [GetNegativeKeywordsByEntityIds](https://msdn.microsoft.com/library/dn743730(v=msads.100).aspx) should be used instead of the `GetNegativeKeywordsByCampaignIds` and `GetNegativeKeywordsByAdGroupIds` operations.

In turn the `AdGroupNegativeKeywords Data Object``CampaignNegativeKeywords Data Object` are also removed.

#### Ad Group Status
The `Expired` value is added to the [AdGroupStatus Value Set](https://msdn.microsoft.com/library/bb671715(v=msads.100).aspx). Previously expired ad groups were returned with a `Deleted` status, although the true status has always been expired. The `Deleted` value is retained in version 10, but is now reserved for internal use.

The `Draft` value is removed from the [AdGroupStatus Value Set](https://msdn.microsoft.com/library/bb671715(v=msads.100).aspx). In turn, the `SubmitAdGroupForApproval` operation is also removed. To pause and resume ad groups, use the [UpdateAdGroups](https://msdn.microsoft.com/library/dn277528(v=msads.100).aspx) operation.

#### Partial Success and Partial Errors
Partial success means that when adding, updating, or deleting entities in batches of one or more, the operation may succeed for some and fail for part of the batch. For each list index where an entity was not added, the corresponding element will be null. The `PartialErrors` element represents an array of [BatchError](https://msdn.microsoft.com/library/bb671765.aspx(v=msads.100).aspx) objects that contain details for any entities that were not successfully added, updated, or deleted. The list only includes a [BatchError](https://msdn.microsoft.com/library/bb671765.aspx(v=msads.100).aspx) for unsuccessful attempts, and does not include null elements at the index of each successfully added entity. Similarly some operations return `NestedPartialErrors` as a list of [BatchErrorCollection](https://msdn.microsoft.com/library/dn743731(v=msads.100).aspx), or a two dimensional [BatchError](https://msdn.microsoft.com/library/bb671765.aspx(v=msads.100).aspx).

The following operations now include `PartialErrors` in the response.

-   [AddAdGroups](https://msdn.microsoft.com/library/dn277502(v=msads.100).aspx)

-   [AddCampaigns](https://msdn.microsoft.com/library/dn277510(v=msads.100).aspx)

-   [AppealEditorialRejections](https://msdn.microsoft.com/library/dn277533(v=msads.100).aspx)

-   [DeleteAdGroupCriterions](https://msdn.microsoft.com/library/dn236302(v=msads.100).aspx)

-   [DeleteAdGroups](https://msdn.microsoft.com/library/dn236307(v=msads.100).aspx)

-   [DeleteCampaigns](https://msdn.microsoft.com/library/dn236314(v=msads.100).aspx)

-   [GetAdExtensionsAssociations](https://msdn.microsoft.com/library/dn236309(v=msads.100).aspx)

-   [GetAdGroupsByIds](https://msdn.microsoft.com/library/dn277529(v=msads.100).aspx)

-   [GetCampaignsByIds](https://msdn.microsoft.com/library/dn236303(v=msads.100).aspx)

-   [GetEditorialReasonsByIds](https://msdn.microsoft.com/library/dn236306(v=msads.100).aspx)

-   [GetNegativeSitesByAdGroupIds](https://msdn.microsoft.com/library/dn277521(v=msads.100).aspx)

-   [GetNegativeSitesByCampaignIds](https://msdn.microsoft.com/library/dn277525(v=msads.100).aspx)

-   [GetTargetsByAdGroupIds](https://msdn.microsoft.com/library/dn236297(v=msads.100).aspx)

-   [GetTargetsByCampaignIds](https://msdn.microsoft.com/library/dn236300(v=msads.100).aspx)

-   [SetAdExtensionsAssociations](https://msdn.microsoft.com/library/dn277532(v=msads.100).aspx)

-   [SetNegativeSitesToAdGroups](https://msdn.microsoft.com/library/dn236317(v=msads.100).aspx)

-   [SetNegativeSitesToCampaigns](https://msdn.microsoft.com/library/dn277504(v=msads.100).aspx)

-   [UpdateAdGroups](https://msdn.microsoft.com/library/dn277528(v=msads.100).aspx)

-   [UpdateCampaigns](https://msdn.microsoft.com/library/dn277536(v=msads.100).aspx)

The following operations now include `NestedPartialErrors` in the response.

-   [AddAdGroupCriterions](https://msdn.microsoft.com/library/dn277499(v=msads.100).aspx)

-   [UpdateAdGroupCriterions](https://msdn.microsoft.com/library/dn277527(v=msads.100).aspx)

For more information and a complete list of operations that support partial success, see [Partial Success using the Campaign Management Service](../guides/handling-service-errors-and-exceptions.md#partialsuccess).

#### Editorial Operations Require Ad Group Identifiers
The [AppealEditorialRejections](https://msdn.microsoft.com/library/dn277533(v=msads.100).aspx) and [GetEditorialReasonsByIds](https://msdn.microsoft.com/library/dn236306(v=msads.100).aspx) operations now require the ad group identifier in addition to ad or keyword ID. The `EntityIds` element is removed from both operations and replaced by `EntityIdToParentIdAssociations`, which is a list of [EntityIdToParentIdAssociation](https://msdn.microsoft.com/library/mt179358(v=msads.100).aspx). Each [EntityIdToParentIdAssociation](https://msdn.microsoft.com/library/mt179358(v=msads.100).aspx) contains the unique system identifier of an entity such as ad or keyword, and the identifier of its parent. An ad group is the parent of an ad or keyword.

Additionally, an `AdGroupId` element is added to the [EditorialReasonCollection data object](https://msdn.microsoft.com/library/ff728504(v=msads.100).aspx).

#### Get Criterions
The `GetAdGroupCriterionsByAdGroupId` operation is removed. To get all ad group criterions for an ad group, you can leave `AdGroupCriterionIds` null in the request to [GetAdGroupCriterionsByIds](https://msdn.microsoft.com/library/dn277520(v=msads.100).aspx).

The `GetCampaignCriterionsByCampaignId` operation is removed. To get all campaign criterions for a campaign, you can leave `CampaignCriterionIds` null in the request to [GetCampaignCriterionsByIds](https://msdn.microsoft.com/library/dn913135(v=msads.100).aspx).

#### Upgrade to Final URLs
Final URLs will eventually replace Destination URLs that are specified today for your ads and keywords. Version 9 will not support Final URLs, so you'll need to use Version 10.

> [!NOTE]
> Details on the migration plan from Destination URLs to Final URLs are coming soon.

The `FinalAppUrls`, `FinalMobileUrls`, and `FinalUrls` elements are added to the following objects.

-   [Ad](https://msdn.microsoft.com/library/bb671952(v=msads.100).aspx)

    > [!NOTE]
    > [ProductAd](https://msdn.microsoft.com/library/jj738612(v=msads.100).aspx) and [TextAd](https://msdn.microsoft.com/library/bb672081(v=msads.100).aspx) inherit these new elements from the [Ad](https://msdn.microsoft.com/library/bb671952(v=msads.100).aspx) base class.

-   [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538(v=msads.100).aspx)

-   [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.100).aspx)

-   [SiteLink](https://msdn.microsoft.com/library/jj134381(v=msads.100).aspx)

#### Tracking Templates and Custom Parameters
Tracking templates and custom parameters are added to provide more flexibility and simplify management of [Dynamic Text Substitution](../guides/dynamic-text-substitution.md) for URL tracking.

> [!NOTE]
> Details on support for Tracking Templates and Custom Parameters are coming soon.

The `TrackingUrlTemplate` and `UrlCustomParameters` elements are added to the following objects.

-   [Ad](https://msdn.microsoft.com/library/bb671952(v=msads.100).aspx)

    > [!NOTE]
    > [ProductAd](https://msdn.microsoft.com/library/jj738612(v=msads.100).aspx) and [TextAd](https://msdn.microsoft.com/library/bb672081(v=msads.100).aspx) inherit these new elements from the [Ad](https://msdn.microsoft.com/library/bb671952(v=msads.100).aspx) base class.

-   [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.100).aspx)

-   [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538(v=msads.100).aspx)

-   [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.100).aspx)

-   [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.100).aspx)

-   [SiteLink](https://msdn.microsoft.com/library/jj134381(v=msads.100).aspx)

### <a name="reporting_june2015"></a>Reporting
The [AdDistributionReportFilter](https://msdn.microsoft.com/library/bb671722(v=msads.90).aspx) has been added to these report filters:

-   [ConversionPerformanceReportFilter](https://msdn.microsoft.com/library/gg262849(v=msads.90).aspx)

-   [GoalsAndFunnelsReportFilter](https://msdn.microsoft.com/library/gg262854(v=msads.90).aspx)

-   [SearchCampaignChangeHistoryReportFilter](https://msdn.microsoft.com/library/hh912356(v=msads.90).aspx)

The `AdDistributionReportFilter` value set includes a value for `Native` ads that is reserved for future use.

### <a name="change_DownloadRequestID"></a>Updated Length of Download Request ID
A request ID is used by clients when downloading reports with the Reporting service and when downloading campaign settings using the Bulk service. The request ID is returned immediately once the download is requested. The client can then use the request ID to poll for status and download the data when processing is completed. Previously the request ID is a string of length 10, and with this change the length of the string can be up to 40. The string currently contains only numbers, for example 1234567890; however, your application should be prepared for any string value.

The report ID is used by these request and response messages:

-   The response for Bulk download operations [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/jj885755(v=msads.100).aspx) and [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/jj885756(v=msads.100).aspx) returns the request ID as `DownloadRequestId`.

-   The request for Bulk download status operations [GetDownloadStatus](https://msdn.microsoft.com/library/jj885754(v=msads.100).aspx) and [GetDetailedBulkDownloadStatus](https://msdn.microsoft.com/library/dn600289(v=msads.100).aspx) includes the request ID as `RequestId`

-   The response for Report download operation [SubmitGenerateReport](https://msdn.microsoft.com/library/jj879321(v=msads.90).aspx) returns the request ID as `ReportRequestId`.

-   The request for Report download status operation [PollGenerateReport](https://msdn.microsoft.com/library/jj879320(v=msads.90).aspx) includes the request ID as `ReportRequestId`.

    **Note**: The Bulk upload request ID has a different format as a GUID and is not impacted by this change.

## <a name="april2015"></a>April 2015
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Campaign Management Version 9](#campaign_april2015)

-   [Reporting Version 9](#reporting_april2015)

### <a name="campaign_april2015"></a>Campaign Management Version 9

#### Bing Shopping Campaigns
A Bing Shopping campaign enables you to advertise the products from your Bing Merchant Center store product catalog. Product ads from a Bing Shopping campaign include details about the product, an image, and optional promotional text. For more information, see [Bing Shopping Campaigns](../Topic/Bing%20Shopping%20Campaigns.md) and the following reference documentation.

The following service operations are reserved for working with Bing Shopping campaigns.

-   [AddAdGroupCriterions](https://msdn.microsoft.com/library/dn277499(v=msads.90).aspx)

-   [AddCampaignCriterions](https://msdn.microsoft.com/library/dn913127(v=msads.90).aspx)

-   [ApplyProductPartitionActions](https://msdn.microsoft.com/library/dn913134(v=msads.90).aspx)

-   [DeleteAdGroupCriterions](https://msdn.microsoft.com/library/dn236302(v=msads.90).aspx)

-   [DeleteCampaignCriterions](https://msdn.microsoft.com/library/dn913125(v=msads.90).aspx)

-   [GetAdGroupCriterionsByIds](https://msdn.microsoft.com/library/dn277520(v=msads.90).aspx)

-   [GetCampaignCriterionsByCampaignId](https://msdn.microsoft.com/library/dn913136(v=msads.90).aspx)

-   [GetCampaignCriterionsByIds](https://msdn.microsoft.com/library/dn913135(v=msads.90).aspx)

-   [UpdateAdGroupCriterions](https://msdn.microsoft.com/library/dn277527(v=msads.90).aspx)

-   [UpdateCampaignCriterions](https://msdn.microsoft.com/library/dn913121(v=msads.90).aspx)

To support  Bing Shopping campaigns, the `CampaignType` and `Settings` elements are added to the [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.90).aspx) object. When you get a campaign object using [GetCampaignsByAccountId](https://msdn.microsoft.com/library/dn236299(v=msads.90).aspx) or [GetCampaignsByIds](https://msdn.microsoft.com/library/dn236303(v=msads.90).aspx), these new elements are only returned for Bing Shopping campaigns when you  set the respective operation's `CampaignType` element to `Shopping`.

### <a name="reporting_april2015"></a>Reporting Version 9

#### Bing Shopping Campaigns
A Bing Shopping campaign enables you to advertise the products from your Bing Merchant Center store product catalog. Product ads from a Bing Shopping campaign include details about the product, an image, and optional promotional text. For more information, see [Bing Shopping Campaigns](../Topic/Bing%20Shopping%20Campaigns.md) and the following reference documentation.

The following reports are added for Bing Shopping campaigns.

|Report Name|Description|Request|Filter|Columns|
|---------------|---------------|-----------|----------|-----------|
|Product Dimensionn|Defines a product dimension performance report request that aggregates the performance data by product category, custom label, title, and type for a specified time period. You can include details in the report such as impressions, clicks, and spend that you can use to identify whether or not the Bing Shopping products are performing well.|[ProductDimensionPerformanceReportRequest](https://msdn.microsoft.com/library/dn913141(v=msads.90).aspx)|[ProductDimensionPerformanceReportFilter](https://msdn.microsoft.com/library/dn913139(v=msads.90).aspx)|[ProductDimensionPerformanceReportColumn](https://msdn.microsoft.com/library/dn913140(v=msads.90).aspx)|
|Product Partition|Defines a product partition performance report request that aggregates the performance data by product group and product partition type for a specified time period. You can include details in the report such as impressions, clicks, and spend that you can use to identify whether or not the Bing Shopping products are performing well.|[ProductPartitionPerformanceReportRequest](https://msdn.microsoft.com/library/dn913138(v=msads.90).aspx)|[ProductPartitionPerformanceReportFilter](https://msdn.microsoft.com/library/dn913143(v=msads.90).aspx)|[ProductPartitionPerformanceReportColumn](https://msdn.microsoft.com/library/dn913142(v=msads.90).aspx)|

### Negative Keyword Conflict Report
The [NegativeKeywordConflictReportColumn](https://msdn.microsoft.com/library/hh560535(v=msads.90).aspx) value set has been updated to include:

-   BidMatchType

-   NegativeKeywordListId

-   NegativeKeywordList

-   NegativeKeywordId

-   NegativeKeywordMatchType

Use these IDs to find and resolve negative keyword conflicts when the keywords are shared via a list.
            For more information refer to the [Bing Ads API blog post](http://blogs.msdn.com/b/bing_ads_api/archive/2015/04/08/enhanced-negative-keyword-conflicts-report.aspx) *Enhanced Negative Keyword Conflicts Report*.

## <a name="january2015"></a>January 2015
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Optimizer Version 9](#optimizer_january2015)

-   [Reporting Version 9](#reporting_january2015)

### <a name="optimizer_january2015"></a>Optimizer Version 9
The [KeywordOpportunity](https://msdn.microsoft.com/library/jj649133(v=msads.90).aspx) data object has been updated to include:

-   EstimatedIncreaseInClicks

-   EstimatedIncreaseInCost

-   EstimatedIncreaseInImpressions

These elements have been removed from the [BroadMatchKeywordOpportunity](https://msdn.microsoft.com/library/dn766186(v=msads.90).aspx) data object. This object inherits from `KeywordOpportunity`, so the elements remain available in the `BroadMatchKeywordOpportunity` data object.

This change allows users to retrieve keyword opportunities using the `BroadMatch` and `CampaignContext` settings in the [KeywordOpportunityType](https://msdn.microsoft.com/library/dn766184(v=msads.90).aspx).

In the [GetKeywordOpportunities](https://msdn.microsoft.com/library/dn376336(v=msads.90).aspx), set the `IncludeEstimations` flag to true to include the estimated impact elements in the response body of the `KeywordOpportunity` object. These elements are part of the `KeywordOpportunity` data object and can be used in objects that inherit from `KeywordOpportunity`, such as [BroadMatchKeywordOpportunity](https://msdn.microsoft.com/library/dn766186(v=msads.90).aspx).

### <a name="reporting_january2015"></a>Reporting Version 9

#### Support for Universal Event Tracking
Additional support for Universal Event Tracking has been added to the Reporting API.

|New Elements/Attributes|Available in these Report Columns|Use these Report Requests|
|---------------------------|-------------------------------------|-----------------------------|
|`AverageDurationPerVisit`<br /><br />`AveragePagesPerVisit`<br /><br />`BounceRate`<br /><br />`TotalVisits`|[AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bb671947(v=msads.90).aspx)<br /><br />[AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)<br /><br />[CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)<br /><br />[KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bb672087(v=msads.90).aspx)|[AccountPerformanceReportRequest](https://msdn.microsoft.com/library/bb671927(v=msads.90).aspx)<br /><br />[AdGroupPerformanceReportRequest](https://msdn.microsoft.com/library/bb671686(v=msads.90).aspx)<br /><br />[CampaignPerformanceReportRequest](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)<br /><br />[KeywordPerformanceReportRequest](https://msdn.microsoft.com/library/bb671816(v=msads.90).aspx)|
|`GoalId`|[GoalsAndFunnelsReportColumn](https://msdn.microsoft.com/library/gg262845(v=msads.90).aspx)|[GoalsAndFunnelsReportRequest](https://msdn.microsoft.com/library/gg262840(v=msads.90).aspx)|
For more information about using the Reporting service to analyze Campaign Analytics data, see the [Getting Reports](http://msdn.microsoft.com/library/bing-ads-universal-event-tracking-uet-tags-analytics-scripts.aspx#getreports) section of the topic [Track sales and other conversions](http://go.microsoft.com/fwlink/?LinkID=624771).

## <a name="october2014"></a>October 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Reporting Version 9](#reporting_october2014)

### <a name="reporting_october2014"></a>Reporting Version 9

-   [Universal Event Tracking (UET)](#uet)

-   [Campaign Analytics Scripts](#campaignanalytics)

#### <a name="uet"></a>Universal Event Tracking (UET)
Universal Event Tracking replaces the current Campaign Analytics conversion tracking.

For more information about using Universal Event Tracking, see the topic [Track sales and other conversions](http://go.microsoft.com/fwlink/?LinkID=624771).

#### <a name="campaignanalytics"></a>Campaign Analytics Scripts
Campaign Analytics Scripts are being deprecated. For more information see the deprecation warning on the [Managing Campaign Analytics Scripts](https://msdn.microsoft.com/library/gg985267(v=msads.90).aspx) page.

## <a name="september2014"></a>September 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Campaign Management](#campaign_september2014)

-   [Reporting Version 9](#reporting_september2014)

### <a name="campaign_september2014"></a>Campaign Management

#### Targets
> [!NOTE]
> Previously this feature was only available for pilot participants.

The [Target2 Data Object](https://msdn.microsoft.com/library/dn743781(v=msads.90).aspx) is now generally available and includes the [DayTimeTarget](https://msdn.microsoft.com/library/dn743766(v=msads.90).aspx) and [LocationTarget2](https://msdn.microsoft.com/library/dn743770(v=msads.90).aspx) objects, which are not included in the legacy [Target](https://msdn.microsoft.com/library/bb671789(v=msads.90).aspx) object.

The following service operations are reserved for working with `Target2` objects.

-   [AddTargetsToLibrary2](https://msdn.microsoft.com/library/dn743775(v=msads.90).aspx)

-   [GetTargetsByAdGroupIds2](https://msdn.microsoft.com/library/dn743775(v=msads.90).aspx)

-   [GetTargetsByCampaignIds2](https://msdn.microsoft.com/library/dn743778(v=msads.90).aspx)

-   [GetTargetsByIds2](https://msdn.microsoft.com/library/dn743779(v=msads.90).aspx)

-   [UpdateTargetsInLibrary2](https://msdn.microsoft.com/library/dn743774(v=msads.90).aspx)

The following service operations may be used with either `Target` or `Target2` objects.

-   [DeleteTargetFromAdGroup](https://msdn.microsoft.com/library/dn277500(v=msads.90).aspx)

-   [DeleteTargetFromCampaign](https://msdn.microsoft.com/library/dn277503(v=msads.90).aspx)

-   [DeleteTargetsFromLibrary](https://msdn.microsoft.com/library/dn277507(v=msads.90).aspx)

-   [GetTargetsInfoFromLibrary](https://msdn.microsoft.com/library/dn236308(v=msads.90).aspx)

-   [SetTargetToAdGroup](https://msdn.microsoft.com/library/dn277508(v=msads.90).aspx)

-   [SetTargetToCampaign](https://msdn.microsoft.com/library/dn277512(v=msads.90).aspx)

The following service operations are reserved for working with the legacy `Target` objects.

-   [AddTargetsToLibrary](https://msdn.microsoft.com/library/dn277526(v=msads.90).aspx)

-   [GetTargetsByAdGroupIds](https://msdn.microsoft.com/library/dn236297(v=msads.90).aspx)

-   [GetTargetsByCampaignIds](https://msdn.microsoft.com/library/dn236300(v=msads.90).aspx)

-   [GetTargetsByIds](https://msdn.microsoft.com/library/dn236304(v=msads.90).aspx)

-   [UpdateTargetsInLibrary](https://msdn.microsoft.com/library/dn236301(v=msads.90).aspx)

For code examples that show how to associate targets with a campaign and ad group, see [Targets in C&#35;](../guides/targets-in-csharp.md) | [Targets in Java](../guides/targets-in-java.md) | [Targets in PHP](../guides/targets-in-php.md).

#### Negative Keywords
> [!NOTE]
> Previously this feature was only available for pilot participants.

The [NegativeKeyword Data Object](https://msdn.microsoft.com/library/dn743739(v=msads.90).aspx) is now generally available and defines a negative keyword with match type. Each negative keyword can be added and deleted, but cannot be updated.

> [!NOTE]
> The same negative keyword and match type can be added to all campaigns, ad groups, and negative keyword lists if you choose. Each instance must be added and associated individually and would be assigned a unique negative keyword identifier.

You may choose to associate an exclusive set of negative keywords to an individual campaign or ad group. An exclusive set of negative keywords cannot be shared with other campaigns or ad groups. You can manage an exclusive set of negative keywords with the [AddNegativeKeywordsToEntities](https://msdn.microsoft.com/library/dn743724(v=msads.90).aspx),  [DeleteNegativeKeywordsFromEntities](https://msdn.microsoft.com/library/dn743725(v=msads.90).aspx), and [GetNegativeKeywordsByEntityIds](https://msdn.microsoft.com/library/dn743730(v=msads.90).aspx) operations.

Negative keywords can also be added and deleted from a shared negative keyword list. The negative keyword list can be shared or associated with multiple campaigns.

> [!NOTE]
> Negative keyword lists cannot be associated with an ad group. An ad group can only be assigned an exclusive set of negative keywords. In addition to the exclusive set of negative keywords that can be assigned to a campaign, each campaign can be associated with one negative keyword list.

To create a negative keyword list, call the [AddSharedEntity](https://msdn.microsoft.com/library/dn743722(v=msads.90).aspx) operation and pass a [NegativeKeywordList](https://msdn.microsoft.com/library/dn743737(v=msads.90).aspx), which inherits from both [SharedList](https://msdn.microsoft.com/library/dn743734(v=msads.90).aspx) and [SharedEntity](https://msdn.microsoft.com/library/dn743735(v=msads.90).aspx).You can create up to 20 negative keyword lists per account and share or associate them with any campaign in the same account.  You can get existing negative keyword lists by calling the [GetSharedEntitiesByAccountId](https://msdn.microsoft.com/library/dn743728(v=msads.90).aspx) operation. You can update the name of the negative keyword list by calling the [UpdateSharedEntities](https://msdn.microsoft.com/library/dn743732(v=msads.90).aspx) operation. You can delete the negative keyword list by calling the [DeleteSharedEntities](https://msdn.microsoft.com/library/dn743726(v=msads.90).aspx) operation.

To add negative keywords to a negative keyword list, call the [AddListItemsToSharedList](https://msdn.microsoft.com/library/dn743721(v=msads.90).aspx) operation and pass a list of [NegativeKeyword](https://msdn.microsoft.com/library/dn743739(v=msads.90).aspx), which inherits from [SharedListItem](https://msdn.microsoft.com/library/dn743738(v=msads.90).aspx).You can add up to 10,000 negative keywords to each negative keyword list.  You can get negative keywords within a specified list by calling the [GetListItemsBySharedList](https://msdn.microsoft.com/library/dn743729(v=msads.90).aspx) operation. Negative keywords can be removed from a list by calling  the [DeleteListItemsFromSharedList](https://msdn.microsoft.com/library/dn743723(v=msads.90).aspx) operation.

To associate a negative keyword list with a campaign, specify an array of [SharedEntityAssociation](https://msdn.microsoft.com/library/dn743769(v=msads.90).aspx) with  the [SetSharedEntityAssociations](https://msdn.microsoft.com/library/dn743780(v=msads.90).aspx) service operation. Each `SharedEntityAssociation` should include the type of entity (currently only Campaign is supported), campaign identifier, and negative keyword list identifier. You can get the associations by entity identifier or negative keyword list identifier by calling the respective [GetSharedEntityAssociationsByEntityIds](https://msdn.microsoft.com/library/dn743771(v=msads.90).aspx) and [GetSharedEntityAssociationsBySharedEntityIds](https://msdn.microsoft.com/library/dn743773(v=msads.90).aspx) operations. You can remove the association between the campaign and negative keyword list by calling the [DeleteSharedEntityAssociations](https://msdn.microsoft.com/library/dn743727(v=msads.90).aspx) operation.

For code examples that show how to associate negative keywords and negative keyword lists with a campaign, see [Negative Keywords in C&#35;](../guides/negative-keywords-in-csharp.md) | [Negative Keywords in Java](../guides/negative-keywords-in-java.md) | [Negative Keywords in PHP](../guides/negative-keywords-in-php.md).

### <a name="reporting_september2014"></a>Reporting Version 9
The `AdExtensionDimensionReport` is deprecated and no longer supported. A call to generate this report will throw an exception.

## <a name="august2014"></a>August 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Ad Intelligence Version 9](#adintel_august2014)

-   [Bulk Version 9](#bulk_august2014)

-   [Campaign Management Version 9](#campaign_august2014)

-   [Customer Billing Version 9](#billing_august2014)

-   [Customer Management Version 9](#customer_august2014)

-   [Reporting Version 9](#reporting_august2014)

### <a name="adintel_august2014"></a>Ad Intelligence Version 9

#### Keyword Suggestion Types
The following values are now supported in the `SuggestionType` element of the [SuggestKeywordsFromExistingKeywords](https://msdn.microsoft.com/library/dn336990(v=msads.90).aspx) operation.

-   2 - Now supported for Italy (IT), Netherlands (NL), and Norway (NO), in addition to existing markets.

-   4 - Now supported for Taiwan (TW), in addition to existing markets.

For a complete list of possible providers, the language and country restrictions of each provider, and the default provider by country, see the [Remarks](https://msdn.microsoft.com/library/dn336990(v=msads.90).aspx#remarks) section in [SuggestKeywordsFromExistingKeywords](https://msdn.microsoft.com/library/dn336990(v=msads.90).aspx).

### <a name="bulk_august2014"></a>Bulk Version 9

#### Format Version 3.0
The latest supported value for the `FormatVersion` element of [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/jj885755(v=msads.90).aspx) and [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/jj885756(v=msads.90).aspx) service operations is 3.0. The bulk format version is separate from the Bing Ads API version.  Format versions enable a flexible upgrade path to adopt the latest supported features without breaking your application. For more information, see [Bulk File Schema](https://msdn.microsoft.com/library/dn539651(v=msads.90).aspx#referencekeys).

> [!IMPORTANT]
> Before you upgrade to the latest format version, you should read [Bulk File Deprecated Record Types](https://msdn.microsoft.com/library/dn539650(v=msads.90).aspx). If you currently use any of the deprecated records, you should read about and understand the differences between the deprecated version and the latest version of the [Bulk File Record Types](https://msdn.microsoft.com/library/jj134998(v=msads.90).aspx).

### <a name="campaign_august2014"></a>Campaign Management Version 9

#### Image Ad Extension
The `Description` element is added to the [ImageAdExtension](https://msdn.microsoft.com/library/dn766199(v=msads.90).aspx) object.

This element can be used by the advertiser, agency, or account manager to track, label, or manage image media. This description is not displayed with the ad or image.

#### Media Associations
The [GetMediaAssociations](https://msdn.microsoft.com/library/dn336990(v=msads.90).aspx) operation is added and returns a list of [KeywordOpportunities](https://msdn.microsoft.com/library/dn798358(v=msads.90).aspx) objects.

This operation gets the media associations of the specified entity type from an account’s media library. For example you can get the identifier of media for an image ad extension associated with an ad group.

### <a name="billing_august2014"></a>Customer Billing Version 9

#### Order By Field for Search Operations
The `LifeCycleStatus` value is added to the [OrderByField](https://msdn.microsoft.com/library/dn743750(v=msads.90).aspx) value set.

> [!NOTE]
> This value is reserved for future use.

### <a name="customer_august2014"></a>Customer Management Version 9

#### Order By Field for Search Operations
The `LifeCycleStatus` value is added to the [OrderByField](https://msdn.microsoft.com/library/dn743750(v=msads.90).aspx) value set.

When calling [SearchAccounts](https://msdn.microsoft.com/library/dn743757(v=msads.90).aspx), for example you may choose to order the results by account life cycle status.

### <a name="reporting_august2014"></a>Reporting Version 9

#### Exclude Zero Click Search Term Data
The `ExcludeZeroClicks` element is added to the [SearchQueryPerformanceReportFilter](https://msdn.microsoft.com/library/ee703961(v=msads.90).aspx), and can be used when submitting the [SearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/ee703962(v=msads.90).aspx).

If the value of the `ExcludeZeroClicks` element is set to true, the report will exclude data for search terms that had one or more ad impressions but resulted in zero clicks.

## <a name="july2014"></a>July 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Campaign Management Version 9](#campaign_july2014)

-   [Customer Management Version 9](#customer_july2014)

### <a name="campaign_july2014"></a>Campaign Management Version 9

#### ActiveLimited Editorial Status
The `ActiveLimited` value is now available in the `EditorialStatus` element of the [Ad](https://msdn.microsoft.com/library/bb671952(v=msads.90).aspx), [BiddableAdGroupCriterion](https://msdn.microsoft.com/library/jj689538(v=msads.90).aspx), and [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.90).aspx) data objects.

This value indicates that the entity passed editorial review in one or more markets, and one or more elements of the entity is undergoing editorial review in another market. For example, a keyword that passed editorial review for Canada and is still pending review in the United States.

### <a name="customer_july2014"></a>Customer Management Version 9

#### User Invitations
The [SendUserInvitation](https://msdn.microsoft.com/library/dn789440(v=msads.90).aspx) operation is added. You can send an invitation for  a Microsoft account user to manage one or more Bing Ads customer accounts. When the invitation is accepted, the user's Microsoft account is linked to the specified Bing Ads customer accounts. For more information about user authentication, see [Managing User Authentication with OAuth](../Topic/Managing%20User%20Authentication%20with%20OAuth.md).

To get pending user invitations you can use the [SearchUserInvitations](https://msdn.microsoft.com/library/dn771300(v=msads.90).aspx) operation and filter by CustomerId.

## <a name="june2014"></a>June 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Ad Intelligence Version 9](#adintel_june2014)

-   [Bulk Version 9](#bulk_june2014)

-   [Campaign Management Version 9](#campaign_june2014)

-   [Customer Management Version 9](#customer_june2014)

-   [Optimizer Version 9](#optimizer_june2014)

-   [Reporting Version 9](#reporting_june2014)

### <a name="adintel_june2014"></a>Ad Intelligence Version 9

#### Ad Group Bid Landscape
The [GetBidLandscapeByAdGroupIds](https://msdn.microsoft.com/library/dn743755(v=msads.90).aspx) service operation is added and takes our bid tuning functionality one step further than [GetBidLandscapeByKeywordIds](https://msdn.microsoft.com/library/dn631945(v=msads.90).aspx). Given a list of existing ad groups, this operation returns for each a list of suggested bids and estimated performance statistics. You can use the landscape view of multiple bid points with estimated traffic for the same ad group to help make decisions about how to adjust your ad group level default bid to optimize for clicks, impressions, and cost. For example you might use the resulting data to visualize a clicks to cost curve or a bid to impressions curve.

You can get bid landscape for an entire ad group in either default or uniform mode. For more information, see [AdGroupBidLandscapeType Value Set](https://msdn.microsoft.com/library/dn743748(v=msads.90).aspx).

### <a name="bulk_june2014"></a>Bulk Version 9

#### BulkDownloadEntity
The `NegativeKeywordList`, `NegativeKeyword`, and `CampaignNegativeKeywordList` elements of the [BulkDownloadEntity](https://msdn.microsoft.com/library/dn249982(v=msads.90).aspx) value set have been renamed to `NegativeKeywordLists`, `SharedNegativeKeywords`, and `CampaignNegativeKeywordListAssosciations` respectively.

#### Image Ad Extensions
Bulk upload and download now support [Image Ad Extensions](#imageadextensions). The record types `Image Ad Extension` and `Ad Group Image Ad Extension` have been added to the bulk file schema and are documented in the [Bulk File Record Types](https://msdn.microsoft.com/library/jj134998(v=msads.90).aspx) topic.

#### Radius Target Bid Units
A new column, `Unit`, has been added to the `Campaign Radius Target` and `Ad Group Radius Target` record types. This column corresponds to the `RadiusUnit` element of the [RadiusTargetBid2](https://msdn.microsoft.com/library/dn743768(v=msads.90).aspx) data object.

### <a name="campaign_june2014"></a>Campaign Management Version 9

#### Negative Keywords
The [NegativeKeyword Data Object](https://msdn.microsoft.com/library/dn743739(v=msads.90).aspx) is added and defines a negative keyword with match type. Each negative keyword can be added and deleted, but cannot be updated.

> [!NOTE]
> The same negative keyword and match type can be added to all campaigns, ad groups, and negative keyword lists if you choose. Each instance must be added and associated individually and would be assigned a unique negative keyword identifier.

You may choose to associate an exclusive set of negative keywords to an individual campaign or ad group. An exclusive set of negative keywords cannot be shared with other campaigns or ad groups. You can manage an exclusive set of negative keywords with the [AddNegativeKeywordsToEntities](https://msdn.microsoft.com/library/dn743724(v=msads.90).aspx),  [DeleteNegativeKeywordsFromEntities](https://msdn.microsoft.com/library/dn743725(v=msads.90).aspx), and [GetNegativeKeywordsByEntityIds](https://msdn.microsoft.com/library/dn743730(v=msads.90).aspx) operations.

Negative keywords can also be added and deleted from a shared negative keyword list. The negative keyword list can be shared or associated with multiple campaigns.

> [!NOTE]
> Negative keyword lists cannot be associated with an ad group. An ad group can only be assigned an exclusive set of negative keywords. In addition to the exclusive set of negative keywords that can be assigned to a campaign, each campaign can be associated with one negative keyword list.

To create a negative keyword list, call the [AddSharedEntity](https://msdn.microsoft.com/library/dn743722(v=msads.90).aspx) operation and pass a [NegativeKeywordList](https://msdn.microsoft.com/library/dn743737(v=msads.90).aspx), which inherits from both [SharedList](https://msdn.microsoft.com/library/dn743734(v=msads.90).aspx) and [SharedEntity](https://msdn.microsoft.com/library/dn743735(v=msads.90).aspx).You can create up to 20 negative keyword lists per account and share or associate them with any campaign in the same account.  You can get existing negative keyword lists by calling the [GetSharedEntitiesByAccountId](https://msdn.microsoft.com/library/dn743728(v=msads.90).aspx) operation. You can update the name of the negative keyword list by calling the [UpdateSharedEntities](https://msdn.microsoft.com/library/dn743732(v=msads.90).aspx) operation. You can delete the negative keyword list by calling the [DeleteSharedEntities](https://msdn.microsoft.com/library/dn743726(v=msads.90).aspx) operation.

To add negative keywords to a negative keyword list, call the [AddListItemsToSharedList](https://msdn.microsoft.com/library/dn743721(v=msads.90).aspx) operation and pass a list of [NegativeKeyword](https://msdn.microsoft.com/library/dn743739(v=msads.90).aspx), which inherits from [SharedListItem](https://msdn.microsoft.com/library/dn743738(v=msads.90).aspx).You can add up to 10,000 negative keywords to each negative keyword list.  You can get negative keywords within a specified list by calling the [GetListItemsBySharedList](https://msdn.microsoft.com/library/dn743729(v=msads.90).aspx) operation. Negative keywords can be removed from a list by calling  the [DeleteListItemsFromSharedList](https://msdn.microsoft.com/library/dn743723(v=msads.90).aspx) operation.

To associate a negative keyword list with a campaign, specify an array of [SharedEntityAssociation](https://msdn.microsoft.com/library/dn743769(v=msads.90).aspx) with  the [SetSharedEntityAssociations](https://msdn.microsoft.com/library/dn743780(v=msads.90).aspx) service operation. Each `SharedEntityAssociation` should include the type of entity (currently only Campaign is supported), campaign identifier, and negative keyword list identifier. You can get the associations by entity identifier or negative keyword list identifier by calling the respective [GetSharedEntityAssociationsByEntityIds](https://msdn.microsoft.com/library/dn743771(v=msads.90).aspx) and [GetSharedEntityAssociationsBySharedEntityIds](https://msdn.microsoft.com/library/dn743773(v=msads.90).aspx) operations. You can remove the association between the campaign and negative keyword list by calling the [DeleteSharedEntityAssociations](https://msdn.microsoft.com/library/dn743727(v=msads.90).aspx) operation.

For code examples that show how to associate negative keywords and negative keyword lists with a campaign, see [Negative Keywords in C&#35;](../guides/negative-keywords-in-csharp.md) | [Negative Keywords in Java](../guides/negative-keywords-in-java.md) | [Negative Keywords in PHP](../guides/negative-keywords-in-php.md).

#### Targets
The [Target2 Data Object](https://msdn.microsoft.com/library/dn743781(v=msads.90).aspx) is added and includes the [DayTimeTarget](https://msdn.microsoft.com/library/dn743766(v=msads.90).aspx) and [LocationTarget2](https://msdn.microsoft.com/library/dn743770(v=msads.90).aspx) objects, which are not included in the legacy [Target](https://msdn.microsoft.com/library/bb671789(v=msads.90).aspx) object.

The following service operations are reserved for working with `Target2` objects.

-   [AddTargetsToLibrary2](https://msdn.microsoft.com/library/dn743775(v=msads.90).aspx)

-   [GetTargetsByAdGroupIds2](https://msdn.microsoft.com/library/dn743775(v=msads.90).aspx)

-   [GetTargetsByCampaignIds2](https://msdn.microsoft.com/library/dn743778(v=msads.90).aspx)

-   [GetTargetsByIds2](https://msdn.microsoft.com/library/dn743779(v=msads.90).aspx)

-   [UpdateTargetsInLibrary2](https://msdn.microsoft.com/library/dn743774(v=msads.90).aspx)

The following service operations may be used with either `Target` or `Target2` objects.

-   [DeleteTargetFromAdGroup](https://msdn.microsoft.com/library/dn277500(v=msads.90).aspx)

-   [DeleteTargetFromCampaign](https://msdn.microsoft.com/library/dn277503(v=msads.90).aspx)

-   [DeleteTargetsFromLibrary](https://msdn.microsoft.com/library/dn277507(v=msads.90).aspx)

-   [GetTargetsInfoFromLibrary](https://msdn.microsoft.com/library/dn236308(v=msads.90).aspx)

-   [SetTargetToAdGroup](https://msdn.microsoft.com/library/dn277508(v=msads.90).aspx)

-   [SetTargetToCampaign](https://msdn.microsoft.com/library/dn277512(v=msads.90).aspx)

The following service operations are reserved for working with the legacy `Target` objects.

-   [AddTargetsToLibrary](https://msdn.microsoft.com/library/dn277526(v=msads.90).aspx)

-   [GetTargetsByAdGroupIds](https://msdn.microsoft.com/library/dn236297(v=msads.90).aspx)

-   [GetTargetsByCampaignIds](https://msdn.microsoft.com/library/dn236300(v=msads.90).aspx)

-   [GetTargetsByIds](https://msdn.microsoft.com/library/dn236304(v=msads.90).aspx)

-   [UpdateTargetsInLibrary](https://msdn.microsoft.com/library/dn236301(v=msads.90).aspx)

For code examples that show how to associate targets with a campaign and ad group, see [Targets in C&#35;](../guides/targets-in-csharp.md) | [Targets in Java](../guides/targets-in-java.md) | [Targets in PHP](../guides/targets-in-php.md).

#### Replace Target Associations
The `ReplaceAssociation` element is added to the [SetTargetToAdGroup](https://msdn.microsoft.com/library/dn277508(v=msads.90).aspx) and [SetTargetToCampaign](https://msdn.microsoft.com/library/dn277512(v=msads.90).aspx) service operations.

If the specified ad group or campaign entity is already associated with a target, this element determines whether to replace the existing association between the entity and target with the specified `TargetId`.

If set to True the operation will replace the existing association between the entity and target with the specified `TargetId`.

The default value is False if not otherwise specified. If the value is False and if an association already exists, the operation will throw error `1427`, `CampaignServiceTargetAlreadyAssociatedWithEntity`.

> [!NOTE]
> If the specified entity is not currently associated with a target, this element has no effect.

#### Granular Radius Target Bid
Previously Bing Ads only allowed radius targets by increments of 5, for example 5, 10, 20, as the radius of a radius target bid. Positive integer increments from 1 to 500 (for example 1, 2, 3, 499, and 500) are now supported. Please ensure your clients can handle such values in the `Radius` element of the [RadiusTargetBid](https://msdn.microsoft.com/library/dd796863(v=msads.90).aspx) and [RadiusTargetBid2](https://msdn.microsoft.com/library/dn743768(v=msads.90).aspx) moving forward.

#### <a name="imageadextensions"></a>Image Ad Extensions
The [ImageAdExtension Data Object](https://msdn.microsoft.com/library/dn766199(v=msads.90).aspx) is added and defines an ad extension that specifies an image with alternative text to include in a text ad. The `ImageAdExtension` object derives from the [AdExtension](https://msdn.microsoft.com/library/hh527708(v=msads.90).aspx) object and can be managed using existing ad extensions operations, for example [AddAdExtensions](https://msdn.microsoft.com/library/dn236319(v=msads.90).aspx) and [SetAdExtensionsAssociations](https://msdn.microsoft.com/library/dn277532(v=msads.90).aspx). For more information, see [Ad Extensions](../guides/ad-extensions.md).

Before you can create an image ad extension, you must add valid media to your account's library with the [AddMedia](https://msdn.microsoft.com/library/dn277518(v=msads.90).aspx) operation. Then you can get the media identifiers for image ad extensions with the [GetMediaMetaDataByAccountId](https://msdn.microsoft.com/library/dn766196(v=msads.90).aspx) operation. Once you know the media meta data identifiers then you can alternatively call [GetMediaMetaDataByIds](https://msdn.microsoft.com/library/dn766200(v=msads.90).aspx).

#### Site Link Description
You can now add two additional lines of text with each site link in your ad extension. The `Description1` and `Description2` elements are added to the [SiteLink Data Object](https://msdn.microsoft.com/library/jj134381(v=msads.90).aspx).

#### Site Link Device Preference
You can now set the of the `DevicePreference` element of the [SiteLink](https://msdn.microsoft.com/library/jj134381(v=msads.90).aspx) object to indicate whether you prefer to show site links on mobile devices or all devices.

#### Enhanced Exact Match
For accounts in the United States which have English language ad groups, Bing Ads automatically includes close variations of your exact match keywords, such as plural forms. For example, if your keyword is “motorcycle,” close variations would include “motorcycles".

If you don’t want your ads to show for close variations of your exact match keywords, then use the `ForwardCompatibilityMap` element of the [Campaign Data Object](https://msdn.microsoft.com/library/bb672054(v=msads.90).aspx) and set the value of the KeywordVariantMatchEnabled key to False.

### <a name="customer_june2014"></a>Customer Management Version 9

#### UTM AutoTag
Determines whether to append or replace the supported UTM tracking codes within all ad and keyword destination URLs for the account. To manage auto tag settings, use the `ForwardCompatibilityMap` element of the [Account Data Object](https://msdn.microsoft.com/library/bb671588(v=msads.90).aspx) and set the value of the AutoTag key to one of the following supported values.

-   0 - Bing Ads will not append any UTM tracking codes to your ad or keyword destination URL.

-   1 - Bing Ads will automatically append the supported UTM tracking codes, and preserve any existing UTM tracking codes that you added to your ad or keyword's destination URL.

-   2 - Bing Ads will automatically append the supported UTM tracking codes, and replace any of the existing and supported UTM tracking codes that you added to your ad or keyword's destination URL.

### <a name="optimizer_june2014"></a>Optimizer Version 9

#### Unified Bid Opportunity
The [GetBidOpportunities](https://msdn.microsoft.com/library/dn376337(v=msads.90).aspx) service operation is updated to support bid opportunities for client specified position goals, for example first page versus mainline ad position. When calling `GetBidOpportunities`, you can set the optional `OpportunityType` request element to one or more of the [BidOpportunityType](https://msdn.microsoft.com/library/dn766183(v=msads.90).aspx) values.

> [!NOTE]
> The operation will only return opportunities if there’s a suggested increase within 100% of your current bid that will help you achieve the specified goal.

#### Unified Keyword Opportunity
The [GetKeywordOpportunities](https://msdn.microsoft.com/library/dn376336(v=msads.90).aspx) service operation is updated to support broad match keyword opportunities. When calling `GetKeywordOpportunities`, you can set the optional `OpportunityType` request element to one or more of the [KeywordOpportunityType](https://msdn.microsoft.com/library/dn766184(v=msads.90).aspx) values. For example if you include only the BroadMatch keyword opportunity type, the operation would only return [BroadMatchKeywordOpportunity](https://msdn.microsoft.com/library/dn766186(v=msads.90).aspx) objects. If you do not specify any opportunity type or include only the CampaignContext keyword opportunity type, the operation would only return [KeywordOpportunity](https://msdn.microsoft.com/library/jj649133(v=msads.90).aspx) objects as before.

#### Opportunity Modifiers
The [ApplyOpportunities](https://msdn.microsoft.com/library/dn376334(v=msads.90).aspx) service operation is updated and now enables you to apply a modified or customized opportunity. When calling `ApplyOpportunities`, you can set the optional `OpportunityModifiers` request element to include one or more of the [OpportunityModifier](https://msdn.microsoft.com/library/dn766182(v=msads.90).aspx) objects. For example you can specify a bid different than the suggested opportunity by setting the `Bid` element of a [BidOpportunityModifier](https://msdn.microsoft.com/library/dn766190(v=msads.90).aspx) object and including the object in a call to `ApplyOpportunities`.

> [!NOTE]
> If specified, the `OpportunityModifiers` overrides any specified `OpportunityKeys`.

### <a name="reporting_june2014"></a>Reporting Version 9

#### Search Campaign Change History Report
The optional `AccountNumber` and `AccountName` columns are added to the [SearchCampaignChangeHistoryReportColumn Value Set](https://msdn.microsoft.com/library/hh912353(v=msads.90).aspx).

#### Reduced Impression Share Column Restrictions
For reports that include impression share performance statistics columns you can now include the BidMatchType, DeliveredMatchType, DeviceType, and Network attributes in the same report request. Likewise if you include any of those attribute columns, you can include any of the impression share performance statistics columns.

For information about standing attribute restrictions with impression share reports, please see [Column Restrictions](../Topic/Getting%20Reports.md#columnrestrictions).

## <a name="may2014"></a>May 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Customer Billing Version 9](#billing_may2014)

-   [Customer Management Version 9](#customer_may2014)

-   [Reporting Version 9](#reporting_may2014)

### <a name="billing_may2014"></a>Customer Billing Version 9

#### Insertion Order
The following operations to enable agency management of insertion orders are added.

-   [AddInsertionOrder](https://msdn.microsoft.com/library/dn743758(v=msads.90).aspx)

-   [SearchInsertionOrders](https://msdn.microsoft.com/library/dn743759(v=msads.90).aspx)

-   [UpdateInsertionOrder](https://msdn.microsoft.com/library/dn743760(v=msads.90).aspx)

### <a name="customer_may2014"></a>Customer Management Version 9

#### Search Accounts
The [SearchAccounts](https://msdn.microsoft.com/library/dn743757(v=msads.90).aspx) operation is added, and you can search accounts by AccountId, AccountNumber, CustomerId, and UserId.

### <a name="reporting_may2014"></a>Reporting Version 9

#### Geo Location
The [GeoLocationPerformanceReportRequest](https://msdn.microsoft.com/library/dn743772(v=msads.90).aspx), [GeoLocationPerformanceReportFilter](https://msdn.microsoft.com/library/dn743754(v=msads.90).aspx), and [GeoLocationPerformanceReportColumn](https://msdn.microsoft.com/library/dn743762(v=msads.90).aspx) are added.

> [!NOTE]
> With the introduction of this new report, the `GeographicalLocationReport` programming elements are deprecated.

#### Product Offer
The [ProductOfferPerformanceReportRequest](https://msdn.microsoft.com/library/dn743719(v=msads.90).aspx), [ProductOfferPerformanceReportFilter](https://msdn.microsoft.com/library/dn743718(v=msads.90).aspx), and [ProductOfferPerformanceReportColumn](https://msdn.microsoft.com/library/dn743720(v=msads.90).aspx) are added.

## <a name="april2014"></a>April 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Ad Intelligence Version 9](#adintel_april2014)

-   [Bulk Version 9](#bulk_april2014)

-   [Campaign Management Version 9](#campaign_april2014)

-   [Customer Management Version 9](#customer_april2014)

-   [Reporting Version 9](#reporting_april2014)

### <a name="adintel_april2014"></a>Ad Intelligence Version 9

#### Keyword Bid Landscape
The [GetBidLandscapeByKeywordIds](https://msdn.microsoft.com/library/dn631945(v=msads.90).aspx) service operation is added. Given a list of existing keywords, this operation returns for each a list of suggested bids and estimated performance statistics from 1 to  7 days.

You can use the landscape view of multiple bid points with estimated traffic for the same keyword to help make decisions about how to adjust your keyword bid to optimize for clicks, impressions, and cost. For example you might use the resulting data to visualize a clicks to cost curve or a bid to impressions curve.

### <a name="bulk_april2014"></a>Bulk Version 9

#### <a name="clientid"></a>Client Identifiers
The `Client Id` field is added to the bulk upload and upload results file. Client identifiers may be used to associate input records in the bulk upload file with output records in the results file. For example when adding new records you may set the `Client Id` field to a string value of your choosing. The Bing Ads system makes no modifications to your client identifiers and passes them through to the results file for the corresponding record. For more information, see [Client Identifiers](https://msdn.microsoft.com/library/dn539651(v=msads.90).aspx#clientid).

### <a name="campaign_april2014"></a>Campaign Management Version 9

#### <a name="campaignsuspended"></a>Campaign Status Suspended
The `Suspended` value is added to the [CampaignStatus Value Set](https://msdn.microsoft.com/library/bb672025(v=msads.90).aspx), and indicates that your  campaign has been suspended and no ads are eligible for delivery because of potentially fraudulent activity.

### <a name="customer_april2014"></a>Customer Management Version 9

#### Client Link
The following operations to enable agency management of client accounts are added.

-   [AddClientLinks](https://msdn.microsoft.com/library/dn632187(v=msads.90).aspx)

-   [SearchClientLinks](https://msdn.microsoft.com/library/dn632186(v=msads.90).aspx)

-   [UpdateClientLinks](https://msdn.microsoft.com/library/dn632185(v=msads.90).aspx)

Linking enables any agency Super Admin to access and manage the specified client account. For more information, see [Link to Client Accounts](../guides/management-model-for-agencies.md#clientlink).

> [!NOTE]
> Client link operations are currently not supported in sandbox.

#### <a name="accountsuspended"></a>Account Status Suspended
The `Suspended` value is added to the [AccountLifeCycleStatus Value Set](https://msdn.microsoft.com/library/ff728394(v=msads.90).aspx), and indicates that your account has been suspended and no ads are eligible for delivery because of potentially fraudulent activity.

### <a name="reporting_april2014"></a>Reporting Version 9

#### Entity Identifiers
One or more of the `AccountId`, `CampaignId`, and `AdGroupId` entity identifiers have been added to the following report column value sets.

|Value Set|Columns Added|
|-------------|-----------------|
|[AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bb671947(v=msads.90).aspx)|AccountId|
|[AdDynamicTextPerformanceReportColumn](https://msdn.microsoft.com/library/bb671878(v=msads.90).aspx)|AccountId|
|[AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)|AccountId|
|[AdPerformanceReportColumn](https://msdn.microsoft.com/library/bb671923(v=msads.90).aspx)|AccountId<br /><br />CampaignId|
|[AgeGenderDemographicReportColumn](https://msdn.microsoft.com/library/bb671786(v=msads.90).aspx)|AccountId<br /><br />AdGroupId<br /><br />CampaignId|
|[BudgetSummaryReportColumn](https://msdn.microsoft.com/library/bb671925(v=msads.90).aspx)|AccountId<br /><br />CampaignId|
|[CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)|AccountId|
|[DestinationUrlPerformanceReportColumn](https://msdn.microsoft.com/library/bb671820(v=msads.90).aspx)|AccountId|
|[GeographicalLocationReportColumn](https://msdn.microsoft.com/library/dn411634(v=msads.90).aspx)|AccountId<br /><br />AdGroupId<br /><br />CampaignId|
|[RichAdComponentPerformanceReportColumn](https://msdn.microsoft.com/library/hh180149(v=msads.90).aspx)|AccountId|
|[SearchCampaignChangeHistoryReportColumn](https://msdn.microsoft.com/library/hh912353(v=msads.90).aspx)|AccountId<br /><br />AdGroupId<br /><br />CampaignId|

## <a name="march2014"></a>March 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bulk Version 9](#bulk_march2014)

-   [Campaign Management Version 9](#campaign_march2014)

-   [Reporting Version 9](#reporting_march2014)

### <a name="bulk_march2014"></a>Bulk Version 9

#### Detailed Download Status
The [GetDetailedBulkDownloadStatus](https://msdn.microsoft.com/library/dn600289(v=msads.90).aspx) service operation now returns completion progress of a bulk download request in the `PercentComplete` response element.

### <a name="campaign_march2014"></a>Campaign Management Version 9

#### <a name="radiustargetbid"></a>Granular Radius Target Bid
Currently Bing Ads only allows radius targets by increments of 5, for example 5, 10, 20, as the radius of a radius target bid. Positive integer increments from 1 to 500 (for example 1, 2, 3, 499, and 500) will be supported in a future update. Please ensure your clients can handle such values in the `Radius` element of the [RadiusTargetBid](https://msdn.microsoft.com/library/dd796863(v=msads.90).aspx) moving forward.

#### <a name="sitelinkdescription"></a>Site Link Description
Soon you will be able to add two additional lines of text with each site link in your ad extension. The `Description1` and `Description2` elements are added to the [SiteLink](https://msdn.microsoft.com/library/jj134381(v=msads.90).aspx). Until the feature is available, these fields will be available in the WSDL only as stubs, and they cannot be specified nor will they be returned. In the meantime you should refresh your campaign management proxy to get the latest references.

### <a name="reporting_march2014"></a>Reporting Version 9

#### Ad Extension Detail Report
The ad extension detail report is added to the reporting service. Use this report to discover the effectiveness of individual ad extension items, for example each link of a sitelink extension.
                You can request impressions, clicks, spend, and average cost per click of individual extension items. Once downloaded, this data can be sorted by the individual ad extension display name, ad extension ID, and ad extension type.

To use the report, submit the [AdExtensionDetailReportRequest](https://msdn.microsoft.com/library/dn610364(v=msads.90).aspx) with an optional [AdExtensionDetailReportFilter](https://msdn.microsoft.com/library/dn610806(v=msads.90).aspx). Specify attribute and performance statistic columns with the [AdExtensionDetailReportColumn](https://msdn.microsoft.com/library/dn610365(v=msads.90).aspx). For more information, see [Getting Reports](../Topic/Getting%20Reports.md).

#### Common Attributes and Performance Statistics
The following report column value sets are updated to include popular attribute and performance statistic columns.

-   [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bb671947(v=msads.90).aspx)

-   [AdExtensionByAdReportColumn](https://msdn.microsoft.com/library/jj713608(v=msads.90).aspx)

-   [AdExtensionByKeywordReportColumn](https://msdn.microsoft.com/library/jj713610(v=msads.90).aspx)

-   [AdExtensionDetailReportColumn](https://msdn.microsoft.com/library/dn610365(v=msads.90).aspx)

-   [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)

-   [AdPerformanceReportColumn](https://msdn.microsoft.com/library/bb671923(v=msads.90).aspx)

-   [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)

-   [DestinationUrlPerformanceReportColumn](https://msdn.microsoft.com/library/bb671820(v=msads.90).aspx)

-   [GeographicalLocationReportColumn](https://msdn.microsoft.com/library/dn411634(v=msads.90).aspx)

-   [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bb672087(v=msads.90).aspx)

-   [ProductTargetPerformanceReportColumn](https://msdn.microsoft.com/library/dn195844(v=msads.90).aspx)

-   [PublisherUsagePerformanceReportColumn](https://msdn.microsoft.com/library/dd797159(v=msads.90).aspx)

-   [SearchQueryPerformanceReportColumn](https://msdn.microsoft.com/library/ee703958(v=msads.90).aspx)

The following attributes and performance statistics are now available in all of the reports listed above.

|Attributes|Performance Statistics|
|--------------|--------------------------|
|BidMatchType<br /><br />DeliveredMatchType<br /><br />DeviceOS<br /><br />DeviceType<br /><br />Language<br /><br />Network<br /><br />TopVsOther|Assists<br /><br />Clicks<br /><br />ConversionRate<br /><br />Conversions<br /><br />CostPerAssist<br /><br />CostPerConversion<br /><br />Ctr<br /><br />ExtendedCost<br /><br />Impressions<br /><br />ReturnOnAdSpend<br /><br />Revenue<br /><br />RevenuePerAssist<br /><br />RevenuePerConversion<br /><br />Spend|
For more information, see [Report Attributes and Performance Statistics](../guides/report-attributes-and-performance-statistics.md).

#### Impression Share Column Restrictions
For reports that include impression share performance statistics columns you should not include the following attributes in the same report request. Likewise if you include any of the following attribute columns, you should exclude all of the impression share performance statistics columns.

-   BidMatchType

-   ClickType

-   DeliveredMatchType

-   DeviceOS

-   DeviceType

-   Network

-   TopVsOther

> [!IMPORTANT]
> In the Bing Ads web application, users are not allowed to select the restricted column combinations. Using the Bing Ads API the report submission will not fail, for example if you include BidMatchType and ImpressionLostToBidPercent; however, the fields returned in the downloaded report will be 0 (zero)  in place of any meaningful data.

For more information, see [Column Restrictions](../Topic/Getting%20Reports.md#columnrestrictions).

#### Report Aggregation for Impression Share
The `Weekly`, `Monthly`, `Yearly`, and `Summary` values of the [ReportAggregation value set](https://msdn.microsoft.com/library/bb672067(v=msads.90).aspx) may now be specified when including the impression share columns within the following reports.

-   [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bb671947(v=msads.90).aspx)

-   [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)

-   [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)

#### Search Query Report Impressions and CTR
Previously the number of impressions listed in a search query report might be just a fraction of the total impressions that are generated for a search query. The report would display only impressions that result in at least one click during a one-hour reporting period. For example, if a search query resulted in one or more clicks during hour one, all impressions during hour one were reported. If the same search query resulted in zero clicks during hour two, no impressions were reported for hour two. As a result, the click-through rate (CTR) may have been overstated.

With this release all impressions for search queries are reported, and the click-through rate (CTR) is represented accurately in the report.

#### Search Query Report Aggregation
You may now submit a [SearchQueryPerformanceReportRequest](https://msdn.microsoft.com/library/ee703962(v=msads.90).aspx) with new aggregation values. The `DayOfWeek`, `HourOfDay`, and `Yearly` values are added to the [SearchQueryReportAggregation value set](https://msdn.microsoft.com/library/ee703960(v=msads.90).aspx).

## <a name="february2014"></a>February 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Customer Management Version 9](#customer_february2014)

-   [Reporting Version 9](#reporting_february2014)

### <a name="customer_february2014"></a>Customer Management Version 9

#### Microsoft Account User
Previously when retrieving a [User data object](https://msdn.microsoft.com/library/bb671824(v=msads.90).aspx), the value of the `UserName` element varied as follows.

-   If the value of `IsMigratedToMicrosoftAccount` is false, this element contained the user's Bing Ads managed sign-in user name. The name is case-insensitive.

-   If the value of `IsMigratedToMicrosoftAccount` is true, and if the user never had a Bing Ads managed sign-in user name, this element contained the email address corresponding to the authenticated Microsoft Account.

-   If the value of `IsMigratedToMicrosoftAccount` is true, and if the user migrated from a Bing Ads managed sign-in user name, this element contained the user's Bing Ads managed sign-in user name.

Now when retrieving a [User data object](https://msdn.microsoft.com/library/bb671824(v=msads.90).aspx), the value of the `UserName` element varies as follows.

-   If the value of `IsMigratedToMicrosoftAccount` is false, this element contains the user's Bing Ads managed sign-in user name. The name is case-insensitive.

-   If the value of `IsMigratedToMicrosoftAccount` is true, this element contains the email address corresponding to the authenticated Microsoft Account.

> [!NOTE]
> The email address of the Microsoft Account may differ from the Email element of the [ContactInfo data object](https://msdn.microsoft.com/library/bb671639(v=msads.90).aspx).

### <a name="reporting_february2014"></a>Reporting Version 9

#### Change History Report for Call and Sitelinks Ad Extensions
Change history reporting is now available for [CallAdExtension](https://msdn.microsoft.com/library/jj721598(v=msads.90).aspx) and [SitelinksAdExtension](https://msdn.microsoft.com/library/jj134387(v=msads.90).aspx), including their associations to [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.90).aspx) or [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.90).aspx) entities. You should submit a [SearchCampaignChangeHistoryReportRequest](https://msdn.microsoft.com/library/hh912353(v=msads.90).aspx) using the [SubmitGenerateReport service operation](https://msdn.microsoft.com/library/jj879321(v=msads.90).aspx).

For more information, see [Call extension](https://msdn.microsoft.com/library/hh912353(v=msads.90).aspx#callextension) and [Sitelink extension](https://msdn.microsoft.com/library/hh912353(v=msads.90).aspx#sitelinkextension) within [SearchCampaignChangeHistoryReportColumn Value Set](https://msdn.microsoft.com/library/hh912353(v=msads.90).aspx).

## <a name="january2014"></a>January 2014
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bulk Version 9](#bulk_january2014)

-   [Campaign Management Version 9](#campaign_january2014)

### <a name="bulk_january2014"></a>Bulk Version 9

#### Detailed Download Status
The [GetDetailedBulkDownloadStatus](https://msdn.microsoft.com/library/dn600289(v=msads.90).aspx) service operation is added, and `GetDownloadStatus` is deprecated. This operation provides the status for the bulk download.

> [!NOTE]
> Completion progress of a bulk download request will also be available in a future release.

#### Detailed Upload Status
The [GetDetailedBulkUploadStatus](https://msdn.microsoft.com/library/dn600289(v=msads.90).aspx) service operation is added, and `GetBulkUploadStatus` is deprecated. This operation provides the status and progress completion percentage for the bulk upload.

### <a name="campaign_january2014"></a>Campaign Management Version 9

#### <a name="activelimited"></a>ActiveLimited Editorial Status
The `ActiveLimited` value is added to the following value sets.

-   [AdEditorialStatus](https://msdn.microsoft.com/library/cc565084(v=msads.90).aspx)

-   [AdGroupCriterionEditorialStatus](https://msdn.microsoft.com/library/dn195643(v=msads.90).aspx)

-   [KeywordEditorialStatus](https://msdn.microsoft.com/library/cc565085(v=msads.90).aspx)

This value indicates that the entity passed editorial review in one or more markets, and one or more elements of the entity is undergoing editorial review in another market. For example, a keyword that passed editorial review for Canada and is still pending review in the United States.

## <a name="december2013"></a>December 2013
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bulk Version 9](#bulk_december2013)

### <a name="bulk_december2013"></a>Bulk Version 9

#### Format Version
The `FormatVersion` element is added to the request object of both [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/jj885755(v=msads.90).aspx) and [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/jj885756(v=msads.90).aspx) service operations.

#### Shared Ad Extensions
With file format version 1.0, an ad extension and associated entity  are specified in one record, for example `Campaign Call Ad Extension`. With file format version 2.0 you need only specify a shareable ad extension library item once, and then set an association to one or more entities. For file format version 2.0, the following ad extension record types are available for download and upload.

To download the shareable ad extensions, set `FormatVersion` to 2.0 and include the following [BulkDownloadEntity](https://msdn.microsoft.com/library/dn249982(v=msads.90).aspx) values in the download request.

-   `CallAdExtensions`

-   `LocationAdExtensions`

-   `ProductAdExtensions`

-   `SiteLinksAdExtensions`

#### Negative Reference Key
When referring to a new ad extension record set the extension's `Id` field to a negative number of your choice. This custom identifier is known as a negative reference key. Then you may use the negative reference key within the `Id` field of a dependent record. For more information, see [Reference Keys](https://msdn.microsoft.com/library/dn539651(v=msads.90).aspx#referencekeys).

## <a name="november2013"></a>November 2013
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Ad Intelligence Version 9](#adintelligence_november2013)

-   [Error Handling](#errors_november2013)

### <a name="adintelligence_november2013"></a>Ad Intelligence Version 9

#### Currencies
Support for the following currency values is added.

-   `Baht` (The Thai Baht)

-   `MalaysianRinggit` (The MalaysianRinggit)

-   `PhilippinePeso` (The Philippine Peso)

-   `Rupiah` (The Indonesian Rupiah)

> [!NOTE]
> The [Currency value set](https://msdn.microsoft.com/library/gg712234(v=msads.90).aspx) contains both supported and unsupported currencies. For information about supported currencies, see [Currencies](https://msdn.microsoft.com/library/dn271769(v=msads.100).aspx).

### <a name="errors_november2013"></a>Error Handling

#### Authentication Token Expired
The `AuthenticationTokenExpired` error code (109) is introduced for catching Microsoft Account authentication errors. The InvalidCredentials error code (105) will still be returned if the specified `AuthenticationToken` header element is not and has never been valid. Code 109 indicates that the specified value used to be valid and has since expired. You should request a new token before the current access token expires, or catch the `AuthenticationTokenExpired` error code (109) and then request a refresh token. For more information, see [Managing User Authentication with OAuth](../Topic/Managing%20User%20Authentication%20with%20OAuth.md).

## <a name="october2013"></a>October 2013
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Customer Billing Version 9](#billing_october2013)

-   [Customer Management Version 9](#customer_october2013)

-   [Reporting Version 9](#reporting_october2013)

### <a name="billing_october2013"></a>Customer Billing Version 9

#### Updated the Namespace
The new namespace name is https://bingads.microsoft.com/Billing/v9. For the production endpoint, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

> [!NOTE]
> The Customer Billing service is not supported in sandbox.

#### Production Availability
The Customer Billing service is now generally available in production at [https://clientcenter.api.bingads.microsoft.com/Api/Billing/v9/CustomerBillingService.svc](https://clientcenter.api.bingads.microsoft.com/Api/Billing/v9/CustomerBillingService.svc).

#### Billing Documents
Programming elements related to invoices are renamed as billing documents.

-   `GetInvoices` is replaced with [GetBillingDocuments](https://msdn.microsoft.com/library/dn451265(v=msads.90).aspx).

-   `GetInvoicesInfo` is replaced with [GetBillingDocumentsInfo](https://msdn.microsoft.com/library/dn451271(v=msads.90).aspx).

-   `Invoice` is replaced with [BillingDocument](https://msdn.microsoft.com/library/dn469177(v=msads.90).aspx).

-   `InvoiceInfo` is replaced with [BillingDocumentInfo](https://msdn.microsoft.com/library/dn469176(v=msads.90).aspx).

### <a name="customer_october2013"></a>Customer Management Version 9

#### Updated the Namespace
The new namespace name is https://bingads.microsoft.com/Customer/v9. For the production and sandbox endpoints, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

> [!IMPORTANT]
> The Customer Management sandbox endpoint is updated to [https://clientcenter.api.sandbox.bingads.microsoft.com/Api/CustomerManagement/v9/CustomerManagementService.svc](https://clientcenter.api.sandbox.bingads.microsoft.com/Api/CustomerManagement/v9/CustomerManagementService.svc).

#### Production Availability
The Customer service is now generally available in production at [https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v9/CustomerManagementService.svc](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v9/CustomerManagementService.svc).

#### Managing User Authentication
Permissions to access Bing Ads accounts should be managed with a linked Microsoft Account. For more information, see [Managing User Authentication with OAuth](../Topic/Managing%20User%20Authentication%20with%20OAuth.md).

The `IsMigratedToMicrosoftAccount` flag is added to the [User](https://msdn.microsoft.com/library/bb671824(v=msads.90).aspx) object. Use the flag to determine whether the user can be authenticated using  a Microsoft Account.

The `AddUser` operation and `UserRole` value set are removed.

The `User` element is removed from calls to the [SignupCustomer](https://msdn.microsoft.com/library/dn451287(v=msads.90).aspx) operation. The response will no longer include a `UserId` element.

#### Getting the Current User
The `UserId` element of the [GetUser](https://msdn.microsoft.com/library/dn451280(v=msads.90).aspx) operation is no longer required. To get details for the current authenticated user specified in the request header, set the `UserId` element to null or do not specify it in the request to `GetUser`.

#### Account and Application Type
Bing Ads services are used to manage advertising campaigns. The Publisher value is removed from the [AccountType](https://msdn.microsoft.com/library/ff728392(v=msads.90).aspx) and [ApplicationType](https://msdn.microsoft.com/library/ee704168(v=msads.90).aspx) value sets.

### <a name="reporting_october2013"></a>Reporting Version 9

#### Rich Ads
The rich ad component report is added.

The following programming elements for the rich ad component report are added.

-   [RichAdComponentPerformanceReportRequest](https://msdn.microsoft.com/library/hh180150(v=msads.90).aspx)

-   [RichAdComponentPerformanceReportFilter](https://msdn.microsoft.com/library/hh180147(v=msads.90).aspx)

-   [RichAdComponentPerformanceReportColumn](https://msdn.microsoft.com/library/hh180149(v=msads.90).aspx)

-   [RichAdSubTypeFilter](https://msdn.microsoft.com/library/hh180148(v=msads.90).aspx)

-   [ComponentTypeFilter](https://msdn.microsoft.com/library/hh180146(v=msads.90).aspx)

#### Product Target Report
The following optional columns are added to the [ProductTargetPerformanceReportColumn](https://msdn.microsoft.com/library/dn195844(v=msads.90).aspx).

-   AccountStatus

-   AdGroupStatus

-   CampaignStatus

-   DestinationUrl

#### Search Query Report
The following optional columns are added to the [SearchQueryPerformanceReportColumn](https://msdn.microsoft.com/library/ee703958(v=msads.90).aspx).

-   AdGroupCriterionId

-   ProductTarget

## <a name="september2013"></a>September 2013
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Ad Intelligence Version 9](#adintelligence_september2013)

-   [Bulk Version 9](#bulk_september2013)

-   [Campaign Management Version 9](#campaign_september2013)

-   [Customer Billing Version 9](#billing_september2013)

-   [Customer Management Version 9](#customer_september2013)

-   [Optimizer Version 9](#optimizer_september2013)

-   [Reporting Version 9](#reporting_september2013)

### <a name="adintelligence_september2013"></a>Ad Intelligence Version 9

#### Production Availability
The Ad Intelligence service is now generally available in production at [https://api.bingads.microsoft.com/Api/Advertiser/AdIntelligence/v9/AdIntelligenceService.svc](https://api.bingads.microsoft.com/Api/Advertiser/AdIntelligence/v9/AdIntelligenceService.svc).

#### Estimated Clicks and Impressions
The data type for estimated clicks and impressions elements in the following data objects are updated from int to double and long respectively.

-   [AdGroupEstimatedBid](https://msdn.microsoft.com/library/dn144841(v=msads.90).aspx)

-   [EstimatedBidAndTraffic](https://msdn.microsoft.com/library/gg986821(v=msads.90).aspx)

-   [EstimatedPositionAndTraffic](https://msdn.microsoft.com/library/gg986823(v=msads.90).aspx)

-   [KeywordKPI](https://msdn.microsoft.com/library/gg986837(v=msads.90).aspx)

#### Estimated Ad Position
The data type for the `EstimatedAdPosition` element of the [EstimatedPositionAndTraffic](https://msdn.microsoft.com/library/gg986823(v=msads.90).aspx) object is updated from [AdPosition](https://msdn.microsoft.com/library/gg712236(v=msads.90).aspx) to `double`.

#### Historical Search Count Date Range
For [GetHistoricalSeachCount](https://msdn.microsoft.com/library/dn336988(v=msads.90).aspx), the `StartTimePeriod` and `EndTimePeriod` elements are renamed `StartDate` and `EndDate` respectively.

#### Historical Search Count Data Type
The `SearchCount` element of the [HistoricSearchCountPeriodic](https://msdn.microsoft.com/library/hh921728(v=msads.90).aspx) data object is updated from `int` to `long`.

#### Increased Bid Coverage
The `GetIncreasedBidCoverage` element is removed from the [GetEstimatedBidByKeywordIds](https://msdn.microsoft.com/library/dn336995(v=msads.90).aspx) and [GetEstimatedBidByKeywords](https://msdn.microsoft.com/library/dn336987(v=msads.90).aspx) operations. The version 9 operations return data fields equivalent to setting the `GetIncreasedBidCoverage` element `True` in version 8. An estimated minimum bid will be returned for all requested keywords, and NULL values can be returned in the [EstimatedBidAndTraffic Data Object](https://msdn.microsoft.com/library/gg986821(v=msads.90).aspx).

#### Estimates By Keyword Identifiers
You may now specify 1,000 keyword identifiers with each call to the [GetEstimatedBidByKeywordIds](https://msdn.microsoft.com/library/dn336995(v=msads.90).aspx) and [GetEstimatedPositionByKeywordIds](https://msdn.microsoft.com/library/dn336989(v=msads.90).aspx) service operations. This is an increase from the previous limit of 100 identifiers.

### <a name="bulk_september2013"></a>Bulk Version 9

#### Production Availability
The Bulk service is now generally available in production at [https://api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v9/BulkService.svc](https://api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v9/BulkService.svc).

### <a name="campaign_september2013"></a>Campaign Management Version 9

#### Production Availability
The Campaign Management service is now generally available in production at [https://api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v9/CampaignManagementService.svc](https://api.bingads.microsoft.com/Api/Advertiser/CampaignManagement/v9/CampaignManagementService.svc).

#### Ad Extension Associations
The string All is removed from the [AssociationType value set](https://msdn.microsoft.com/library/dn249973(v=msads.90).aspx). To get all extensions using [GetAdExtensionIdsByAccountId](https://msdn.microsoft.com/library/dn277509(v=msads.90).aspx), including those not associated with any entity, set the `AssociationType` element to NULL.

## <a name="billing_september2013"></a>Customer Billing Version 9

### Sandbox Availability
The Customer Billing service is available in Sandbox at [https://clientcenter.api.sandbox.bingads.microsoft.com/Api/Billing/v9/CustomerBillingService.svc](https://clientcenter.api.sandbox.bingads.microsoft.com/Api/Billing/v9/CustomerBillingService.svc).

### Updated the Version Number
The namespace has been changed to reflect the new version number for this release. The new namespace name is https://bingads.microsoft.com/CustomerBilling/v9. For the sandbox endpoint, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

## <a name="customer_september2013"></a>Customer Management Version 9

### Sandbox Availability
The Customer Management service is available in Sandbox at [https://clientcenter.api.sandbox.bingads.microsoft.com/Api/CustomerManagement/v9/CustomerManagementService.svc](https://clientcenter.api.sandbox.bingads.microsoft.com/Api/CustomerManagement/v9/CustomerManagementService.svc).

### Updated the Version Number
The namespace has been changed to reflect the new version number for this release. The new namespace name is https://bingads.microsoft.com/CustomerManagement/v9. For the sandbox endpoint, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

### Customer Pilot Features
The `GetCustomerPilotFeature` operation is renamed [GetCustomerPilotFeatures](https://msdn.microsoft.com/library/dn451285(v=msads.90).aspx) (plural). The new name reflects the list of items returned by the service.

Rename the `GetCustomerPilotFeature` operation as `GetCustomerPilotFeatures`.

### User Life Cycle Status
The `New` value within the [UserLifeCycleStatus value set](https://msdn.microsoft.com/library/ee704179(v=msads.90).aspx) is replaced with `Pending`.

Replace usage of the `New` value of the `UserLifeCycleStatus` value set with `Pending`.

### Forward Compatibility
The `ForwardCompatibilityMap` element is added to the following objects and reserved for future use.

-   [Account](https://msdn.microsoft.com/library/bb671588(v=msads.90).aspx)

-   [Customer](https://msdn.microsoft.com/library/bb671875(v=msads.90).aspx)

### Account Payment Instruments
The following account payment elements are added to the [AdvertiserAccount data object](https://msdn.microsoft.com/library/ee704163(v=msads.90).aspx).

-   `BackUpPaymentInstrumentId`

-   `BillingThresholdAmount`

## <a name="optimizer_september2013"></a>Optimizer Version 9

### Production Availability
The Optimizer service is now generally available in production at [https://api.bingads.microsoft.com/Api/Advertiser/Optimizer/v9/OptimizerService.svc](https://api.bingads.microsoft.com/Api/Advertiser/Optimizer/v9/OptimizerService.svc).

### Budget Landscape
The [GetBudgetLandscape](https://msdn.microsoft.com/library/dn434657(v=msads.90).aspx) operation is added. The operation gets the campaign budget landscape and corresponding budget points for the specified campaign in an account. You may use the budget points to compare your current budget to the suggested budget and optimize your campaign budget.

### Estimated Clicks and Impressions
The data type for estimated clicks and impressions elements in the following data objects are updated from int to double and long respectively.

-   [BidOpportunity](https://msdn.microsoft.com/library/hh802384(v=msads.90).aspx)

-   [BudgetOpportunity](https://msdn.microsoft.com/library/hh418054(v=msads.90).aspx)

### <a name="reporting_september2013"></a>Reporting Version 9

#### Production Availability
The Reporting service is now generally available in production at [https://api.bingads.microsoft.com/Api/Advertiser/Reporting/v9/ReportingService.svc](https://api.bingads.microsoft.com/Api/Advertiser/Reporting/v9/ReportingService.svc).

## <a name="august2013"></a>August 2013
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bulk Version 9](#bulk_august2013)

-   [Campaign Management Version 9](#campaign_august2013)

-   [Reporting Version 9](#reporting_august2013)

### <a name="bulk_august2013"></a>Bulk Version 9

#### Download Status
For the [GetDownloadStatus](https://msdn.microsoft.com/library/jj885754(v=msads.90).aspx) response message, the `Status` element of type `DownloadStatus` is replaced by `RequestStatus` of type `string`.

#### Custom Dates
Elements of the [PerformanceStatsDateRange](https://msdn.microsoft.com/library/dn249975(v=msads.90).aspx) object, `CustomDateRangeEnd` and `CustomDateRangeStart`, are updated from type `DateTime` to type [Date](https://msdn.microsoft.com/library/jj134989(v=msads.90).aspx).

### <a name="campaign_august2013"></a>Campaign Management Version 9

#### Product Ads
The [GetBMCStoresByCustomerId](https://msdn.microsoft.com/library/dn411607(v=msads.90).aspx) operation is added and returns a list of Bing Merchant Center store information for the specified customer. The `StoreId` element of each [BMCStore](https://msdn.microsoft.com/library/dn411606(v=msads.90).aspx) can be used when adding a [ProductAdExtension](https://msdn.microsoft.com/library/jj721706(v=msads.90).aspx).

#### Partial Success for Ads and Keywords
When adding, updating, or deleting ads or keywords in batches of one or more, the operation may succeed for some and fail for part of the batch.

The `PartialErrors` element is added to the response message for the following service operations.

-   [GetAdsByIds](https://msdn.microsoft.com/library/dn236296(v=msads.90).aspx)

-   [GetKeywordsByIds](https://msdn.microsoft.com/library/dn277505(v=msads.90).aspx)

The `PartialErrors` element represents an array of `BatchError` objects that contain details for any entities that were not successfully added, updated, or deleted.

If the `BatchError` objects are derived `EditorialError` objects, then the reason why the add or keyword failed editorial review will be included.

### <a name="reporting_august2013"></a>Reporting Version 9

#### Error Codes
The `ReportingService` prefix for all `ErrorCode` elements is removed.

#### Ad Extension By Ad Report
`AdExtensionByAdsReportRequest` (Ads plural) is replaced by [AdExtensionByAdReportRequest](https://msdn.microsoft.com/library/jj713606(v=msads.90).aspx) (Ad singular).

`AdExtensionByAdsReportColumn` (Ads plural) is replaced by [AdExtensionByAdReportColumn](https://msdn.microsoft.com/library/jj713608(v=msads.90).aspx) (Ad singular).

The [AdExtensionByAdReportFilter](https://msdn.microsoft.com/library/dn393942(v=msads.90).aspx) is added, and includes the [DeviceOSReportFilter](https://msdn.microsoft.com/library/dn411633(v=msads.90).aspx) and [DeviceTypeReportFilter](https://msdn.microsoft.com/library/gg262850(v=msads.90).aspx).

#### Geographical Location Report
To match its feature scope and for parity with the Bing Ads web application, the metro area demographic report is renamed as the geographical location report.

The `MetroAreaDemographicReportRequest` object is replaced by [GeographicalLocationReportRequest](https://msdn.microsoft.com/library/dn393955(v=msads.90).aspx).

The `MetroAreaDemographicReportFilter` object is replaced by [GeographicalLocationReportFilter](https://msdn.microsoft.com/library/dn393954(v=msads.90).aspx).

The `MetroAreaDemographicReportColumn` value set is replaced by [GeographicalLocationReportColumn](https://msdn.microsoft.com/library/dn411634(v=msads.90).aspx).

#### Country Code Filter
The `CountryReportFilter` value set is removed.

Within the [GeographicalLocationReportFilter](https://msdn.microsoft.com/library/dn393954(v=msads.90).aspx), the `Country` element of type `CountryReportFilter` is replaced by the `CountryCode` element as a list of `string`.

#### Entity Identifiers
Entity identifiers are renamed within the ad group and campaign report scope objects.

Within the [AdGroupReportScope](https://msdn.microsoft.com/library/bb671622(v=msads.90).aspx) object  `ParentAccountId` is replaced by `AccountId`, and `ParentCampaignId` is replaced by `CampaignId`.

Within the [CampaignReportScope](https://msdn.microsoft.com/library/bb671721(v=msads.90).aspx) object  `ParentAccountId` is replaced by  `AccountId`.

#### Campaign Report Scope
You may specify individual campaigns for the [BudgetSummaryReportRequest](https://msdn.microsoft.com/library/bb672028(v=msads.90).aspx).

The data type of its `Scope` element is updated from [AccountReportScope](https://msdn.microsoft.com/library/bb671563(v=msads.90).aspx) to [AccountThroughCampaignReportScope](https://msdn.microsoft.com/library/bb671549(v=msads.90).aspx).

#### Delivered Match Type
Within the following report columns, the `MatchType` column value is renamed `DeliveredMatchType`.

-   [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bb672087(v=msads.90).aspx)

-   [SearchQueryPerformanceReportColumn](https://msdn.microsoft.com/library/ee703958(v=msads.90).aspx)

-   [ShareOfVoiceReportColumn](https://msdn.microsoft.com/library/jj592910(v=msads.90).aspx)

-   [SitePerformanceReportColumn](https://msdn.microsoft.com/library/dd797115(v=msads.90).aspx)

#### Rich Ads
The rich ad component report is removed.

The following programming elements for the rich ad component report are removed.

-   `RichAdComponentPerformanceReportRequest`

-   `RichAdComponentPerformanceReportFilter`

-   `RichAdComponentPerformanceReportColumn`

-   `RichAdSubTypeFilter`

-   `ComponentTypeFilter`

#### Device Filters
You may filter report results by device type and device operating system with the respective [DeviceTypeReportFilter](https://msdn.microsoft.com/library/gg262850(v=msads.90).aspx) and [DeviceOSReportFilter](https://msdn.microsoft.com/library/dn411633(v=msads.90).aspx).

The `DeviceOS` element of type `DeviceOSReportFilter` is added to the following report filters.

-   [AccountPerformanceReportFilter](https://msdn.microsoft.com/library/bb671671(v=msads.90).aspx)

-   [AdGroupPerformanceReportFilter](https://msdn.microsoft.com/library/bb671729(v=msads.90).aspx)

-   [CampaignPerformanceReportFilter](https://msdn.microsoft.com/library/bb671808(v=msads.90).aspx)

The `Filter` element is added to [AdExtensionByKeywordReportRequest](https://msdn.microsoft.com/library/jj713605(v=msads.90).aspx) and [AdExtensionDimensionReportRequest](https://msdn.microsoft.com/library/jj713607(v=msads.90).aspx).

The type of `Filter` for `AdExtensionByKeywordReportRequest` is  [AdExtensionByKeywordReportFilter](https://msdn.microsoft.com/library/dn393943(v=msads.90).aspx) and contains both `DeviceTypeReportFilter` and `DeviceOSReportFilter`.

The type of `Filter` for `AdExtensionDimensionReportRequest` is  [AdExtensionDimensionReportFilter](https://msdn.microsoft.com/library/dn393947(v=msads.90).aspx) and contains both `DeviceTypeReportFilter` and `DeviceOSReportFilter`.

#### Pricing Model Filter
You may filter publisher usage report results by pricing model with the new [PricingModelReportFilter](https://msdn.microsoft.com/library/dn411635(v=msads.90).aspx).

The `PricingModel` filter element of type `PricingModelReportFilter` is added to the [PublisherUsagePerformanceReportFilter](https://msdn.microsoft.com/library/dd797159(v=msads.90).aspx).

#### Network
You may optionally specify `Network` as one the following report columns, and the report will include a column that contains the network of the ad group that contains the ad.

-   [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bb671947(v=msads.90).aspx)

-   [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)

-   [AdPerformanceReportColumn](https://msdn.microsoft.com/library/bb671923(v=msads.90).aspx)

-   [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)

#### Top Versus Other
You may optionally specify `TopVsOther` as one the following report columns, and the report will include a column that indicates whether the ad impression appeared in a top position or elsewhere.

-   [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bb671947(v=msads.90).aspx)

-   [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)

-   [AdPerformanceReportColumn](https://msdn.microsoft.com/library/bb671923(v=msads.90).aspx)

-   [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)

#### Ad Status
You may optionally specify `AdStatus` as one the [AdPerformanceReportColumn](https://msdn.microsoft.com/library/bb671923(v=msads.90).aspx) values, and the report will include a column that indicates the current status of the corresponding ad.

## <a name="july2013"></a>July 2013
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Ad Intelligence Version 9](#adintelligence_july2013)

-   [Campaign Management Version 9](#campaign_july2013)

-   [Optimizer Version 9](#optimizer_july2013)

-   [Reporting Version 9](#reporting_july2013)

### <a name="adintelligence_july2013"></a>Ad Intelligence Version 9

#### Updated the Version Number
The namespace has been changed to reflect the new version number of this release; otherwise, there are no updates to the Administration API. The new namespace name is https://bingads.microsoft.com/AdIntelligence/v9. For the production and sandbox endpoints, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

#### Specifying Dates
The `MonthAndYear` object is removed, and all dates should be specified using the [DayMonthAndYear](https://msdn.microsoft.com/library/hh921738(v=msads.90).aspx) object.

With the [GetHistoricalSearchCount](https://msdn.microsoft.com/library/dn336988(v=msads.90).aspx) operation, `EndMonthAndYear` and `StartMonthAndYear` are replaced by `EndTimePeriod` and `StartTimePeriod` respectively.

The `TimePeriodRollup` element is added to the `GetHistoricalSearchCount` operation.

The `HistoricalSearchCount` object is removed, and instead you should use the [HistoricSearchCountPeriodic](https://msdn.microsoft.com/library/hh921728(v=msads.90).aspx) object. For the [KeywordSearchCount](https://msdn.microsoft.com/library/gg712245(v=msads.90).aspx) object, the data type of `HistoricalSearchCounts` should be an array of `HistoricSearchCountPeriodic` objects instead of an array of `HistoricSearchCount`.

#### Historical Data by Device
The `GetHistoricalKeywordPerformanceByDevice` and `GetHistoricalSearchCountByDevice` operations are removed, and instead you may use the corresponding [GetHistoricalKeywordPerformance](https://msdn.microsoft.com/library/dn336996(v=msads.90).aspx) and [GetHistoricalSearchCount](https://msdn.microsoft.com/library/dn336988(v=msads.90).aspx) operations.

The optional `Devices` element has been added to both `GetHistoricalKeywordPerformance` and `GetHistoricalSearchCount` operations. The `Device` element is added to the [KeywordHistoricalPerformance](https://msdn.microsoft.com/library/gg986820(v=msads.90).aspx) and [KeywordSearchCount](https://msdn.microsoft.com/library/gg712245(v=msads.90).aspx) objects returned by the corresponding operations.

The `KeywordHistoricalPerformanceByDevice` and `KeywordSearchCountByDevice` data objects are removed.

#### Historical Data by Match Type
You may specify multiple match types for keyword performance data requested with the [GetHistoricalKeywordPerformance](https://msdn.microsoft.com/library/dn336996(v=msads.90).aspx) operation.

The `MatchType` element of the `GetHistoricalKeywordPerformance` request is replaced by `MatchTypes`. You may specify `MatchTypes` with an array of [MatchType](https://msdn.microsoft.com/library/gg712238(v=msads.90).aspx).

#### Keyword Estimates by Match Type
The following elements of the [GetEstimatedBidByKeywords](https://msdn.microsoft.com/library/dn336987(v=msads.90).aspx) operation are updated.

-   The `MatchTypes` element is removed.

-   The data type of the `Keywords` element is updated to an array of [KeywordAndMatchType](https://msdn.microsoft.com/library/dn320461(v=msads.90).aspx) objects instead of a `string` array.

#### Keyword Suggestions
The `AdGroupId` and `CampaignId` elements are added to the request message of the [SuggestKeywordsFromExistingKeywords](https://msdn.microsoft.com/library/dn336990(v=msads.90).aspx) operation.

> [!NOTE]
> These elements are not yet supported and may be used to influence keyword suggestions in a future release.

#### Entity Identifiers
The `AdGroupId` and `CampaignId` elements of both [GetEstimatedBidByKeywords](https://msdn.microsoft.com/library/dn336987(v=msads.90).aspx) and [GetEstimatedPositionByKeywords](https://msdn.microsoft.com/library/dn337006(v=msads.90).aspx) operations have updated data types from `string` to `long`.

### <a name="campaign_july2013"></a>Campaign Management Version 9

#### Editorial Reason
The data type of the `Location` element of the [EditorialReason](https://msdn.microsoft.com/library/ff728493(v=msads.90).aspx) object is a string instead of an `AdComponent` value.

The `AdComponent` value set is removed.

## <a name="optimizer_july2013"></a>Optimizer Version 9

### Updated the Version Number
The namespace has been changed to reflect the new version number of this release; otherwise, there are no updates to the Administration API. The new namespace name is https://bingads.microsoft.com/Optimizer/v9. For the production and sandbox endpoints, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

### Apply Opportunities
The `ApplyBudgetOpportunities` operation is deprecated in Bing Ads API Version 8, and removed in Version 9. Instead you may use the [ApplyOpportunities](https://msdn.microsoft.com/library/dn376334(v=msads.90).aspx) operation to apply opportunities of all types.

### Budget Opportunity
The `BudgetDepletionDate` element of the [BudgetOpportunity](https://msdn.microsoft.com/library/hh418054(v=msads.90).aspx) object is removed.

### Error Codes
The `ErrorCodes` value set is removed. The data type of the `Code` element for [BatchError](https://msdn.microsoft.com/library/dn169131(v=msads.90).aspx) and [BatchError](https://msdn.microsoft.com/library/dn169126(v=msads.90).aspx) objects is updated from `ErrorCodes` to `int`.

## <a name="reporting_july2013"></a>Reporting Version 9

### Updated the Version Number
The namespace has been changed to reflect the new version number of this release; otherwise, there are no updates to the Administration API. The new namespace name is https://bingads.microsoft.com/Reporting/v9. For the production and sandbox endpoints, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

### Language Codes
The combined `LanguageAndRegion` element is deprecated in Bing Ads API Version 8, and removed in Version 9. Instead you may use the respective `LanguageCode` and `Country` elements.

The `LanguageAndRegionReportFilter` object is removed.

The `LanguageAndRegion` element is removed from the following report filter data objects, and instead you may filter by language using the respective `LanguageCode` element.

-   [AdDynamicTextPerformanceReportFilter](https://msdn.microsoft.com/library/bb672086(v=msads.90).aspx)

-   [AdGroupPerformanceReportFilter](https://msdn.microsoft.com/library/bb671729(v=msads.90).aspx)

-   [AdPerformanceReportFilter](https://msdn.microsoft.com/library/bb671609(v=msads.90).aspx)

-   [AgeGenderDemographicReportFilter](https://msdn.microsoft.com/library/bb671580(v=msads.90).aspx)

-   [DestinationUrlPerformanceReportFilter](https://msdn.microsoft.com/library/bb671544(v=msads.90).aspx)

-   [DestinationUrlPerformanceReportFilter](https://msdn.microsoft.com/library/bb672082(v=msads.90).aspx)

-   [PublisherUsagePerformanceReportFilter](https://msdn.microsoft.com/library/dd796865(v=msads.90).aspx)

-   [SearchQueryPerformanceReportFilter](https://msdn.microsoft.com/library/ee703961(v=msads.90).aspx)

-   [ShareOfVoiceReportFilter](https://msdn.microsoft.com/library/jj592908(v=msads.90).aspx)

-   [SitePerformanceReportFilter](https://msdn.microsoft.com/library/dd796955(v=msads.90).aspx)

The `LanguageAndRegion` value is removed from the following report columns.

-   [AdDynamicTextPerformanceReportColumn](https://msdn.microsoft.com/library/bb671878(v=msads.90).aspx)

-   [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)

-   [AdPerformanceReportColumn](https://msdn.microsoft.com/library/bb671923(v=msads.90).aspx)

-   [AgeGenderDemographicReportColumn](https://msdn.microsoft.com/library/bb671786(v=msads.90).aspx)

-   [DestinationUrlPerformanceReportColumn](https://msdn.microsoft.com/library/bb671820(v=msads.90).aspx)

-   [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bb672087(v=msads.90).aspx)

-   [PublisherUsagePerformanceReportColumn](https://msdn.microsoft.com/library/dd797159(v=msads.90).aspx)

-   [SearchQueryPerformanceReportColumn](https://msdn.microsoft.com/library/ee703958(v=msads.90).aspx)

-   [ShareOfVoiceReportColumn](https://msdn.microsoft.com/library/jj592910(v=msads.90).aspx)

-   [SitePerformanceReportColumn](https://msdn.microsoft.com/library/dd797115(v=msads.90).aspx)

### Impression Share
The `ImpressionLostToOthersPercent` and `ImpressionLostToRelevancePercent` elements are deprecated in Bing Ads API Version 8, and removed in Version 9.

The `ImpressionLostToOthersPercent` and `ImpressionLostToRelevancePercent` values are removed from the following report columns.

-   [AccountPerformanceReportColumn](https://msdn.microsoft.com/library/bb671947(v=msads.90).aspx)

-   [AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bb671495(v=msads.90).aspx)

-   [CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bb671804(v=msads.90).aspx)

### Migration Reports
Bing Ads has transitioned away from multiple match types per keyword. The programming elements for migration reporting are removed in version 9.

The `KeywordMigrationReportRequest` data object and the `KeywordMigrationReportColumn` value set are removed.

### Cashback
The Cashback feature is no longer supported.

The `CashbackReportFilter` is removed.

The `Cashback` element is removed from the [DestinationUrlPerformanceReportFilter](https://msdn.microsoft.com/library/bb672082(v=msads.90).aspx).

The `Cashback` value is removed from the [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bb672087(v=msads.90).aspx) report column.

### Behavioral and User Segment Targeting
The behavioral and user segment targeting features are no longer supported.

The following data objects related to behavioral and segment targeting are removed.

-   `BehavioralPerformanceReportFilter`

-   `BehavioralPerformanceReportRequest`

-   `BehavioralTargetReportFilter`

-   `BehavioralTargetReportRequest`

-   `SegmentationReportFilter`

-   `SegmentationReportRequest`

The following value sets related to behavioral and segment targeting are removed.

-   `BehavioralPerformanceReportColumn`

-   `BehavioralTargetReportColumn`

-   `SegmentationReportColumn`

-   `AgeGroupReportFilter`

-   `GenderReportFilter`

### Ad Group Report Scope
You may now specify individual ad groups for the [AdExtensionByAdsReportRequest](https://msdn.microsoft.com/library/jj713606(v=msads.90).aspx) and [AdExtensionByKeywordReportRequest](https://msdn.microsoft.com/library/jj713605(v=msads.90).aspx).

The data type of their `Scope` element is updated from [AccountThroughCampaignReportScope](https://msdn.microsoft.com/library/bb671549(v=msads.90).aspx) to [AccountThroughAdGroupReportScope](https://msdn.microsoft.com/library/bb671547(v=msads.90).aspx).

### Call Detail Report
Remove the `TimePeriod` value from the [CallDetailReportColumn](https://msdn.microsoft.com/library/dn195843(v=msads.90).aspx) value set.

### Top Results Sorted by Report Column
You may get performance data and attributes sorted ascending or descending with the [KeywordPerformanceReportRequest](https://msdn.microsoft.com/library/bb671816(v=msads.90).aspx).

Within the `KeywordPerformanceReportRequest` object, set the `MaxRows` element to specify the top number of rows to return per aggregation period. The `Sort` element is a list of [KeywordPerformanceReportSort](https://msdn.microsoft.com/library/dn342799(v=msads.90).aspx) objects, each of which specify the sort order and corresponding [KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bb672087(v=msads.90).aspx).

## <a name="v9"></a>June 2013
For information about the changes to the Bing Ads services included in this release, see the following sections.

-   [Bulk Version 9](#bulk_v9)

-   [Campaign Management Version 9](#campaign_v9)

### <a name="bulk_v9"></a>Bulk Version 9

#### Updated the Version Number
The namespace has been changed to reflect the new version number of this release; otherwise, there are no updates to the Administration API. The new namespace name is https://bingads.microsoft.com/CampaignManagement/v9. For the production and sandbox endpoints, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

#### Bulk Upload
Support is added for uploading entity data in bulk.

Upload data in bulk using the following operations.

-   [GetBulkUploadStatus](https://msdn.microsoft.com/library/dn249979(v=msads.90).aspx)

-   [GetBulkUploadUrl](https://msdn.microsoft.com/library/dn249978(v=msads.90).aspx)

With the [ResponseMode](https://msdn.microsoft.com/library/dn249983(v=msads.90).aspx) value set, you may specify whether the bulk service should return upload errors with their corresponding data.

#### Download Performance Data
You may specify whether to include performance data such as spend, with your entity data such as campaign settings.

For the following operation requests, the `DataScope` and `PerformanceStatsDateRange` elements are added.

-   [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/jj885755(v=msads.90).aspx)

-   [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/jj885756(v=msads.90).aspx)

Specify data scope with the [DataScope](https://msdn.microsoft.com/library/dn249976(v=msads.90).aspx) value set.

Specify the date range for performance data with the [PerformanceStatsDateRange](https://msdn.microsoft.com/library/dn249975(v=msads.90).aspx) data object. The start and end dates can be specified with the [ReportTimePeriod](https://msdn.microsoft.com/library/dn249977(v=msads.90).aspx) value set.

#### Error Handling
The `Type` element is added to the [BatchError](https://msdn.microsoft.com/library/bb671765.aspx(v=msads.90).aspx) object.

The [EditorialError](https://msdn.microsoft.com/library/cc197190(v=msads.90).aspx) object is derived from the `BatchError` object, and is added to the Bulk service in version 9.

#### Downloading Entities
Support is added for more granular selection of entities to download.

For the following operation requests, the `AdditionalEntities` element is renamed `Entities`.

-   [DownloadCampaignsByAccountIds](https://msdn.microsoft.com/library/jj885755(v=msads.90).aspx)

-   [DownloadCampaignsByCampaignIds](https://msdn.microsoft.com/library/jj885756(v=msads.90).aspx)

The `AdditionalEntity` value set is replaced by the [BulkDownloadEntity](https://msdn.microsoft.com/library/dn249982(v=msads.90).aspx) value set.

#### Download File Type
Support for downloading data as comma separated value (Csv) and tab separated value (Tsv) file types is added in the [DownloadFileType](https://msdn.microsoft.com/library/jj919219(v=msads.90).aspx) value set.

### <a name="campaign_v9"></a>Campaign Management Version 9

#### Updated the Version Number
The namespace has been changed to reflect the new version number for this release. The new namespace name is https://bingads.microsoft.com/CampaignManagement/v9. For the production and sandbox endpoints, see [Bing Ads Web Service Addresses](../guides/bing-ads-web-service-addresses.md).

#### Error Handling
The `Type` element is added to the [BatchError](https://msdn.microsoft.com/library/bb671765.aspx(v=msads.90).aspx) object.

The [EditorialError](https://msdn.microsoft.com/library/cc197190(v=msads.90).aspx) object is derived from the `BatchError` object, and the string value of the inherited `Type` element is `EditorialError`. Where the following elements were direct members of `EditorialError` in version 8, they are inherited from the `BatchError` object in version 9.

-   `Code`

-   `ErrorCode`

-   `Index`

-   `Message`

The `Location` and `ReasonCode` elements are added to the `EditorialError` object.

#### Ad Extensions
`AdExtension2` has been renamed [AdExtension](https://msdn.microsoft.com/library/hh527708(v=msads.90).aspx), and retains the `Id`, `Status`, `Type`, and `Version` elements. The `CampaignId`, `EnableLocationExtension`, and `PhoneExtension` elements of the version 8 `AdExtension` are not available in version 9.

#### Ad Extension Association
In version 8, ad extensions can be associated with campaigns. In version 9, ad extensions may be associated with campaigns and ad groups.

Manage extensions associations with the following operations.

-   [GetAdExtensionsAssociations](https://msdn.microsoft.com/library/dn236309(v=msads.90).aspx)

-   [DeleteAdExtensionsAssociations](https://msdn.microsoft.com/library/dn236305(v=msads.90).aspx)

-   [SetAdExtensionsAssociations](https://msdn.microsoft.com/library/dn277532(v=msads.90).aspx)

Manage extensions associations with the following data objects.

-   [AdExtensionAssociation](https://msdn.microsoft.com/library/dn250012(v=msads.90).aspx)

-   [AdExtensionAssociationCollection](https://msdn.microsoft.com/library/dn250010(v=msads.90).aspx)

-   [AdExtensionIdToEntityIdAssociation](https://msdn.microsoft.com/library/dn249980(v=msads.90).aspx)

The `AssociationFilter` value set is replaced by the [AssociationType](https://msdn.microsoft.com/library/dn249973(v=msads.90).aspx) value set, specifically when calling the [GetAdExtensionIdsByAccountId](https://msdn.microsoft.com/library/dn277509(v=msads.90).aspx) operation.

#### Ad Extension Editorial
You may get the reasons why an ad extension with associated entity failed editorial review.

The `GetAdExtensionsEditorialReasonsByCampaignIds` operation is replaced by the [GetAdExtensionsEditorialReasons](https://msdn.microsoft.com/library/dn236313(v=msads.90).aspx) operation.

The [AdExtensionEditorialStatus](https://msdn.microsoft.com/library/dn249989(v=msads.90).aspx) value set represents the editorial status of an ad extension with an entity, and is surfaced in the new [AdExtensionAssociation](https://msdn.microsoft.com/library/dn250012(v=msads.90).aspx) data object.

#### Device Preference
You will be able to specify whether you prefer to show text ads or ad extensions on mobile devices or all devices.

The `DevicePreference` element is added to the following data objects.

-   [Ad](https://msdn.microsoft.com/library/bb671952(v=msads.90).aspx)

-   [CallAdExtension](https://msdn.microsoft.com/library/jj721598(v=msads.90).aspx)

-   [SiteLink](https://msdn.microsoft.com/library/jj134381(v=msads.90).aspx)

#### Forward Compatibility
To avoid otherwise breaking changes when new elements are added in future releases of Bing Ads API Version 9 , the `ForwardCompatibilityMap` element is added to the following objects.

-   [Ad](https://msdn.microsoft.com/library/bb671952(v=msads.90).aspx)

-   [AdExtension](https://msdn.microsoft.com/library/hh527708(v=msads.90).aspx)

-   [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.90).aspx)

-   [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.90).aspx)

-   [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.90).aspx)

-   [Target](https://msdn.microsoft.com/library/bb671789(v=msads.90).aspx)

#### Partial Success for Ads and Keywords
When adding, updating, or deleting ads or keywords in batches of one or more, the operation may succeed for some and fail for part of the batch.

The `PartialErrors` element is added to the response message for the following service operations.

-   [AddAds](https://msdn.microsoft.com/library/dn277506(v=msads.90).aspx)

-   [AddKeywords](https://msdn.microsoft.com/library/dn277513(v=msads.90).aspx)

-   [DeleteAds](https://msdn.microsoft.com/library/dn236310(v=msads.90).aspx)

-   [DeleteKeywords](https://msdn.microsoft.com/library/dn236318(v=msads.90).aspx)

-   [UpdateAds](https://msdn.microsoft.com/library/dn277531(v=msads.90).aspx)

-   [UpdateKeywords](https://msdn.microsoft.com/library/dn236295(v=msads.90).aspx)

The `PartialErrors` element represents an array of `BatchError` objects that contain details for any entities that were not successfully added, updated, or deleted.

If the `BatchError` objects are derived `EditorialError` objects, then the reason why the add or keyword failed editorial review will be included.

#### Pausing and Resuming Entities
You may pause and resume the following entities by setting or updating the respective status element.

-   [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.90).aspx)

-   [Campaign](https://msdn.microsoft.com/library/dn764752(v=msads.90).aspx)

-   [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.90).aspx)

-   [MobileAd](https://msdn.microsoft.com/library/cc512741(v=msads.90).aspx)

-   [ProductAd](https://msdn.microsoft.com/library/jj738612(v=msads.90).aspx)

-   [SitePlacement](https://msdn.microsoft.com/library/dd797248(v=msads.90).aspx)

-   [TextAd](https://msdn.microsoft.com/library/bb672081(v=msads.90).aspx)

#### Ad Rotation
Ad rotation is set within the [Ad Group](https://msdn.microsoft.com/library/bb671956(v=msads.90).aspx) data object instead of using the `GetAdRotationByAdGroupIds` and `SetAdRotationToAdGroups` operations.

#### Publisher Countries
In version 8 the concept of publisher countries for an ad group was deprecated. With version 9 the `PublisherCountries` element is removed from the [AdGroup](https://msdn.microsoft.com/library/bb671956(v=msads.90).aspx) object. To target your ads by location use location targeting, and otherwise your ads will be displayed to all eligible markets for your customer.

#### Keyword Bid Match Type
Bing Ads has transitioned from multiple match types per keyword. Each keyword may have one bid and one match type. This is already enforced in version 8, and the version 9 object model is updated to reflect the new paradigm.

For a given [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.90).aspx) data object, all of the following elements replaced by both `Bid` and `MatchType`.

-   `BroadMatchBid`

-   `ContentMatchBid`

-   `ExactMatchBid`

-   `PhraseMatchBid`

The `MatchType` can be specified with the [MatchType](https://msdn.microsoft.com/library/dn249974(v=msads.90).aspx) value set.

#### Bid Adjustment
Bing Ads is transitioning from incremental bid adjustments to multiplicative bid adjustments. Support will also be added for a wider range and more granular bid adjustments, for example negative 17 percent.

The `IncrementalBid` element is replaced by the `BidAdjustment` element in each of the target bid objects.

#### Keyword Destination Url
The keyword level destination URL is now included in the [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.90).aspx) object instead of managing via the `GetDestinationUrlByKeywordIds` and `SetDestinationUrlToKeywords` operations.

#### Negative Keywords
Support for negative keywords within the Keyword data object was discontinued in version 8, and with version 9 the`NegativeKeywords` element was removed from the [Keyword](https://msdn.microsoft.com/library/bb671833(v=msads.90).aspx) object.

#### Device OS Targeting
The device OS target can be managed in parity with other target types. An object named [DeviceOSTarget](https://msdn.microsoft.com/library/dn249988(v=msads.90).aspx) exists in version 9, and its usage and elements have changed from version 8.

#### Targeting All Locations
The version 8 `TargetAllLocations` element is deprecated. In version 8 when `TargetAllLocations` is set to true, your ads participate in the auction for all locations. The service uses the base bid value for all locations that you did not target, and the incremental bid value for all locations that you did target. The default is false, whereby your ads participate in the auction only if the user is in all of the specified target locations. The service uses the incremental bid values of all specified targets in the auction.

In version 9 `TargetAllLocations` is removed and the behavior is identical to setting the version 8 `TargetAllLocations` element to false. To target all available countries and regions for your Bing Ads customer, do not create any location target. To target specific countries or regions, create individual targets for each city, country, metro area, radius, and state.

The `TargetAllLocations` element is removed from the [LocationTarget](https://msdn.microsoft.com/library/bb671646(v=msads.90).aspx) object.

#### Location Exclusions
You may specify locations to exclude from a target within the corresponding location target bid.

To exclude a target set the `IsExcluded` element to true within any of the following target bids. The default is false.

-   [CityTargetBid](https://msdn.microsoft.com/library/dd796932(v=msads.90).aspx)

-   [CountryTargetBid](https://msdn.microsoft.com/library/bb671882(v=msads.90).aspx)

-   [MetroAreaTargetBid](https://msdn.microsoft.com/library/bb672080(v=msads.90).aspx)

-   [RadiusTargetBid](https://msdn.microsoft.com/library/dd796863(v=msads.90).aspx)

    > [!NOTE]
    > For `RadiusTargetBid`, the `IsExcluded` element is currently not supported and reserved for future use.

-   [StateTargetBid](https://msdn.microsoft.com/library/dd796942(v=msads.90).aspx)

#### Business Locations
Business locations contain addresses used by business location targeting and the version 8 `AdExtension` object. These are deprecated in version 8, and the corresponding objects and service operations are removed in version 9.

#### Legacy Targeting
The following operations were deprecated in version 8, and removed in version 9.

-   `AddTarget`

-   `DeleteTarget`

-   `GetTargetByAdGroupId`

-   `UpdateTarget`

#### Migration Status Info
Bing Ads has transitioned away from multiple match types per keyword. The programming elements for migration status information are removed in version 9.

#### Campaign Analytics
Programming elements for managing campaign analytics are removed.

#### Image and Media
The `AddImage` and `GetImageById` operations are deprecated in version 8 and removed in version 9.

Instead you may use [AddMedia](https://msdn.microsoft.com/library/dn277518(v=msads.90).aspx) and [GetMediaByIds](https://msdn.microsoft.com/library/dn277511(v=msads.90).aspx) respectively.

#### String Normalization
The `GetNormalizedStrings` operation has been removed.

#### Ad Components
The CashbackTextParam value of the `AdComponent` value set has been removed.
