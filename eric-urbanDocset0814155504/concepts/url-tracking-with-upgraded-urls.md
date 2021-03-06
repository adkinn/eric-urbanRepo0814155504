---
title: "URL Tracking with Upgraded URLs"
ms.custom: ""
ms.date: "08/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3f823be-4cc2-457b-a8b8-a7fdc3d4b798
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# URL Tracking with Upgraded URLs
URL tracking allows you to find out how people got to your website by adding tracking parameters in Bing Ads and then using a third-party tracking tool or service to analyze the data. When an ad is served, the tracking parameters are dynamically appended to your landing page URL. This landing page URL is recorded on your web server and then a third-party tracking tool, like Adobe or Google Analytics, can interpret the data.

If you have set up [tracking in Bing Ads](https://help.bingads.microsoft.com/#apex/3/en/56798/2) by adding URL parameters to your destination URLs, you will be interested in Upgraded URLs. Upgraded URLs separate the landing page URL from the tracking or URL parameters so if you want to edit your URL parameters, your ad doesn't have to go through another editorial review. It also allows you to define a separate mobile landing page URL if you have a website that is optimized for smaller devices.

> [!IMPORTANT]
> If you are currently using Destination URLs, you must eventually replace them with Final URLs. This will be required no earlier than calendar year 2017.  

By separating the tracking template details from the final URLs you can take advantage of the following benefits:
-   You can define tracking templates for one or more account, campaign, ad group, keyword, ad, or Sitelink Extension. If you use a common tracking template for all ads in your campaign for example, you can update it once at the campaign level instead of making changes to all of your ads. Tracking templates and custom parameters defined for lower level entities e.g. keyword override those set for higher level entities e.g. campaign. For more information, see [Entity Hierarchy and Limits](../concepts/entity-hierarchy-and-limits.md).  
-   When you update your tracking template information, the URL doesn't need to go through editorial review and your ads will continue to serve uninterrupted. Editorial review is only required when you change your actual ads, keywords or extensions.  
-   Doing so helps [!INCLUDE[brand](../concepts/includes/brand.md)] understand what information is URL versus tracking template information, and reduces crawling on your website.  

For an overview of Final URLs and tracking templates, see the following Bing Ads help articles.
-   [How do I create an account tracking template?](http://help.bingads.microsoft.com/#apex/3/en/56772/-1)  
-   [Can I use custom parameters?](http://help.bingads.microsoft.com/#apex/3/en/56774/-1)  
-   [What are Upgraded URLs and how do I upgrade?](http://help.bingads.microsoft.com/#apex/3/en/56751/-1)  

You can manage Final URLs, Custom Parameters, and Tracking Templates with either the [Bulk Service](~/bulk-api/bulk-service-reference.md) or [Campaign Management Service](~/customer-api/campaign-management-service-reference.md). You should use the [Bulk Service](~/bulk-api/bulk-service-reference.md) service if you need to upload or download a high volume of entity settings. For example you can update all keyword bids for your entire account in a single upload. In comparison, with the [Campaign Management Service](~/customer-api/campaign-management-service-reference.md) service you can only update 1,000 keywords per call and those keywords must be in the same ad group. For more details about Final URLs and tracking templates using the Bing Ads API, see the sections below.
-   [Tracking Templates](#trackingtemplatevalidation)  
-   [Final URLs](#finalurlvalidation)  
-   [Custom Parameters](#customparametersvalidation)  
-   [URL Tracking with the Bulk Service](#bulkservice)  
-   [URL Tracking with the Campaign Management Service](#campaignservice)  
-   [URL Tracking with the Reporting Service](#reportingservice)  

## <a name="trackingtemplatevalidation"></a>Tracking Templates
Tracking templates can be used in tandem with final URLs to assemble the landing page URL where a user is directed after the ad is clicked. Here is an example:

**Final URL:** *http://contoso.com/contact-us*

**Tracking template:** *{lpurl}?ref=bing&keyword={Keyword}&cmpid={CampaignID}&agid={AdGroupID}&adid={AdID}*. The *{lpurl}* tag references the Landing Page URL. Bing will replace this with your Final URL when your ad is served.

[!INCLUDE[validationrules_trackingurltemplate](../concepts/includes/validationrules-trackingurltemplate.md)]

For an account, campaign, or ad group level tracking template, please note the following:

-   [!INCLUDE[validationrules_trackingurltemplate_account_through_adgroup](../concepts/includes/validationrules-trackingurltemplate-account-through-adgroup.md)]

We recommend adding a default tracking template at the account level so that all the campaigns, ad groups, ads, and Sitelink Extensions use the same URL format. If you add more tracking templates at the campaign, ad group, ad or Sitelink Extension level, they will override the account level settings. You can set the account level tracking template as the value of the *TrackingUrlTemplate* key within the *ForwardCompatibilityMap* element of the [Account Data Object](~/customer-api/account-data-object.md).

**Important:** Only super admin and standard users can update an account.

## <a name="finalurlvalidation"></a>Final URLs
[!INCLUDE[validationrules_finalurls](../concepts/includes/validationrules-finalurls.md)]

Also note the following validation rules for ad and site link final URLs.

-   You may not specify final mobile URLs if the device preference is set to mobile.

-   If the ad or site link's tracking template or custom parameters are specified, then at least one final URL is required.


## <a name="customparametersvalidation"></a>Custom Parameters
URL parameters are used to track information about the source of an ad click. By adding these parameters to your ads and campaigns, you can learn if people who clicked on your ads came from mobile devices, where they were located when they clicked your ads, and much more. For example if you use the {AdId} tag in your URL, then when the user clicks your ad the unique system identifier for that ad will be included in the URL where the user lands. For a list of supported parameters, see the *Available parameters* sections within the Bing Ads help article [How do I create an account tracking template?](https://help.bingads.microsoft.com/#apex/3/en/56772/-1).

Custom parameters work exactly the same as URL parameters with respect to dynamic substitutions, except that you will choose the parameter names and values (also known as key and value pairs). You can define custom parameters for one or more campaign, ad group, keyword, ad, or Sitelink Extension. If you use a common custom parameter for all ads in your campaign for example, you can update it once at the campaign level instead of making changes to all of your ads.

Custom parameters are helpful with sharing dynamic information across multiple URLs in a meaningful way for you to report on. Similarly how dynamic texts are provided by Bing Ads to give you more campaign insights on your performance. Custom parameters are advertiser created. 

[!INCLUDE[validationrules_customparameters](../concepts/includes/validationrules-customparameters.md)]

## <a name="bulkservice"></a>URL Tracking with the Bulk Service
The [Bulk Service](~/bulk-api/bulk-service-reference.md) create, update, and delete operations can be completed using Bulk upload. You can use Bulk download to read back your data. For more information see [Bulk File Schema](https://msdn.microsoft.com/library/dn539651.aspx) and [Bulk Download and Upload](../concepts/bulk-download-and-upload.md).

These are the [!INCLUDE[brand](../concepts/includes/brand.md)] entities with properties for managing URLs that can be accessed using the [Bulk Service](~/bulk-api/bulk-service-reference.md).

-   [Campaign](~/bulk-api/campaign.md)
-   [Ad Group](~/bulk-api/ad-group.md)
-   [Ad Group Dynamic Search Ad Target](~/bulk-api/ad-group-dynamic-search-ad-target.md) 
-   [Ad Group Product Partition](~/bulk-api/ad-group-product-partition.md) 
-   [App Install Ad](~/bulk-api/app-install-ad.md)
-   [Expanded Text Ad](~/bulk-api/expanded-text-ad.md)
-   [Text Ad](~/bulk-api/text-ad.md)
-   [Keyword](~/bulk-api/keyword.md)
-   [Sitelink Ad Extension](~/bulk-api/sitelink-ad-extension.md)
-   [Sitelink2 Ad Extension](~/bulk-api/sitelink2-ad-extension.md)

## <a name="campaignservice"></a>URL Tracking with the Campaign Management Service
These are the [!INCLUDE[brand](../concepts/includes/brand.md)] entities with properties for managing URLs that can be accessed using the [Campaign Management Service](~/campaign-api/campaign-management-service-reference.md). You can create, read, update, and delete these entities.
-  [AdGroup](~/campaign-api/adgroup-data-object.md)  
-  [AppInstallAd](~/campaign-api/appinstallad-data-object.md)  
-  [BiddableAdGroupCriterion](~/campaign-api/biddableadgroupcriterion-data-object.md)  
-  [DynamicSearchAd](~/campaign-api/dynamicsearchad-data-object.md)  
-  [ExpandedTextAd](~/campaign-api/expandedtextad-data-object.md)  
-  [Keyword](~/campaign-api/keyword-data-object.md)  
-  [SiteLink](~/campaign-api/sitelink-data-object.md)  
-  [Sitelink2AdExtension](~/campaign-api/sitelink2adextension-data-object.md)  
-  [TextAd](~/campaign-api/textad-data-object.md)  

## <a name="reportingservice"></a>URL Tracking with the Reporting Service
The following reports can be submitted and downloaded with the [Reporting Service](~/reporting-api/reporting-service-reference.md) to get performance data for Final URLs and Tracking Templates. 

The *TrackingTemplate* and *CustomParameters* columns for upgraded URLs are available in the following reports.

|Report Request|Report Filter|Report Column|
|-------------|-----------------|-----------------|
|[AdPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportrequest(v=msads.90).aspx)|[AdPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportfilter(v=msads.90).aspx)|[AdPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportcolumn(v=msads.90).aspx)|
|[AdGroupPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportrequest(v=msads.90).aspx)|[AdGroupPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportfilter(v=msads.90).aspx)|[AdGroupPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportcolumn(v=msads.90).aspx)|
|[CampaignPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportrequest(v=msads.90).aspx)|[CampaignPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportfilter(v=msads.90).aspx)|[CampaignPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportcolumn(v=msads.90).aspx)|
|[DestinationUrlPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportrequest(v=msads.90).aspx)|[DestinationUrlPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportfilter(v=msads.90).aspx)|[DestinationUrlPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportcolumn(v=msads.90).aspx)|
|[KeywordPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportrequest(v=msads.90).aspx)|[KeywordPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportfilter(v=msads.90).aspx)|[KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportcolumn(v=msads.90).aspx)|
|[SitePerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-siteperformancereportrequest(v=msads.90).aspx)|[SitePerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-siteperformancereportfilter(v=msads.90).aspx)|[SitePerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-siteperformancereportcolumn(v=msads.90).aspx)|
|[ProductPartitionPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportrequest(v=msads.90).aspx)|[ProductPartitionPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportfilter(v=msads.90).aspx)|[ProductPartitionPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportcolumn(v=msads.90).aspx)|
|[ProductPartitionUnitPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionunitperformancereportrequest(v=msads.90).aspx)|[ProductPartitionUnitPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionunitperformancereportfilter(v=msads.90).aspx)|[ProductPartitionUnitPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionunitperformancereportcolumn(v=msads.90).aspx)|

The *FinalURL* and *FinalMobileURL* columns for upgraded URLs are available in the following reports.

|Report Request|Report Filter|Report Column|
|-------------|-----------------|-----------------|
|[AdDynamicTextPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-addynamictextperformancereportrequest(v=msads.90).aspx)|[AdDynamicTextPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-addynamictextperformancereportfilter(v=msads.90).aspx)|[AdDynamicTextPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-addynamictextperformancereportcolumn(v=msads.90).aspx)|
|[AdPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportrequest(v=msads.90).aspx)|[AdPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportfilter(v=msads.90).aspx)|[AdPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportcolumn(v=msads.90).aspx)|
|[DestinationUrlPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportrequest(v=msads.90).aspx)|[DestinationUrlPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportfilter(v=msads.90).aspx)|[DestinationUrlPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportcolumn(v=msads.90).aspx)|
|[KeywordPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportrequest(v=msads.90).aspx)|[KeywordPerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportfilter(v=msads.90).aspx)|[KeywordPerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportcolumn(v=msads.90).aspx)|
|[SitePerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-siteperformancereportrequest(v=msads.90).aspx)|[SitePerformanceReportFilter](https://msdn.microsoft.com/library/bing-ads-reporting-siteperformancereportfilter(v=msads.90).aspx)|[SitePerformanceReportColumn](https://msdn.microsoft.com/library/bing-ads-reporting-siteperformancereportcolumn(v=msads.90).aspx)|


## See Also
[Bing Ads Web Service Addresses](../concepts/bing-ads-web-service-addresses.md)

