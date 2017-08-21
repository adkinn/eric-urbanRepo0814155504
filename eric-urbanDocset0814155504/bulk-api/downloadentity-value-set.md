---
title: "DownloadEntity Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14cff3e2-4968-43e1-a4a4-fd994af0d92d
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DownloadEntity Value Set
Defines the entities that may be downloaded in bulk.

For more information, see [Bulk File Schema](../bulk-api/bulk-file-schema.md).

## Syntax

```xml
<xs:simpleType name="DownloadEntity">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Campaigns"/>
    <xs:enumeration value="AdGroups"/>
    <xs:enumeration value="Ads"/>
    <xs:enumeration value="Keywords"/>
    <xs:enumeration value="CampaignNegativeKeywords"/>
    <xs:enumeration value="AdGroupNegativeKeywords"/>
    <xs:enumeration value="CampaignNegativeSites"/>
    <xs:enumeration value="AdGroupNegativeSites"/>
    <xs:enumeration value="CampaignSiteLinksAdExtensions"/>
    <xs:enumeration value="CampaignLocationAdExtensions"/>
    <xs:enumeration value="CampaignCallAdExtensions"/>
    <xs:enumeration value="AdGroupSiteLinksAdExtensions"/>
    <xs:enumeration value="LocationAdExtensions"/>
    <xs:enumeration value="CallAdExtensions"/>
    <xs:enumeration value="SiteLinksAdExtensions"/>
    <xs:enumeration value="NegativeKeywordLists"/>
    <xs:enumeration value="SharedNegativeKeywords"/>
    <xs:enumeration value="CampaignNegativeKeywordListAssociations"/>
    <xs:enumeration value="ImageAdExtensions"/>
    <xs:enumeration value="AdGroupImageAdExtensions"/>
    <xs:enumeration value="CampaignImageAdExtensions"/>
    <xs:enumeration value="AppAdExtensions"/>
    <xs:enumeration value="AdGroupAppAdExtensions"/>
    <xs:enumeration value="CampaignAppAdExtensions"/>
    <xs:enumeration value="ReviewAdExtensions"/>
    <xs:enumeration value="CampaignNegativeDynamicSearchAdTargets"/>
    <xs:enumeration value="AdGroupProductPartitions"/>
    <xs:enumeration value="CampaignProductScopes"/>
    <xs:enumeration value="CampaignReviewAdExtensions"/>
    <xs:enumeration value="AdGroupReviewAdExtensions"/>
    <xs:enumeration value="CalloutAdExtensions"/>
    <xs:enumeration value="CampaignCalloutAdExtensions"/>
    <xs:enumeration value="AdGroupCalloutAdExtensions"/> 
    <xs:enumeration value="Sitelink2AdExtensions"/>
    <xs:enumeration value="CampaignSitelink2AdExtensions"/>
    <xs:enumeration value="AdGroupSitelink2AdExtensions"/>       
    <xs:enumeration value="StructuredSnippetAdExtensions"/>
    <xs:enumeration value="CampaignStructuredSnippetAdExtensions"/>
    <xs:enumeration value="AdGroupStructuredSnippetAdExtensions"/>
    <xs:enumeration value="Budgets"/>
    <xs:enumeration value="TextAds"/>
    <xs:enumeration value="ProductAds"/>
    <xs:enumeration value="AppInstallAds"/>
    <xs:enumeration value="ExpandedTextAds"/>
    <xs:enumeration value="DynamicSearchAds"/>
    <xs:enumeration value="AdGroupDynamicSearchAdTargets"/>
    <xs:enumeration value="AdGroupNegativeDynamicSearchAdTargets"/>
    <xs:enumeration value="AdGroupTargetCriterions"/>
    <xs:enumeration value="CampaignTargetCriterions"/>
    <xs:enumeration value="CustomAudiences"/>
    <xs:enumeration value="AdGroupCustomAudienceAssociations"/>
    <xs:enumeration value="AdGroupNegativeCustomAudienceAssociations"/>
    <xs:enumeration value="InMarketAudiences"/>
    <xs:enumeration value="AdGroupInMarketAudienceAssociations"/>
    <xs:enumeration value="AdGroupNegativeInMarketAudienceAssociations"/>
    <xs:enumeration value="RemarketingLists"/>
    <xs:enumeration value="AdGroupRemarketingListAssociations"/>
    <xs:enumeration value="AdGroupNegativeRemarketingListAssociations"/>
    <xs:enumeration value="Audiences"/>
    <xs:enumeration value="AdGroupAudienceAssociations"/>
    <xs:enumeration value="AdGroupNegativeAudienceAssociations"/>
    <xs:enumeration value="PriceAdExtensions"/>
    <xs:enumeration value="AccountPriceAdExtensions"/>
    <xs:enumeration value="AdGroupPriceAdExtensions"/>
    <xs:enumeration value="CampaignPriceAdExtensions"/>
    <xs:enumeration value="AccountAppAdExtensions"/>
    <xs:enumeration value="AccountCalloutAdExtensions"/>
    <xs:enumeration value="AccountImageAdExtensions"/>
    <xs:enumeration value="AccountLocationAdExtensions"/>
    <xs:enumeration value="AccountReviewAdExtensions"/>
    <xs:enumeration value="AccountSitelink2AdExtensions"/>
    <xs:enumeration value="AccountStructuredSnippetAdExtensions"/>
    <xs:enumeration value="Labels"/>
    <xs:enumeration value="CampaignLabels"/>
    <xs:enumeration value="AdGroupLabels"/>
    <xs:enumeration value="KeywordLabels"/>
    <xs:enumeration value="AppInstallAdLabels"/>
    <xs:enumeration value="DynamicSearchAdLabels"/>
    <xs:enumeration value="ExpandedTextAdLabels"/>
    <xs:enumeration value="ProductAdLabels"/>
    <xs:enumeration value="TextAdLabels"/>
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountAppAdExtensions|Include [Account App Ad Extension](../bulk-api/account-app-ad-extension.md) records in the download that each represent the association relationship between an account and an app ad extension. For [App Ad Extension](../bulk-api/app-ad-extension.md) records, you should include the *AppAdExtensions* value in the download request.|
|AccountCalloutAdExtensions|Include [Account Callout Ad Extension](../bulk-api/account-callout-ad-extension.md) records in the download that represents the association relationship between an account and a callout ad extension. For [Callout Ad Extension](../bulk-api/callout-ad-extension.md) records, you should include the *CalloutAdExtensions* value in the download request.|
|AccountImageAdExtensions|Include [Account Image Ad Extension](../bulk-api/account-image-ad-extension.md) records in the download that represents the association relationship between an account and an image ad extension. For [Image Ad Extension](../bulk-api/image-ad-extension.md) records, you should include the *ImageAdExtensions* value in the download request.|
|AccountLocationAdExtensions|Include [Account Location Ad Extension](../bulk-api/account-location-ad-extension.md) records in the download that represents the association relationship between an account and a location ad extension. For [Location Ad Extension](../bulk-api/location-ad-extension.md) records, you should include the *LocationAdExtensions* value in the download request.|
|AccountPriceAdExtensions|Include [Account Price Ad Extension](../bulk-api/account-price-ad-extension.md) records in the download that represents the association relationship between an account and a price ad extension. For [Price Ad Extension](../bulk-api/price-ad-extension.md) records, you should include the *PriceAdExtensions* value in the download request.|
|AccountReviewAdExtensions|Include [Account Review Ad Extension](../bulk-api/account-review-ad-extension.md) records in the download that each represent the association relationship between an account and a review ad extension. For [Review Ad Extension](../bulk-api/review-ad-extension.md) records, you should include the *ReviewAdExtensions* value in the download request.|
|AccountSitelink2AdExtensions|Include [Account Sitelink2 Ad Extension](../bulk-api/account-sitelink2-ad-extension.md) records in the download that represents the association relationship between an account and a sitelink2 ad extension. For [Sitelink2 Ad Extension](../bulk-api/sitelink2-ad-extension.md) records, you should include the *Sitelink2AdExtensions* value in the download request.|
|AccountStructuredSnippetAdExtensions|Include [Account Structured Snippet Ad Extension](../bulk-api/account-structured-snippet-ad-extension.md) records in the download that represents the association relationship between an account and a structured snippet ad extension. For [Structured Snippet Ad Extension](../bulk-api/structured-snippet-ad-extension.md) records, you should include the *StructuredSnippetAdExtensions* value in the download request.|
|AdGroupAppAdExtensions|Include [Ad Group App Ad Extension](../bulk-api/ad-group-app-ad-extension.md) records in the download that each represent the association relationship between an ad group and an app ad extension. For [App Ad Extension](../bulk-api/app-ad-extension.md) records, you should include the *AppAdExtensions* value in the download request.|
|AdGroupAudienceAssociations|Include [Ad Group Custom Audience Association](../bulk-api/ad-group-custom-audience-association.md), [Ad Group In Market Audience Association](../bulk-api/ad-group-in-market-audience-association.md), and [Ad Group Remarketing List Association](../bulk-api/ad-group-remarketing-list-association.md) records in the download data.<br/><br/>**Note:** To get audience associations by type instead of requesting all types of audience associations, you can include one or more of the *AdGroupCustomAudienceAssociations*, *AdGroupInMarketAudienceAssociations*, and *AdGroupRemarketingListAssociations* values in the download request.|
|AdGroupCalloutAdExtensions|Include [Ad Group Callout Ad Extension](../bulk-api/ad-group-callout-ad-extension.md) records in the download that each represent the association relationship between an ad group and a callout ad extension. For [Callout Ad Extension](../bulk-api/callout-ad-extension.md) records, you should include the *CalloutAdExtensions* value in the download request.|
|AdGroupCustomAudienceAssociations|Include [Ad Group Custom Audience Association](../bulk-api/ad-group-custom-audience-association.md) records in the download that each represent the association relationship between an ad group and a custom audience. For [Custom Audience](../bulk-api/custom-audience.md) records, you should include the *CustomAudiences* value in the download request.|
|AdGroupDynamicSearchAdTargets|Include [Ad Group Dynamic Search Ad Target](../bulk-api/ad-group-dynamic-search-ad-target.md) records in the download data.|
|AdGroupImageAdExtensions|Include [Ad Group Image Ad Extension](../bulk-api/ad-group-image-ad-extension.md) records in the download that each represent the association relationship between an ad group and an image ad extension. For [Image Ad Extension](../bulk-api/callout-ad-extension.md) records, you should include the *ImageAdExtensions* value in the download request.|
|AdGroupInMarketAudienceAssociations|Include [Ad Group In Market Audience Association](../bulk-api/ad-group-in-market-audience-association.md) records in the download that each represent the association relationship between an ad group and an in-market audience. For [In Market Audience](../bulk-api/in-market-audience.md) records, you should include the *InMarketAudiences* value in the download request.|
|AdGroupLabels|Include [Ad Group Label](../bulk-api/ad-group-label.md) records in the download that each represent a label applied to an ad group. For [Label](../bulk-api/label.md) records, you should include the *Labels* value in the download request.|
|AdGroupNegativeAudienceAssociations|Include [Ad Group Negative Custom Audience Association](../bulk-api/ad-group-negative-custom-audience-association.md), [Ad Group Negative In Market Audience Association](../bulk-api/ad-group-negative-in-market-audience-association.md), and [Ad Group Negative Remarketing List Association](../bulk-api/ad-group-negative-remarketing-list-association.md) records in the download data.<br/><br/>**Note:** To get negative audience associations by type instead of requesting all types of negative audience associations, you can include one or more of the *AdGroupNegativeCustomAudienceAssociations*, *AdGroupInMarketAudienceNegativeAssociations*, and *AdGroupNegativeRemarketingListAssociations* values in the download request.|
|AdGroupNegativeCustomAudienceAssociations|Include [Ad Group Negative Custom Audience Association](../bulk-api/ad-group-negative-custom-audience-association.md) records in the download that each represent the association relationship between an ad group and a custom audience exclusion. For [Custom Audience](../bulk-api/custom-audience.md) records, you should include the *CustomAudiences* value in the download request.|
|AdGroupNegativeDynamicSearchAdTargets|Include [Ad Group Negative Dynamic Search Ad Target](../bulk-api/ad-group-negative-dynamic-search-ad-target.md) records in the download data.|
|AdGroupNegativeInMarketAudienceAssociations|Include [Ad Group Negative In Market Audience Association](../bulk-api/ad-group-negative-in-market-audience-association.md) records in the download that each represent the association relationship between an ad group and an in-market audience exclusion. For [In Market Audience](../bulk-api/in-market-audience.md) records, you should include the *InMarketAudiences* value in the download request.|
|AdGroupNegativeKeywords|Include [Ad Group Negative Keyword](../bulk-api/ad-group-negative-keyword.md) records in the download data.|
|AdGroupNegativeRemarketingListAssociations|Include [Ad Group Negative Remarketing List Association](../bulk-api/ad-group-negative-remarketing-list-association.md) records in the download that each represent the association relationship between an ad group and a remarketing list exclusion. For [Remarketing List](../bulk-api/remarketing-list.md) records, you should include the *RemarketingLists* value in the download request.|
|AdGroupNegativeSites|Include [Ad Group Negative Site](../bulk-api/ad-group-negative-site.md) records in the download data.|
|AdGroupPriceAdExtensions|Include [Ad Group Price Ad Extension](../bulk-api/ad-group-price-ad-extension.md) records in the download that each represent the association relationship between an ad group and a price ad extension. For [Price Ad Extension](../bulk-api/price-ad-extension.md) records, you should include the *PriceAdExtensions* value in the download request.|
|AdGroupProductPartitions|Include [Ad Group Product Partition](../bulk-api/ad-group-product-partition.md) records in the download data.|
|AdGroupRemarketingListAssociations|Include [Ad Group Remarketing List Association](../bulk-api/ad-group-remarketing-list-association.md) records in the download that each represent the association relationship between an ad group and a remarketing list. For [Remarketing List](../bulk-api/remarketing-list.md) records, you should include the *RemarketingLists* value in the download request.|
|AdGroupReviewAdExtensions|Include [Ad Group Review Ad Extension](../bulk-api/ad-group-review-ad-extension.md) records in the download that each represent the association relationship between an ad group and a review ad extension. For [Review Ad Extension](../bulk-api/review-ad-extension.md) records, you should include the *ReviewAdExtensions* value in the download request.|
|AdGroups|Include [Ad Group](../bulk-api/ad-group.md) records in the download data.|
|AdGroupSiteLinksAdExtensions|Include [AdGroup Sitelink Ad Extension](../bulk-api/adgroup-sitelink-ad-extension.md) records in the download that each represent the association relationship between an ad group and a sitelink ad extension. For [Sitelink Ad Extension](../bulk-api/sitelink-ad-extension.md) records, you should include the *SiteLinksAdExtensions* value in the download request.|
|AdGroupSitelink2AdExtensions|Include [Ad Group Sitelink2 Ad Extension](../bulk-api/ad-group-sitelink2-ad-extension.md) records in the download that each represent the association relationship between an ad group and a sitelink2 ad extension. For [Sitelink2 Ad Extension](../bulk-api/sitelink2-ad-extension.md) records, you should include the *Sitelink2AdExtensions* value in the download request.|
|AdGroupStructuredSnippetAdExtensions|Include [Ad Group Structured Snippet Ad Extension](../bulk-api/ad-group-structured-snippet-ad-extension.md) records in the download that each represent the association relationship between an ad group and a structured snippet ad extension. For [Structured Snippet Ad Extension](../bulk-api/structured-snippet-ad-extension.md) records, you should include the *StructuredSnippetAdExtensions* value in the download request.|
|AdGroupTargetCriterions|Include [Ad Group Age Criterion](../bulk-api/ad-group-age-criterion.md), [Ad Group DayTime Criterion](../bulk-api/ad-group-daytime-criterion.md), [Ad Group DeviceOS Criterion](../bulk-api/ad-group-deviceos-criterion.md), [Ad Group Gender Criterion](../bulk-api/ad-group-gender-criterion.md), [Ad Group Location Criterion](../bulk-api/ad-group-location-criterion.md), [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md), [Ad Group Negative Location Criterion](../bulk-api/ad-group-negative-location-criterion.md), and [Ad Group Radius Criterion](../bulk-api/ad-group-radius-criterion.md) records in the download data.|
|Ads|Include [App Install Ad](../bulk-api/app-install-ad.md), [Dynamic Search Ad](../bulk-api/dynamic-search-ad.md), [Expanded Text Ad](../bulk-api/expanded-text-ad.md), [Product Ad](../bulk-api/product-ad.md), and [Text Ad](../bulk-api/text-ad.md) records in the download data.<br/><br/>**Note:** To get ads by type instead of requesting all types of ads, you can include one or more of the *AppInstallAds*, *DynamicSearchAds*, *ExpandedTextAds*, *ProductAds*, and *TextAds* values in the download request.|
|AppAdExtensions|Include [App Ad Extension](../bulk-api/app-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all app ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the app ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|AppInstallAdLabels|Include [App Install Ad Label](../bulk-api/app-install-ad-label.md) records in the download that each represent a label applied to an app install ad. For [Label](../bulk-api/label.md) records, you should include the *Labels* value in the download request.|
|AppInstallAds|Include [App Install Ad](../bulk-api/app-install-ad.md) records in the download data.<br/><br/>**Note:** To get all types of ads instead of requesting ads by type, you can include the *Ads* value in the download request.|
|Audiences|Include [Custom Audience](../bulk-api/custom-audience.md), [In Market Audience](../bulk-api/in-market-audience.md), and [Remarketing List](../bulk-api/remarketing-list.md) records in the download data.<br/><br/>**Note:** The [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) and [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operations return the same set of audiences for the current authenticated user. All audiences that have *Scope* set to *Customer* are included. The audiences that have *Scope* set to *Account* are also included if the user has access to view or manage those accounts. In other words, if an audience is in account scope for an account that the user cannot access, then it is excluded from the download results.<br/><br/>**Note:** To get audiences by type instead of requesting all types of audiences, you can include one or more of the *CustomAudiences*, *InMarketAudiences*, and *RemarketingLists* values in the download request.|
|Budgets|Include [Budget](../bulk-api/budget.md) records in the download data.|
|CallAdExtensions|Include [Call Ad Extension](../bulk-api/call-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all call ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the call ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|CalloutAdExtensions|Include [Callout Ad Extension](../bulk-api/callout-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all callout ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the callout ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|CampaignAppAdExtensions|Include [Campaign App Ad Extension](../bulk-api/campaign-app-ad-extension.md) records in the download that each represent the association relationship between a campaign and an app ad extension. For [App Ad Extension](../bulk-api/app-ad-extension.md) records, you should include the *AppAdExtensions* value in the download request.|
|CampaignCallAdExtensions|Include [Campaign Call Ad Extension](../bulk-api/campaign-call-ad-extension.md) records in the download that represents the association relationship between a campaign and a call ad extension. For [Call Ad Extension](../bulk-api/call-ad-extension.md) records, you should include the *CallAdExtensions* value in the download request.|
|CampaignCalloutAdExtensions|Include [Campaign Callout Ad Extension](../bulk-api/campaign-callout-ad-extension.md) records in the download that represents the association relationship between a campaign and a callout ad extension. For [Callout Ad Extension](../bulk-api/callout-ad-extension.md) records, you should include the *CalloutAdExtensions* value in the download request.|
|CampaignImageAdExtensions|Include [Campaign Image Ad Extension](../bulk-api/campaign-image-ad-extension.md) records in the download that represents the association relationship between a campaign and an image ad extension. For [Image Ad Extension](../bulk-api/image-ad-extension.md) records, you should include the *ImageAdExtensions* value in the download request.|
|CampaignLabels|Include [Campaign Label](../bulk-api/campaign-label.md) records in the download that each represent a label applied to a campaign. For [Label](../bulk-api/label.md) records, you should include the *Labels* value in the download request.|
|CampaignLocationAdExtensions|Include [Campaign Location Ad Extension](../bulk-api/campaign-location-ad-extension.md) records in the download that represents the association relationship between a campaign and a location ad extension. For [Location Ad Extension](../bulk-api/location-ad-extension.md) records, you should include the *LocationAdExtensions* value in the download request.|
|CampaignNegativeDynamicSearchAdTargets|Include [Campaign Negative Dynamic Search Ad Target](../bulk-api/campaign-negative-dynamic-search-ad-target.md) records in the download data.|
|CampaignNegativeKeywords|Include [Campaign Negative Keyword](../bulk-api/campaign-negative-keyword.md) records in the download data.|
|CampaignNegativeKeywordListAssociations|Include [Campaign Negative Keyword List Association](../bulk-api/campaign-negative-keyword-list-association.md) records in the download that represents the association relationship between a campaign and a negative keyword list. For [Negative Keyword List](../bulk-api/negative-keyword-list.md) records, you should include the *NegativeKeywordLists* value in the download request.|
|CampaignNegativeSites|Include [Campaign Negative Site](../bulk-api/campaign-negative-site.md) records in the download data.|
|CampaignPriceAdExtensions|Include [Campaign Price Ad Extension](../bulk-api/campaign-price-ad-extension.md) records in the download that represents the association relationship between a campaign and a price ad extension. For [Price Ad Extension](../bulk-api/price-ad-extension.md) records, you should include the *PriceAdExtensions* value in the download request.|
|CampaignProductScopes|Include [Campaign Product Scope](../bulk-api/campaign-product-scope.md) records in the download data.|
|CampaignReviewAdExtensions|Include [Campaign Review Ad Extension](../bulk-api/campaign-review-ad-extension.md) records in the download that each represent the association relationship between a campaign and a review ad extension. For [Review Ad Extension](../bulk-api/review-ad-extension.md) records, you should include the *ReviewAdExtensions* value in the download request.|
|Campaigns|Include [Campaign](../bulk-api/campaign.md) records in the download data.|
|CampaignSiteLinksAdExtensions|Include [Campaign Sitelink Ad Extension](../bulk-api/campaign-sitelink-ad-extension.md) records in the download that represents the association relationship between a campaign and a sitelink ad extension. For [Sitelink Ad Extension](../bulk-api/sitelink-ad-extension.md) records, you should include the *SiteLinksAdExtensions* value in the download request.|
|CampaignSitelink2AdExtensions|Include [Campaign Sitelink2 Ad Extension](../bulk-api/campaign-sitelink2-ad-extension.md) records in the download that represents the association relationship between a campaign and a sitelink2 ad extension. For [Sitelink2 Ad Extension](../bulk-api/sitelink2-ad-extension.md) records, you should include the *Sitelink2AdExtensions* value in the download request.|
|CampaignStructuredSnippetAdExtensions|Include [Campaign Structured Snippet Ad Extension](../bulk-api/campaign-structured-snippet-ad-extension.md) records in the download that represents the association relationship between a campaign and a structured snippet ad extension. For [Structured Snippet Ad Extension](../bulk-api/structured-snippet-ad-extension.md) records, you should include the *StructuredSnippetAdExtensions* value in the download request.|
|CampaignTargetCriterions|Include [Campaign Age Criterion](../bulk-api/campaign-age-criterion.md), [Campaign DayTime Criterion](../bulk-api/campaign-daytime-criterion.md), [Campaign DeviceOS Criterion](../bulk-api/campaign-deviceos-criterion.md), [Campaign Gender Criterion](../bulk-api/campaign-gender-criterion.md), [Campaign Location Criterion](../bulk-api/campaign-location-criterion.md), [Campaign Location Intent Criterion](../bulk-api/campaign-location-intent-criterion.md), [Campaign Negative Location Criterion](../bulk-api/campaign-negative-location-criterion.md), and [Campaign Radius Criterion](../bulk-api/campaign-radius-criterion.md) records in the download data.|
|CustomAudiences|Include [Custom Audience](../bulk-api/custom-audience.md) records in the download data.<br/><br/>**Note:** The [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) and [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operations return the same set of custom audiences for the current authenticated user. All custom audiences that have *Scope* set to *Customer* are included. The custom audiences that have *Scope* set to *Account* are also included if the user has access to view or manage those accounts. In other words, if a custom audience is in account scope for an account that the user cannot access, then it is excluded from the download results.|
|DynamicSearchAdLabels|Include [Dynamic Search Ad Label](../bulk-api/dynamic-search-ad-label.md) records in the download that each represent a label applied to a dynamic search ad. For [Label](../bulk-api/label.md) records, you should include the *Labels* value in the download request.|
|DynamicSearchAds|Include [Dynamic Search Ad](../bulk-api/dynamic-search-ad.md) records in the download data.<br/><br/>**Note:** To get all types of ads instead of requesting ads by type, you can include the *Ads* value in the download request.|
|ExpandedTextAdLabels|Include [Expanded Text Ad Label](../bulk-api/expanded-text-ad-label.md) records in the download that each represent a label applied to an expanded text ad. For [Label](../bulk-api/label.md) records, you should include the *Labels* value in the download request.|
|ExpandedTextAds|Include [Expanded Text Ad](../bulk-api/expanded-text-ad.md) records in the download data.<br/><br/>**Note:** To get all types of ads instead of requesting ads by type, you can include the *Ads* value in the download request.|
|ImageAdExtensions|Include [Image Ad Extension](../bulk-api/image-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all image ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the image ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|InMarketAudiences|Include [In Market Audience](../bulk-api/in-market-audience.md) records in the download data.<br/><br/>**Note:** The [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) and [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operations return the same set of in-market audiences for the current authenticated user. All in-market audiences that have *Scope* set to *Customer* are included. The in-market audiences that have *Scope* set to *Account* are also included if the user has access to view or manage those accounts. In other words, if an in-market audience is in account scope for an account that the user cannot access, then it is excluded from the download results.|
|Keywords|Include [Keyword](../bulk-api/keyword.md) records in the download data.|
|KeywordLabels|Include [Keyword Label](../bulk-api/keyword-label.md) records in the download that each represent a label applied to a keyword. For [Label](../bulk-api/label.md) records, you should include the *Labels* value in the download request.|
|Labels|Include [Label](../bulk-api/label.md) records in the download data.<br/><br/>**Note:** The [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation will ignore campaign scope and return all labels from your account's labels library. Likewise the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation will return all labels from your account's labels library.|
|LocationAdExtensions|Include [Location Ad Extension](../bulk-api/location-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all location ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the location ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|NegativeKeywordLists|Include [Negative Keyword List](../bulk-api/negative-keyword-list.md) records in the download data. The [Negative Keyword List](../bulk-api/negative-keyword-list.md) records do not include negative keywords that are shared in each list. For [Shared Negative Keyword](../bulk-api/shared-negative-keyword.md) records, you should include the *SharedNegativeKeywords* value in the download request.<br/><br/>**Note:** The [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) will return all negative keyword lists from your account's negative keyword list library, whether or not the lists are associated with the specified campaigns .|
|PriceAdExtensions|Include [Price Ad Extension](../bulk-api/price-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all price ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the price ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|ProductAdLabels|Include [Product Ad Label](../bulk-api/product-ad-label.md) records in the download that each represent a label applied to a product ad. For [Label](../bulk-api/label.md) records, you should include the *Labels* value in the download request.|
|ProductAds|Include [Product Ad](../bulk-api/product-ad.md) records in the download data.<br/><br/>**Note:** To get all types of ads instead of requesting ads by type, you can include the *Ads* value in the download request.|
|ReviewAdExtensions|Include [Review Ad Extension](../bulk-api/review-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all review ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the review ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|RemarketingLists|Include [Remarketing List](../bulk-api/remarketing-list.md) records in the download data.<br/><br/>**Note:** The [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) and [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operations return the same set of remarketing lists for the current authenticated user. All remarketing lists that have *Scope* set to *Customer* are included. The remarketing lists that have *Scope* set to *Account* are also included if the user has access to view or manage those accounts. In other words, if a remarketing list is in account scope for an account that the user cannot access, then it is excluded from the download results.|
|SharedNegativeKeywords|Include [Shared Negative Keyword](../bulk-api/shared-negative-keyword.md) records in the download data. Shared negative keywords belong to a negative keyword list. For [Negative Keyword List](../bulk-api/negative-keyword-list.md) records, you should include the *NegativeKeywordLists* value in the download request.|
|SiteLinksAdExtensions|Include [Sitelink Ad Extension](../bulk-api/sitelink-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all sitelink ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the sitelink ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|Sitelink2AdExtensions|Include [Sitelink2 Ad Extension](../bulk-api/sitelink2-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all sitelink2 ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the sitelink2 ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|StructuredSnippetAdExtensions|Include [Structured Snippet Ad Extension](../bulk-api/structured-snippet-ad-extension.md) records in the download data.<br/><br/>**Note:** To get all structured snippet ad extensions from your account's extension library, use the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) operation. To get only the structured snippet ad extensions that are associated with entities within the specified campaigns, use the [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) operation.|
|TextAdLabels|Include [Text Ad Label](../bulk-api/text-ad-label.md) records in the download that each represent a label applied to a text ad. For [Label](../bulk-api/label.md) records, you should include the *Labels* value in the download request.|
|TextAds|Include [Text Ad](../bulk-api/text-ad.md) records in the download data.<br/><br/>**Note:** To get all types of ads instead of requesting ads by type, you can include the *Ads* value in the download request.|

## Requirements
[!INCLUDE[reqbulk](../bulk-api/includes/reqbulk.md)]  

## See Also
[DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md)  
[DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)  

