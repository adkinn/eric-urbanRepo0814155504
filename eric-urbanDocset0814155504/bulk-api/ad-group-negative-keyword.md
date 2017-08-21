---
title: "Ad Group Negative Keyword"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbb34709-1eba-491d-b8e5-cc015ed1df52
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Group Negative Keyword
Defines a negative keyword assigned to an ad group that can be uploaded and downloaded in a bulk file.

In the bulk schema each of the negative keywords associated with an ad group are represented individually by their own row. For example if an ad group has two negative keywords, they are represented by two *Ad Group Negative Keyword* records in the bulk file with *Status* set to Active.

> [!NOTE]
> The *Ad Group Negative Keyword* can be added and deleted, but cannot be updated.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group Negative Keyword* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Id](#id)
- [Keyword](#keyword)
- [Match Type](#matchtype)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)

You can download all fields of the *Ad Group Negative Keyword* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroupNegativeKeywords* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new ad group negative keyword given a valid ad group ID (*Parent Id*). 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Keyword,Match Type,Name
Format Version,,,,,,,,,,5
Ad Group Negative Keyword,Active,,-1111,,,ClientIdGoesHere,,shoes,Exact,
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroupNegativeKeyword* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAdGroupNegativeKeyword
var bulkAdGroupNegativeKeyword = new BulkAdGroupNegativeKeyword
{
    // 'Parent Id' column header in the Bulk file
    AdGroupId = adGroupIdKey,
    // 'Ad Group' column header in the Bulk file
    AdGroupName = null,
    // 'Campaign' column header in the Bulk file
    CampaignName = null,
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",

    // Map properties in the Bulk file to the 
    // NegativeKeyword object of the Campaign Management service.
    NegativeKeyword = new NegativeKeyword
    {
        // 'Id' column header in the Bulk file
        Id = null,
        // 'Match Type' column header in the Bulk file
        MatchType = MatchType.Exact,
        // 'Text' column header in the Bulk file
        Text = "shoes"
    },
                
    // 'Status' column header in the Bulk file
    Status = Status.Active
};

uploadEntities.Add(bulkAdGroupNegativeKeyword);

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

### <a name="adgroup"></a>Ad Group
The name of the ad group that contains the negative keyword.

**Add:** Read-only and Required  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.  
**Delete:** Read-only and Required  

> [!NOTE]
> For add and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="campaign"></a>Campaign
The name of the campaign that contains the ad group and negative keyword.

**Add:** Read-only  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.  
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the negative keyword.

**Add:** Read-only  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.  
**Delete:** Read-only and Required  

### <a name="keyword"></a>Keyword
The negative keyword text. 

The text can contain a maximum of 100 characters.

**Add:** Required  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.    
**Delete:** Read-only

### <a name="matchtype"></a>Match Type
The type of match to compare the negative keyword and the user's search term.

The supported match type values for a negative keyword are *Phrase* and *Exact*.

**Add:** Required  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.    
**Delete:** Read-only

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the ad group that contains the negative keyword.

This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record.

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are adding new negative keywords to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.  
**Delete:** Read-only  

> [!NOTE]
> For add and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="status"></a>Status
Represents the association status between the ad group and the negative keyword.

If the negative keyword is associated with the ad group, this  field's value is *Active*.

Possible values are *Active* or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.    
**Delete:** Required. The Status must be set to *Deleted*. To delete a specific negative keyword, you must upload the *Status*, *Id*, and *Parent Id*. To delete all negative keywords for the ad group, you only need to upload the *Status* and *Parent Id* in a single record. Then optionally you can add new negative keyword records to replace the deleted set.

