---
title: "In Market Audience"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1fe8601c-5dfe-474d-8067-38ba275a6f6e
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# In Market Audience
Defines an in-market audience that can be downloaded in a bulk file. 

> [!NOTE]
> Bulk upload is not supported. You cannot add, update, or delete an in-market audience using the Bing Ads API.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *In Market Audience* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Audience](#audience)
- [Client Id](#clientid)
- [Description](#description)
- [Id](#id)
- [Membership Duration](#membershipduration)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Scope](#scope)
- [Status](#status)

You can download all fields of the *In Market Audience* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *InMarketAudiences* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following is a Bulk CSV example download for in-market audience. 

```csv
Type,Status,Id,Parent Id,Client Id,Modified Time,Name,Description,Membership Duration,Scope,Audience,Remarketing Targeting Setting,
Format Version,,,,,,5,,,,,
In Market Audience,Active,IdHere,ParentIdHere,ClientIdGoesHere,,,In Market Audience Description,30,Account,In Market Audience,,
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to download the *BulkInMarketAudience* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
// Map properties in the Bulk file to the BulkInMarketAudience
var bulkInMarketAudience = new BulkInMarketAudience
{
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",

    // Map properties in the Bulk file to the 
    // InMarketAudience object of the Campaign Management service.
    InMarketAudience = new InMarketAudience
    {
        // 'Description' column header in the Bulk file
        Description = "In Market Audience Description",
        // 'Id' column header in the Bulk file
        Id = InMarketAudienceIdKey,
        // 'Membership Duration' column header in the Bulk file
        MembershipDuration = 30,
        // 'Audience' column header in the Bulk file
        Name = "In Market Audience",
        // 'Parent Id' column header in the Bulk file
        ParentId = accountIdKey,
        // 'Scope' column header in the Bulk file
        Scope = EntityScope.Account,
    },
                
    // 'Status' column header in the Bulk file
    Status = Status.Active
};
```

### <a name="audience"></a>Audience
The name of the in-market audience.

The name can contain a maximum of 128 characters

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported  

### <a name="description"></a>Description
The description of the in-market audience. Use a description to help you remember what audience you are targeting with this in-market audience.

The description can contain a maximum of 1,024 characters.

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported  

### <a name="id"></a>Id
The system generated identifier of the in-market audience.

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported  

### <a name="membershipduration"></a>Membership Duration
When you create an in-market audience in the Bing Ads web application, you can specify how far back in time Bing Ads should look for actions that match your in-market audience definition in order to add people to your list.

The mimimum duration is 1 day and the maximum duration allowed is 180 days.

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported  

### <a name="parentid"></a>Parent Id
The system generated identifier of the account or customer. If the *Scope* is set to *Account*, this is the account ID, and otherwise it is the customer ID.

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported  

### <a name="scope"></a>Scope
Scope defines what accounts can use this in-market audience. If scope is set to *Account*, the in-market audience can only be associated with ad groups within one specified account (*Parent Id*). If scope is set to *Customer*, the in-market audience can be associated with any ad groups across all of the customer's accounts.

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported  

### <a name="status"></a>Status
The in-market audience status.

Possible values are *Active* or *Deleted*. 

**Add:** Not supported  
**Update:** Not supported    
**Delete:** Not supported

