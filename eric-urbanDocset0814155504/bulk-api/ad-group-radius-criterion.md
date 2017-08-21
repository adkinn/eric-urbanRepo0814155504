---
title: "Ad Group Radius Criterion"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b97e02b5-1d3a-481f-8f65-d921a5c56fc3
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Group Radius Criterion
Defines an ad group radius criterion that can be uploaded and downloaded in a bulk file.

With radius criterions, you can choose to show ads to potential customers in, searching for, or viewing pages about a specified radius around a zip code, coordinates, landmark, or area.

Each radius criterion defines a radius, latitude, and longitude for the accompanying criterion bid adjustment. 

The maximum number of radius criterions that you can specify per campaign or ad group is 2,000.

> [!NOTE]
> You can only have one [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md) record per ad group to determine the location intent option that applies for all of the ad group's [Ad Group Location Criterion](../bulk-api/ad-group-location-criterion.md) and [Ad Group Radius Criterion](../bulk-api/ad-group-radius-criterion.md) records. When you create the ad group's first criterion, an [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md) record will also be added automatically with the default *Target* set to *PeopleInOrSearchingForOrViewingPages*. You can add or update an ad group's [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md), whether or not the ad group has any other criterions. You cannot delete an ad group's [Ad Group Location Intent Criterion](../bulk-api/ad-group-location-intent-criterion.md), although it has no purpose without location or radius criterions. 

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For an *Ad Group Radius Criterion* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Ad Group](#adgroup)
- [Bid Adjustment](#bidadjustment)
- [Campaign](#campaign)
- [Client Id](#clientid)
- [Id](#id)
- [Latitude](#latitude)
- [Longitude](#longitude)
- [Modified Time](#modifiedtime)
- [Name](#name)
- [Parent Id](#parentid)
- [Radius](#radius)
- [Status](#status)
- [Unit](#unit)

You can download all fields of the *Ad Group Radius Criterion* record by including the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value of *AdGroupTargetCriterions* in the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. Additionally the download request must include the [DataScope](../bulk-api/datascope-value-set.md) value of *EntityData*. For more information, see [Bulk Download and Upload](~/concepts/bulk-download-and-upload.md).

The following Bulk CSV example would add a new ad group radius criterion if a valid ad group identifier (*Parent Id*) is provided. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Ad Group,Client Id,Modified Time,Target,Bid Adjustment,Name,OS Names,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,5,,,,,,,,,
Ad Group Radius Criterion,Active,,-1111,,,,ClientIdGoesHere,,RadiusName,20,,,10,Kilometers,,,,,10.5,40.5
```

If you are using the [Bing Ads SDKs](~/concepts/bing-ads-client-libraries.md) for .NET, Java, or Python, you can save time using the *BulkServiceManager* to upload and download the *BulkAdGroupRadiusCriterion* class, instead of calling the service operations directly and writing custom code to parse each field in the bulk file. 

```csharp
var uploadEntities = new List<BulkEntity>();

// Map properties in the Bulk file to the BulkAdGroupRadiusCriterion
var bulkAdGroupRadiusCriterion = new BulkAdGroupRadiusCriterion
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

        Criterion = new RadiusCriterion
        {
            // 'Latitude' column header in the Bulk file
            LatitudeDegrees = 10.5,

            // 'Longitude' column header in the Bulk file
            LongitudeDegrees = 40.5,

            // 'Name' column header in the Bulk file
            Name = "RadiusName",

            // 'Radius' column header in the Bulk file
            Radius = 10,

            // 'Unit' column header in the Bulk file
            RadiusUnit = DistanceUnit.Kilometers,
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

uploadEntities.Add(bulkAdGroupRadiusCriterion);

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
The percentage amount that you want to adjust the bid for the corresponding radius criterion. 

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

### <a name="latitude"></a>Latitude
The latitude, in degrees, of the radius criterion.

The latitude must be greater than or equal to -85.0 and less than or equal to +85.0.

You specify the latitude and longitude as decimal values. For example, the latitude and longitude of One Redmond Way, Redmond, WA is 47.755367 and -122.091827, respectively. To get these values, you can enter the address of a geographical location into [Bing Maps](http://www.bing.com/maps/) and the coordinates will be displayed below the address.

**Add:** Required  
**Update:** Required  
**Delete:** Read-only  

### <a name="longitude"></a>Longitude
The longitude, in degrees, of the radius criterion.

The longitude must be greater than or equal to -180.0 and less than or equal to +180.0.

You specify the latitude and longitude as decimal values. For example, the latitude and longitude of One Redmond Way, Redmond, WA is 47.755367 and -122.091827, respectively. To get these values, you can enter the address of a geographical location into [Bing Maps](http://www.bing.com/maps/) and the coordinates will be displayed below the address.

**Add:** Required  
**Update:** Required  
**Delete:** Read-only  

### <a name="modifiedtime"></a>Modified Time
[!INCLUDE[bulkcolumn_modifiedtime](../bulk-api/includes/bulkcolumn-modifiedtime.md)]

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  

### <a name="name"></a>Name
The name of the geographical location being targeted. 

The name can contain a maximum of 50 characters.

**Add:** Optional  
**Update:** Read-only  
**Delete:** Read-only 

### <a name="parentid"></a>Parent Id
The identifier of the ad group where this criterion is applied or removed.
	
This bulk field maps to the *Id* field of the [Ad Group](../bulk-api/ad-group.md) record. 

**Add:** Read-only and Required. You must either specify an existing ad group identifier, or specify a negative identifier that is equal to the *Id* field of the parent [Ad Group](../bulk-api/ad-group.md) record. This is recommended if you are adding new criterions to a new ad group in the same Bulk file. For more information, see [Bulk File Schema Reference Keys](~/bulk-api/bulk-file-schema.md#referencekeys).  
**Update:** Read-only and Required  
**Delete:** Read-only and Required  
 
### <a name="radius"></a>Radius
The radius that specifies the area surrounding the geographical location to target.

If the *Radius Unit* field is set to *Miles*, then positive integer values from 1 to 500 are accepted.

If the *Radius Unit* field is set to *Kilometers*, then positive integer values from 1 to 800 are accepted.

> [!NOTE]
> The data type is double and may be supported in a future release. Currently the service only accepts and returns integer values.

**Add:** Required  
**Update:** Required  
**Delete:** Read-only    

### <a name="status"></a>Status
Represents the association status between the ad group and the criterion bid. If the criterion bid is set for the ad group, this field's value is *Active*, and otherwise the value is *Deleted*.

**Add:** Read-only  
**Update:** Optional  
**Delete:** Required. The Status must be set to *Deleted*. To delete a specific radius criterion bid, you must upload the *Status*, *Id*, and *Parent Id*.  

### <a name="unit"></a>Unit
The unit of measurement for the specified radius.

Supported values are *Miles* (default) and *Kilometers*.

**Add:** Optional. If not specified, the default value of *Miles* will be set.  
**Update:** Required  
**Delete:** Read-only  
