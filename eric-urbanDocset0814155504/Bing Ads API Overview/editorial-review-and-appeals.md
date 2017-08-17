---
title: "Editorial Review and Appeals"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 431d287f-2c42-45e4-b62a-d338d54a22b2
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Editorial Review and Appeals
For an ad to be eligible to be served, it must meet the editorial guidelines of the market that it serves. The same is true for ad extensions and keywords. For editorial guidelines by market, see [Editorial Guidelines](http://advertise.bingads.microsoft.com/editorial-guidelines).

For information about the editorial review process and how to determine whether the entity passed or failed the review, see the following sections.

-   [Entities and Delivery Status](#entitydeliverystatus)

-   [Ad Editorial Review](#adeditorialreview)

-   [Ad Extension Editorial Review](#adextensioneditorialreview)

-   [Keyword Editorial Review](#keywordeditorialreview)

To find ads or keywords that failed the editorial review process, call the respective [GetAdsByEditorialStatus](http://msdn.microsoft.com/library/0faf6178-4fc8-40b4-9ba5-9e5cdd21ce96) or [GetKeywordsByEditorialStatus](http://msdn.microsoft.com/library/d94ae758-2fc3-47b4-a041-377c0d9498b9) operation. Set the `EditorialStatus` element to Disapproved.

To determine the reason why an ad or keyword failed the review and whether it’s appealable, call the respective [GetEditorialReasonsByIds](http://msdn.microsoft.com/library/c6c8b301-c2d3-4f50-82a6-47fa74f59e22) operation. The operation returns an array of [EditorialReasonCollection](http://msdn.microsoft.com/library/ab58a13a-3e7c-4f55-81b0-d60d7854b261) objects. The rejection is appealable if the `AppealStatus` element of `EditorialReasonCollection` is set to Appealable. For possible status values, see [AppealStatus](http://msdn.microsoft.com/library/c30bf88f-f5bc-4388-8f7e-b1672093ec32).

For a list of the possible reason codes for an ad or keyword that failed editorial review, see [Bing Ads Editorial Failure Reason Codes](../Bing Ads API Overview/bing-ads-editorial-failure-reason-codes.md). The codes can be returned in the `ReasonCode` element of the [EditorialReason](http://msdn.microsoft.com/library/8855cb88-dd05-4e4f-9059-e15718849c43) object.

If the failure is appealable, call the [AppealEditorialRejections](http://msdn.microsoft.com/library/ba87645c-f131-4a6a-addc-53e459f633a2) operation to appeal the rejection. You can request a maximum of 2,000 appeals per account per 24-hour rolling window. For example, if you request 2,000 appeals at 10:00 AM PST today, you cannot request new appeals until after 10:00 AM PST tomorrow. The maximum number of appeals that you can have pending for a single account is 10,000.

You cannot call `AppealEditorialRejections` to appeal ad extensions that failed editorial review.

## <a name="entitydeliverystatus"></a>Entities and Delivery Status
The respective [KeywordEditorialStatus](http://msdn.microsoft.com/library/f1b1c9e5-3989-4207-bf56-0f5fd7e17068) and [AdEditorialStatus](http://msdn.microsoft.com/library/e79f0dfa-2c74-4219-86a8-c2e1a1b810a0) values for keywords and ads may differ from the corresponding delivery status shown in the [!INCLUDE[brand](../Bing Ads API Overview/includes/brand.md)] web application.

For example after adding a new keyword or ad which must go through the offline review process, read operations such as `GetKeywordsByIds` or `GetAdsByIds` will return `Disapproved`, and the delivery status in the web application will indicate that the entity is pending editorial review. The delivery status in the web application will indicate that the entity is disapproved if and when all elements of the keyword or ad are rejected.

If you have updated a previously approved and active keyword or ad, and if any element of that entity must go through the offline review process, then read operations such as `GetKeywordsByIds` or `GetAdsByIds` will return `Inactive` and the delivery status in the web application will indicate that the entity is pending editorial review.

> [!NOTE]
> For an entity undergoing offline review the editorial status may be either `Active` or `Inactive`, determined respectively by whether a reviewable term is considered to have a low or high risk of rejection.

## <a name="adeditorialreview"></a>Ad Editorial Review
Before an ad can be served, it must pass editorial review. An initial review is performed at the time you add the ad to an ad group. If the ad fails the initial review, the [AddAds](http://msdn.microsoft.com/library/223bd85b-47d3-4156-8ce5-58f3ca34307f) operation throws an editorial fault, which identifies the editorial issue. If the initial review succeeds, the ad is added to the ad group.

The ad then goes through an in-depth review in the background. To find ads that failed the more in-depth review, call the [GetAdsByEditorialStatus](http://msdn.microsoft.com/library/0faf6178-4fc8-40b4-9ba5-9e5cdd21ce96) operation. To determine the reason why an ad failed the review and whether it’s appealable, call the [GetEditorialReasonsByIds](http://msdn.microsoft.com/library/c6c8b301-c2d3-4f50-82a6-47fa74f59e22) operation.

If the status of an ad group is `Draft`, the ads will begin the in-depth review when you update its status to `Paused` or `Active`.

If an ad is updated, it is subject to the same review process as a new ad. Effectively the ad is paused unless or until the updated ad copy is immediately approved.

## <a name="adextensioneditorialreview"></a>Ad Extension Editorial Review
When you associate an ad extension with a campaign or ad group, the extension goes through an initial editorial review. The review is performed for each publisher country that supports the languages specified in the campaign’s ad groups. If the extension fails the initial review, the operation fails and returns an editorial fault. The fault’s `Details` element contains the term that failed review. If the extension passes the initial review, the extension then goes through an in-depth, offline editorial review. Our full list of Ad Extension policies can be found [here](http://go.microsoft.com/fwlink?LinkId=746651). 

> [!NOTE]
> If the `IconMediaId` or `ImageMediaId` elements of a [LocationAdExtension](http://msdn.microsoft.com/library/90fb2536-bff4-4e96-a7b3-ae7cc13753b7) are set with custom media, the location ad extension validations are done offline. Otherwise all ad extension editorial validations occur up front when associated with an entity.

Because the editorial review is conducted in the context of the campaign or ad group, the extension is reviewed each time you associate the extension with a campaign or ad group. In addition, the extension associated with a campaign will go through a review anytime you add to the campaign an ad group which specifies a different language, or you target a different country at the campaign or ad group level.

To determine whether the extension passed the in-depth review with associated entities, call the [GetAdExtensionsAssociations](http://msdn.microsoft.com/library/9c972e9c-688a-4c72-8d19-41aeffaec383) operation. The response contains one or more lists of [AdExtensionAssociation](http://msdn.microsoft.com/library/60233ced-a506-459f-aba2-a76d294697f2) objects. The extension passed editorial review if the `EditorialStatus` element is set to Active. If the status is set to ActiveLimited or Disapproved, call the [GetAdExtensionsEditorialReasons](http://msdn.microsoft.com/library/e02a796d-a36d-49fc-b3b0-161be089c4dc) operation to identify the countries where the extension failed review and the reason for the failure.

## <a name="keywordeditorialreview"></a>Keyword Editorial Review
When you add keywords, they go through an initial editorial review. If a keyword fails the initial review, the [AddKeywords](http://msdn.microsoft.com/library/957a7fce-ed33-4bf4-a3c2-a1411e1573a0) operation fails and throws an editorial fault that identifies the editorial issues. If the initial review succeeds, the keywords are added to the ad group. They then go through an in-depth review in the background.

To find keywords that failed the more in-depth review, call the [GetKeywordsByEditorialStatus](http://msdn.microsoft.com/library/d94ae758-2fc3-47b4-a041-377c0d9498b9) operation. To determine the reason why a keyword failed the review and whether it’s appealable, call the [GetEditorialReasonsByIds](http://msdn.microsoft.com/library/c6c8b301-c2d3-4f50-82a6-47fa74f59e22) operation.

If the status of an ad group is `Draft`, the keywords will begin the in-depth review when you update its status to `Paused` or `Active`.

## See Also
[Campaign Management Service Reference](http://msdn.microsoft.com/library/5f50ed8a-6bca-4d30-8340-7290bc074f0e)
[Bing Ads Web Service Addresses](../Bing Ads API Overview/bing-ads-web-service-addresses.md)

