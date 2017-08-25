---
title: "Campaign Management Data Objects"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35ce83af-dce8-4161-8b5c-763672467bce
caps.latest.revision: 34
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Campaign Management Data Objects
The Campaign Management service defines the following data objects.

|Data Object|Description|
|---------------|---------------|
|[AccountMigrationStatusesInfo](../campaign-api/accountmigrationstatusesinfo-data-object.md)[AccountMigrationStatusesInfo](../campaign-api/accountmigrationstatusesinfo-data-object.md)|Defines an object that contains migration status for an account.|
|[AccountProperty](../campaign-api/accountproperty-data-object.md)|Maps an account level property name to a string value.|
|[Ad](../campaign-api/ad-data-object.md)|Defines the base class of an ad.|
|[Address](../campaign-api/address-data-object.md)|Defines a postal address.|
|[AdExtension](../campaign-api/adextension-data-object.md)|Defines an object that determines whether text ads in the specified campaign will contain decorative elements, for example the customer's location or phone number.|
|[AdExtensionAssociation](../campaign-api/adextensionassociation-data-object.md)|Defines the relationship and editorial status of an ad extension with an account, campaign, or ad group.|
|[AdExtensionAssociationCollection](../campaign-api/adextensionassociationcollection-data-object.md)|Defines an array of objects that associate an ad extension and its editorial status to an account, campaign, or ad group.|
|[AdExtensionEditorialReason](../campaign-api/adextensioneditorialreason-data-object.md)|Defines an object that you can use to determine the component of an ad extension that failed editorial review, and the reason for the failure.|
|[AdExtensionEditorialReasonCollection](../campaign-api/adextensioneditorialreasoncollection-data-object.md)|Defines a collection of ad extensions that failed editorial review.|
|[AdExtensionIdentity](../campaign-api/adextensionidentity-data-object.md)|Defines an object that identifies an ad extension.|
|[AdExtensionIdToEntityIdAssociation](../campaign-api/adextensionidtoentityidassociation-data-object.md)|Defines an object that associates an ad extension to an account, campaign, or ad group.|
|[AdGroup](../campaign-api/adgroup-data-object.md)|Defines an ad group.|
|[AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md)|Defines a criterion that you want applied to the specified ad group.|
|[AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md)|Defines the action to apply to a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md), specifically one that contains a [ProductPartition](../campaign-api/productpartition-data-object.md). You can send a group of [AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md) objects, also known as a product group, to the [ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md) service operation.|
|[AdGroupNegativeSites](../campaign-api/adgroupnegativesites-data-object.md)|Defines an object that contains the negative site URLs of an ad group.|
|[AdRotation](../campaign-api/adrotation-data-object.md)|Defines an object that specifies an ad rotation type.|
|[AgeCriterion](../campaign-api/agecriterion-data-object.md)|Defines a criterion that can be used to show ads to users in a specific age range.|
|[AppAdExtension](../campaign-api/appadextension-data-object.md)|Defines an app ad extension that can be included in a text ad.|
|[AppInstallAd](../campaign-api/appinstallad-data-object.md)|Defines an app install ad.|
|[AppInstallGoal](../campaign-api/appinstallgoal-data-object.md)|Defines an app install conversion goal. Use this type of goal to track every time someone installs your app as a conversion.|
|[AppUrl](../campaign-api/appurl-data-object.md)|Defines the operating system platform and URL of the app store download webpage.<br /><br />Reserved for future use.|
|[Audience](../campaign-api/audience-data-object.md)|Defines the base class of an audience.|
|[AudienceCriterion](../campaign-api/audiencecriterion-data-object.md)|Defines a criterion that can be used to show ads to a specific audience.|
|[Bid](../campaign-api/bid-data-object.md)|Defines a bid.|
|[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)|Defines a criterion that helps determine whether ads in the campaign can be served. If the condition is met, the specified bid is used in the auction.|
|[BiddableCampaignCriterion](../campaign-api/biddablecampaigncriterion-data-object.md)|Defines a criterion that helps determine whether ads in the ad group can be served. If the condition is met, the specified bid is used in the auction.|
|[BiddingScheme](../campaign-api/biddingscheme-data-object.md)|Defines the base object of a bidding scheme for how you want to manage your bids. A bidding scheme is known as a *bid strategy type* in the Bing Ads web application.|
|[BidMultiplier](../campaign-api/bidmultiplier-data-object.md)|Defines the multiplier by which to adjust your base bid for the corresponding criterion.|
|[BMCStore](../campaign-api/bmcstore-data-object.md)|Defines a [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store.|
|[Budget](../campaign-api/budget-data-object.md)|Represents a budget that can be shared by any campaigns in an account.|
|[CallAdExtension](../campaign-api/calladextension-data-object.md)|Defines a call ad extension that can be included in a text ad.|
|[CalloutAdExtension](../campaign-api/calloutadextension-data-object.md)|Defines a callout ad extension that can be included in a text ad.|
|[Campaign](../campaign-api/campaign-data-object.md)|Defines a campaign.|
|[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md)|Defines a criterion that you want applied to the specified campaign.|
|[CampaignNegativeSites](../campaign-api/campaignnegativesites-data-object.md)|Defines an object that contains the negative site URLs of a campaign.|
|[ConversionGoal](../campaign-api/conversiongoal-data-object.md)|efines the base object of a conversion goal.|
|[ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md)|Defines properties for revenue that can be tracked by a conversion goal.|
|[Criterion](../campaign-api/criterion-data-object.md)|Defines the base object of a criterion.|
|[CriterionBid](../campaign-api/criterionbid-data-object.md)|Defines a base class for criterion bids.|
|[CustomAudience](../campaign-api/customaudience-data-object.md)|Defines a custom audience.|
|[CustomEventsRule](../campaign-api/customeventsrule-data-object.md)|Defines a custom events remarketing rule.|
|[CustomParameter](../campaign-api/customparameter-data-object.md)|Defines a key and value custom parameter for URL tracking. Used for campaign, ad group, ad, keyword, sitelink, and ad group criterion URL custom parameters.|
|[CustomParameters](../campaign-api/customparameters-data-object.md)|Defines a collection of key and value custom parameters for URL tracking. Used for campaign, ad group, ad, keyword, sitelink, and ad group criterion URL custom parameters.|
|[DayTime](../campaign-api/daytime-data-object.md)|Defines a day of the week and time range for ad extension scheduling.|
|[DayTimeCriterion](../campaign-api/daytimecriterion-data-object.md)|Defines a criterion that can be used to show ads during a specific day and time range.|
|[DeviceCriterion](../campaign-api/devicecriterion-data-object.md)|Defines a criterion that can be used to show ads on specific devices.|
|[DurationGoal](../campaign-api/durationgoal-data-object.md)|Defines a duration conversion goal. Use this type of goal to count every time someone stays on a website for longer than a certain amount of time as a conversion.|
|[DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md)|Defines an dynamic search ad that is generated automatically based on the website domain and language that you want to target.|
|[DynamicSearchAdsSetting](../campaign-api/dynamicsearchadssetting-data-object.md)|Defines the campaign level settings for a Dynamic Search Ads campaign.|
|[EditorialReason](../campaign-api/editorialreason-data-object.md)|Defines an object that you can use to determine the component of an ad or keyword that failed editorial review, and the reason for the failure.|
|[EditorialReasonCollection](../campaign-api/editorialreasoncollection-data-object.md)|Defines a collection of ads or keywords that failed editorial review, and the reason for the failure.|
|[EnhancedCpcBiddingScheme](../campaign-api/enhancedcpcbiddingscheme-data-object.md)|Defines an object that represents the enhanced CPC bid strategy type.|
|[EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md)|Defines an object that contains the unique system identifier of an entity such as ad or keyword, and the identifier of its parent. An ad group is the parent of an ad or keyword.|
|[EntityNegativeKeyword](../campaign-api/entitynegativekeyword-data-object.md)|Defines an object that contains a set of negative keywords and the associated entity such as a campaign.|
|[EventGoal](../campaign-api/eventgoal-data-object.md)|Defines a custom event conversion goal. Use this type of goal to count every time someone completes a specific action such as, subscribing to newsletter or downloading white paper, as a conversion.|
|[ExpandedTextAd](../campaign-api/expandedtextad-data-object.md)|Defines an expanded text ad.|
|[FixedBid](../campaign-api/fixedbid-data-object.md)|Defines the fixed bid to use in the auction.|
|[GenderCriterion](../campaign-api/gendercriterion-data-object.md)|Defines a criterion that can be used to show ads to users of a specific gender.|
|[GeoPoint](../campaign-api/geopoint-data-object.md)|Defines an object that contains the longitude and latitude coordinates of a geographical location.|
|[IdCollection](../campaign-api/idcollection-data-object.md)|Defines an object that contains a list of entity identifiers.|
|[Image](../campaign-api/image-data-object.md)|Defines an image object that can be added to an account?s media library.|
|[ImageAdExtension](../campaign-api/imageadextension-data-object.md)|Defines an ad extension that specifies an image with alternative text to include in a text ad.|
|[ImageMediaRepresentation](../campaign-api/imagemediarepresentation-data-object.md)|Defines an image media representation with height and width.|
|[InheritFromParentBiddingScheme](../campaign-api/inheritfromparentbiddingscheme-data-object.md)|Defines an object that represents the inherit from parent bid strategy type.|
|[InMarketAudience](../campaign-api/inmarketaudience-data-object.md)|Defines an in-market audience.|
|[InStoreTransactionGoal](../campaign-api/instoretransactiongoal-data-object.md)|Defines an in-store transaction goal.|
|[Keyword](../campaign-api/keyword-data-object.md)|Defines a keyword.|
|[Label](../campaign-api/label-data-object.md)|Labels let you organize campaigns, ad groups, ads, and keywords into groups based on whatever is important to you. You can then filter and run reports on your labels to get the data that is most meaningful to you.|
|[LabelAssociation](../campaign-api/labelassociation-data-object.md)|Defines the relationship between a label and campaign, ad group, ad, or keyword entity.|
|[LocationAdExtension](../campaign-api/locationadextension-data-object.md)|Defines an ad extension that specifies a business? address and phone number to include in a text ad.|
|[LocationCriterion](../campaign-api/locationcriterion-data-object.md)|Defines a criterion that can be used to show ads to users in a specific location.|
|[LocationIntentCriterion](../campaign-api/locationintentcriterion-data-object.md)|Defines a criterion that determines the intent option for all location and radius criterions of the campaign or ad group.|
|[ManualCpcBiddingScheme](../campaign-api/manualcpcbiddingscheme-data-object.md)|Defines an object that represents the manual CPC bid strategy type.|
|[MaxClicksBiddingScheme](../campaign-api/maxclicksbiddingscheme-data-object.md)|Defines an object that represents the maximum clicks bid strategy type.|
|[MaxConversionsBiddingScheme](../campaign-api/maxconversionsbiddingscheme-data-object.md)|Defines an object that represents the maximum conversions bid strategy type.|
|[Media](../campaign-api/media-data-object.md)|Defines the base object of media.|
|[MediaAssociation](../campaign-api/mediaassociation-data-object.md)|Defines an object that represents the identified media and an associated entity, for example media associated with an ad group.|
|[MediaMetaData](../campaign-api/mediametadata-data-object.md)|Defines a media meta data object. The meta data includes download Urls for one or more media representations.|
|[MediaRepresentation](../campaign-api/mediarepresentation-data-object.md)|Defines a media representation base class that includes a  media download Url.|
|[MigrationStatusInfo](../campaign-api/migrationstatusinfo-data-object.md)|Defines an object that contains the migration type and status for an account.|
|[NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md)|Defines a criterion that you want to exclude from the specified ad group.|
|[NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md)|Defines a criterion that you want to exclude from the specified campaign.|
|[NegativeKeyword](../campaign-api/negativekeyword-data-object.md)|Defines a negative keyword with match type.|
|[NegativeKeywordList](../campaign-api/negativekeywordlist-data-object.md)|Defines a negative keyword list.|
|[OfflineConversion](../campaign-api/offlineconversion-data-object.md)|Defines an offline conversion that you send to Bing Ads.|
|[OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md)|Defines an offline conversion goal. Use this type of goal if you have lead generation as an objective. Lead generation is when potential customers fill out a form or quote of interest, and then the sale is completed offline in person or over the phone (for example, car purchases, insurance quotes, mortgages, etc.).|
|[PagesViewedPerVisitGoal](../campaign-api/pagesviewedpervisitgoal-data-object.md)|Defines a pages viewed per visit conversion goal. Use this type of goal to count every time someone visits more than a specified number of pages on your website as a conversion.|
|[PageVisitorsRule](../campaign-api/pagevisitorsrule-data-object.md)|Defines a page visitors remarketing rule.|
|[PageVisitorsWhoDidNotVisitAnotherPageRule](../campaign-api/pagevisitorswhodidnotvisitanotherpagerule-data-object.md)|Defines a page visitors who did not visit another page remarketing rule.|
|[PageVisitorsWhoVisitedAnotherPageRule](../campaign-api/pagevisitorswhovisitedanotherpagerule-data-object.md)|Defines a page visitors who visited another page remarketing rule.|
|[Paging](../campaign-api/paging-data-object.md)|Defines a paging object that you can use to request labels and label associations in batches.|
|[PriceAdExtension](../campaign-api/priceadextension-data-object.md)|Defines an ad extension that includes between 3 and 8 price table rows.|
|[PriceTableRow](../campaign-api/pricetablerow-data-object.md)|Defines pricing information by currency and unit that you can use with price ad extensions.|
|[ProductAd](../campaign-api/productad-data-object.md)|Defines a product ad.|
|[ProductCondition](../campaign-api/productcondition-data-object.md)|Defines a condition that determines whether the product is selected.|
|[ProductPartition](../campaign-api/productpartition-data-object.md)|Defines an ad group level product partition with one condition that helps determine whether a product from the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store gets served as a product ad.|
|[ProductScope](../campaign-api/productscope-data-object.md)|Defines a campaign level product scope with list of conditions that help determine whether a product from the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store gets served as a product ad.|
|[RadiusCriterion](../campaign-api/radiuscriterion-data-object.md)|Defines a criterion that can be used to show ads to users within the radius of a specific geographical location.|
|[RemarketingList](../campaign-api/remarketinglist-data-object.md)|Defines a remarketing list.|
|[RemarketingRule](../campaign-api/remarketingrule-data-object.md)|Defines the base object of a remarketing rule.|
|[ReviewAdExtension](../campaign-api/reviewadextension-data-object.md)|Defines a review ad extension that can be included in a text ad.|
|[RuleItem](../campaign-api/ruleitem-data-object.md)|Defines the base class of a remarketing list rule item.|
|[RuleItemGroup](../campaign-api/ruleitemgroup-data-object.md)|Defines an object that contains a list of remarketing list rule items that apply to the same visited page.|
|[Schedule](../campaign-api/schedule-data-object.md)|Defines the start and end date ranges for ad extension scheduling.|
|[Setting](../campaign-api/setting-data-object.md)|Defines the base class of a setting.|
|[SharedEntity](../campaign-api/sharedentity-data-object.md)|Defines the base class of a shared entity.|
|[SharedEntityAssociation](../campaign-api/sharedentityassociation-data-object.md)|Defines an object that contains association information for a campaign and shared entity such as a negative keyword list.|
|[SharedList](../campaign-api/sharedlist-data-object.md)|Defines the base class of a shared list.|
|[SharedListItem](../campaign-api/sharedlistitem-data-object.md)|Defines the base class of a shared list item.|
|[ShoppingSetting](../campaign-api/shoppingsetting-data-object.md)|Defines a shopping setting for a [!INCLUDE[brand_bsc](../campaign-api/includes/brand-bsc.md)] campaign.|
|[SiteLink](../campaign-api/sitelink-data-object.md)|Defines a site link to include in an ad.|
|[SiteLinksAdExtension](../campaign-api/sitelinksadextension-data-object.md)|Defines an object with *multiple* sitelinks per ad extension.|
|[Sitelink2AdExtension](../campaign-api/sitelink2adextension-data-object.md)|Defines an object with *one* sitelink per ad extension.|
|[StringRuleItem](../campaign-api/stringruleitem-data-object.md)|Defines a rule expression that depends on the string values of the Url or Referrer Url. |
|[TargetCpaBiddingScheme](../campaign-api/targetcpabiddingscheme-data-object.md)|Defines an object that represents the target CPA bid strategy type.|
|[TextAd](../campaign-api/textad-data-object.md)|Defines a text ad.|
|[UetTag](../campaign-api/uettag-data-object.md)|Defines a Universal Event Tracking (UET) tag that you can add to your website to allow Bing Ads to collect actions people take on your website.|
|[UrlGoal](../campaign-api/urlgoal-data-object.md)|Defines a URL conversion goal. Use this type of goal to count every time someone visits a web page as a conversion.|
|[Webpage](../campaign-api/webpage-data-object.md)|Defines a webpage parameter that contains a list of webpage conditions or criteria that help determine whether you want to show dynamic search ads.|
|[WebpageCondition](../campaign-api/webpagecondition-data-object.md)|Defines a condition or criterion that helps determine whether you want to show dynamic search ads.|
|[WebpageParameter](../campaign-api/webpageparameter-data-object.md)|Defines the conditions or criteria that determine whether you want to show dynamic search ads.|
