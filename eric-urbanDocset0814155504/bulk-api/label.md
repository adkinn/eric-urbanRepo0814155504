---
title: "Label"
ms.custom: ""
ms.date: "07/28/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: baa4eb66-5ca9-49c1-932d-18a01c5ac82a
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
---
# Label
Defines a label that can be uploaded and downloaded in a bulk file.

Labels let you organize campaigns, ad groups, ads, and keywords into groups based on whatever is important to you. You can then filter and run reports on your labels to get the data that is most meaningful to you.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../bulk-api/includes/pilot-comingsoon.md)]

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Label* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Color](#color)
- [Client Id](#clientid)
- [Description](#description)
- [Id](#id)
- [Label](#label)
- [Modified Time](#modifiedtime)
- [Status](#status)

You can download all fields of the *Label* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *Labels* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would add a new label. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Name,Description,Label,Color
Format Version,,,,,,,,5,,,
Label,,-22,,,,ClientIdGoesHere,,,Label Description,Label Name,#FFFFFF
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkLabel* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkLabel
var bulkLabel = new BulkLabel
{
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",

    // Map properties in the Bulk file to the 
    // Label object of the Campaign Management service.
    Label = new Label
    {
        // 'Color' column header in the Bulk file
        ColorCode = "#FFFFFF",
        // 'Description' column header in the Bulk file
        Description = "Label Description",
        // 'Id' column header in the Bulk file
        Id = labelIdKey,
        // 'Label' column header in the Bulk file
        Name = "Label Name " + DateTime.UtcNow
    },

    // 'Status' column header in the Bulk file
    Status = Status.Active
};

uploadEntities.Add(bulkLabel);

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

### <a name="color"></a>Color
The label color as a hexadecimal code.

The hexadecimal value must have the '#' prefix. For example you can use the value of *#FFFFFF* for a white label.

The color can be viewed in the Bing Ads web application. Your application can display the color or utilize the hexadecimal value to categorize a set of labels.

**Add:** Optional. If you do not specify any color, the value will be assigned at random for each label.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)] You can update the color code but cannot remove it.   
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Read-only  

### <a name="description"></a>Description
The label description.

The label description can be between 1 to 200 characters in length.

**Add:** Optional  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier of the label.

**Add:** Optional. You must either leave this field empty, or specify a negative identifier. A negative identifier set for the label can then be referenced in the *Parent Id* field of dependent record types such as [Campaign Label](../bulk-api/campaign-label.md). This is recommended if you are adding new label and new dependent records in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="label"></a>Label
The label name.

The case-sensitive label name can be between 1 to 80 characters in length, and must be unique across all labels in the account.

**Add:** Required  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Read-only  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="status"></a>Status
The status of the label.

Possible values are *Active* or *Deleted*. 

**Add:** Optional. The default value is *Active*.  
**Update:** [!INCLUDE[update_optional_setting_unchanged](../bulk-api/includes/update-optional-setting-unchanged.md)]    
**Delete:** Required. The Status must be set to *Deleted*.

