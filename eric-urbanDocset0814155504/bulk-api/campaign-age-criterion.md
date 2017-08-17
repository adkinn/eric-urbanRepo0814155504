---
title: "Campaign Age Criterion"
ms.custom: ""
ms.date: "07/25/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ffeda9d-3ddb-4362-b2b9-9ebab6ee6487
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Campaign Age Criterion
Defines a campaign age criterion that can be uploaded and downloaded in a bulk file. 

You can target customers by age so that your ads are displayed more frequently to people who will be interested in them. 

Each age criterion defines an age range for the accompanying criterion bid adjustment. 

The maximum number of age criterions that you can specify per campaign or ad group is five, i.e. one for each of the supported age ranges *EighteenToTwentyFour*, *TwentyFiveToThirtyFour*, *ThirtyFiveToFortyNine*, *FiftyToSixtyFour*, and *SixtyFiveAndAbove*.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For a *Campaign Age Criterion* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Bid Adjustment](#bidadjustment)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)
- [Target](#target)

You can download all fields of the *Campaign Age Criterion* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *CampaignTargetCriterions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would add a new campaign age criterion if a valid campaign identifier (*Parent Id*) is provided. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Bid Adjustment,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,5,,,,,,,,
Campaign Age Criterion,Active,,-111,,,ClientIdGoesHere,,EighteenToTwentyFour,20,,,,,,,,,
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdCampaignAgeCriterion* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 

```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkCampaignAgeCriterion
var bulkCampaignAgeCriterion = new BulkCampaignAgeCriterion
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

        Criterion = new AgeCriterion
        {
            // 'Target' column header in the Bulk file
            AgeRange = AgeRange.EighteenToTwentyFour,
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
};

uploadEntities.Add(bulkCampaignAgeCriterion);

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

Supported values are negative ninety (-90) through positive nine hundred (900). 

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
**Delete:** Required. The Status must be set to *Deleted*.To delete a specific age criterion bid, you must upload the *Status*, *Id*, and *Parent Id*.

### <a name="target"></a>Target
The age range that you want to target with the corresponding *Bid Adjustment*. 

Supported values are *EighteenToTwentyFour*, *TwentyFiveToThirtyFour*, *ThirtyFiveToFortyNine*, *FiftyToSixtyFour*, and *SixtyFiveAndAbove*. 

> [!NOTE]
> In many countries, online advertisers are not supposed to target any users less than 18 years old. Bing Ads does not deliver interest-based advertising to children whose birthdate in their Microsoft account identifies them as under 13 years of age. For more information see the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).
> 
> Currently people ages 13 to 17 can see your ads, although you cannot adjust the bid for that age range. Soon in Bing Ads you will be enabled to specifically exclude ages 13 to 17. The target value of *ThirteenToSeventeen* will be supported with negative bid adjustments between -100 and 0. We will announce more specific dates within the next few months.

**Add:** Required  
**Update:** Required  
**Delete:** Read-only  

