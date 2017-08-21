---
title: "Shared Negative Keyword"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4067f745-876d-4616-9948-cec381bb84c9
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Shared Negative Keyword
Defines a negative keyword that is shared in a negative keyword list and can be downloaded and uploaded in a bulk file.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Shared Negative Keyword* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Client Id](#clientid)
- [Id](#id)
- [Keyword](#keyword)
- [Match Type](#matchtype)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)

You can download all fields of the *Shared Negative Keyword* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *SharedNegativeKeywords* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new negative keyword to a negative keyword list given a valid negative keyword list ID (*Parent Id*). 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Keyword,Match Type,Name
Format Version,,,,,,,,,,5
Shared Negative Keyword,Active,,-19,,,ClientIdGoesHere,,shoes,Exact,
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkSharedNegativeKeyword* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkSharedNegativeKeyword
var bulkSharedNegativeKeyword = new BulkSharedNegativeKeyword
{
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

    // 'Parent Id' column header in the Bulk file
    NegativeKeywordListId = negativeKeywordListIdKey,

    // 'Status' column header in the Bulk file
    Status = Status.Active
};

uploadEntities.Add(bulkSharedNegativeKeyword);

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
The system generated identifier of the negative keyword list that contains the negative keyword.

This bulk field maps to the *Id* field of the [Negative Keyword List](../bulk-api/negative-keyword-list.md) record.

**Add:** Read-only and Required. You must either specify an existing negative keyword list identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Negative Keyword List](../bulk-api/negative-keyword-list.md) record. This is recommended if you are adding new negative keywords to a new negative keyword list in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.  
**Delete:** Read-only  

### <a name="status"></a>Status
Represents the association status between the negative keyword list and the negative keyword.

If the negative keyword is associated with the negative keyword list, this  field's value is *Active*.

Possible values are *Active* or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** Not applicable. A negative keyword can be added and deleted, but cannot be updated.    
**Delete:** Required. The Status must be set to *Deleted*.

