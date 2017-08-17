---
title: "App Install Ads"
ms.custom: ""
ms.date: "08/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59f2c8b2-c90d-4311-9f18-f375e00ff057
caps.latest.revision: 2
---
# App Install Ads
Create an app install ad if your intention is to drive app downloads, and not necessarily to direct leads to a web site. If you want to direct leads to a web site in addition to driving app downloads, then you should create a text ad with app ad extensions.

> [!NOTE]
> Before you can use app install ads, you must upgrade to Final Urls. For more information, see [URL Tracking with Upgraded URLs](https://msdn.microsoft.com/library/bing-ads-tracking-template-urls-guide.aspx).
>
> Bing Ads only supports *EN-US* apps.

## <a name="bulk"></a>Bulk API for App Install Ads
The following Bulk record is added for managing app install ads.
* [App Install Ad](https://msdn.microsoft.com/library/bing-ads-bulk-app-install-ad-record.aspx)

## <a name="campaign"></a>Campaign Management API for App Install Ads
The [AppInstallAd](https://msdn.microsoft.com/library/bing-ads-campaign-management-appinstallad.aspx) object is derived from the [Ad](https://msdn.microsoft.com/library/bing-ads-campaign-management-ad.aspx) base class and can be managed with any of the existing ad operations e.g. [AddAds](https://msdn.microsoft.com/library/bing-ads-campaign-management-addads.aspx), [DeleteAds](https://msdn.microsoft.com/library/bing-ads-campaign-management-deleteads.aspx), and [UpdateAds](https://msdn.microsoft.com/library/bing-ads-campaign-management-updateads.aspx). 

You can include *AppInstallAd* as an [AdType](https://msdn.microsoft.com/library/bing-ads-campaign-management-adtype.aspx) in the *AdTypes* request element of the following operations to retrieve app install ads.
* [GetAdsByAdGroupId](https://msdn.microsoft.com/library/dn277534.aspx)
* [GetAdsByEditorialStatus](https://msdn.microsoft.com/library/dn277538.aspx)
* [GetAdsByIds](https://msdn.microsoft.com/library/dn236296.aspx)
