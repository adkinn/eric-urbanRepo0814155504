---
title: "Upgrade Targets to Criterions"
ms.custom: ""
ms.date: "08/09/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b1a4a8d-47bc-4b38-a694-4cdc0d04f7ab
caps.latest.revision: 27
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Upgrade Targets to Criterions
Instead of using targets to show your ads based on age, day and time, device, gender, and location, starting with Bing Ads API version 11 you must use criterions. Where necessary to distinguish from other criterion types the documentation may refer to these entities as *target criterions*.  There are two architectural changes required to upgrade from targets to criterions. 

The first change divides the single target entity (with multiple sub target types) into multiple criterion entities. Instead of using one target identifier across all target sub types such as age and location, each criterion will have its own entity identifier. For example two location criterion set to an ad group would each have unique identifiers. This change enables partial update of criterions, whereas previously clients using Campaign Management API version 10 were required to submit the full set of target sub types with the update request, and now with criterion you can update each criterion individually. Even though Bulk API version 10 already supported partial target updates, the Bulk file schema is updated in version 11 to reflect and support the new criterion architecture. To get started, see [Using Target Criterions](#usingcriterions).

The second change ends support for sharing a library target across multiple campaigns or ad groups. Previously clients using Campaign Management API version 10 could create a target with AddTargetsToLibrary and then share the target to multiple ad groups or campaigns using the SetTargetToAdGroup and SetTargetToCampaign operations. Going forward you must add criterions directly to the ad group or campaign. There is an important consideration to make regarding the deprecation of shared targets. If your application only manages campaigns that do not share any targets, then migration could be as simple as using the new Campaign Management service operations or new Bulk file records. However, if your application manages any campaigns with shared targets, then you should prepare for inline shared target migration. For more information, see [Shared Target Migration](#sharedtargetmigration).

> [!NOTE] 
> Bing Ads API version 10 targets and version 11 criterions can be managed in parallel. For example an account can be managed by an application that only uses criterions, and during the same day and hour can be managed by the same application or a different application that still uses the deprecated target data model. Support for targets will end no later than the sunset of Bing Ads API version 10. Specific sunset dates will be announced via the [Bing Ads API Blog](https://blogs.msdn.microsoft.com/bing_ads_api/).


## <a name="usingcriterions"></a>Using Target Criterions

If you have been using targets with the Bing Ads API, web application, or another entry point, then in a sense you are already using criterions. Underneath each target are multiple criterions corresponding to each sub target bid. Bing Ads API version 11 enables access to the underlying criterion identifiers. Upgrading to criterions requires that you sync the set of criterion identifiers for each campaign or ad group in place of using a single target identifier. 

### <a name="synccriterions"></a>Sync Criterions
Sync the new criterions with campaigns and ad groups. For example you can use the Bulk service to download  all criterions in the account and discover the mapping between criterions and campaigns and ad groups. 

Let's look at an example where the campaign targets were downloaded using Bing Ads API version 10, Bulk file format 4.0. Each campaign sub target in this example shares the same target identifier i.e. *10*, and each ad group sub target in this example shares the same target identifier i.e. *20*. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Physical Intent,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,4,,,,,,,,
Account,,AcccountIdHere,CustomerIdHere,,,,,,,,,,,,,,,,,
Campaign Location Target,Active,10,CampaignIdHere,Country,Campaign One,,41:34.8,US,PeopleIn,20,,,,,,,,,,
Campaign Radius Target,Active,10,CampaignIdHere,,Campaign One,,41:34.8,,PeopleIn,20,380349406,RadiusName,10,Kilometers,,,,,10.5,40.5
Campaign Age Target,Active,10,CampaignIdHere,,Campaign One,,41:34.8,EighteenToTwentyFive,,20,,,,,,,,,,
Campaign DayTime Target,Active,10,CampaignIdHere,,Campaign One,,41:34.8,Monday,,20,,,,,0,0,4,0,,
Campaign Gender Target,Active,10,CampaignIdHere,,Campaign One,,41:34.8,Female,,20,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignIdHere,,Campaign One,,41:34.8,Computers,,20,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignIdHere,,Campaign One,,41:34.8,Smartphones,,0,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignIdHere,,Campaign One,,41:34.8,Tablets,,0,,,,,,,,,,
Campaign Negative Location Target,Active,10,CampaignIdHere,Postal Code,Campaign One,,41:34.8,"91708, CA US",,,,,,,,,,,,
Ad Group Location Target,Active,20,AdGroupIdHere,Country,Campaign One,,41:35.7,US,PeopleIn,20,,,,,,,,,,
Ad Group Radius Target,Active,20,AdGroupIdHere,,Campaign One,,41:35.7,,PeopleIn,20,380349407,RadiusName,10,Kilometers,,,,,10.5,40.5
Ad Group Age Target,Active,20,AdGroupIdHere,,Campaign One,,41:35.7,EighteenToTwentyFive,,20,,,,,,,,,,
Ad Group DayTime Target,Active,20,AdGroupIdHere,,Campaign One,,41:35.7,Monday,,20,,,,,0,0,4,0,,
Ad Group Gender Target,Active,20,AdGroupIdHere,,Campaign One,,41:35.7,Female,,20,,,,,,,,,,
Ad Group DeviceOS Target,Active,20,AdGroupIdHere,,Campaign One,,41:35.7,Computers,,20,,,,,,,,,,
Ad Group DeviceOS Target,Active,20,AdGroupIdHere,,Campaign One,,41:35.7,Smartphones,,0,,,,,,,,,,
Ad Group DeviceOS Target,Active,20,AdGroupIdHere,,Campaign One,,41:35.7,Tablets,,0,,,,,,,,,,
Ad Group Negative Location Target,Active,20,AdGroupIdHere,Postal Code,Campaign One,,41:35.7,"91708, CA US",,,,,,,,,,,,
```

Now let's download the target criterions using Bing Ads API version 11, Bulk file format 5.0, and we can see that each criterion has its own identifier e.g. 101, 102, 103, and so on. You will notice a few more differences between Bulk file format 4.0 targets and Bulk file format 5.0 criterions. For example instead of sharing the *Physical Intent* field across location and radius records, Bulk file format 5.0 introduces the [Campaign Location Intent Criterion](Campaign%20Location%20Intent%20Criterion.md) and [Ad Group Location Intent Criterion](Ad%20Group%20Location%20Intent%20Criterion.md) records. For more information, see [Migrating to Bing Ads API Version 11 - Bulk - Target Criterions](../concepts/migrating-to-bing-ads-api-version-11.md#bulk_targetcriterions).

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Physical Intent,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Account,,AcccountIdHere,CustomerIdHere,,,,,,,,,,,,,,,,,
Campaign Age Criterion,Active,101,CampaignIdHere,,CampaignNameHere,,41:34.8,EighteenToTwentyFour,,20,,,,,,,,,,
Campaign Gender Criterion,Active,102,CampaignIdHere,,CampaignNameHere,,41:34.8,Female,,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,103,CampaignIdHere,,CampaignNameHere,,41:34.8,Computers,,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,104,CampaignIdHere,,CampaignNameHere,,41:34.8,Smartphones,,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,105,CampaignIdHere,,CampaignNameHere,,41:34.8,Tablets,,0,,,,,,,,,,
Campaign Location Criterion,Active,106,CampaignIdHere,Country,CampaignNameHere,,41:34.8,190,,20,,,,,,,,,,
Campaign Negative Location Criterion,Active,107,CampaignIdHere,PostalCode,CampaignNameHere,,41:34.8,79381,,,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignIdHere,CampaignIdHere,,CampaignNameHere,,41:34.8,PeopleIn,,,,,,,,,,,,
Campaign Radius Criterion,Active,108,CampaignIdHere,,CampaignNameHere,,41:34.8,,,20,,RadiusName,10,Kilometers,,,,,10.5,40.5
Campaign DayTime Criterion,Active,109,CampaignIdHere,,CampaignNameHere,,41:34.8,Monday,,20,,,,,0,0,4,0,,
Ad Group Age Criterion,Active,201,AdGroupIdHere,,CampaignNameHere,,41:35.7,EighteenToTwentyFour,,20,,,,,,,,,,
Ad Group Gender Criterion,Active,202,AdGroupIdHere,,CampaignNameHere,,41:35.7,Female,,20,,,,,,,,,,
Ad Group DeviceOS Criterion,Active,203,AdGroupIdHere,,CampaignNameHere,,41:35.7,Computers,,20,,,,,,,,,,
Ad Group DeviceOS Criterion,Active,204,AdGroupIdHere,,CampaignNameHere,,41:35.7,Smartphones,,0,,,,,,,,,,
Ad Group DeviceOS Criterion,Active,205,AdGroupIdHere,,CampaignNameHere,,41:35.7,Tablets,,0,,,,,,,,,,
Ad Group Location Criterion,Active,206,AdGroupIdHere,Country,CampaignNameHere,,41:35.7,190,,20,,,,,,,,,,
Ad Group Negative Location Criterion,Active,207,AdGroupIdHere,PostalCode,CampaignNameHere,,41:35.7,79381,,,,,,,,,,,,
Ad Group Location Intent Criterion,Active,AdGroupIdHere,AdGroupIdHere,,CampaignNameHere,,41:35.7,PeopleIn,,,,,,,,,,,,
Ad Group Radius Criterion,Active,208,AdGroupIdHere,,CampaignNameHere,,41:35.7,,,20,,RadiusName,10,Kilometers,,,,,10.5,40.5
Ad Group DayTime Criterion,Active,209,AdGroupIdHere,,CampaignNameHere,,41:35.7,Monday,,20,,,,,0,0,4,0,,
```

### <a name="addcriterion"></a>Add or Update Criterions
Add new criterions directly to the campaign or ad group, or use the synced criterion identifiers to update or delete existing criterions. 

Here are a few tips to keep in mind before you begin:
*  When you first create a campaign or ad group using the Bing Ads API, it will not have any criterions. Effectively the brand new campaign and ad group target all ages, days, hours, devices, genders, and locations. You should specify your minimum target criterions at the campaign level and then use ad group level criterions to narrow or refine your targeting requirements. As a best practice you should consider at minimum adding a campaign location criterion corresponding to the customer market country. Its worth noting that when creating campaigns via the Bing Ads web application, the recommended [default criterions](#defaultcriterions) are added. 
*  If you specify the same [criterion types](#criteriontypes) at the ad group and campaign level, the ad group-level criterions will override the campaign-level criterions. For example, if the campaign location criterion is *US* and the ad group location criterion is *California*, the ads will display only to users in California. Or, if the campaign criterions are *Monday* and *Wednesday* and the ad group criterions are *Tuesday* and *Thursday*, the ads will display only on Tuesdays and Thursdays.
*  When a criterion type is not specified at the ad group level, that type is effectively inherited from the campaign if it exists in the campaign. For example, you can specify location criterions at the campaign level and day and time criterions at the ad group level. If the location criterion is set to U.S. and the day and time criterion is set to Monday from 11am - 3pm, then the ads will display to users in the U.S. on Mondays from 11am - 3pm. 
*  You must consider the location, negative location, and radius criterions as a set of *geo criterions*. If the ad group has any geo criterions, then none of the campaign's geo criterions are inherited. If the ad group doesn't have any geo criterions, then all of the campaign's geo criterions are inherited. The geo criterions can be inherited from the campaign even if the ad group has a location intent criterion. If the ad group's geo criterions are used, then the ad group's location intent criterion is used; if the campaign's geo criterions are inherited, then the campaign's location intent criterion is used and the ad group's location intent criterion is ignored. You cannot delete a campaign or ad group's location intent criterion, although it has no purpose without location or radius criterions. 
*  Partial update is supported, so you can update each criterion individually. For example if you only want to update the bid adjustment for 1 location, only send that location criterion. There is no need to send all locations. 
*  With one exception, partial success is supported, such that if you add or update multiple criterions each can fail or succeed independently. The exception is that during [Shared Target Migration](#sharedtargetmigration), if any criterion errors are returned then none of the criterions that belong to the same campaign or ad group target are migrated. 
*  If you added or updated criterions and the result file included any criterion records with status set to *Deleted* and the *Id* field set to '0' (zero), then inline shared target migration has occurred for that specific campaign's target. The campaign is no longer associated with the original target and underlying criterions, and in their place the campaign has been assigned new criterion identifiers. For more information, see [Shared Target Migration](#sharedtargetmigration).
*  If you delete the campaign or ad group, all of the criterions for the same campaign or ad group are also deleted. 
*  If you upload multiple records with the same criterion identifier, then the first record will succeed and the subsequent duplicates will fail. 
*  Individual criterions are validated first, and then system limits are enforced if the number of valid criterions would exceed the allowed limit of criterions per campaign or ad group. Partial success of criterions is allowed up to the system limit.

Let's assume we have already retrieved the criterion identifiers as described in [Sync Criterions](#synccriterions), and we attempt to upload the following criterions. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Physical Intent,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Account,,AcccountIdHere,CustomerIdHere,,,,,,,,,,,,,,,,,
Campaign Location Criterion,Active,,CampaignIdHere,Country,,,,190,,20,,,,,,,,,,
Campaign Location Intent Criterion,Deleted,CampaignIdHere,CampaignIdHere,,,,,,,,,,,,,,,,,
Ad Group Age Criterion,Active,,AdGroupIdHere,,,,,EighteenToTwentyFour,,20,,,,,,,,,,
Ad Group DeviceOS Criterion,Deleted,203,AdGroupIdHere,,,,,Computers,,20,,,,,,,,,,
Ad Group DeviceOS Criterion,Deleted,204,AdGroupIdHere,,,,,Smartphones,,0,,,,,,,,,,
Ad Group DeviceOS Criterion,Deleted,205,AdGroupIdHere,,,,,Tablets,,0,,,,,,,,,,
```

As observed in the example upload results file below:
*  We successfully targeted Canada (LocationId = 32) by adding a new campaign location criterion.
*  Location intent criterions can never be deleted. The attempt to delete the location intent criterion from the campaign failed but did not cause other criterion updates to fail.
*  Without the assigned identifier for an existing age criterion, the upload attempt failed with code 1043 i.e. CampaignServiceEntityAlreadyExists. If the *EighteenToTwentyFour* age criterion had not existed already or if we had specified an age range that is not yet set for the campaign, then the upload would have succeeded and created a new criterion with unique identifier. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Physical Intent,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude,Error,Error Number
Format Version,,,,,,,,,,,,5,,,,,,,,,,
Account,,AcccountIdHere,CustomerIdHere,,,,,,,,,,,,,,,,,,,
Campaign Location Criterion,Active,110,CampaignIdHere,Country,,,,190,,20,,,,,,,,,,,,
Campaign Location Intent Criterion,Deleted,CampaignIdHere,CampaignIdHere,,,,,,,,,,,,,,,,,,,
Campaign Location Intent Criterion Error,Deleted,CampaignIdHere,CampaignIdHere,,,,,,,,,,,,,,,,,,LocationIntentCriterionCannotBeDeleted,2965
Ad Group Age Criterion,Active,,AdGroupIdHere,,,,,EighteenToTwentyFour,,20,,,,,,,,,,,,
Ad Group Age Criterion Error,Active,,AdGroupIdHere,,,,,EighteenToTwentyFour,,20,,,,,,,,,,,CampaignServiceEntityAlreadyExists,1043
Ad Group DeviceOS Criterion,Deleted,203,AdGroupIdHere,,,,,Computers,,20,,,,,,,,,,,,
Ad Group DeviceOS Criterion,Deleted,204,AdGroupIdHere,,,,,Smartphones,,0,,,,,,,,,,,,
Ad Group DeviceOS Criterion,Deleted,205,AdGroupIdHere,,,,,Tablets,,0,,,,,,,,,,,,
```

## <a name="sharedtargetmigration"></a>Shared Target Migration

If your application only manages campaigns that do not share any targets, then upgrading to criterions could be as simple as using the new Campaign Management service operations or new Bulk file records for criterions. To get started, see [Using Target Criterions](#usingcriterions).

If your application manages any campaigns with shared targets, then you should prepare for inline shared target migration. Shared target migration occurs whenever your application adds or updates a criterion for an ad group or campaign that shares a target with another ad group or campaign. The ad group or campaign that you updated will be assigned new criterion identifiers, whereas the other entities will keep the original identifiers. 

Let's look at an example where the same target was associated to three different campaigns. For example using Bing Ads Campaign Management API version 10, an application might have used the AddTargetsToLibrary and SetTargetToCampaign operations as follows:

```csharp
var sharedTarget = new Target
{
    Name = "My Campaign Target",

    DeviceOS = new DeviceOSTarget
    {
        Bids = new[]
        {
            new DeviceOSTargetBid
            {
                BidAdjustment = 20,
                DeviceName = "Computers",
            },
        },
    },
};

var addTargetsToLibraryResponse = (await AddTargetsToLibraryAsync(new[] { sharedTarget }));
await SetTargetToCampaignAsync((long)campaignIds[0], addTargetsToLibraryResponse.TargetIds[0]);
await SetTargetToCampaignAsync((long)campaignIds[1], addTargetsToLibraryResponse.TargetIds[0]);
await SetTargetToCampaignAsync((long)campaignIds[2], addTargetsToLibraryResponse.TargetIds[0]);
```

> [!IMPORTANT]
> The above workflow is an example of a deprecated scenario. You must no longer use the *AddTargetsToLibrary*, *SetTargetToCampaign*, or *SetTargetToAdGroup* operations. Instead you will be required to use criterions in Bing Ads API version 11. Support for targets will end no later than the sunset of Bing Ads API version 10. Specific sunset dates will be announced via the [Bing Ads API Blog](https://blogs.msdn.microsoft.com/bing_ads_api/). 


We can then observe how the target associations are represented in the download file using Bing Ads API version 10, Bulk file format 4.0. Each sub target downloaded in this example shares the same target identifier i.e. *10*. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Physical Intent,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,4,,,,,,,,
Account,,AcccountIdHere,CustomerIdHere,,,,,,,,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignOneIdHere,,Campaign One,,15:59.6,Computers,,20,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignOneIdHere,,Campaign One,,15:59.6,Smartphones,,0,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignOneIdHere,,Campaign One,,15:59.6,Tablets,,0,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignTwoIdHere,,Campaign Two,,15:59.6,Computers,,20,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignTwoIdHere,,Campaign Two,,15:59.6,Smartphones,,0,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignTwoIdHere,,Campaign Two,,15:59.6,Tablets,,0,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignThreeIdHere,,Campaign Three,,15:59.6,Computers,,20,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignThreeIdHere,,Campaign Three,,15:59.6,Smartphones,,0,,,,,,,,,,
Campaign DeviceOS Target,Active,10,CampaignThreeIdHere,,Campaign Three,,15:59.6,Tablets,,0,,,,,,,,,,
```

Now let's download the campaign's target criterions using Bing Ads API version 11, Bulk file format 5.0, and we can see that with the exception of location intent criterion even the underlying criterions (*201*, *202*, and *203*) are shared by all three of the campaigns. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Account,,AcccountIdHere,CustomerIdHere,,,,,,,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignOneIdHere,,Campaign One,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignOneIdHere,,Campaign One,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignOneIdHere,,Campaign One,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignOneIdHere,CampaignOneIdHere,,Campaign One,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignTwoIdHere,,Campaign Two,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignTwoIdHere,,Campaign Two,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignTwoIdHere,,Campaign Two,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignTwoIdHere,CampaignTwoIdHere,,Campaign One,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignThreeIdHere,,Campaign Three,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignThreeIdHere,,Campaign Three,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignThreeIdHere,,Campaign Three,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignThreeIdHere,CampaignThreeIdHere,,Campaign Three,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
```

> [!NOTE] Using Bing Ads Campaign Management API version 10 you can continue to retrieve the criterions as targets using [GetTargetsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-gettargetsbyids.aspx). In parallel with Bing Ads Campaign Management API version 11 you will use [GetAdGroupCriterionsByIds](~/campaign-api/getadgroupcriterionsbyids-service-operation.md) or [GetCampaignCriterionsByIds](~/campaign-api/getcampaigncriterionsbyids-service-operation.md) to retreive the underlying criterions.

### <a name="migrationexamplea"></a>Migration Example A
Given the above shared target scenario, now let's turn attention towards the migration process whereby the updated campaign will be assigned new criterion identifiers, and the other two campaigns will keep the original identifiers. For example let's add a day and time criterion to *Campaign One*. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Campaign DayTime Criterion,Active,,CampaignOneIdHere,,,,,Monday,20,,,,,0,0,4,0,,
```

The example upload result file below includes the following records:

  * One [Campaign DeviceOS Criterion](Campaign%20DeviceOS%20Criterion.md) record with *Status* set to *Deleted* and *Id* set to *0* (zero). This record indicates that the previous *Campaign DeviceOS Criterion* identifiers are no longer valid for the corresponding campaign, and you must sync the new identifiers provided below in the same bulk file.

  * One [Campaign Location Intent Criterion](Campaign%20Location%20Intent%20Criterion.md) record with *Status* set to *Deleted* and *Id* set to *0* (zero). This record indicates that the previous [Campaign Location Intent Criterion](Campaign%20Location%20Intent%20Criterion.md) identifier is no longer valid for the corresponding campaign, and you must sync the new identifiers provided below in the same bulk file. That said, the location intent criterion identifier is currently always equal to the campaign identifier. This is subject to change, so it is recommended that you treat it as a unique identifier and follow the same workflow as other criterions i.e. sync the identifier like it is new.

  * One [Campaign DayTime Criterion](Campaign%20DayTime%20Criterion.md) record with the unique identifier for the day and time criterion that we added. Of course if we had added more criterions of any type, a result record with unique identifiers would be included for each of them. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Campaign DeviceOS Criterion,Deleted,0,CampaignOneIdHere,,,,,,,,,,,,,,,,
Campaign Location Intent Criterion,Deleted,0,CampaignOneIdHere,,,,,,,,,,,,,,,,
Campaign DayTime Criterion,Active,304,CampaignOneIdHere,,,,,Monday,20,,,,,0,0,4,0,,
Campaign DeviceOS Criterion,Active,301,CampaignOneIdHere,,Campaign One,,,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,302,CampaignOneIdHere,,Campaign One,,,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,303,CampaignOneIdHere,,Campaign One,,,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignOneIdHere,CampaignOneIdHere,,Campaign One,,,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
```

Let's download all of the criterions again and we can see that the original criterions (*201*, *202*, and *203*) are still shared by *Campaign Two* and *Campaign Three*. Only the criterions associated with the modified campaign (*Campaign One*) were migrated and assigned new identifiers. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Campaign DayTime Criterion,Active,304,CampaignOneIdHere,,,,16:00.0,Monday,20,,,,,0,0,4,0,,
Campaign DeviceOS Criterion,Active,301,CampaignOneIdHere,,Campaign One,,16:00.0,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,302,CampaignOneIdHere,,Campaign One,,16:00.0,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,303,CampaignOneIdHere,,Campaign One,,16:00.0,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignOneIdHere,CampaignOneIdHere,,Campaign One,,16:00.0,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignTwoIdHere,,Campaign Two,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignTwoIdHere,,Campaign Two,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignTwoIdHere,,Campaign Two,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignTwoIdHere,CampaignTwoIdHere,,Campaign One,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignThreeIdHere,,Campaign Three,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignThreeIdHere,,Campaign Three,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignThreeIdHere,,Campaign Three,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignThreeIdHere,CampaignThreeIdHere,,Campaign Three,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
```

> [!NOTE] With Bing Ads Campaign Management API version 11 the response message for [AddAdGroupCriterions](~/campaign-api/addadgroupcriterions-service-operation.md), [DeleteAdGroupCriterions](~/campaign-api/deleteadgroupcriterions-service-operation.md), [UpdateAdGroupCriterions](~/campaign-api/updateadgroupcriterions-service-operation.md), [AddCampaignCriterions](~/campaign-api/addcampaigncriterions-service-operation.md), [DeleteCampaignCriterions](~/campaign-api/deletecampaigncriterions-service-operation.md), and [UpdateCampaignCriterions](~/campaign-api/updatecampaigncriterions-service-operation.md) each include the *IsMigrated* element. The *IsMigrated* element indicates whether or not the campaign or ad group where you added, deleted, or updated target criterions previously shared target criterions with another campaign or ad group. If *IsMigrated* is set to *true*, it indicates that the service migrated the shared target associations and assigned new criterion IDs. If you already have criterion IDs for targets such as age, day and time, device, gender, and location, then you should replace those IDs with all of the new IDs returned by the [GetAdGroupCriterionsByIds](~/campaign-api/getadgroupcriterionsbyids-service-operation.md) or [GetCampaignCriterionsByIds](~/campaign-api/getcampaigncriterionsbyids-service-operation.md) operation (specify *TargetCriterions* as the *CriterionType*). You only need to sync target criterion IDs, as other criterion types such as webpage criterions are not migrated.

### <a name="migrationexampleb"></a>Migration Example B
As previously mentioned support for targets will end no later than the sunset of Bing Ads API version 10. Without the target data model in version 10, there will come a time when you can be sure the targets and underlying criterions can no longer be shared by multiple campaigns or ad groups. Even before version 10 sunsets, if your application is the only application that manages targets for an account then you might already have confidence that no additional targets will be shared. With that in mind, this example describes how you can migrate all remaining shared targets to criterions with unique identifiers. Again, if you have confidence that no further target sharing will occur, you might rightly consider this a one time or final shared target migration.   

As shown in [Migration Example A](#migrationexamplea) we will first download the campaign's target criterions using Bing Ads API version 11, Bulk file format 5.0, and we can see that with the exception of location intent criterion even the underlying criterions (*201*, *202*, and *203*) are shared by all three of the campaigns. This time we will simply round trip the file i.e. upload the same file with no changes.

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignOneIdHere,,Campaign One,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignOneIdHere,,Campaign One,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignOneIdHere,,Campaign One,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignOneIdHere,CampaignOneIdHere,,Campaign One,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignTwoIdHere,,Campaign Two,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignTwoIdHere,,Campaign Two,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignTwoIdHere,,Campaign Two,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignTwoIdHere,CampaignTwoIdHere,,Campaign One,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignThreeIdHere,,Campaign Three,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignThreeIdHere,,Campaign Three,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignThreeIdHere,,Campaign Three,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignThreeIdHere,CampaignThreeIdHere,,Campaign Three,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
```

As a result we can see that the criterions associated with the first two campaigns (*Campaign One* and *Campaign Two*) were migrated and assigned new identifiers. The original criterions (*201*, *202*, and *203*) are only associated with *Campaign Three*. The Bulk service assigns new criterions to the first entities it modifies, and the original criterion identifiers only remain associated to last campaign or ad group.

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Campaign DeviceOS Criterion,Deleted,0,CampaignOneIdHere,,,,,,,,,,,,,,,,
Campaign Location Intent Criterion,Deleted,0,CampaignOneIdHere,,,,,,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,301,CampaignOneIdHere,,Campaign One,,16:00.0,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,302,CampaignOneIdHere,,Campaign One,,16:00.0,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,303,CampaignOneIdHere,,Campaign One,,16:00.0,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignOneIdHere,CampaignOneIdHere,,Campaign One,,16:00.0,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
Campaign DeviceOS Criterion,Deleted,0,CampaignTwoIdHere,,,,,,,,,,,,,,,,
Campaign Location Intent Criterion,Deleted,0,CampaignTwoIdHere,,,,,,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,304,CampaignTwoIdHere,,Campaign Two,,16:00.0,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,305,CampaignTwoIdHere,,Campaign Two,,16:00.0,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,306,CampaignTwoIdHere,,Campaign Two,,16:00.0,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignTwoIdHere,CampaignTwoIdHere,,Campaign One,,16:00.0,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
Campaign DeviceOS Criterion,Active,201,CampaignThreeIdHere,,Campaign Three,,15:59.6,Computers,20,,,,,,,,,,
Campaign DeviceOS Criterion,Active,202,CampaignThreeIdHere,,Campaign Three,,15:59.6,Smartphones,0,,,,,,,,,,
Campaign DeviceOS Criterion,Active,203,CampaignThreeIdHere,,Campaign Three,,15:59.6,Tablets,0,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignThreeIdHere,CampaignThreeIdHere,,Campaign Three,,15:59.6,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,
```

## <a name="criteriontypes"></a>Criterion Types
The following criterion types are supported for targeting.
*  [Age Criterion](#agecriterion)
*  [DayTime Criterion](#daytimecriterion)
*  [DeviceOS Target](#deviceoscriterion)
*  [Gender Criterion](#gendercriterion)
*  [Location Criterion](#locationcriterion)
*  [Location Intent Criterion](#locationintentcriterion)
*  [Negative Location Criterion](#negativelocationcriterion)
*  [Radius Criterion](#radiuscriterion)

> [!NOTE] Bing Ads supports other criterion types e.g. product partition and webpage. This guide is limited to criterions that you can use to target your ads by age, day and time, device, gender, and location.

### <a name="agecriterion"></a>Age Criterion
You can target customers by age so that your ads are displayed more frequently to people who will be interested in them. 

Each age criterion defines an age range for the accompanying criterion bid adjustment. If you are using the Campaign Management service, add the *AgeCriterion* to either the *BiddableCampaignCriterion* or *BiddableAdGroupCriterion* objects. If you are using the Bulk service, use either the [Campaign Age Criterion](Campaign%20Age%20Criterion.md) or [Ad Group Age Criterion](Ad%20Group%20Age%20Criterion.md) records. 

The maximum number of age criterions that you can specify per campaign or ad group is five, i.e. one for each of the supported age ranges *EighteenToTwentyFour*, *TwentyFiveToThirtyFour*, *ThirtyFiveToFortyNine*, *FiftyToSixtyFour*, and *SixtyFiveAndAbove*.

**Note:** In Bulk file format version 4.0, the supported age ranges were *EighteenToTwentyFive*, *TwentyFiveToThirtyFive*, *ThirtyFiveToFifty*, *FiftyToSixtyFive*, and *SixtyFiveAndAbove*. For more information, see [Migrating to Bing Ads API Version 11 - Bulk - Target Criterions](../concepts/migrating-to-bing-ads-api-version-11.md#bulk_targetcriterions).

### <a name="daytimecriterion"></a>DayTime Criterion
As your campaign progresses, you may find that your click-through rate and conversion rate are highest during certain times, for example, weeknights. This might be a perfect opportunity to use bid adjustments to improve your chances of displaying your ad Monday through Friday from 6:00 P.M. to 11:00 P.M.. When targeting by time, you are targeting the searcher's local time zone. For example, if you increase your bid by 10% for 6:00 P.M. to 11:00 P.M., that bid adjustment will be effective from 6:00 P.M. to 11:00 P.M. Eastern Time for searchers in New York, then be effective 6:00 P.M. to 11:00 P.M. Pacific Time for searchers in Seattle. Now you are showing your ads when your potential customers are online!

Each day and time criterion defines the day, from hour, from minute, to hour, and to minute requirements for the accompanying criterion bid adjustment. If you are using the Campaign Management service, add the *DayTimeCriterion* to either the *BiddableCampaignCriterion* or *BiddableAdGroupCriterion* objects. If you are using the Bulk service, use either the [Campaign DayTime Criterion](Campaign%20DayTime%20Criterion.md) or [Ad Group DayTime Criterion](Ad%20Group%20DayTime%20Criterion.md) records. 

The maximum number of day and time criterions that you can specify per campaign or ad group is 49. You may not specify any overlapping day and time ranges, for example Monday from 3:00AM to 5:00AM and Monday 4:00AM to 6:00AM are not allowed for the same campaign or ad group. Also for a given campaign or ad group, the maximum number of day and time criterions per day that you can specify is seven. For example you can specify up to 7 day and time criterions where the *Day* is set to Monday. 

### <a name="deviceoscriterion"></a>DeviceOS Criterion
When you target by device, you choose to show ads to potential customers when they're using desktops and tablets or smartphones. 

Each device criterion defines a device name for the accompanying criterion bid adjustment. If you are using the Campaign Management service, add the *DeviceCriterion* to either the *BiddableCampaignCriterion* or *BiddableAdGroupCriterion* objects. If you are using the Bulk service, use either the [Campaign DeviceOS Criterion](Campaign%20DeviceOS%20Criterion.md) or [Ad Group DeviceOS Criterion](Ad%20Group%20DeviceOS%20Criterion.md) records. 

The maximum number of device criterions that you can specify per campaign or ad group is three. You must either have three separate criterions for *Computers*, *Smartphones*, and *Tablets*, otherwise no device criterions can exist for the campaign or ad group.

### <a name="gendercriterion"></a>Gender Criterion
You can target customers by gender so that your ads are displayed more frequently to people who will be interested in them. 

Each gender criterion defines a gender for the accompanying criterion bid adjustment. If you are using the Campaign Management service, add the *GenderCriterion* to either the *BiddableCampaignCriterion* or *BiddableAdGroupCriterion* objects. If you are using the Bulk service, use either the [Campaign Gender Criterion](Campaign%20Gender%20Criterion.md) or [Ad Group Gender Criterion](Ad%20Group%20Gender%20Criterion.md) records. 

The maximum number of gender criterions that you can specify per campaign or ad group is two i.e. one for *Male* and one for *Female*.

### <a name="locationcriterion"></a>Location Criterion
With location criterions, you can choose to show ads to potential customers in, searching for, or viewing pages about:
*  All available countries/regions
*  Selected cities, zip codes, metro areas, states/provinces, and countries/regions

Each location criterion defines a location code for the accompanying criterion bid adjustment. If you are using the Campaign Management service, add the *LocationCriterion* to either the *BiddableCampaignCriterion* or *BiddableAdGroupCriterion* objects. If you are using the Bulk service, use either the [Campaign Location Criterion](Campaign%20Location%20Criterion.md) or [Ad Group Location Criterion](Ad%20Group%20Location%20Criterion.md) records. 

The maximum number of combined location and negative location criterions that you can specify per campaign or ad group is 10,000.  

> [!NOTE]
> Although location criterions are most often used to designate the specific locations where you want to show your ads, [!INCLUDE[brand](../concepts/includes/brand.md)] also lets you specify locations you want to exclude from seeing your ads. To exclude a location, see [Negative Location Criterion](#negativelocationcriterion).

### <a name="locationintentcriterion"></a>Location Intent Criterion
Set the location intent criterion to *PeopleInOrSearchingForOrViewingPages* if you want to show ads to people in, searching for, or viewing pages about your targeted location. For example if the [Location Criterion](#locationcriterion) includes London and the location intent criterion is *PeopleInOrSearchingForOrViewingPages*, then someone physically located in Florida searching for London hotels will see the ad.

Set the location intent criterion to *PeopleIn* if you only want to show ads to people in your targeted location. For example if the [Location Criterion](#locationcriterion) is set to London and the location intent criterion is *PeopleIn*, then someone physically located in Florida searching for London hotels will not see the ad.

Set the location intent criterion to *PeopleSearchingForOrViewingPages* if you want to show ads to people searching for or viewing pages about your targeted location. For example if the [Location Criterion](#locationcriterion) includes London and the location intent criterion is *PeopleSearchingForOrViewingPages*, then someone physically located in Florida searching for London hotels will see the ad. Someone located in London who searches for your keywords, but does not search for or about the targeted location will not see the ads.

Each location intent criterion defines the intent option for all location and radius criterions of the campaign or ad group. There isn't any accompanying criterion bid adjustment. If you are using the Campaign Management service, add the *LocationIntentCriterion* to either the *BiddableCampaignCriterion* or *BiddableAdGroupCriterion* objects. If you are using the Bulk service, use either the [Campaign Location Intent Criterion](Campaign%20Location%20Intent%20Criterion.md) or [Ad Group Location Intent Criterion](Ad%20Group%20Location%20Intent%20Criterion.md) records. 

The maximum number of location intent criterions that you can specify per campaign or ad group is one.

For more information and examples, please see [How can I get my ads in front of my customers?](https://help.bingads.microsoft.com/#apex/3/en/51029/0).

### <a name="negativelocationcriterion"></a>Negative Location Criterion
Although location criterions are most often used to designate the specific locations where you want to show your ads, [!INCLUDE[brand](../concepts/includes/brand.md)] also lets you specify locations you want to exclude from seeing your ads.

Each negative location criterion defines a location code where you do not want your ads to show. If you are using the Campaign Management service, add the *LocationCriterion* to either the *NegativeCampaignCriterion* or *NegativeAdGroupCriterion* objects. If you are using the Bulk service, use either the [Campaign Negative Location Criterion](Campaign%20Negative%20Location%20Criterion.md) or [Ad Group Negative Location Criterion](Ad%20Group%20Negative%20Location%20Criterion.md) records. 

The maximum number of combined location and negative location criterions that you can specify per campaign or ad group is 10,000. 

> [!NOTE]
> To designate the specific locations where you want to show your ads, see [Location Criterion](#locationcriterion).

### <a name="radiuscriterion"></a>Radius Criterion
With radius criterions, you can choose to show ads to potential customers in, searching for, or viewing pages about a specified radius around a zip code, coordinates, landmark, or area.

Each radius criterion defines a radius, latitude, and longitude for the accompanying criterion bid adjustment. If you are using the Campaign Management service, add the *RadiusCriterion* to either the *BiddableCampaignCriterion* or *BiddableAdGroupCriterion* objects. If you are using the Bulk service, use either the [Campaign Radius Criterion](Campaign%20Radius%20Criterion.md) or [Ad Group Radius Criterion](Ad%20Group%20Radius%20Criterion.md) records. 

The maximum number of radius criterions that you can specify per campaign or ad group is 2,000.

## <a name="bidadjust"></a>Criterion Bid Adjustments
The ad group or keyword bid is used as the default or base bid. When you define a criterion, you can choose to adjust the base bid by a specified percentage. This is known as a bid adjustment or bid multiplier. For example, if your business sells pet supplies on the Internet, and you also have a storefront in Seattle, you can set your base bid for the "pet supplies" keyword to $1, and create a location criterion for your campaign that adjusts the bid by 50% for users in the Seattle metropolitan area. If a user in Los Angeles searches for "pet supplies", your bid for that keyword will be the base bid of $1.00. If a user in Seattle searches for "pet supplies", your bid is adjusted by 50% to $1.50. Placing a bid adjustment increases the likelihood that your ad is displayed in a better position for customers who meet your targeting criteria.

The base bid is adjusted by multipliers of the bid adjustment percentage values that you specify for each criterion type that applies to the search user. For example, say you specify a day criterion for Saturday with a 20% bid adjustment, and a Seattle metropolitan area criterion with a 30% bid adjustment. If the user resides in Seattle and searches on a Saturday, the service increases the base bid by 56%. The example is calculated as follows.

`1.00` (base bid default) `* 1.20` (day bid adjustment) `* 1.30` (location bid adjustment)`= 1.56` (56 percent adjustment)

> [!NOTE]
> After calculation, bid adjustments are rounded to two decimals of precision. For example, 1.1749 is rounded to 1.17 (17%), or 1.175 is rounded to 1.18 (18%).

> [!NOTE]
> Multiple bid adjustments across location criterions are not combined. If you specify geographically-related combinations of country/region, state/province, metropolitan area, or city criterions, the bid adjustment of the most refined criterion would apply.
> 
> For example, if the search user is located in Redmond and country is set to `US` with a 10% bid adjustment, state is set to *US-WA* with a 20% bid adjustment, metro area is set to *Seattle-Tacoma, WA, WA US* with a 30% bid adjustment, and city is set to *Redmond, Seattle-Tacoma, WA WA US* with a 40% bid adjustment, then the bid would be adjusted by 40%. If the user is located elsewhere within the Seattle-Tacoma metropolitan area, for example in Bellevue, the bid would be increased by 30%.

## <a name="defaultcriterions"></a>Default Criterion Settings
When you first create a campaign or ad group using the Bing Ads API, it will not have any criterions. Effectively the brand new campaign and ad group target all ages, days, hours, devices, genders, and locations. You should specify your minimum target criterions at the campaign level and then use ad group level criterions to narrow or refine your targeting requirements. As a best practice you should consider at minimum adding a campaign location criterion corresponding to the customer market country. 

Its worth noting that when creating campaigns via the Bing Ads web application, the recommended default criterions are added. For example if you keep the default setting in the web application e.g. *United States, Canada*, the download will include the following campaign location and campaign location intent criterions. 

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Physical Intent,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Account,,AcccountIdHere,CustomerIdHere,,,,,,,,,,,,,,,,,
Campaign Location Criterion,Active,101,CampaignIdHere,Country,CampaignNameHere,,41:34.8,32,,0,,Canada,,,,,,,,
Campaign Location Criterion,Active,102,CampaignIdHere,Country,CampaignNameHere,,41:34.8,190,,0,,United States,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignIdHere,CampaignIdHere,,CampaignNameHere,,41:34.8,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,,
```

If you choose *All available countries/regions* in the Bing Ads web application, the download will only include the following campaign location intent criterion. This is the effective equivalent of targeting all ages, days, genders, hours, and locations worldwide.

```csv
Type,Status,Id,Parent Id,Sub Type,Campaign,Client Id,Modified Time,Target,Physical Intent,Bid Adjustment,Radius Target Id,Name,Radius,Unit,From Hour,From Minute,To Hour,To Minute,Latitude,Longitude
Format Version,,,,,,,,,,,,5,,,,,,,,
Account,,AcccountIdHere,CustomerIdHere,,,,,,,,,,,,,,,,,
Campaign Location Intent Criterion,Active,CampaignIdHere,CampaignIdHere,,CampaignNameHere,,41:34.8,PeopleInOrSearchingForOrViewingPages,,,,,,,,,,,,
```

The above examples assume that you did not change any other defaults such as demographic or device settings. 

