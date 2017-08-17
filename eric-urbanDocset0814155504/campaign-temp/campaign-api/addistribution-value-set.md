---
title: "AdDistribution Value Set"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e9fc2ab-d871-4fd1-a1fc-c2d97b6234b5
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdDistribution Value Set
Defines the ad distribution for the ad group.

## Syntax

```xml
\<xs:simpleType name="AdDistribution">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="Search" />
        \<xs:enumeration value="Content" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Content|The content network is the ad distribution network for Bing Ads running in Windows apps. When you select the content network as the distribution channel, any keyword you add will have the content match type in addition to any other match type you select. Ads for the content network are referred to as "content ads."<br /><br />For example, content ads display if a keyword for the ad is part of the app. If an ad for a clothing company has the keyword "dress" and the keyword "shoes", a content-network app related to fashion could display the ad even though a person viewing the app did not search for "dress" or "shoes." That's where the content match type keyword works for you. To learn more see, [Differences between search ads and content ads](https://help.bingads.microsoft.com/#apex/3/en/52030/0) and [How content ads work](https://help.bingads.microsoft.com/#apex/3/en/51063/0).<br /><br />**Note:** [!INCLUDE[market_contentads](../campaign-api/includes/market-contentads.md)]|
|Search|The search network includes Bing.com, AOL.com, Yahoo.com, other Bing, AOL, or Yahoo owned and operated sites, and syndicated search partner sites that offer search capabilities, as well as on a variety of other syndicated search partner sites. For more information, see the `Network` element of [AdGroup](../campaign-api/adgroup-data-object.md).<br /><br />With the search network, you can narrow ad distribution if needed: you can display your search ads on all sites in the search network; just Bing, AOL, and Yahoo owned and operated websites; or just the syndicated search partner sites. See [Differences between search ads and content ads](https://help.bingads.microsoft.com/#apex/3/en/52030/0) for more information.<br /><br />You might also be interested in Native Ads. A native ad is an ad whose subject matter and visual design are relevant to the page it is displayed on. More and more advertisers are turning to native ads for their proven ability to assist in brand building and to drive purchase intent. Both search ads and native ads are distributed on the search network. [Native ads](https://msdn.microsoft.com/library/bing-ads-native-ads.aspx) are currently available to only a limited number of customers and will be shown only on select websites such as MSN. If native ads are available for your campaign, you can manage your use of these ads and their bids using the native ads bid adjustment on both the campaign and ad group settings pages. For more information, see the [About Bing Native Ads](http://help.bingads.microsoft.com/#apex/3/en/56674/0) article in Bing Ads help.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)

