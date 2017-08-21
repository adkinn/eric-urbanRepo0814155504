---
title: "Ad Group Negative Remarketing List Association"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cf64ac9-d83c-47b4-b603-3a9e0de089ee
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Group Negative Remarketing List Association
Defines an Ad Group Negative Remarketing List Association that can be uploaded and downloaded in a bulk file. 

[!INCLUDE[guide_uet](../bulk-api/includes/guide-uet.md)]

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group Negative Remarketing List Association* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Audience](#audience)
- [Audience Id](#audienceid)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)

You can download all fields of the *Ad Group Negative Remarketing List Association* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroupNegativeRemarketingListAssociations* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new Ad Group Negative Remarketing List Association given a valid ad group ID (*Parent Id*). 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Bid Adjustment,Name,Audience Id,Audience,Remarketing Targeting Setting
Format Version,,,,,,,,,5,,,
Ad Group Negative Remarketing List Association,Paused,,-1111,,,ClientIdGoesHere,,,,RemarketingListIdHere,My Remarketing List,
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroupNegativeRemarketingListAssociation* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 


```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAdGroupNegativeRemarketingListAssociation
var bulkAdGroupNegativeRemarketingListAssociation = new BulkAdGroupNegativeRemarketingListAssociation
{
    // 'Ad Group' column header in the Bulk file
    AdGroupName = null,

    // Map properties in the Bulk file to the 
    // NegativeAdGroupCriterion object of the Campaign Management service.
    NegativeAdGroupCriterion = new NegativeAdGroupCriterion
    {
        // 'Parent Id' column header in the Bulk file
        AdGroupId = adGroupIdKey,
        Criterion = new AudienceCriterion
        {
            // 'Audience Id' column header in the Bulk file
            AudienceId = remarketingListIdKey,
        },
        // 'Id' column header in the Bulk file
        Id = null,
        // 'Status' column header in the Bulk file
        Status = AdGroupCriterionStatus.Paused
    },
    // 'Campaign' column header in the Bulk file
    CampaignName = null,
    // 'Client Id' column header in the Bulk file
    ClientId = "ClientIdGoesHere",
    // 'Audience' column header in the Bulk file
    RemarketingListName = null,
};

uploadEntities.Add(bulkAdGroupNegativeRemarketingListAssociation);

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
The name of the ad group that is associated with the remarketing list.

**Add:** Read-only and Required  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.


### <a name="audience"></a>Audience
The name of the remarketing list.

This bulk field maps to the *Audience* field of the [Remarketing List](../bulk-api/remarketing-list.md) record.

**Add:** Read-only and Required for some use cases. You must either specify the *Audience* or *Audience Id* field. If you are adding new Ad Group Negative Remarketing List Associations with new remarketing lists in the same Bulk file, and if you do not set the *Audience Id* field, then this *Audience* field must be set as a logical key to the same value as the *Audience* field of the [Remarketing List](../bulk-api/remarketing-list.md) record. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only    
**Delete:** Read-only  

### <a name="audienceid"></a>Audience Id
The Bing Ads identifier of the remarketing list associated with the ad group.

This bulk field maps to the *Id* field of the [Remarketing List](../bulk-api/remarketing-list.md) record.

**Add:** Read-only and Required for some use cases. You must either specify the *Audience* or *Audience Id* field. If you set the *Audience Id* field, you must either specify an existing remarketing list identifier or specify a negative identifier that is equal to the *Id* field of the parent [Remarketing List](../bulk-api/remarketing-list.md) record. If the *Audience Id* field is not set, then you must set the *Audience* field as a logical key to the same value as the *Audience* field of the [Remarketing List](../bulk-api/remarketing-list.md) record. Any of these options are recommended if you are adding new Ad Group Negative Remarketing List Associations with new remarketing lists in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only    
**Delete:** Read-only  

### <a name="campaign"></a>Campaign
The name of the campaign that contains the ad group.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Read-only  

### <a name="id"></a>Id
The system generated identifier for the association between an ad group and remarketing list.

**Add:** Read-only  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The system generated identifier of the ad group that is associated to the remarketing list.

This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record.

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are associating remarketing lists to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only  
**Delete:** Read-only  

> [!NOTE]
> For add, update, and delete, you must specify either the *Parent Id* or *Ad Group* field.

### <a name="status"></a>Status
The association status. 

Possible values are *Active*, *Paused*, or *Deleted*. 

**Add:** Optional. The default status value is *Active*.   
**Update:** Optional    
**Delete:** Required. The Status must be set to *Deleted*.

