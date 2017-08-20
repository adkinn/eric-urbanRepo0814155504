---
title: "SearchCampaignChangeHistoryReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2912a26f-4743-4e1c-80a1-0167a216359c
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchCampaignChangeHistoryReportColumn Value Set
Defines the attribute columns that you can include in the [SearchCampaignChangeHistoryReportRequest](../reporting-api/searchcampaignchangehistoryreportrequest-data-object.md).

[!INCLUDE[reportcolumn_headerattributesonly](../reporting-api/includes/reportcolumn-headerattributesonly.md)]
## Syntax

```xml
\<xs:simpleType name="SearchCampaignChangeHistoryReportColumn">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="DateTime" />
    \<xs:enumeration value="AccountId" />
    \<xs:enumeration value="AccountName" />
    \<xs:enumeration value="AccountNumber" />
    \<xs:enumeration value="ChangedBy" />
    \<xs:enumeration value="CampaignName" />
    \<xs:enumeration value="CampaignId" />
    \<xs:enumeration value="AdGroupName" />
    \<xs:enumeration value="AdGroupId" />
    \<xs:enumeration value="AdTitle" />
    \<xs:enumeration value="AdDescription" />
    \<xs:enumeration value="DisplayUrl" />
    \<xs:enumeration value="Keyword" />
    \<xs:enumeration value="ItemChanged" />
    \<xs:enumeration value="AttributeChanged" />
    \<xs:enumeration value="HowChanged" />
    \<xs:enumeration value="OldValue" />
    \<xs:enumeration value="NewValue" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|AdDescription|[!INCLUDE[reportcolumn_addescription](../reporting-api/includes/reportcolumn-addescription.md)] **Note**: This column will be empty if *ItemChanged* is not Ad.|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)] **Note**: This column will be empty if *ItemChanged* is not Ad , Ad group, or Keyword.|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)] **Note**: This column will be empty if *ItemChanged* is not Ad , Ad group, or Keyword.|
|AdTitle|[!INCLUDE[reportcolumn_adtitle](../reporting-api/includes/reportcolumn-adtitle.md)]|
|AttributeChanged|[!INCLUDE[reportcolumn_attributechanged](../reporting-api/includes/reportcolumn-attributechanged.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|ChangedBy|[!INCLUDE[reportcolumn_changedby](../reporting-api/includes/reportcolumn-changedby.md)]|
|DateTime|[!INCLUDE[reportcolumn_datetime](../reporting-api/includes/reportcolumn-datetime.md)]|
|DisplayUrl|[!INCLUDE[reportcolumn_displayurl](../reporting-api/includes/reportcolumn-displayurl.md)] **Note**: This column will be empty if *ItemChanged* is not Ad.|
|HowChanged|[!INCLUDE[reportcolumn_howchanged](../reporting-api/includes/reportcolumn-howchanged.md)]|
|ItemChanged|[!INCLUDE[reportcolumn_itemchanged](../reporting-api/includes/reportcolumn-itemchanged.md)]|
|Keyword|[!INCLUDE[reportcolumn_keyword](../reporting-api/includes/reportcolumn-keyword.md)] **Note**: This column will be empty if *ItemChanged* is not Keyword.|
|NewValue|[!INCLUDE[reportcolumn_newvalue](../reporting-api/includes/reportcolumn-newvalue.md)]|
|OldValue|[!INCLUDE[reportcolumn_oldvalue](../reporting-api/includes/reportcolumn-oldvalue.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following column.

|Column|
|----------|
|DateTime|

## <a name="remarks"></a>Remarks
The following are the entity types whose change history is reported.

> [!NOTE]
> If the *AttributeChanged* field is blank or empty, and the *HowChanged* field is Added or Deleted, then the contents of the *NewValue* or *OldValue* field represents an element of the entity that was added or deleted, respectively. For example if a keyword is added, the *NewValue* field contains the keyword text.

-   [Account](#account)  
-   [Ad](#ad)  
-   [Ad group](#adgroup)  
-   [Call extension](#callextension)  
-   [Campaign](#campaign)  
-   [Keyword](#keyword)  
-   [Location extension](#locationextension)  
-   [Negative Keyword List](#negativekeywordlist)  
-   [Sitelink extension](#sitelinkextension)  
-   [User](#user)  

### <a name="account"></a>Account
When the *ItemChanged* field's value is Account, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|None (blank)|Refers to the name of the account that was added.<br /><br />**Note:** The value of the corresponding *HowChanged* field is Added.|
|Account|Refers to the name of the account that was changed.|
|Agency contact|Refers to the name of the agency contact.|
|Sales house customer|Refers to the sales house customer.|
|Bill-to customer|Refers to the bill-to customer|
|Financial status|Refers to the financial status|
|Lock status|Refers to the lock status|
|Payment option|Refers to the payment option|
|Preferred bill-to payment method|Refers to the preferred bill-to payment method|
|Preferred language|Refers to the preferred language|
|Sold-to payment method|Sold-to payment method|
|Status|Refers to the account status.|
|Preferred user|Refers to the preferred user|
|Spend limit|Refers to the spend limit|
|Tracking template|Refers to the tracking template of the account.|

### <a name="ad"></a>Ad
When the *ItemChanged* field's value is Ad, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|None (blank)|Refers to the title of the ad that was added.<br /><br />**Note:** The value of the corresponding *HowChanged* field is Added.|
|Ad text|Refers to the description of the ad copy.|
|Ad title|Refers to the title of the ad that was changed.|
|Custom parameters|Refers to the custom parameters of the ad.|
|Destination URL|Refers to the destination URL of the ad.|
|Display URL|Refers to the display URL of the ad.|
|Editorial status|Refers to the editorial status of the ad.<br /><br />**Note:** If the ad is pending offline editorial review, then within a downloaded change history report the editorial status is represented as either *Pending – Active* or *Pending – Inactive*. For more information, see [Entities and Delivery Status](https://msdn.microsoft.com/library/bing-ads-editorial-guide.aspx#entitydeliverystatus).|
|Final URL|Refers to the Final URL of the ad.|
|Mobile URL|Refers to the Final Mobile URL of the ad.|
|Status|Refers to the delivery status of the ad.<br /><br />**Note:** If reporting a deleted ad,  the *ItemChanged* field is Status, the *HowChanged* field is Changed, and the *NewValue* field is Deleted.|
|Tracking template|Refers to the tracking template of the ad.|

### <a name="adgroup"></a>Ad group
When the *ItemChanged* field's value is Ad group, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|None (blank)|Refers to the name of the ad group that was added.<br /><br />**Note:** The value of the corresponding *HowChanged* field is Added.|
|Ad group|Refers to the name of the ad group that was changed.|
|Advanced location targeting|Refers to intent option of the location target that is associated with the ad group.|
|Age|Refers to the age target.|
|Custom parameters|Refers to the custom parameters of the ad group.|
|Day|Refers to the day target that was deprecated after Bing Ads API version 9.|
|Default broad match bid|Refers to the default broad match bid|
|Default content match bid|Refers to the default content match bid|
|Default exact match bid|Refers to the default exact match bid|
|Default phrase match bid|Refers to the default phrase match bid|
|Device|Refers to the defers to the device target.|
|Distance|Refers to the distance of the radius target.|
|End date|Refers to the scheduled end date for the ad group.|
|End time|Refers to the combined To Hour and To Minute of the DayTime target. The bid adjustment is also included in this field, delimited from the time by a single vertical bar character. |
|Gender|Refers to the gender target.|
|Hour|Refers to the hour target that was deprecated after Bing Ads API version 9.|
|Location|Refers to the location target.|
|Location exclusion|Refers to excluding locations from a location target.|
|Medium|Refers to the Search or Content ad distribution.|
|Negative keyword|Refers to a negative keyword associated with the ad group.<br /><br />**Note:** Updates to negative keywords are reported as a Removed and Added change in two rows. The Removed record corresponds to the old value, and the Added record reflects the new value.|
|Pause status|Refers to the any of the paused states of the ad group.|
|Product group|The product conditions of a product group are delimited from each other by a backward slash ('\'), and delimited from the bid by a single space character.|
|Site Exclusion|Refers to the ad group’s negative site URLs. An ad group can have multiple site exclusions, and each site exclusion is represented separately in its own report row.|
|Start time|Refers to the combined From Hour and From Minute of the DayTime target. The bid adjustment is also included in this field, delimited from the time by a single vertical bar character. |
|Status|Refers to the delivery status of the ad group.<br /><br />**Note:** If reporting a deleted ad group,  the *ItemChanged* field is Status, the *HowChanged* field is Changed, and the *NewValue* field is Deleted.|
|Targeted days|Refers day of the DayTime target. The bid adjustment is also included in this field, delimited from the day by a single vertical bar character. |
|Tracking template|Refers to the tracking template of the ad group.|

### <a name="callextension"></a>Call extension
When the *ItemChanged* field's value is Call extension, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|Association|Refers to the association of a call extension with an entity.<br /><br />For example if the extension is associated with a campaign, *CampaignName* field's value is the name of the associated campaign, the *ItemChanged* field's value is Call extension, the *AttributeChanged* field's value is Association, and the *HowChanged* field's value is Added.|
|Country/region|Refers to the country/region of the call extension.|
|Phone Number|Refers to the phone number of the call extension.|
|Show website or phone|Refers to whether the website should be displayed  with the phone number of the call extension. Possible values in the *OldValue* and *NewValue* columns are Phone and Website and phone.|
|Use forward number|Refers to whether forwarding is set up for the call extension. Possible values in the *OldValue* and *NewValue* columns are No and Yes.|

### <a name="campaign"></a>Campaign
When the *ItemChanged* field's value is Campaign, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|None (blank)|Refers to the name of the campaign that was added.<br /><br />**Note:** The value of the corresponding *HowChanged* field is Added.|
|Advanced location targeting|Refers to intent option of the location target that is associated with the campaign.|
|Age|Refers to the age target.|
|Budget type|Refers to the campaign budget type.<br /><br />Possible values in the *OldValue* and *NewValue* columns are as follows:<br /><br />- Value of Daily target (accelerated) corresponds to the [!INCLUDE[brand](../reporting-api/includes/brand.md)] web application Daily Accelerated setting.<br /><br />- Value of Daily target (standard) corresponds to the [!INCLUDE[brand](../reporting-api/includes/brand.md)] web application Daily Standard setting.<br /><br />- Value of Monthly (open) corresponds to the [!INCLUDE[brand](../reporting-api/includes/brand.md)] web application Monthly setting.|
|Campaign priority|Refers to the priority of a Bing Shopping campaign.|
|Custom parameters|Refers to the custom parameters of the campaign.|
|Daily budget|Refers to the campaign daily budget amount.|
|Day|Refers to the day target that was deprecated after Bing Ads API version 9.|
|Device|Refers to the device target.|
|Distance|Refers to the distance of the radius target.|
|End date|Refers to the scheduled end date for the ad group.|
|End time|Refers to the combined To Hour and To Minute of the DayTime target. The bid adjustment is also included in this field, delimited from the time by a single vertical bar character. |
|Gender|Refers to the gender target.|
|Hour|Refers to the hour target that was deprecated after Bing Ads API version 9.|
|IP exclusion|Refers to the IP exclusions created via the [!INCLUDE[brand](../reporting-api/includes/brand.md)] web application.|
|Location|Refers to the location target.|
|Location exclusion|Refers to excluding locations from a location target.|
|Monthly budget|Refers to the campaign monthly budget amount.|
|Name|Refers to the name of the campaign that was changed.|
|Negative keyword|Refers to a negative keyword associated with the campaign.<br /><br />**Note:** Updates to negative keywords are reported as a Removed and Added change in two rows. The Removed record corresponds to the old value, and the Added record reflects the new value.|
|Pause status|Refers to the any of the paused states of the campaign.<br /><br />Possible values in the *OldValue**NewValue* columns are Budget Paused and Not paused.|
|Product flter|Refers to the product scope or condition of a Bing Shopping campaign. A Bing Shopping campaign can have multiple product conditions, and each condition is represented separately in its own report row.|
|Site Exclusion|Refers to the campaign’s negative site URLs. A campaign can have multiple site exclusions, and each site exclusion is represented separately in its own report row.|
|Start date|For internal use.|
|Start time|Refers to the combined From Hour and From Minute of the DayTime target. The bid adjustment is also included in this field, delimited from the time by a single vertical bar character. |
|Status|Refers to the delivery status of the campaign.<br /><br />**Note:** If reporting a deleted campaign,  the *ItemChanged* field is Status, the *HowChanged* field is Changed, and the *NewValue* field is Deleted.|
|Targeted days|Refers day of the DayTime target. The bid adjustment is also included in this field, delimited from the day by a single vertical bar character. |
|Tracking template|Refers to the Tracking template of the campaign.|

### <a name="keyword"></a>Keyword
When the *ItemChanged* field's value is Keyword, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|None (blank)|Refers to the text of the keyword that was added.<br /><br />**Note:** The value of the corresponding *HowChanged* field is Added.|
|Broad match bid|Refers to the broad match bid amount for the keyword.|
|Content match bid|Refers to the content match bid amount for the keyword.|
|Custom parameters|Refers to the custom parameters of the keyword.|
|Editorial status|Refers to the editorial status of the keyword.<br /><br />**Note:** If the keyword is pending offline editorial review, then within a downloaded change history report the editorial status is represented as either *Pending – Active* or *Pending – Inactive*. For more information, see [Entities and Delivery Status](https://msdn.microsoft.com/library/bing-ads-editorial-guide.aspx#entitydeliverystatus).|
|Exact match bid|Refers to the exact match bid amount for the keyword.|
|Final URL|Refers to the Final URL of the keyword.|
|Mobile URL|Refers to the Final Mobile URL of the keyword.|
|Match type|Refers to the bid match type for the keyword.<br /><br />**Note:** The bid match type cannot be updated using [!INCLUDE[brand](../reporting-api/includes/brand.md)] API; however, it is possible to change the bid match type using the [!INCLUDE[brand](../reporting-api/includes/brand.md)] web application.|
|Phrase match bid|Refers to the phrase match bid amount for the keyword.|
|Status|Refers to the delivery status of the keyword.<br /><br />**Note:** If reporting a deleted keyword,  the *ItemChanged* field is Status, the *HowChanged* field is Changed, and the *NewValue* field is Deleted.|
|Tracking template|Refers to the tracking template of the keyword.|

### <a name="locationextension"></a>Location extension
When the *ItemChanged* field's value is Location extension, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|Association|Refers to the association of a location extension with an entity.<br /><br />For example if the extension is associated with a campaign, *CampaignName* field's value is the name of the associated campaign, the *ItemChanged* field's value is Location extension, the *AttributeChanged* field's value is Association, and the *HowChanged* field's value is Added.|

### <a name="negativekeywordlist"></a>Negative Keyword List
When the *ItemChanged* field's value is Negative Keyword List, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|Association|Refers to the association of a Negative Keyword List with a campaign.<br /><br />For example if the negative keyword list is associated with a campaign, *CampaignName* field's value is the name of the associated campaign, the *ItemChanged* field's value is Negative Keyword List, the *AttributeChanged* field's value is Association, and the *HowChanged* field's value is Added.|
|Negative keyword|Refers to the negative keyword that was added or removed from the negative keyword list.|
|Negative Keyword List Name|Refers to the name of the negative keyword list.|

### <a name="sitelinkextension"></a>Sitelink extension
When the *ItemChanged* field's value is Sitelink extension, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|Association|Refers to the association of a sitelink extension with an entity.<br /><br />For example if the extension is associated with a campaign, *CampaignName* field's value is the name of the associated campaign, the *ItemChanged* field's value is Sitelink extension, the *AttributeChanged* field's value is Association, and the *HowChanged* field's value is Added.|
|Custom parameters|Refers to the custom parameters of a sitelink.|
|Destination URL|Refers to the destination URL of the sitelink extension.|
|Display Text|Refers to the display text of the sitelink extension.|
|Final URL|Refers to the Final URL of a sitelink.|
|Mobile URL|Refers to the Final Mobile URL of a sitelink.|
|Tracking template|Refers to the tracking template of a sitelink.|

### <a name="user"></a>User
When the *ItemChanged* field's value is User, change history for the following attributes are available.

|Attribute Changed|Description|
|---------------------|---------------|
|None (blank)|Refers to the user name of the user that was added.<br /><br />**Note:** The value of the corresponding *HowChanged* field is Added.|
|Code|For internal use.|
|Email|Refers to the contact email address of the user.|
|First name|Refers to the first name of the user.|
|Last name|Refers to the last name of the user.|
|Status|Refers to the status of the user.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[SearchCampaignChangeHistoryReportRequest](../reporting-api/searchcampaignchangehistoryreportrequest-data-object.md)  

