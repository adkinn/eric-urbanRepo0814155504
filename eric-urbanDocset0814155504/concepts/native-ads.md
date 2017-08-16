---
title: "Native Ads"
ms.custom: na
ms.date: "07/28/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 66ebd619-255d-464d-a4d8-c319d4e1864c
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Native Ads
Native ads are an extension of search network, and are targeted to user intent based on various combinations of search history, page content, and past user behavior. Native ads are created automatically by [!INCLUDE[brand](../concepts/includes/brand.md)] leveraging all of your [!INCLUDE[brand](../concepts/includes/brand.md)] creative elements including ad title, text, URL, and ad extensions including image extensions. Native ads are a part of standard [!INCLUDE[brand](../concepts/includes/brand.md)] campaigns on the search network and support all of the targeting available from [!INCLUDE[brand](../concepts/includes/brand.md)]. Native ads have CPC pricing. Native ads are currently available to a limited number of customers and will only be shown on select premium publisher websites.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot_comingsoon.md)]

You can set a bid adjustment for each campaign and ad group. The bid adjustment is the percent amount by which to adjust your bid for native ads above or below the base ad group or keyword bid. Supported values are negative one hundred (-100) through positive nine hundred (900). Setting the bid adjustment to -100 percent will prevent native ads from showing for the campaign or ad group. If you do not set a bid adjustment for your ad groups they will inherit from the campaign bid adjustment setting by default.

You can manage native ads settings with either the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) or [Campaign Management Service](https://msdn.microsoft.com/library/bb671719.aspx). You should use the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) if you need to upload or download a high volume of entity settings. For example you can update all ad groups for your entire account in a single upload. In comparison, with the [Campaign Management Service](https://msdn.microsoft.com/library/bb671719.aspx) you can only update 100 ad groups per call and those ad groups must be in the same campaign. For details see the following sections.

-   [Managing Native Ads Settings with the Bulk Service](#bulkservice)  
-   [Managing Native Ads Settings with the Campaign Management Service](#campaignservice)  
-   [Getting Performance Reports for Native Ads](#reporting)  

## <a name="bulkservice"></a>Managing Native Ads Settings with the Bulk Service
The [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) service create, update, and delete operations can be completed using Bulk upload. You can use Bulk download to read back your data. For more information see [Bulk File Schema](https://msdn.microsoft.com/library/dn539651.aspx) and [Bulk Download and Upload](../concepts/bulk-download-and-upload.md).

These are the [!INCLUDE[brand](../concepts/includes/brand.md)] entities with properties for managing Native ads that can be accessed using the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx). Use the *Bid Adjustment* column of the following records to get and set the Native ads bid adjustment.

-   [Campaign](https://msdn.microsoft.com/library/dn764752.aspx)  
-   [Ad Group](https://msdn.microsoft.com/library/dn764731.aspx)  
-   [Image Ad Extension](https://msdn.microsoft.com/library/dn764742.aspx)  
-   [Campaign Image Ad Extension](https://msdn.microsoft.com/library/dn764758.aspx)  
-   [Ad Group Image Ad Extension](https://msdn.microsoft.com/library/dn764738.aspx)  

For example you can follow these steps to set up an image ad extension for native ads.

**Note:** You can use the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx) for most steps, but you will still need to use the [Campaign Management Service](https://msdn.microsoft.com/library/bb671719.aspx) to add media to your account's media library.

1.  Add one to six [Image](https://msdn.microsoft.com/library/dn195581.aspx) items to your account's media library with the [AddMedia](https://msdn.microsoft.com/library/dn277518.aspx) operation. The images must be one of the supported [Media](https://msdn.microsoft.com/library/dn195580.aspx) types (aspect ratios) for an [Image Ad Extension](https://msdn.microsoft.com/library/dn764742.aspx).

    > [!NOTE]
    > While the minimum required for an image ad extension is one image, in order to qualify for all native ad placements you must provide four images, where each [Image](https://msdn.microsoft.com/library/dn195581.aspx) corresponds to one of the four supported [Media](https://msdn.microsoft.com/library/dn195580.aspx) types (aspect ratios). The supported aspect ratios for native ads are 16:9, 1.5:1, 4:3, and 1.2:1.

2.  Upload an [Image Ad Extension](https://msdn.microsoft.com/library/dn764742.aspx) record to your account's ad extension library. This will link the images from your media library to a specific image ad extension.

    > [!NOTE]
    > You will set the *Media Ids* field of the [Image Ad Extension](https://msdn.microsoft.com/library/dn764742.aspx) record with the media identifiers returned from [AddMedia](https://msdn.microsoft.com/library/dn277518.aspx) in the previous step.

3.  Associate your [Image Ad Extension](https://msdn.microsoft.com/library/dn764742.aspx) record to one or more [Campaign](https://msdn.microsoft.com/library/dn764752.aspx) or [Ad Group](https://msdn.microsoft.com/library/dn764731.aspx) records by uploading the corresponding [Campaign Image Ad Extension](https://msdn.microsoft.com/library/dn764758.aspx) or [Ad Group Image Ad Extension](https://msdn.microsoft.com/library/dn764738.aspx) records.

4.  Optionally use the *Bid Adjustment* column of the [Campaign](https://msdn.microsoft.com/library/dn764752.aspx) and [Ad Group](https://msdn.microsoft.com/library/dn764731.aspx) records to get and set the native ads bid adjustment.

## <a name="campaignservice"></a>Managing Native Ads Settings with the Campaign Management Service
These are the Native ads entities that can be accessed using the [Campaign Management Service](https://msdn.microsoft.com/library/bb671719.aspx). You can create, read, update, and delete these entities.

> [!NOTE]
> Partial success is supported for a subset of these operations. For example if you submit 10 ad groups and 2 fail, the remaining 8 will succeed. For more information, see [Partial Success using the Campaign Management Service](../concepts/handling-service-errors-and-exceptions.md#partialsuccess).

|Entities|Create|Read|Update|Delete|
|------------|----------|--------|----------|----------|
|[Campaign](https://msdn.microsoft.com/library/bb672054.aspx)|[AddCampaigns](https://msdn.microsoft.com/library/dn277510.aspx)|[GetCampaignsByAccountId](https://msdn.microsoft.com/library/dn236299.aspx)<br /><br />[GetCampaignsByIds](https://msdn.microsoft.com/library/dn236303.aspx)|[UpdateCampaigns](https://msdn.microsoft.com/library/dn277536.aspx)|[DeleteCampaigns](https://msdn.microsoft.com/library/dn236314.aspx)|
|[AdGroup](https://msdn.microsoft.com/library/bb671956.aspx)|[AddAdGroups](https://msdn.microsoft.com/library/dn277502.aspx)|[GetAdGroupsByCampaignId](https://msdn.microsoft.com/library/dn277524.aspx)<br /><br />[GetAdGroupsByIds](https://msdn.microsoft.com/library/dn277529.aspx)|[UpdateAdGroups](https://msdn.microsoft.com/library/dn277528.aspx)|[DeleteAdGroups](https://msdn.microsoft.com/library/dn236307.aspx)|
|[Image](https://msdn.microsoft.com/library/dn195581.aspx)<br /><br />[Media](https://msdn.microsoft.com/library/dn195580.aspx)|[AddMedia](https://msdn.microsoft.com/library/dn277518.aspx)|[GetMediaAssociations](https://msdn.microsoft.com/library/dn798359.aspx)<br /><br />[GetMediaMetaDataByAccountId](https://msdn.microsoft.com/library/dn766196.aspx)<br /><br />[GetMediaMetaDataByIds](https://msdn.microsoft.com/library/dn766200.aspx)<br /><br />[GetMediaByIds](https://msdn.microsoft.com/library/dn277511.aspx)|Media cannot be updated. You can delete media in your account's media library and add new media.|[DeleteMedia](https://msdn.microsoft.com/library/dn766193.aspx)|
|[ImageAdExtension](https://msdn.microsoft.com/library/dn766199.aspx)<br /><br />**Note:** The [AdExtension](https://msdn.microsoft.com/library/hh527708.aspx) object is the base class from which all ad extensions are derived.|[AddAdExtensions](https://msdn.microsoft.com/library/dn236319.aspx)<br /><br />[SetAdExtensionsAssociations](https://msdn.microsoft.com/library/dn277532.aspx)|[GetAdExtensionsByIds](https://msdn.microsoft.com/library/dn277515.aspx)<br /><br />[GetAdExtensionIdsByAccountId](https://msdn.microsoft.com/library/dn277509.aspx)<br /><br />[GetAdExtensionsAssociations](https://msdn.microsoft.com/library/dn236309.aspx)|[UpdateAdExtensions](https://msdn.microsoft.com/library/dn277522.aspx)<br /><br />**Note:** Partial update is not supported for ad extensions. Any optional elements which are not sent with the [UpdateAdExtensions](https://msdn.microsoft.com/library/dn277522.aspx) request will in effect be deleted from the extension.|[DeleteAdExtensions](https://msdn.microsoft.com/library/dn277537.aspx)<br /><br />[DeleteAdExtensionsAssociations](https://msdn.microsoft.com/library/dn236305.aspx)|
For example you can follow these steps to set up an image ad extension for native ads. You will need 1-6 images for your image ad extension. You will add the images to your account's media library with the [AddMedia](https://msdn.microsoft.com/library/dn277518.aspx) operation, link them to your [ImageAdExtension](https://msdn.microsoft.com/library/dn766199.aspx) with the [AddAdExtensions](https://msdn.microsoft.com/library/dn236319.aspx) operation (*ImageMediaIds* is a property of [ImageAdExtension](https://msdn.microsoft.com/library/dn766199.aspx)), and then associate the image ad extension with a campaign or ad group with [SetAdExtensionsAssociations](http://msdn.microsoft.com/library/111646e5-3d5a-455b-9b6d-e7cc24c4da3f).

1.  Add one to six [Image](https://msdn.microsoft.com/library/dn195581.aspx) items to your account's media library with the [AddMedia](https://msdn.microsoft.com/library/dn277518.aspx) operation. The images must be one of the supported [Media](https://msdn.microsoft.com/library/dn195580.aspx) types (aspect ratios) for an [ImageAdExtension](https://msdn.microsoft.com/library/dn766199.aspx).

    > [!NOTE]
    > While the minimum required for an image ad extension is one image, in order to qualify for all native ad placements you must provide four images, where each [Image](https://msdn.microsoft.com/library/dn195581.aspx) corresponds to one of the four supported [Media](https://msdn.microsoft.com/library/dn195580.aspx) types (aspect ratios). The supported aspect ratios for native ads are 16:9, 1.5:1, 4:3, and 1.2:1.

2.  Add an [ImageAdExtension](https://msdn.microsoft.com/library/dn766199.aspx) to your account's ad extension library with the [AddAdExtensions](https://msdn.microsoft.com/library/dn236319.aspx) operation. This will link the images from your media library to a specific image ad extension. If you already have an image ad extension you can call [UpdateAdExtensions](https://msdn.microsoft.com/library/dn277522.aspx) instead of [AddAdExtensions](https://msdn.microsoft.com/library/dn236319.aspx).

    > [!NOTE]
    > You will set the *ImageMediaIds* element of the [ImageAdExtension](https://msdn.microsoft.com/library/dn766199.aspx) with the media identifiers returned from [AddMedia](https://msdn.microsoft.com/library/dn277518.aspx) in the previous step.

3.  Associate your [ImageAdExtension](https://msdn.microsoft.com/library/dn766199.aspx) to one or more [Campaign](https://msdn.microsoft.com/library/bb672054.aspx) or [AdGroup](https://msdn.microsoft.com/library/bb671956.aspx) objects with the [SetAdExtensionsAssociations](https://msdn.microsoft.com/library/dn277532.aspx) operation.

4.  Optionally use the *NativeBidAdjustment* property of the [Campaign](https://msdn.microsoft.com/library/bb672054.aspx) and [AdGroup](https://msdn.microsoft.com/library/bb671956.aspx) to get and set the native ads bid adjustment.

## <a name="reporting"></a>Getting Performance Reports for Native Ads
For Native ads reporting and analysis you can use the Native ad distribution value in the following ways.

-   You can optionally set the [AdDistributionReportFilter](https://msdn.microsoft.com/library/bb671722.aspx) to Native if you only want native ads data.

-   You can include the *AdDistribution* column value that is available in most performance reports. The possible values are Search, Content, and Native, so you can quickly discover performance data specific to Native ads.

Performance data for native ads will be included in existing reports by default, with a few exceptions. The *SearchQueryPerformanceReport* ([Request](https://msdn.microsoft.com/library/ee703962.aspx) | [Filter](https://msdn.microsoft.com/library/ee703961.aspx) | [Column](https://msdn.microsoft.com/library/ee703958.aspx)) and *ShareOfVoiceReport* ([Request](https://msdn.microsoft.com/library/jj592909.aspx) | [Filter](https://msdn.microsoft.com/library/jj592908.aspx) | [Column](https://msdn.microsoft.com/library/jj592910.aspx)) reports will not have Native performance metrics even when ad distribution is an included column or included filter.

For more information about reporting, see [Reports](../concepts/reports.md) and [Request and Download a Report](../concepts/request-and-download-a-report.md).

You can also get performance data for Native ads using the [Bulk Service](https://msdn.microsoft.com/library/jj134984.aspx). You can get performance data for Native ads when downloading the [Campaign](https://msdn.microsoft.com/library/dn764752.aspx), [Ad Group](https://msdn.microsoft.com/library/dn764731.aspx), and [Keyword](https://msdn.microsoft.com/library/dn764751.aspx) records.

## See Also
[Bing Ads Web Service Addresses](../concepts/bing-ads-web-service-addresses.md)  

