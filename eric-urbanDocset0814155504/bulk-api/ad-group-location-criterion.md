---
title: "Ad Group Location Criterion"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8901a9be-91d9-4ec9-abb6-4d80b4bea004
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Group Location Criterion
Defines an ad group location criterion that can be uploaded and downloaded in a bulk file.

With location criterions, you can choose to show ads to potential customers in, searching for, or viewing pages about:
*  All available countries/regions
*  Selected cities, zip codes, metro areas, states/provinces, and countries/regions

Each location criterion defines a location code for the accompanying criterion bid adjustment. 

The maximum number of combined location and negative location criterions that you can specify per campaign or ad group is 10,000.  

> [!NOTE]
> You can only have one [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md) record per ad group to determine the location intent option that applies for all of the ad group's [Ad Group Location Criterion](../bulk-api/ad-group-location-criterion.md) and [Ad Group Radius Criterion](../bulk-api/ad-group-radius-criterion.md) records. When you create the ad group's first criterion, an [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md) record will also be added automatically with the default *Target* set to *PeopleInOrSearchingForOrViewingPages*. You can add or update an ad group's [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md), whether or not the ad group has any other criterions. You cannot delete an ad group's [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md), although it has no purpose without location or radius criterions. 

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group Location Criterion* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Bid Adjustment](#bidadjustment)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Id](#id)
- [Modified Time](#modifiedtime)
- [Parent Id](#parentid)
- [Status](#status)
- [Sub Type](#subtype)
- [Target](#target)

You can download all fields of the *Ad Group Location Criterion* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroupTargetCriterions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx).

The following Bulk CSV example would add a new ad group location criterion if a valid ad group identifier (*Parent Id*) is provided. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Ad Group,Client Id,Modified Time,Target,Bid Adjustment,Name,OS Names,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,5,,,,,,,,,
Ad Group Location Criterion,Active,,-1111,Country,,,ClientIdGoesHere,,190,20,,,,,,,,,,
```

If you are using the [Bing Ads SDKs](https://msdn.microsoft.com/library/bing-ads-client-libraries.aspx) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroupLocationCriterion* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 

```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAdGroupLocationCriterion
var bulkAdGroupLocationCriterion = new BulkAdGroupLocationCriterion
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

        Criterion = new LocationCriterion
        {
            // 'Target' column header in the Bulk file
            LocationId = 190,

            // 'Sub Type' column header in the Bulk file
            LocationType = "Country"
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
};

uploadEntities.Add(bulkAdGroupLocationCriterion);

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

Supported values are negative ninety (-90) through positive nine hundred (900). 

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

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are adding new criterions to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](https://msdn.microsoft.com/library/bing-ads-bulk-file-schema.aspx#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  

### <a name="status"></a>Status
Represents the association status between the ad group and the criterion bid. If the criterion bid is set for the ad group, this field's value is *Active*, and otherwise the value is *Deleted*.

**Add:** Read-only  
**Update:** Optional  
**Delete:** Required. The Status must be set to *Deleted*. To delete a specific location criterion bid, you must upload the *Status*, *Id*, and *Parent Id*. 

### <a name="subtype"></a>Sub Type
The location sub type that you are targeting. For example the value is *City* if the record represents a city location criterion.

Possible values are *City*, *Country*, *MetroArea*, *PostalCode*, and *State*.

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="target"></a>Target
The identifier of the location that you want to target with the corresponding *Bid Adjustment*. The location identifier corresponds to the *ID* field of the geographical locations file. For more information, see [Geographical Location Codes](https://msdn.microsoft.com/library/bing-ads-geographical-location-codes.aspx) and [GetGeoLocationsFileUrl](https://msdn.microsoft.com/library/bing-ads-campaign-management-getgeolocationsfileurl.aspx).

**Add:** Required  
**Update:** Required  
**Delete:** Read-only  

  
