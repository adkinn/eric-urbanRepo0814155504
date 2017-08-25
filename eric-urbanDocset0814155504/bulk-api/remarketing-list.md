---
title: "Remarketing List"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f510ef7-64db-478a-ba26-d5bbc5a4086d
caps.latest.revision: 20
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Remarketing List
Defines a remarketing list that can be downloaded and uploaded in a bulk file. 

[!INCLUDE[guide_uet](../bulk-api/includes/guide-uet.md)]

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Remarketing List* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Audience](#audience)
- [Client Id](#clientid)
- [Description](#description)
- [Id](#id)
- [Membership Duration](#membershipduration)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Remarketing Rule](#remarketingrule)
- [Scope](#scope)
- [Status](#status)
- [UET Tag Id](#uettagid)

You can download all fields of the *Remarketing List* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *RemarketingLists* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new remarketing list. 

```csv
Type,Status,Id,Parent Id,Client Id,Modified Time,Name,Description,Membership Duration,Scope,UET Tag Id,Audience,Remarketing Targeting Setting,Remarketing Rule
Format Version,,,,,,5,,,,,,,
Remarketing List,Active,-10,ParentIdHere,ClientIdGoesHere,,,New list with CustomEventsRule,30,Account,TagIdHere,Remarketing List with CustomEventsRule,,CustomEvents(Action Equals play) and (Category Equals video) and (Label Equals trailer) and (Value Equals 5.00)
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkRemarketingList* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkRemarketingList
var bulkRemarketingList = new BulkRemarketingList
{
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",

    // Map properties in the Bulk file to the 
    // RemarketingList object of the Campaign Management service.
    RemarketingList = new RemarketingList
    {
        // 'Description' column header in the Bulk file
        Description = "New list with CustomEventsRule",
        // 'Id' column header in the Bulk file
        Id = remarketingListIdKey,
        // 'Membership Duration' column header in the Bulk file
        MembershipDuration = 30,
        // 'Audience' column header in the Bulk file
        Name = "Remarketing List with CustomEventsRule " + DateTime.UtcNow,
        // 'Parent Id' column header in the Bulk file
        ParentId = accountIdKey,
        // 'Remarketing Rule' column header in the Bulk file
        Rule = new CustomEventsRule
        {
            // The rule definition is translated to the following logical expression: 
            // CustomEvents(Category Equals video) and (Action Equals play) and (Label Equals trailer) 
            // and (Value Equals 5)
            Action = "play",
            ActionOperator = StringOperator.Equals,
            Category = "video",
            CategoryOperator = StringOperator.Equals,
            Label = "trailer",
            LabelOperator = StringOperator.Equals,
            Value = 5.00m,
            ValueOperator = NumberOperator.Equals,
        },
        // 'Scope' column header in the Bulk file
        Scope = EntityScope.Account,
        // 'UET Tag Id' column header in the Bulk file
        TagId = tagIdKey
    },
                
    // 'Status' column header in the Bulk file
    Status = Status.Active
};

uploadEntities.Add(bulkRemarketingList);

var entityUploadParameters = new EntityUploadParameters
{
    Entities = uploadEntities,
    ResponseMode = ResponseMode.ErrorsAndResults,
    ResultFileDirectory = FileDirectory,
    ResultFileName = DownloadFileName,
    OverwriteResultFile = true,
};

var uploadResultEntities = (await BulkService.UploadEntitiesAsync(entityUploadParameters)).ToList();
```

### <a name="audience"></a>Audience
The name of the remarketing list.

The name can contain a maximum of 128 characters

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Read-only  

### <a name="description"></a>Description
The description of the remarketing list. Use a description to help you remember what audience you are targeting with this remarketing list.

The description can contain a maximum of 1,024 characters.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the remarketing list.

**Add:** Read-only  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="membershipduration"></a>Membership Duration
When you create a remarketing list, you can specify how far back in time Bing Ads should look for actions that match your remarketing list definition in order to add people to your list.

The mimimum duration is 1 day and the maximum duration allowed is 180 days.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the account or customer. If the *Scope* is set to *Account*, this is the account ID, and otherwise it is the customer ID.

**Add:** Optional  
**Update:** Read-only. You cannot change the parent ID.  
**Delete:** Read-only  

### <a name="remarketingrule"></a>Remarketing Rule
A rule template includes conditions used to determine who to add to your remarketing list.

You can choose one of the four types of rules to target different audiences: *CustomEventsRule*, *PageVisitorsRule*, *PageVisitorsWhoDidNotVisitAnotherPageRule*, and *PageVisitorsWhoVisitedAnotherPageRule*. For details on the format of each rule in the bulk file, see the [CustomEvents](#customevents), [PageVisitors](#PageVisitors), [PageVisitorsWhoDidNotVisitAnotherPage](#PageVisitorsWhoDidNotVisitAnotherPage), and [PageVisitorsWhoVisitedAnotherPage](#PageVisitorsWhoVisitedAnotherPage) rule template remarks sections below.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] If you want to keep any of the previous rule items, then you must explicitly set them again during update. You can choose to change the type of rule during update.    
**Delete:** Read-only  

### <a name="scope"></a>Scope
Scope defines what accounts can use this remarketing list. If scope is set to *Account*, the remarketing list can only be associated with ad groups within one specified account (*Parent Id*). If scope is set to *Customer*, the remarketing list can be associated with any ad groups across all of the customer's accounts.

**Add:** Required  
**Update:** Read-only. You cannot change the scope.    
**Delete:** Read-only  

### <a name="status"></a>Status
The remarketing list status.

Possible values are *Active* or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** Read-only    
**Delete:** Required. The Status must be set to *Deleted*.

### <a name="uettagid"></a>UET Tag Id
The Bing Ads identifier of the Universal Event Tracking (UET) tag that is used with the remarketing list.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

	
## <a name="CustomEvents"></a>CustomEvents Rule Template
For the *CustomEvents* rule, you must include one or more of the following conditional event operator pairs: (*ActionOperator* and *Action*), (*CategoryOperator* and *Category*), (*LabelOperator* and *Label*), (*ValueOperator* and *Value*). If more than one condition is specified, the conditions are joined using the logical *AND* operator. In other words the visitor will only be added to your remarketing list if all of the specified rule conditions are met.

For example let's say that the following custom events are set as a logical expression in the bulk file:

*CustomEvents(Category Equals video) and (Action Equals play) and (Label Equals trailer) and (Value Equals 5)*

Evaluation of the logical expression determines who will be added to the remarketing list.


## <a name="PageVisitors"></a>PageVisitors Rule Template
For the *PageVisitors* rule, you must include one or more rule item groups. With each rule item group, the rule item conditions for the same page are joined using the logical *AND* operator. Then, each result from the list of rule item groups are joined using the logical *OR* operator. In other words the user will be added to your remarketing list if all of the specified rule item conditions within any one of the rule item groups are met.

For example let's say that the following rule item groups are set as a logical expression in the bulk file:

*PageVisitors((Url Contains X) and (ReferrerUrl DoesNotContain Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))*

Evaluation of the logical expression determines which of the following example users will be added to the remarketing list.

|User|Url Visited|Referrer Url|Added to List|
|-----------|---------------|-------------|-------------|
|User 1|A<br/>|X|Yes. Evaluation of the logical expression results as *True*.<br/><br/>*((Url Contains X) and (ReferrerUrl DoesNotContain Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))*<br/><br/>*(False and True) or (True) or (False)*<br/><br/>*False or True or False*<br/><br/>*True*|
|User 2|B<br/>|Y|No. Evaluation of the logical expression results as *False*.<br/><br/>*((Url Contains X) and (ReferrerUrl DoesNotContain Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))*<br/><br/>*(False and True) or (False) or (False)*<br/><br/>*False or False or False*<br/><br/>*False*|
|User 3|C<br/>|Z|Yes. Evaluation of the logical expression results as *True*.<br/><br/>*((Url Contains X) and (ReferrerUrl DoesNotContain Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))*<br/><br/>*(False and False) or (True) or (True)*<br/><br/>*False or True or True*<br/><br/>*True*|

## <a name="PageVisitorsWhoDidNotVisitAnotherPage"></a>PageVisitorsWhoDidNotVisitAnotherPage Rule Template
Remarketing rules are conditions used to determine who to add to your remarketing list. For the *PageVisitorsWhoDidNotVisitAnotherPage* rule, you must include one or more rule item groups for the page visited (*IncludeRuleItemGroups*), and you must also include one or more rule item groups for the page that must not have been visited (*ExcludeRuleItemGroups*). 

For each rule item group within *IncludeRuleItemGroups*, the rule item conditions for the same page are joined using the logical *AND* operator. Then, each result from the list of rule item groups are joined using the logical *OR* operator. 

Likewise for each rule item group within *ExcludeRuleItemGroups*, the rule item conditions for the same page are joined using the logical *AND* operator. Then, each result from the list of rule item groups are joined using the logical *OR* operator. Finally, the logical *NOT* operator will be applied to the aggregated result of exclude rule item groups.

In other words the visitor will be added to your remarketing list if any of the include rule item group conditions are met, and none of the exclude rule item group conditions are met.

For example let's say that the following rule item groups are set as a logical expression in the bulk file:

*(((Url Contains X) and (ReferrerUrl DoesNotContain Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))) and not (((Url BeginsWith A) and (ReferrerUrl BeginsWith B)) or ((Url Contains C)))*

Evaluation of the logical expression determines which of the following example users will be added to the remarketing list.

|User|Url Visited|Referrer Url|Added to List|
|-----------|---------------|-------------|-------------|
|User 1|A<br/>|X|Yes. Evaluation of the logical expression results as *True*.<br/><br/>*(((Url Contains X) and (ReferrerUrl DoesNotContain Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))) and not (((Url BeginsWith A) and (ReferrerUrl BeginsWith B)) or ((Url Contains C)))*<br/><br/>*((False and True) or (True) or (False)) and not ((True and False) or (False))*<br/><br/>*(False or True or False) and not (False or False)*<br/><br/>*True and not False*<br/><br/>*True*|
|User 2|B<br/>|Y|Yes. Evaluation of the logical expression results as *True*.<br/><br/>*(((Url Contains X) and (ReferrerUrl DoesNotContain Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))) and not (((Url BeginsWith A) and (ReferrerUrl BeginsWith B)) or ((Url Contains C)))*<br/><br/>*((False and True) or (True) or (False)) and not ((False and False) or (False))*<br/><br/>*(False or True or False) and not (False or False)*<br/><br/>*True and not False*<br/><br/>*True*|
|User 3|C<br/>|Z|No. Evaluation of the logical expression results as *False*.<br/><br/>*(((Url Contains X) and (ReferrerUrl DoesNotContain Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))) and not (((Url BeginsWith A) and (ReferrerUrl BeginsWith B)) or ((Url Contains C)))*<br/><br/>*((False and False) or (True) or (True)) and not ((False and False) or (True))*<br/><br/>*(False or True or True) and not (False or True)*<br/><br/>*True and not True*<br/><br/>*False*|

## <a name="PageVisitorsWhoVisitedAnotherPage"></a>PageVisitorsWhoVisitedAnotherPage Rule Template
Remarketing rules are conditions used to determine who to add to your remarketing list. For the *PageVisitorsWhoVisitedAnotherPage* rule, you must include one or more rule item groups for the page visited (*RuleItemGroups*), and you must also include one or more rule item groups for another page that must have been visited (*AnotherRuleItemGroups*). 

For each rule item group within *RuleItemGroups*, the rule item conditions for the same page are joined using the logical *AND* operator. Then, each result from the list of rule item groups are joined using the logical *OR* operator. 

Likewise for each rule item group within *AnotherRuleItemGroups*, the rule item conditions for the same page are joined using the logical *AND* operator. Then, each result from the list of rule item groups are joined using the logical *OR* operator. 

In other words the visitor will be added to your remarketing list if any of the rule item group conditions are met, and any of the another rule item group conditions are met.

For example let's say that the following rule item groups are set as a logical expression in the bulk file:

*(((Url Contains X) and (ReferrerUrl NotEquals Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))) and (((Url BeginsWith A) and (ReferrerUrl BeginsWith B)) or ((Url Contains C)))*

Evaluation of the logical expression determines which of the following example users will be added to the remarketing list.

|User|Url Visited|Referrer Url|Added to List|
|-----------|---------------|-------------|-------------|
|User 1|A<br/>|X|No. Evaluation of the logical expression results as *False*.<br/><br/>*(((Url Contains X) and (ReferrerUrl NotEquals Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))) and (((Url BeginsWith A) and (ReferrerUrl BeginsWith B)) or ((Url Contains C)))*<br/><br/>*((False and True) or (True) or (False)) and ((True and False) or (False))*<br/><br/>*(False or True or False) and (False or False)*<br/><br/>*True and False*<br/><br/>*False*|
|User 2|B<br/>|Y|No. Evaluation of the logical expression results as *False*.<br/><br/>*(((Url Contains X) and (ReferrerUrl NotEquals Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))) and (((Url BeginsWith A) and (ReferrerUrl BeginsWith B)) or ((Url Contains C)))*<br/><br/>*((False and True) or (True) or (False)) and ((False and False) or (False))*<br/><br/>*(False or True or False) and (False or False)*<br/><br/>*True and False*<br/>*False*<br/>|
|User 3|C<br/>|Z|Yes. Evaluation of the logical expression results as *True*.<br/><br/>*(((Url Contains X) and (ReferrerUrl NotEquals Z)) or ((Url DoesNotBeginWith Y)) or ((ReferrerUrl Equals Z))) and (((Url BeginsWith A) and (ReferrerUrl BeginsWith B)) or ((Url Contains C)))*<br/><br/>*((False and True) or (True) or (True)) and ((False and False) or (True))*<br/><br/>*(False or True or True) and (False or True)*<br/><br/>*True and True*<br/><br/>*True*|
