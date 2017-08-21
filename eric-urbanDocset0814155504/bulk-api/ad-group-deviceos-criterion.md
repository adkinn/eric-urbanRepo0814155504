---
title: "Ad Group DeviceOS Criterion"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffef0e36-8c73-41e7-870f-9ca767d45e31
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Group DeviceOS Criterion
Defines an ad group device OS criterion that can be uploaded and downloaded in a bulk file.

When you target by device, you choose to show ads to potential customers when they're using desktops and tablets or smartphones. 

Each device criterion defines a device name for the accompanying criterion bid adjustment. 

The maximum number of device criterions that you can specify per campaign or ad group is three. You must either have three separate criterions for *Computers*, *Smartphones*, and *Tablets*, otherwise no device criterions can exist for the campaign or ad group.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group DeviceOS Criterion* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Bid Adjustment](#bidadjustment)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)
- [Target](#target)

You can download all fields of the *Ad Group DeviceOS Criterion* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroupTargetCriterions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add three new ad group device criterions (one for each device type) if a valid ad group identifier (*Parent Id*) is provided. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Ad Group,Client Id,Modified Time,Target,Bid Adjustment,Name,OS Names,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,5,,,,,,,,,
Ad Group DeviceOS Criterion,Active,,-1111,,,,ClientIdGoesHere,,Computers,20,,,,,,,,,,
Ad Group DeviceOS Criterion,,,-1111,,,,ClientIdGoesHere,,Smartphones,0,,,,,,,,,,
Ad Group DeviceOS Criterion,,,-1111,,,,ClientIdGoesHere,,Tablets,0,,,,,,,,,,
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroupDeviceOSCriterion* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 

```csharp
var uploadEntities = new List<BulkEntity>();

var bulkAdGroupDeviceCriterions = new [] {
    // Map properties in the Bulk file to the BulkAdGroupDeviceCriterion
    new BulkAdGroupDeviceCriterion
    {
        // 'Ad Group' column header in the Bulk file is read-only
        AdGroupName = null,
                    
        // 'Campaign' column header in the Bulk file is read-only
        CampaignName = null,

        // 'Client Id' column header in the Bulk file
        ClientId = "ClientIdGoesHere",

        // Map properties in the Bulk file to the 
        // BiddableAdGroupCriterion object of the Campaign Management service.

        AdGroupCriterion = new BiddableAdGroupCriterion
        {
            // 'Parent Id' column header in the Bulk file
            AdGroupId = adGroupIdKey,

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
            Status = AdGroupCriterionStatus.Active,
        }
    },
    new BulkAdGroupDeviceCriterion
    {
        ClientId = "ClientIdGoesHere",
        AdGroupCriterion = new BiddableAdGroupCriterion
        {
            AdGroupId = adGroupIdKey,
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
    new BulkAdGroupDeviceCriterion
    {
        ClientId = "ClientIdGoesHere",
        AdGroupCriterion = new BiddableAdGroupCriterion
        {
            AdGroupId = adGroupIdKey,
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

foreach (var bulkAdGroupDeviceCriterion in bulkAdGroupDeviceCriterions)
{
    uploadEntities.Add(bulkAdGroupDeviceCriterion);
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

### <a name="adgroup"></a>Ad Group
The name of the ad group where this criterion is applied or removed.  

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="bidadjustment"></a>Bid Adjustment
The percentage amount that you want to adjust the bid for the corresponding *Target*. 

Supported values are -100 (negative one hundred) through positive 900 (nine hundred) percent. Setting the bid adjustment to -100 percent will result in the exclusion of the corresponding *Target*.

**Add:** Optional. The bid adjustment will be set to the default of *0* if not included.  
**Update:** Required  
**Delete:** Read-only  

### <a name="campaign"></a>Campaign
The name of the campaign that contains the ad group where this criterion is applied or removed.

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
The identifier of the ad group where this criterion is applied or removed.
	
This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record. 

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are adding new criterions to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="status"></a>Status
Represents the association status between the ad group and the criterion bid. If the criterion bid is set for the ad group, this field's value is *Active*, and otherwise the value is *Deleted*.

**Add:** Read-only  
**Update:** Optional  
**Delete:** Required. The Status must be set to *Deleted*. To delete a specific device criterion bid, you must upload the *Status*, *Id*, and *Parent Id*.

### <a name="target"></a>Target
The name of the device that you want to target with the corresponding *Bid Adjustment*. 

Supported values are *Computers*, *Smartphones*, and *Tablets*.

**Add:** Required. Three separate bids for *Computers*, *Smartphones*, and *Tablets* should be specified together in the bulk file (each bid in a seperate record / row). If you do not add individual device criterions representing each of the three device types, no device criterions will be added for the ad group.  
**Update:** Required  
**Delete:** Read-only  
