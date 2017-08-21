---
title: "Ad Group Label"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e30d2a5-10fd-49b8-8b83-0ddc43e57128
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
---
# Ad Group Label
Defines an association record between an [Ad Group](../bulk-api/ad-group.md) and a [Label](../bulk-api/label.md) that can be uploaded and downloaded in a bulk file. To upload or download the ad group or label, use the [Ad Group](../bulk-api/ad-group.md) or [Label](../bulk-api/label.md) record.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group Label* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)

You can download all fields of the *Ad Group Label* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroupLabels* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would apply a label to an ad group if the valid *Id* and *Parent Id* are provided. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Name,Description,Label,Color
Format Version,,,,,,,,5,,,
Ad Group Label,,-22,-1111,,,ClientIdGoesHere,,,,,
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroupLabel* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAdGroupLabel
var bulkAdGroupLabel = new BulkAdGroupLabel
{
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",

    // Map properties in the Bulk file to the 
    // LabelAssociation object of the Campaign Management service.
    LabelAssociation = new LabelAssociation
    {
        // 'Parent Id' column header in the Bulk file
        EntityId = adGroupIdKey,
        // 'Id' column header in the Bulk file
        LabelId = labelIdKey
    },

    // 'Status' column header in the Bulk file
    Status = Status.Active
};

uploadEntities.Add(bulkAdGroupLabel);

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
The name of the ad group where this label is applied or removed.  

**Add:** Read-only  
**Delete:** Read-only  

> [!NOTE]
> For add and delete, you must specify either the *Parent Id* or both of the *Ad Group* and *Campaign* fields. For bulk download the *Ad Group* and *Campaign* fields are not returned.

### <a name="campaign"></a>Campaign
The name of the campaign that contains the ad group where this label is applied or removed.

**Add:** Read-only  
**Delete:** Read-only  

> [!NOTE]
> For add and delete, you must specify either the *Parent Id* or both of the *Ad Group* and *Campaign* fields. For bulk download the *Ad Group* and *Campaign* fields are not returned.

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Delete:** Read-only  

### <a name="id"></a>Id
The identifier of the label that is applied or removed from the ad group.

This bulk field maps to the *Id* field of the [Label](../bulk-api/label.md) record. 

**Add:** Read-only and Required. You must either specify an existing label identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Label](../bulk-api/label.md) record. This is recommended if you are applying new labels to ad groups in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Delete:** Read-only and Required  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The identifier of the ad group where this label is applied or removed.
	
This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record. 

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are applying labels to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Delete:** Read-only and Required  

> [!NOTE]
> For add and delete, you must specify either the *Parent Id* or both of the *Ad Group* and *Campaign* fields. For bulk download the *Ad Group* and *Campaign* fields are not returned.

### <a name="status"></a>Status
Represents the applied status between the ad group and the label. 

Possible values are *Active* and *Deleted*. If the label is applied to the ad group, this field's value is *Active*.

**Add:** Read-only  
**Delete:** Required. The Status must be set to *Deleted*. 
