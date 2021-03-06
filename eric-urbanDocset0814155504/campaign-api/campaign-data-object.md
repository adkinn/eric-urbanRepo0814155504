---
title: "Campaign Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ebd3b33c-8368-49f0-9ba4-b5f71c411c91
caps.latest.revision: 42
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Campaign Data Object
Defines a campaign.

## Syntax

```xml
<xs:complexType name="Campaign">
  <xs:sequence>
    <xs:element minOccurs="0" name="BiddingScheme" nillable="true" type="tns:BiddingScheme"/>
    <xs:element minOccurs="0" name="BudgetType" nillable="true" type="tns:BudgetLimitType" />
    <xs:element minOccurs="0" name="DailyBudget" nillable="true" type="xs:double" />
    <xs:element minOccurs="0" name="Description" nillable="true" type="xs:string" />
    <xs:element xmlns:q6="http://schemas.datacontract.org/2004/07/System.Collections.Generic" minOccurs="0" name="ForwardCompatibilityMap" nillable="true" type="q6:ArrayOfKeyValuePairOfstringstring"/>
    <xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    <xs:element minOccurs="0" name="Name" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="NativeBidAdjustment" nillable="true" type="xs:int"/>
    <xs:element minOccurs="0" name="Status" nillable="true" type="tns:CampaignStatus" />
    <xs:element minOccurs="0" name="TimeZone" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="TrackingUrlTemplate" nillable="true" type="xs:string"/>
    <xs:element xmlns:q7="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" minOccurs="0" name="UrlCustomParameters" nillable="true" type="q7:CustomParameters"/>
    <xs:element minOccurs="0" name="CampaignType" nillable="true" type="tns:CampaignType"/>
    <xs:element minOccurs="0" name="Settings" nillable="true" type="tns:ArrayOfSetting"/>
    <xs:element minOccurs="0" name="BudgetId" nillable="true" type="xs:long" />
    <xs:element xmlns:q8="http://schemas.microsoft.com/2003/10/Serialization/Arrays" minOccurs="0" name="Languages" nillable="true" type="q8:ArrayOfstring" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BiddingScheme*|The bid strategy type for how you want to manage your bids.<br/><br/>For campaigns you can use either of the [EnhancedCpcBiddingScheme](../campaign-api/enhancedcpcbiddingscheme-data-object.md) or [ManualCpcBiddingScheme](../campaign-api/manualcpcbiddingscheme-data-object.md) objects.<br/><br/>If you are signed up to pilot one or more of the auto bid strategy types, then you can also use the corresponding [MaxClicksBiddingScheme](../campaign-api/maxclicksbiddingscheme-data-object.md), [MaxConversionsBiddingScheme](../campaign-api/maxconversionsbiddingscheme-data-object.md), or [TargetCpaBiddingScheme](../campaign-api/targetcpabiddingscheme-data-object.md) object.<br /><br />[!INCLUDE[autobid_alert](../campaign-api/includes/autobid-alert.md)]<br /><br />[!INCLUDE[tip_biddingscheme](../campaign-api/includes/tip-biddingscheme.md)]<br/><br/>**Note:** For campaigns of type *Shopping* only the [EnhancedCpcBiddingScheme](../campaign-api/enhancedcpcbiddingscheme-data-object.md) or [ManualCpcBiddingScheme](../campaign-api/manualcpcbiddingscheme-data-object.md) objects can be used, and you must be in the Bing Shopping Enhanced CPC pilot. The pilot ID is 340.<br/><br/>**Add:** Optional. If you do not set this element, then [ManualCpcBiddingScheme](../campaign-api/manualcpcbiddingscheme-data-object.md) is used by default.<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[BiddingScheme](../campaign-api/biddingscheme-data-object.md)|
|*BudgetId*|The unique [!INCLUDE[brand](../campaign-api/includes/brand.md)] identifier of the [Budget](../campaign-api/budget-data-object.md) that this campaign shares with other campaigns in the account.<br /><br />If the value is not null and greater than zero, then the campaign is using a shared budget. If the value is null, then the campaign is not using a shared budget. If the campaign is using a shared budget, and you prefer that it use its own budget e.g. *DailyBudget* amount, set this element to '0' (zero) and set *DailyBudget* to a valid budget amount.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*long*|
|*BudgetType*|The budget type determines how the budget is spent.<br/><br/>In the context of shared budgets, the budget type is a read-only property that is always returned regardless of whether or not the campaign uses a shared budget. If you try to update the budget type of a campaign that has a shared budget, the service will return the *CampaignServiceCannotUpdateSharedBudget* error code. You can continue to set this property for unshared budgets, and you can make other updates to the campaign regardless of whether the budget is shared. To determine whether the campaign uses a shared budget, check the value of the *BudgetId* element as described above.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[BudgetLimitType](../campaign-api/budgetlimittype-value-set.md)|
|*CampaignType*|The campaign type determines whether the campaign is a Bing Shopping campaign, Dynamic Search Ads campaign, or Search &amp; Content campaign.<br/><br/>**Add:** Optional. If not specified, then default value of *SearchAndContent* is used and you cannot set Bing Shopping or Dynamic Search Ads campaign settings.<br/>**Update:** Not allowed.|[CampaignType](../campaign-api/campaigntype-value-set.md)|
|*DailyBudget*|The amount to spend daily on the campaign. You must set the daily budget amount if *BudgetId* is not set.<br/><br/>In the context of shared budgets, the budget amount is a read-only property that is always returned regardless of whether or not the campaign uses a shared budget. When a campaign is associated to a shared budget the amount returned is that of the shared budget. If you try to update the budget amount of a campaign that has a shared budget, the service will return the *CampaignServiceCannotUpdateSharedBudget* error code. You can continue to set this property for unshared budgets, and you can make other updates to the campaign regardless of whether the budget is shared. To determine whether the campaign uses a shared budget, check the value of the *BudgetId* element as described above.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*double*|
|*Description*|The description of the campaign.<br/><br/>The description can contain a maximum of 1,000 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *Campaign* object.|*KeyValuePairOfstringstring* array|
|*Id*|The unique [!INCLUDE[brand](../campaign-api/includes/brand.md)] identifier of the campaign.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Languages*|The languages of the ads and keywords in the campaign.<br/><br/>For possible values, see [Ad Languages](~/concepts/ad-languages.md). You can specify multiple languages individually in the list, or only include one list item set to *All* if you want to target all languages.<br/><br/>**IMPORTANT:** Support for multiple languages at the campaign level is in pilot. If languages are set at both the ad group and campaign level, the ad group-level language will override the campaign-level language. The customer is enabled for the pilot if the [GetCustomerPilotFeatures](~/customer-api/getcustomerpilotfeatures-service-operation.md) response includes pilot number *310*. Pilot participants will be able to set multiple languages at the campaign level, and will be able to delete the ad group level language. If your application depends on ad group language being set, then you must prepare for the possibility that ad group language will be nil. More specific dates and implementation details will be provided later through the [Bing Ads API Blog](https://blogs.msdn.microsoft.com/bing_ads_api/), and in the meantime you should update your application right away to support the change. Also note that as a one time migration when the customer is added to pilot, campaign languages are set to the union of all individual ad group languages. For example if you have three ad groups with language set to *English*, *German*, and *French*, then at the time of pilot enablement this campaign's languages will be set to a list including *English*, *German*, and *French*.<br/><br/>**Note:** For Dynamic Search Ads campaigns, only *English* is supported.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)] Once campaign languages are set, you cannot delete all of them. The list of languages that you specify during update replaces the previous settings i.e. does not append to the existing set of languages.|*string* array|
|*Name*|The name of the campaign. The name must be unique among all active or paused campaigns within the account. The name can contain a maximum of 128 characters.<br /><br />The service performs a case-insensitive comparison when it compares the name to existing campaign names.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*NativeBidAdjustment*|The percent amount by which to adjust your bid for native ads above or below the base ad group or keyword bid.<br/><br/>**Note:** [!INCLUDE[pilot_comingsoon](../campaign-api/includes/pilot-comingsoon.md)]<br /><br />Supported values are negative one hundred (-100) through positive nine hundred (900). Setting the bid adjustment to -100 will prevent native ads from showing for this campaign.<br /><br />Set this element to zero (0) if you want to use the base ad group or keyword bid instead of specifying any bid adjustment for native ads.<br /><br />As a best practice you should always specify a bid adjustment value. If you set this element to null the system default bid adjustment will be used. The system default bid adjustment is currently zero (0), and is subject to change.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*int*|
|*Settings*|The settings will vary by campaign type.<br /><br />**Note:**The contract specifies a list; however, currently a maximum of one setting is supported.<br /><br />If the *CampaignType* element is *SearchAndContent*, then this element must be nil or empty. If the *CampaignType* element is *Shopping*, this list will include a [ShoppingSetting](../campaign-api/shoppingsetting-data-object.md) object. If the *CampaignType* element is *DynamicSearchAds*, this list will include a [DynamicSearchAdsSetting](../campaign-api/dynamicsearchadssetting-data-object.md) object.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[Setting](../campaign-api/setting-data-object.md) array|
|*Status*|The status of the campaign.<br /><br />Possible values are *Active* and *Paused*.<br /><br />The service will automatically pause the campaign if the budget is depleted.<br/><br/>**Add:** Optional. The default value is *Paused*.<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|[CampaignStatus](../campaign-api/campaignstatus-value-set.md)|
|*TimeZone*|The time zone where the campaign operates.<br /><br />The time zone is used for reporting and applying the start and end date of an ad group.<br /><br />For possible values, see [Common Market Values](http://go.microsoft.com/fwlink/?LinkId=691345).<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)] You may not update the time zone if the campaign contains or has ever contained ad groups in the *Active* or *Paused* state.|*string*|
|*TrackingUrlTemplate*|The tracking template to use as a default for all URLs in your campaign.<br /><br />[!INCLUDE[validationrules_trackingurltemplate](../campaign-api/includes/validationrules-trackingurltemplate.md)]<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*UrlCustomParameters*|Your custom collection of key and value parameters for URL tracking.<br /><br />You may include up to 3 individual [CustomParameter](../campaign-api/customparameter-data-object.md) objects within the [CustomParameters](../campaign-api/customparameters-data-object.md) object. Each [CustomParameter](../campaign-api/customparameter-data-object.md) contains a *Key* and *Value* element.<br /><br />**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../campaign-api/includes/update-optional-setting-unchanged.md)] Set the *UrlCustomParameters* element to null or empty to retain any existing custom parameters. To remove all custom parameters, set the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object to null or empty. To remove a subset of custom parameters, specify the custom parameters that you want to keep in the *Parameters* element of the [CustomParameters](../campaign-api/customparameters-data-object.md) object.|[CustomParameters](../campaign-api/customparameters-data-object.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AddCampaigns](../campaign-api/addcampaigns-service-operation.md)  
[GetCampaignsByAccountId](../campaign-api/getcampaignsbyaccountid-service-operation.md)  
[GetCampaignsByIds](../campaign-api/getcampaignsbyids-service-operation.md)  
[UpdateCampaigns](../campaign-api/updatecampaigns-service-operation.md)  
[Setting](../campaign-api/setting-data-object.md)  
[ShoppingSetting](../campaign-api/shoppingsetting-data-object.md)  
[DynamicSearchAdsSetting](../campaign-api/dynamicsearchadssetting-data-object.md)  
[CampaignType](../campaign-api/campaigntype-value-set.md)  

