---
title: "Campaign Management Service Operations"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ac4ec81-485b-41b2-8bd2-9423a9f0a0b1
caps.latest.revision: 27
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Campaign Management Service Operations
The Campaign Management service defines the following service operations.

|Service Operation|Description|Request Limits|
|---------------------|---------------|------------------|
|[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)|Adds ad extensions to an account?s ad extension library.|1 *AccountId*<br /><br />100 *AdExtensions*|
|[AddAdGroupCriterions](../campaign-api/addadgroupcriterions-service-operation.md)|Adds ad group criterions.|1 *AccountId*<br /><br />1,000 *AdGroupCriterions*|
|[AddAdGroups](../campaign-api/addadgroups-service-operation.md)|Adds ad groups to a specified campaign.|1,000 *AdGroups*<br /><br />1 *CampaignId*|
|[AddAds](../campaign-api/addads-service-operation.md)|Adds ads to an ad group.|1 *AdGroupId*<br /><br />50 *Ads*|
|[AddAudiences](../campaign-api/addaudiences-service-operation.md)|Adds audiences to an account.|100 *Audiences*|
|[AddBudgets](../campaign-api/addbudgets-service-operation.md)|Adds new budgets to the account's shared budget library.|100 *Budgets*|
|[AddCampaignCriterions](../campaign-api/addcampaigncriterions-service-operation.md)|Adds campaign criterions.|100 *CampaignCriterions*|
|[AddCampaigns](../campaign-api/addcampaigns-service-operation.md)|Adds campaigns to an account.|1 *AccountId*<br /><br />100 *Campaigns*|
|[AddConversionGoals](../campaign-api/addconversiongoals-service-operation.md)|Adds new conversion goals to the account's shared conversion goal library.|100 *ConversionGoals*|
|[AddKeywords](../campaign-api/addkeywords-service-operation.md)|Adds keywords to an ad group.|1 *AdGroupId*<br /><br />1,000 *Keywords*|
|[AddLabels](../campaign-api/addlabels-service-operation.md)|Adds one or more labels to an account.|100 *Labels*|
|[AddListItemsToSharedList](../campaign-api/addlistitemstosharedlist-service-operation.md)|Adds negative keywords to the shared negative keyword list.|1 *SharedList*<br /><br />5,000 *ListItems*|
|[AddMedia](../campaign-api/addmedia-service-operation.md)|Adds the specified media to an account?s media library.|1 *AccountId*<br /><br />10 *Media*|
|[AddNegativeKeywordsToEntities](../campaign-api/addnegativekeywordstoentities-service-operation.md)|Adds negative keywords to the corresponding campaign or ad group entity.|1 *EntityNegativeKeywords*<br /><br />Each *EntityNegativeKeyword* element can contain up to 20,000 negative keywords.|
|[AddSharedEntity](../campaign-api/addsharedentity-service-operation.md)|Adds a negative keyword list to the account's library. Items in the account's library can be associated with any campaign within the account.|1 *SharedEntity*<br /><br />5,000 *ListItems*|
|[AddUetTags](../campaign-api/adduettags-service-operation.md)|Adds new Universal Event Tracking (UET) tags that you can add to your website to allow Bing Ads to collect actions people take on your website.|100 *UetTags*|
|[AppealEditorialRejections](../campaign-api/appealeditorialrejections-service-operation.md)|Appeals the editorial rejections of ads or keywords that failed editorial review.|1,000 *EntityIdToParentIdAssociations*|
|[ApplyOfflineConversions](../campaign-api/applyofflineconversions-service-operation.md)|Applies offline conversions for the account with Microsoft Click Id among other offline conversion data.|1,000 *OfflineConversions*|
|[ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md)|Applies an add, update, or delete action to the respective [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md), which each contain a [ProductPartition](../campaign-api/productpartition-data-object.md).|5,000 *CriterionActions*|
|[DeleteAdExtensions](../campaign-api/deleteadextensions-service-operation.md)|Delete ad extensions from the account?s ad extension library.|1 *AccountId*<br /><br />100 *AdExtensionIds*|
|[DeleteAdExtensionsAssociations](../campaign-api/deleteadextensionsassociations-service-operation.md)|Removes the ad extension association from the respective campaigns or ad groups.|1 *AccountId*<br /><br />100 *AdExtensionIdToEntityIdAssociations*|
|[DeleteAdGroupCriterions](../campaign-api/deleteadgroupcriterions-service-operation.md)|Deletes the list of ad group criterions.|1 *AccountId*<br /><br />1,000 *AdGroupCriterionIds*|
|[DeleteAdGroups](../campaign-api/deleteadgroups-service-operation.md)|Deletes ad groups in a specified campaign.|1,000 *AdGroupIds*<br /><br />1 *CampaignId*|
|[DeleteAds](../campaign-api/deleteads-service-operation.md)|Deletes ads in a specified ad group.|1 *AdGroupId*<br /><br />50 *AdIds*|
|[DeleteAudiences](../campaign-api/deleteaudiences-service-operation.md)|Deletes audiences from an account.|100 *AudienceIds*|
|[DeleteBudgets](../campaign-api/deletebudgets-service-operation.md)|Deletes budgets from the account's shared budget library.|100 *BudgetIds*|
|[DeleteCampaignCriterions](../campaign-api/deletecampaigncriterions-service-operation.md)|Deletes campaign criterions.|100 *CampaignCriterionIds*|
|[DeleteCampaigns](../campaign-api/deletecampaigns-service-operation.md)|Deletes campaigns in a specified account.|1 *AccountId*<br /><br />100 *CampaignIds*|
|[DeleteKeywords](../campaign-api/deletekeywords-service-operation.md)|Deletes keywords in a specified ad group.|1 *AdGroupId*<br /><br />1,000 *KeywordIds*|
|[DeleteLabelAssociations](../campaign-api/deletelabelassociations-service-operation.md)|Deletes label associations.|100 *LabelAssociations*|
|[DeleteLabels](../campaign-api/deletelabels-service-operation.md)|Deletes one or more labels from the account.|100 *LabelIds*|
|[DeleteListItemsFromSharedList](../campaign-api/deletelistitemsfromsharedlist-service-operation.md)|Deletes negative keywords from the shared negative keyword list.|1 *SharedList*<br /><br />5,000 *ListItemIds*|
|[DeleteMedia](../campaign-api/deletemedia-service-operation.md)|Deletes the specified media from an account?s media library.<br/><br/>**Note:** This service operation is not yet supported.|1 *AccountId*<br /><br />100*MediaIds*|
|[DeleteNegativeKeywordsFromEntities](../campaign-api/deletenegativekeywordsfromentities-service-operation.md)|Deletes negative keywords from the corresponding campaign or ad group entity.|1 *EntityNegativeKeywords*<br /><br />Each *EntityNegativeKeyword* element can contain up to 20,000 negative keywords.|
|[DeleteSharedEntities](../campaign-api/deletesharedentities-service-operation.md)|Deletes negative keyword lists from the account's library.|20 *SharedEntities*|
|[DeleteSharedEntityAssociations](../campaign-api/deletesharedentityassociations-service-operation.md)|Removes the association between a negative keyword list and an entity such as a campaign.|10,000 *Associations*|
|[GetAccountMigrationStatuses](../campaign-api/getaccountmigrationstatuses-service-operation.md)|Retrieves the account migration status info.|1,000 *AccountIds*|
|[GetAccountProperties](../campaign-api/getaccountproperties-service-operation.md)|Gets account level properties by name.|Not applicable|
|[GetAdExtensionIdsByAccountId](../campaign-api/getadextensionidsbyaccountid-service-operation.md)|Retrieves the ad extensions from the account?s ad extension library.|1 *AccountId*|
|[GetAdExtensionsAssociations](../campaign-api/getadextensionsassociations-service-operation.md)|Retrieves the ad extension associations for the respective campaign and ad group identifiers.|1 *AccountId*<br /><br />100 *EntityIds*|
|[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)|Retrieves the specified ad extensions from the account?s ad extension library.|1 *AccountId*<br /><br />100 *AdExtensionIds*|
|[GetAdExtensionsEditorialReasons](../campaign-api/getadextensionseditorialreasons-service-operation.md)|Gets editorial rejection reasons for the respective ad extension and entity associations.|1 *AccountId*<br /><br />100 *AdExtensionIdToEntityIdAssociations*|
|[GetAdGroupCriterionsByIds](../campaign-api/getadgroupcriterionsbyids-service-operation.md)|Retrieves the specified ad group criterions.|1 *AccountId*<br /><br />1,000 *AdGroupCriterionIds*|
|[GetAdGroupsByCampaignId](../campaign-api/getadgroupsbycampaignid-service-operation.md)|Retrieves the ad groups that exist within a specified campaign.|1 *CampaignId*|
|[GetAdGroupsByIds](../campaign-api/getadgroupsbyids-service-operation.md)|Retrieves the campaign's ad groups.|1,000 *AdGroupIds*<br /><br />1 *CampaignId*|
|[GetAdsByAdGroupId](../campaign-api/getadsbyadgroupid-service-operation.md)|Retrieves the ads that are associated with an ad group.|1 *AdGroupId*|
|[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)|Retrieves the ad group's ads that have the requested editorial review status.|1 *AdGroupId*|
|[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)|Retrieves the ad group's ads.|1 *AdGroupId*<br /><br />20 *AdIds*|
|[GetAudiencesByIds](../campaign-api/getaudiencesbyids-service-operation.md)|Gets audiences by audience identifiers.|100 *AudienceIds*|
|[GetBMCStoresByCustomerId](../campaign-api/getbmcstoresbycustomerid-service-operation.md)|Retrieves the customer's [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] store details.|Not applicable.|
|[GetBSCCountries](../campaign-api/getbsccountries-service-operation.md)|Retrieves the list of supported sales country codes for Bing Shopping campaigns.|Not applicable.|
|[GetBudgetsByIds](../campaign-api/getbudgetsbyids-service-operation.md)|Retrieves the specified budgets from the account's shared budget library.|100 *BudgetIds*|
|[GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md)|Retrieves the specified campaign criterions.|100 *CampaignCriterionIds*<br /><br />1 *CampaignId*|
|[GetCampaignIdsByBudgetIds](../campaign-api/getbudgetsbyids-service-operation.md)|Retrieves the campaign identifiers that share each specified budget.|100 *BudgetIds*|
|[GetCampaignsByAccountId](../campaign-api/getcampaignsbyaccountid-service-operation.md)|Retrieves all the campaigns that exist within a specified account.|1 *AccountId*|
|[GetCampaignsByIds](../campaign-api/getcampaignsbyids-service-operation.md)|Retrieves the the account's campaigns.|1 *AccountId*<br /><br />100 *CampaignIds*|
|[GetConversionGoalsByIds](../campaign-api/getconversiongoalsbyids-service-operation.md)|Retrieves the requested conversion goals.|100 *ConversionGoalIds*|
|[GetConversionGoalsByTagIds](../campaign-api/getconversiongoalsbytagids-service-operation.md)|Retrieves the conversion goals that use the specified UET tags.|100 *TagIds*|
|[GetEditorialReasonsByIds](../campaign-api/geteditorialreasonsbyids-service-operation.md)|Retrieves the reasons why the specified entities failed editorial review and whether the rejection is appealable.|1 *AccountId*<br /><br />1,000 *EntityIdToParentIdAssociations*|
|[GetGeoLocationsFileUrl](../campaign-api/getgeolocationsfileurl-service-operation.md)|Gets a temporary URL that you can use to download a file that contains the supported geographical location criterion codes.|Not applicable.|
|[GetKeywordsByAdGroupId](../campaign-api/getkeywordsbyadgroupid-service-operation.md)|Retrieves the keywords for an ad group.|1 *AdGroupId*|
|[GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md)|Retrieves the keywords that have the requested editorial review status.|1 *AdGroupId*|
|[GetKeywordsByIds](../campaign-api/getkeywordsbyids-service-operation.md)|Retrieves the specified keywords.|1 *AdGroupId*<br /><br />1,000 *KeywordIds*|
|[GetLabelAssociationsByEntityIds](../campaign-api/getlabelassociationsbyentityids-service-operation.md)|Gets label associations by entity identifiers.|100 *EntityIds*|
|[GetLabelAssociationsByLabelIds](../campaign-api/getlabelassociationsbylabelids-service-operation.md)|Gets label associations by label identifiers.|1 *LabelIds*|
|[GetLabelsByIds](../campaign-api/getlabelsbyids-service-operation.md)|Gets labels by label identifiers.|1,000 *LabelIds*|
|[GetListItemsBySharedList](../campaign-api/getlistitemsbysharedlist-service-operation.md)|Gets the negative keywords of a negative keyword list.|1 *SharedList*|
|[GetMediaAssociations](../campaign-api/getmediaassociations-service-operation.md)|Retrieves the media associations of the specified entity type from an account?s media library.|1 *AccountId*<br /><br />10 *MediaIds*|
|[GetMediaByIds](../campaign-api/getmediabyids-service-operation.md)|Retrieves the specified media from an account?s media library.|1 *AccountId*<br /><br />10 *MediaIds*|
|[GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md)|Retrieves the media meta data of the specified entity type from an account?s media library.|Not applicable.|
|[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)|Retrieves the specified media meta data from an account?s media library.|100 *MediaIds*|
|[GetNegativeKeywordsByEntityIds](../campaign-api/getnegativekeywordsbyentityids-service-operation.md)|Retrieves the negative keywords that are only associated with the specified campaigns or ad groups.|1 *ParentEntityId*<br /><br />1 *EntityIds*|
|[GetNegativeSitesByAdGroupIds](../campaign-api/getnegativesitesbyadgroupids-service-operation.md)|Retrieves the negative site URLs of the specified ad groups.|15 *AdGroupIds*<br /><br />1 *CampaignId*|
|[GetNegativeSitesByCampaignIds](../campaign-api/getnegativesitesbycampaignids-service-operation.md)|Retrieves the negative site URLs of the specified campaigns.|1 *AccountId*<br /><br />15 *CampaignIds*|
|[GetSharedEntitiesByAccountId](../campaign-api/getsharedentitiesbyaccountid-service-operation.md)|Gets the negative keyword lists from the account's library.|Not applicable.|
|[GetSharedEntityAssociationsByEntityIds](../campaign-api/getsharedentityassociationsbyentityids-service-operation.md)|Gets negative keyword list associations for the specified campaigns.|100 *EntityIds*|
|[GetSharedEntityAssociationsBySharedEntityIds](../campaign-api/getsharedentityassociationsbysharedentityids-service-operation.md)|Gets shared entity associations for the specified negative keyword lists.|1 *SharedEntityIds*|
|[GetUetTagsByIds](../campaign-api/getuettagsbyids-service-operation.md)|Retrieves the specified Universal Event Tracking (UET) tags.|100 *TagIds*|
|[SetAccountProperties](../campaign-api/setaccountproperties-service-operation.md)|Sets account level properties by name.|Not applicable|
|[SetAdExtensionsAssociations](../campaign-api/setadextensionsassociations-service-operation.md)|Associates the specified ad extensions with the respective campaigns or ad groups.|1 *AccountId*<br /><br />100 *AdExtensionIdToEntityIdAssociations*|
|[SetLabelAssociations](../campaign-api/setlabelassociations-service-operation.md)|Sets label associations.|100 *LabelAssociations*|
|[SetNegativeSitesToAdGroups](../campaign-api/setnegativesitestoadgroups-service-operation.md)|Sets the negative site URLs of the specified ad groups.|5,000 *AdGroupNegativeSites*<br /><br />1 *CampaignId*|
|[SetNegativeSitesToCampaigns](../campaign-api/setnegativesitestocampaigns-service-operation.md)|Sets the negative site URLs of the specified campaigns.|1 *AccountId*<br /><br />5,000 *CampaignNegativeSites*|
|[SetSharedEntityAssociations](../campaign-api/setsharedentityassociations-service-operation.md)|Sets the association between a campaign and a negative keyword list.|10,000 *Associations*|
|[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)|Updates ad extensions within an account?s ad extension library.|1 *AccountId*<br /><br />100 *AdExtensions*|
|[UpdateAdGroupCriterions](../campaign-api/updateadgroupcriterions-service-operation.md)|Updates ad group criterions.|1 *AccountId*<br /><br />1,000 *AdGroupCriterions*|
|[UpdateAdGroups](../campaign-api/updateadgroups-service-operation.md)|Updates the specified ad groups in a specified campaign.|1,000 *AdGroups*<br /><br />1 *CampaignId*|
|[UpdateAds](../campaign-api/updateads-service-operation.md)|Updates the specified ads within a particular ad group.|1 *AdGroupId*<br /><br />50 *Ads*|
|[UpdateAudiences](../campaign-api/updateaudiences-service-operation.md)|Updates audiences in an account.|100 *Audiences*|
|[UpdateBudgets](../campaign-api/updatebudgets-service-operation.md)|Updates budgets in the account's shared budget library.|100 *Budgets*|
|[UpdateCampaignCriterions](../campaign-api/updatecampaigncriterions-service-operation.md)|Updates campaign criterions.|100 *CampaignCriterions*|
|[UpdateCampaigns](../campaign-api/updatecampaigns-service-operation.md)|Updates specified campaigns in a specified account.|1 *AccountId*<br /><br />100 *Campaigns*|
|[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)|Updates conversion goals within the account's shared conversion goal library.|100 *ConversionGoals*|
|[UpdateKeywords](../campaign-api/updatekeywords-service-operation.md)|Updates the keywords within a specified ad group.|1 *AdGroupId*<br /><br />1,000 *Keywords*|
|[UpdateLabels](../campaign-api/updatelabels-service-operation.md)|Updates the labels within the account.|100 *Labels*|
|[UpdateSharedEntities](../campaign-api/updatesharedentities-service-operation.md)|Updates negative keyword lists within the account's library.|20 *SharedEntities*|
|[UpdateUetTags](../campaign-api/updateuettags-service-operation.md)|Updates the specified Universal Event Tracking (UET) tags.|100 *UetTags*|
