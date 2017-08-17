---
title: "Labels"
ms.custom: na
ms.date: "08/09/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: ad40088c-deb4-41bc-a4b2-3ce0172b4a61
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# Labels
Labels let you organize campaigns, ad groups, ads, and keywords into groups based on whatever is important to you. You can then filter and run reports on your labels to get the data that is most meaningful to you.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../../concepts/includes/pilot_comingsoon.md)]
> 
> Reporting for labels is not yet available via Bing Ads API. You can use Reporting in the Bing Ads web applicationn. 

With labels, you could:
* Run a report to compare “Holiday 2015” and “Holiday 2016” performance, across campaigns, ad groups, ads, and keywords.
* Run a report to compare ads and keywords that include brand names against ads and keywords that use generic terms.
* Quickly filter and view performance for keywords labeled “Suggested by Bing Ads.”
* Create an automated rule to change bids on keywords labeled “CPA bidding.”

The important thing is that it’s all up to you. You decide what your labels mean and how to apply them to your campaigns, ad groups, ads, and keywords.

![Labels in the Bing Ads Web Application](../../concepts/guides/media/labels-in-the-bing-ads-web-application.png)

## <a name="bulkservice"></a>Managing Labels with the Bulk Service
You can use the [Bulk Service](https://msdn.microsoft.com/library/bing-ads-bulk-service-reference.aspx) i.e., [Bulk Download and Upload](../../concepts/guides/bulk-download-and-upload.md) to create, get, update, and delete both labels and label associations. 

The following Bulk records are available for managing labels and label associations. 

-   [Label](https://msdn.microsoft.com/library/bing-ads-bulk-label-record.aspx)  
-   [Campaign Label](https://msdn.microsoft.com/library/bing-ads-bulk-campaign-label-record.aspx)  
-   [Ad Group Label](https://msdn.microsoft.com/library/bing-ads-bulk-ad-group-label-record.aspx)  
-   [Keyword Label](https://msdn.microsoft.com/library/bing-ads-bulk-keyword-label-record.aspx)  
-   [App Install Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-app-install-ad-label-record.aspx)  
-   [Dynamic Search Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-dynamic-search-ad-label-record.aspx)  
-   [Expanded Text Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-exapanded-text-ad-label-record.aspx)  
-   [Product Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-product-ad-label-record.aspx)  
-   [Text Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-text-ad-label-record.aspx)  

For example, the following Bulk CSV example would apply a label to the campaign, ad group, keyword, and expanded text ad if the valid *Id* and *Parent Id* are provided. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Name,Description,Label,Color
Format Version,,,,,,,,5,,,
Label,Active,-22,,,,ClientIdGoesHere,,,Label Description,Label Name 7/27/2017 6:50:54 PM,#FFFFFF
Campaign Label,Active,-22,-111,,,ClientIdGoesHere,,,,,
Ad Group Label,Active,-22,-1111,,,ClientIdGoesHere,,,,,
Expanded Text Ad Label,Active,-22,-11112,,,ClientIdGoesHere,,,,,
Keyword Label,Active,-22,-11113,,,ClientIdGoesHere,,,,,
```

## <a name="campaignservice"></a>Managing Labels with the Campaign Management Service
You can use the [Campaign Management Service](https://msdn.microsoft.com/library/bing-ads-campaign-management-service-reference.aspx) to create, get, update, and delete both labels and label associations. 

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



