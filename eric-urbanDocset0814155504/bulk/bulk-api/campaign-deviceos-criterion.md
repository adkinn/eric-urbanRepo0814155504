---
title: "Campaign DeviceOS Criterion"
ms.custom: ""
ms.date: "07/25/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4bcf0ccc-7cf7-41d0-bc5d-6b8428adae39
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Campaign DeviceOS Criterion
Defines a campaign device OS criterion that can be uploaded and downloaded in a bulk file.

When you target by device, you choose to show ads to potential customers when they're using desktops and tablets or smartphones. 

Each device criterion defines a device name for the accompanying criterion bid adjustment. 

The maximum number of device criterions that you can specify per campaign or ad group is three. You must either have three separate criterions for *Computers*, *Smartphones*, and *Tablets*, otherwise no device criterions can exist for the campaign or ad group.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Campaign DeviceOS Criterion* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Bid Adjustment](#bidadjustment)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)
- [Target](#target)

You can download all fields of the *Campaign DeviceOS Criterion* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *CampaignTargetCriterions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would add three new campaign device criterions (one for each device type) if a valid campaign identifier (*Parent Id*) is provided. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Bid Adjustment,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,5,,,,,,,,
Campaign DeviceOS Criterion,Active,,-111,,,ClientIdGoesHere,,Computers,20,,,,,,,,,
Campaign DeviceOS Criterion,,,-111,,,ClientIdGoesHere,,Smartphones,0,,,,,,,,,
Campaign DeviceOS Criterion,,,-111,,,ClientIdGoesHere,,Tablets,0,,,,,,,,,
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkCampaignDeviceOSCriterion* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 

```csharp
var uploadEntities = new List<BulkEntity>();

var bulkCampaignDeviceCriterions = new[] {
    // Map properties in the Bulk file to the BulkCampaignDeviceCriterion
    new BulkCampaignDeviceCriterion
    {
        // 'Campaign' column header in the Bulk file is read-only
        CampaignName = null,

        // 'Client Id' column header in the Bulk file
        ClientId = "ClientIdGoesHere",

        // Map properties in the Bulk file to the 
        // BiddableCampaignCriterion object of the Campaign Management service.

        CampaignCriterion = new BiddableCampaignCriterion
        {
            // 'Parent Id' column header in the Bulk file
            CampaignId = campaignIdKey,

            Criterion = new DeviceCriterion
            {
                // 'Target' column header in the Bulk file
                DeviceName = "Computers",
            },

            CriterionBid = new BidMultiplier
            {
                // 'Bid Adjustment' column header in the Bulk file
                Multiplier = 20,
            },

            // 'Id' column header in the Bulk file
            Id = null,

            // 'Status' column header in the Bulk file
            Status = CampaignCriterionStatus.Active,
        }
    },
    new BulkCampaignDeviceCriterion
    {
        ClientId = "ClientIdGoesHere",
        CampaignCriterion = new BiddableCampaignCriterion
        {
            CampaignId = campaignIdKey,
            Criterion = new DeviceCriterion
            {
                DeviceName = "Smartphones",
            },
            CriterionBid = new BidMultiplier
            {
                Multiplier = 0,
            },
        }
    },
    new BulkCampaignDeviceCriterion
    {
        ClientId = "ClientIdGoesHere",
        CampaignCriterion = new BiddableCampaignCriterion
        {
            CampaignId = campaignIdKey,
            Criterion = new DeviceCriterion
            {
                DeviceName = "Tablets",
            },
            CriterionBid = new BidMultiplier
            {
                Multiplier = 0,
            },
        }
    },
};

foreach (var bulkCampaignDeviceCriterion in bulkCampaignDeviceCriterions)
{
    uploadEntities.Add(bulkCampaignDeviceCriterion);
}

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

### <a name="bidadjustment"></a>Bid Adjustment
The percentage amount that you want to adjust the bid for the corresponding *Target*. 

Supported values are -100 (negative one hundred) through positive 900 (nine hundred) percent. Setting the bid adjustment to -100 percent will result in the exclusion of the corresponding *Target*.

**Add:** Optional. The bid adjustment will be set to the default of *0* if not included.  
**Update:** Required  
**Delete:** Read-only  

### <a name="campaign"></a>Campaign
The name of the campaign where this criterion is applied or removed.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="clientid"></a>Client Id
[!INCLUDE[bulkcolumn_clientid](../bulk-api/includes/bulkcolumn-clientid.md)]

**Add:** Optional  
**Update:** Optional    
**Delete:** Optional  

### <a name="id"></a>Id
[!INCLUDE[bulkcolumn_targetcriterionid](../bulk-api/includes/bulkcolumn-targetcriterionid.md)]

**Add:** Read-only  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="parentid"></a>Parent Id
The identifier of the campaign where this criterion is applied or removed.
	
This bulk field maps to the *Id* field of the [Campaign](../bulk-api/campaign.md) record. 

**Add:** Read-only and Required. You must either specify an existing campaign identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Campaign](../bulk-api/campaign.md) record. This is recommended if you are adding new criterions to a new campaign in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="status"></a>Status
Represents the association status between the campaign and the criterion bid. If the criterion bid is set for the campaign, this field's value is *Active*, and otherwise the value is *Deleted*.

**Add:** Read-only  
**Update:** Optional  
**Delete:** Required. The Status must be set to *Deleted*. To delete a specific device criterion bid, you must upload the *Status*, *Id*, and *Parent Id*.

### <a name="target"></a>Target
The name of the device that you want to target with the corresponding *Bid Adjustment*. 

Supported values are *Computers*, *Smartphones*, and *Tablets*.
  
**Add:** Required. Three separate bids for *Computers*, *Smartphones*, and *Tablets* should be specified together in the bulk file (each bid in a seperate record / row). If you do not add individual device criterions representing each of the three device types, no device criterions will be added for the campaign.  
**Update:** Required  
**Delete:** Read-only  
