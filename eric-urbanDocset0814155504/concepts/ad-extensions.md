---
title: "Ad Extensions"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca01453b-7e0c-4d2d-afea-378501023cd6
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Extensions
Ad extensions are additional pieces of information about your business, like a phone number or a link to a specific page on your website, you can add to your ads. Ad extensions are free to add to your ads, with the usual charges for any clicks you get. Including ad extensions can improve the visibility of your ads, which can lead to more clicks and improve your ROI. There are many types of ad extensions available in Bing Ads: [App Extensions](#appextensions), [Call Extensions](#callextensions), [Callout Extensions](#calloutextensions), [Image Extensions](#imageextensions), [Location Extensions](#locationextensions), [Price Extensions](#priceextensions), [Review Extensions](#reviewextensions), [Sitelink Extensions](#sitelinkextensions), and [Structured Snippet Extensions](#structuredsnippetextensions). For more about ad extensions, see [Bing Ads Web Application Help - What are ad extensions?](http://help.bingads.microsoft.com/#apex/3/en/51001/1)

> [!TIP]
> Providing extension data allows our algorithms to evaluate all the possible layouts for your ad. It increases the changes of additional space being allocated and increasing clicks for your ad.

Ad extensions are stored in a shared library at the account level. After adding the extension to your shared library, you must also explicitly associate it with the account or one or more campaigns or ad groups within the account for the extension to become eligible for delivery. For more details on associating ad extensions, see [Managing Ad Extensions with the Bulk Service](#bulkservice) and [Managing Ad Extensions with the Campaign Management Service](#campaignservice) in the sections below. For ad extension association limits per entity, please see [Entity Limits for Ad Extensions](../concepts/entity-hierarchy-and-limits.md#adextensions).

> [!NOTE]
> Call ad extensions can only be associated at the campaign level. 
> 
> Location ad extensions can only be associated at the account and campaign level i.e., cannot be associated with ad groups.

Ad extensions that are associated at a lower level e.g., ad group will override ad extensions of the same type that are associated at a higher level e.g., campaign. For example if you have 2 callout extensions set for *Campaign A*, zero callout extensions associated with *Ad Group AA*, and one callout extension associated with *Ad Group AB*, then only *Ad Group AA* is eligible to have its ads decorated with callouts. 

You can manage ad extensions with either the [Bulk Service](~/bulk-api/bulk-service-reference.md) or [Campaign Management Service](~/campaign-api/campaign-management-service-reference.md). You should use the [Bulk Service](~/bulk-api/bulk-service-reference.md) if you need to upload or download a high volume of entity settings. For example you can update all ad extensions for your entire account in a single upload. In comparison, with the [Campaign Management Service](~/campaign-api/campaign-management-service-reference.md) you can only update 100 ad extensions per call. For details see the following sections.

-   [Ad Extension Types](#adextensiontypes)  
-   [Managing Ad Extensions with the Bulk Service](#bulkservice)  
-   [Managing Ad Extensions with the Campaign Management Service](#campaignservice)  
-   [Editorial Review](#editorial)  
-   [Reporting](#reporting)  

## <a name="adextensiontypes"></a>Ad Extension Types

-   [App Extensions](#appextensions)  
-   [Call Extensions](#callextensions)  
-   [Callout Extensions](#calloutextensions)  
-   [Image Extensions](#imageextensions)  
-   [Location Extensions](#locationextensions)  
-   [Price Extensions](#priceextensions)  
-   [Review Extensions](#reviewextensions)  
-   [Sitelink Extensions](#sitelinkextensions)  
-   [Structured Snippet Extensions](#structuredsnippetextensions)  

### <a name="appextensions"></a>App Extensions
You can associate app ad extensions with your campaigns and ad groups, and your ads will include a link to install an application.

![overview_appadextension](../concepts/media/overview-appadextension.png "overview_appadextension")

### <a name="callextensions"></a>Call Extensions
With Call Extensions, you can provide a phone number that is not associated with a particular location, but is appropriate for all locations where your ads display. In comparison, you typically use Location Extensions to provide an address and local phone number associated with a local location.

If the campaign is also associated with a [Location Extensions](#locationextensions), the call extension phone number will override the location extension phone number.

![overview_calladextension](../concepts/media/overview-calladextension.png "overview_calladextension")

### <a name="calloutextensions"></a>Callout Extensions
With Callout Extensions, you can provide an extra snippet of text that highlights your business, products, or services to include in An ad. This extension is not clickable and can appear in addition to your ad?s description. Providing additional details about your store can make your ad more relevant to potential customers.

Each account, campaign, or ad group can be associated with between 2 and 20 callout ad extensions. If you associate one or fewer callout extensions with your account, campaign, or ad group, no callout text will serve with your ad. An ad may include between 2 to 4 callouts per impression.

![Callout ad extension](../concepts/media/callout-ad-extension.png)

### <a name="imageextensions"></a>Image Extensions
You can associate image ad extensions with your campaigns and ad groups, and your ads may include an image or alternative text.

![Image Ad Extension](../concepts/media/image-ad-extension.png)

### <a name="locationextensions"></a>Location Extensions
When you enable Location Extensions, you can choose to show the address of your business location that is closest to the customer and also include a local phone number. Better yet, if the customer is viewing your ad on a smartphone, they can click that number to give you a call.

If the campaign is also associated with a [Call Extensions](#callextensions), the phone number in the call extension will override the location extension phone number.

![overview_locationadextension](../concepts/media/overview-locationadextension.png "overview_locationadextension")

### <a name="priceextensions"></a>Price Extensions
You can use Price Extensions to display your products or services with their corresponding prices to potential customers on mobile devices. Price Extensions only show on ads listed at the top of the results page, helping to increase your clicks. Keep in mind that though Price Extensions are free to add to your ad, they may not always show for every query.

![Price Ad Extension](../concepts/media/price-ad-extension.png)

### <a name="reviewextensions"></a>Review Extensions
Potential customers like to know about other customers? experiences when searching for products or services. Share positive reviews from a reputable third-party source about your business, products, or services in your ads with a Review Extension. An ad will only include one review per impression.

![Review ad extension](../concepts/media/review-ad-extension.png)

### <a name="sitelinkextensions"></a>Sitelink Extensions
Sitelink Extensions are additional links in your ads that take customers to specific pages on your website. This allows you to promote certain products, services, or sections of your website and take potential customers to exactly the information they were searching for. This can increase both click-through-rate and conversions.

You may associate site links ad extensions with your campaigns or ad groups, and your ads will include up to 10 links to relevant web pages within your website. When displaying an ad, [!INCLUDE[brand](../concepts/includes/brand.md)] determines which links are most relevant to the ad being displayed and includes those with your ad. You can influence which links are included. Links that you specify at the beginning of your list receive higher priority than those toward then end of your list.

![overview_sitelinkadextension](../concepts/media/overview-sitelinkadextension.png "overview_sitelinkadextension")

### <a name="structuredsnippetextensions"></a>Structured Snippet Extensions
Structured Snippet Extensions give potential customers more context on a specific aspect of your products and services. A Structured snippet is made up of a header and a list of 3-10 values which correspond to the header. For example, you might use the header ?Brands:? and the values ?Windows, Xbox, Skype? to let customers know about what brands are available at your store.

![Structured Snippet Ad Extension](../concepts/media/structured-snippet-ad-extension.png)

This extension is not clickable and, similar to other extensions, will appear beneath your ad?s description. Structured Snippets have no impact on the other extensions you?re already using. Structured Snippets should not duplicate what is already stated in the ad. Our full list of Structured Snippet policies can be found [here](https://advertise.bingads.microsoft.com/resources/policies/ad-extensions-policies).

An ad will only include one structured snippet (one headline with 3 - 10 values) per impression. Keep in mind that your ads won?t always show Structured Snippets and if they do show Structured Snippets, the format they appear may vary. Structured Snippets are free to add to your ad, available in all Bing Ads markets (excluding Hong Kong and Taiwan), and serve on desktop and tablet devices. 


## <a name="bulkservice"></a>Managing Ad Extensions with the Bulk Service
You can use the [Bulk Service](~/bulk-api/bulk-service-reference.md) i.e., [Bulk Download and Upload](../concepts/bulk-download-and-upload.md) to create, get, update, and delete both ad extensions and ad extension associations. 

The following Bulk records are available for managing ad extensions and ad extension associations. 

### App Extensions
-   [App Ad Extension](~/bulk-api/app-ad-extension.md)
-   [Ad Group App Ad Extension](~/bulk-api/ad-group-app-ad-extension.md)
-   [Campaign App Ad Extension](~/bulk-api/campaign-app-ad-extension.md)

### Call Ad Extensions
-   [Call Ad Extension](~/bulk-api/call-ad-extension.md)
-   [Campaign Call Ad Extension](~/bulk-api/campaign-call-ad-extension.md)

### Callout Ad Extensions
-   [Callout Ad Extension](~/bulk-api/callout-ad-extension.md)
-   [Ad Group Callout Ad Extension](~/bulk-api/ad-group-callout-ad-extension.md)
-   [Campaign Callout Ad Extension](~/bulk-api/campaign-callout-ad-extension.md)

### Image Ad Extensions
-   [Image Ad Extension](~/bulk-api/image-ad-extension.md)
-   [Ad Group Image Ad Extension](~/bulk-api/ad-group-image-ad-extension.md)
-   [Campaign Image Ad Extension](~/bulk-api/campaign-image-ad-extension.md)

### Location Ad Extensions
-   [Location Ad Extension](~/bulk-api/location-ad-extension.md)
-   [Campaign Location Ad Extension](~/bulk-api/campaign-location-ad-extension.md)

### Price Ad Extensions
-   [Price Ad Extension](~/bulk-api/price-ad-extension.md)
-   [Ad Group Price Ad Extension](~/bulk-api/ad-group-price-ad-extension.md)
-   [Campaign Price Ad Extension](~/bulk-api/campaign-price-ad-extension.md)

### Review Ad Extensions
-   [Review Ad Extension](~/bulk-api/review-ad-extension.md)
-   [Ad Group Review Ad Extension](~/bulk-api/ad-group-review-ad-extension.md)
-   [Campaign Review Ad Extension](~/bulk-api/campaign-review-ad-extension.md)

### SiteLinks Ad Extensions
-   [Sitelink Ad Extension](~/bulk-api/sitelink-ad-extension.md)
-   [AdGroup Sitelink Ad Extension](~/bulk-api/adgroup-sitelink-ad-extension.md)
-   [Campaign Sitelink Ad Extension](~/bulk-api/campaign-sitelink-ad-extension.md)

### Sitelink2 Ad Extensions
-   [Sitelink2 Ad Extension](~/bulk-api/sitelink2-ad-extension.md)
-   [Ad Group Sitelink2 Ad Extension](~/bulk-api/ad-group-sitelink2-ad-extension.md)
-   [Campaign Sitelink2 Ad Extension](~/bulk-api/campaign-sitelink2-ad-extension.md)

### Structured Snippet Ad Extensions
-   [Structured Snippet Ad Extension](~/bulk-api/structured-snippet-ad-extension.md)
-   [Ad Group Structured Snippet Ad Extension](~/bulk-api/ad-group-structured-snippet-ad-extension.md)
-   [Campaign Structured Snippet Ad Extension](~/bulk-api/campaign-structured-snippet-ad-extension.md)

For code examples that show how to set up ad extensions using the Bulk service, see [C&#35;](../concepts/bulk-ad-extensions-in-csharp.md)| [Java](../concepts/bulk-ad-extensions-in-java.md) | [Python](../concepts/bulk-ad-extensions-in-python.md).

## <a name="campaignservice"></a>Managing Ad Extensions with the Campaign Management Service
You can use the [Campaign Management Service](~/campaign-api/campaign-management-service-reference.md) to create, get, update, and delete both ad extensions and ad extension associations. 

For code examples that show how to set up ad extensions using the Campaign Management service, see [C&#35;](../concepts/ad-extensions-in-csharp.md) | [Java](../concepts/ad-extensions-in-java.md) | [PHP](../concepts/ad-extensions-in-php.md) | [Python](../concepts/ad-extensions-in-python.md).

### Entities
These are the ad extension entities that can be accessed using the [Campaign Management Service](~/campaign-api/campaign-management-service-reference.md). You can create, read, update, and delete these entities.

-   [AppAdExtension](~/campaign-api/appadextension-data-object.md)
-   [CallAdExtension](~/campaign-api/calladextension-data-object.md)
-   [CalloutAdExtension](~/campaign-api/calloutadextension-data-object.md)
-   [ImageAdExtension](~/campaign-api/imageadextension-data-object.md)
-   [LocationAdExtension](~/campaign-api/locationadextension-data-object.md)
-   [PriceAdExtension](~/campaign-api/priceadextension-data-object.md)
-   [ReviewAdExtension](~/campaign-api/reviewadextension-data-object.md)
-   [SiteLinksAdExtension](~/campaign-api/sitelinksadextension-data-object.md)
-   [Sitelink2AdExtension](~/campaign-api/sitelink2adextension-data-object.md)
-   [StructuredSnippetAdExtension](~/campaign-api/structuredsnippetadextension-data-object.md)

> [!NOTE]
> The [AdExtension](~/campaign-api/adextension-data-object.md) object is the base class from which all ad extensions are derived.

### Service Operations
These are the [Campaign Management Service](~/campaign-api/campaign-management-service-reference.md) service operations that can be used to add, get, update, and delete ad extensions.

-   [AddAdExtensions](~/campaign-api/addadextensions-service-operation.md)  
-   [SetAdExtensionsAssociations](~/campaign-api/setadextensionsassociations-service-operation.md)  
-   [GetAdExtensionsByIds](~/campaign-api/getadextensionsbyids-service-operation.md)  
-   [GetAdExtensionIdsByAccountId](~/campaign-api/getadextensionidsbyaccountid-service-operation.md)  
-   [GetAdExtensionsAssociations](~/campaign-api/getadextensionsassociations-service-operation.md)  
-   [UpdateAdExtensions](~/campaign-api/updateadextensions-service-operation.md)
-   [DeleteAdExtensions](~/campaign-api/deleteadextensions-service-operation.md)  
-   [DeleteAdExtensionsAssociations](~/campaign-api/deleteadextensionsassociations-service-operation.md)

> [!NOTE]
> Partial update is not supported for ad extensions. Any optional elements which are not sent with the [UpdateAdExtensions](~/campaign-api/updateadextensions-service-operation.md) request will in effect be deleted from the extension.
> 
> Partial success is not supported when adding, updating, and deleting ad extensions. For example if you submit 10 ad extensions and 2 fail, the entire batch will fail.
> 
> Partial success is supported for [GetAdExtensionsAssociations](~/campaign-api/getadextensionsassociations-service-operation.md) and [SetAdExtensionsAssociations](~/campaign-api/setadextensionsassociations-service-operation.md). For example if you submit 10 ad extension associations and 2 fail, the remaining 8 will succeed. For more information, see [Partial Success using the Campaign Management Service](../concepts/handling-service-errors-and-exceptions.md#partialsuccess).

## <a name="editorial"></a>Editorial Review
When you associate an ad extension with a campaign or ad group, the extension goes through an initial editorial review. For more information, see [Ad Extension Editorial Review](../concepts/editorial-review-and-appeals.md#adextensioneditorialreview).

## <a name="reporting"></a>Reporting
You can use the following reports to get statistics about the effectiveness of the ad extensions that you've included in your ads.

-   [AdExtensionByAdReportRequest](~/reporting-api/adextensionbyadreportrequest-data-object.md) ? Aggregates performance data by ad for a specified time period. By including performance details, such as clicks, conversion, and spend, you can identify ad extensions that are performing well, and those that may need to be adjusted to optimize the monthly budget.

-   [AdExtensionByKeywordReportRequest](~/reporting-api/adextensionbykeywordreportrequest-data-object.md) ? Aggregates performance data by keyword for a specified time period. By including performance details, such as clicks, conversion, and spend, you can identify ad extensions that are performing well, and those that may need to be adjusted to optimize the monthly budget.

-   [AdExtensionDimensionReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adextensiondimensionreportrequest.aspx) ? Lists all versions of an ad extension by account. You can use this information along with the performance data from the other two reports to determine which version performed better.

For more information about reporting, see [Reports](../concepts/reports.md) and [Request and Download a Report](../concepts/request-and-download-a-report.md).

## See Also
[Bing Ads Web Service Addresses](../concepts/bing-ads-web-service-addresses.md)

