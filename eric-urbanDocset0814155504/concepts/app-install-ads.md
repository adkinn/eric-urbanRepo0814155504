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
> Before you can use app install ads, you must upgrade to Final Urls. For more information, see [URL Tracking with Upgraded URLs](~/concepts/url-tracking-with-upgraded-urls.md).
>
> Bing Ads only supports *EN-US* apps.

## <a name="bulk"></a>Bulk API for App Install Ads
The following Bulk record is added for managing app install ads.
* [App Install Ad](~/bulk-api/app-install-ad.md)

## <a name="campaign"></a>Campaign Management API for App Install Ads
The [AppInstallAd](~/campaign-api/appinstallad-data-object.md) object is derived from the [Ad](~/campaign-api/ad-data-object.md) base class and can be managed with any of the existing ad operations e.g. [AddAds](~/campaign-api/addads-service-operation.md), [DeleteAds](~/campaign-api/deleteads-service-operation.md), and [UpdateAds](~/campaign-api/updateads-service-operation.md). 

You can include *AppInstallAd* as an [AdType](~/campaign-api/adtype-value-set.md) in the *AdTypes* request element of the following operations to retrieve app install ads.
* [GetAdsByAdGroupId](~/campaign-api/getadsbyadgroupid-service-operation.md)
* [GetAdsByEditorialStatus](~/campaign-api/getadsbyeditorialstatus-service-operation.md)
* [GetAdsByIds](~/campaign-api/getadsbyids-service-operation.md)
