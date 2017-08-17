---
title: "Dynamic Search Ad Label"
ms.custom: ""
ms.date: "07/28/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87e2719b-ad7c-4f05-b60d-bd7c45747d6b
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
---
# Dynamic Search Ad Label
Defines an association record between a [Dynamic Search Ad](../bulk-api/dynamic-search-ad.md) and a [Label](../bulk-api/label.md) that can be uploaded and downloaded in a bulk file. To upload or download the dynamic search ad or label, use the [Dynamic Search Ad](../bulk-api/dynamic-search-ad.md) or [Label](../bulk-api/label.md) record.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Dynamic Search Ad Label* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Client Id](#clientid)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)

You can download all fields of the *Dynamic Search Ad Label* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *DynamicSearchAdLabels* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would apply a label to a dynamic search ad if the valid *Id* and *Parent Id* are provided. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Name,Description,Label,Color
Format Version,,,,,,,,5,,,
Dynamic Search Ad Label,,-22,-11112,,,ClientIdGoesHere,,,,,
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkDynamicSearchAdLabel* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkDynamicSearchAdLabel
var bulkDynamicSearchAdLabel = new BulkDynamicSearchAdLabel
{
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",

    // Map properties in the Bulk file to the 
    // LabelAssociation object of the Campaign Management service.
    LabelAssociation = new LabelAssociation
    {
        // 'Parent Id' column header in the Bulk file
        EntityId = dynamicSearchAdIdKey,
        // 'Id' column header in the Bulk file
        LabelId = labelIdKey
    },

    // 'Status' column header in the Bulk file
    Status = Status.Active
};

uploadEntities.Add(bulkDynamicSearchAdLabel);

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
**Delete:** Read-only  

### <a name="id"></a>Id
The identifier of the label that is applied or removed from the dynamic search ad.

This bulk field maps to the *Id* field of the [Label](../bulk-api/label.md) record. 

**Add:** Read-only and Required. You must either specify an existing label identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Label](../bulk-api/label.md) record. This is recommended if you are applying new labels to dynamic search ads in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Delete:** Read-only and Required  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The identifier of the dynamic search ad where this label is applied or removed.
	
This bulk field maps to the *Id* field of the [Dynamic Search Ad](../bulk-api/dynamic-search-ad.md) record. 

**Add:** Read-only and Required. You must either specify an existing dynamic search ad identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Dynamic Search Ad](../bulk-api/dynamic-search-ad.md) record. This is recommended if you are applying labels to a new dynamic search ad in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Delete:** Read-only and Required  

### <a name="status"></a>Status
Represents the applied status between the dynamic search ad and the label. 

Possible values are *Active* and *Deleted*. If the label is applied to the dynamic search ad, this field's value is *Active*.

**Add:** Read-only  
**Delete:** Required. The Status must be set to *Deleted*. 
