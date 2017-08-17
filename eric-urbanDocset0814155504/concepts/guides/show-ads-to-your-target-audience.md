---
title: "Show Ads to Your Target Audience"
ms.custom: ""
ms.date: "08/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 804b06c8-805d-42b5-9a8f-fa95cb07359f
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Show Ads to Your Target Audience
Getting your ad in front of the right people; that's what targeting is all about. With targeting, [!INCLUDE[brand](../../concepts/guides/includes/brand.md)] can help you focus a campaign or ad group on potential customers who meet specific criteria, so you can increase the chance that they see your ads. You may target your ads to display to users of a certain age group, display at a certain day and time of the week, or display to users in a particular geographical location.

Targets are stored in a library that can be accessed by any campaign or ad group across all accounts within a customer. You may associate the target with one or more ad groups or campaigns. An ad group or campaign can be associated with only one target. For more information, see [Entity Hierarchy and Limits](../../concepts/entity-hierarchy-and-limits.md).

You should specify your minimum target requirements at the campaign level and then use ad group targeting to narrow or refine your targeting requirements.

-   If you specify the same target types at the ad group and campaign level, the ad group-level targets will override the campaign-level targets. For example, if the campaign location target is the U.S. and the ad group location target is California, the ads will display only to users in California. Or, if the campaign targets Mondays and Wednesdays and the ad group targets Tuesdays and Thursdays, the ads will display only on Tuesdays and Thursdays.

-   When a target type is not specified at the ad group level, that type is effectively inherited from the campaign if it exists in the campaign. For example, you can specify country targeting at the campaign level and day and time targeting at the ad group level. If the country target is set to U.S. and the day and time target is set to Monday from 11am - 3pm, then the ads will display to users in the U.S. on Mondays from 11am - 3pm.

For details about managing your targets, see the following sections.

-   [Target Types](#targettypes)

-   [Default Target Settings](#defaulttargets)

-   [Adding Targets](../../concepts/guides/show-ads-to-your-target-audience.md#Adding_Targets)

-   [Getting Targets](../../concepts/guides/show-ads-to-your-target-audience.md#Get_Target)

-   [Updating Targets](../../concepts/guides/show-ads-to-your-target-audience.md#Update_Targets)

-   [Deleting Targets](../../concepts/guides/show-ads-to-your-target-audience.md#Delete_Targets)

-   [Bid Adjustments](#bidadjust)

For code examples that show how to associate targets with a campaign and ad group using the Campaign Management service, see [C&#35;](../../concepts/code-examples/csharp-examples/targets-in-csharp.md) | [Java](../../concepts/code-examples/java-examples/targets-in-java.md) | [PHP](../../concepts/code-examples/targets-in-php.md) | [Python](../../concepts/code-examples/targets-in-python.md).

## <a name="targettypes"></a>Target Types
The sub targets in the following sections are available within the [Target](http://msdn.microsoft.com/library/800bab2c-7d1d-4f05-9ec2-e1f799667a88) object.

-   [Age Target](#agetarget)

-   [DayTime Target](#daytimetarget)

-   [DeviceOS Target](#deviceostarget)

-   [Gender Target](#gendertarget)

-   [Location Target](#locationtarget)

### <a name="agetarget"></a>Age Target
You can target customers by age so that your ads are displayed more frequently to people who will be interested in them. Use the [AgeTarget](http://msdn.microsoft.com/library/f93ffa13-9ed6-4634-91c6-7fbeff730b31) object to define a list of one or more age ranges to target your ads.

### <a name="daytimetarget"></a>DayTime Target
As your campaign progresses, you may find that your click-through rate and conversion rate are highest during certain times, for example, weeknights. This might be a perfect opportunity to use bid adjustments to improve your chances of displaying your ad Monday through Friday from 6:00 P.M. to 11:00 P.M.. When targeting by time, you are targeting the searcher's local time zone. For example, if you increase your bid by 10% for 6:00 P.M. to 11:00 P.M., that bid adjustment will be effective from 6:00 P.M. to 11:00 P.M. Eastern Time for searchers in New York, then be effective 6:00 P.M. to 11:00 P.M. Pacific Time for searchers in Seattle. Now you are showing your ads when your potential customers are online!

Use the [DayTimeTarget](http://msdn.microsoft.com/library/661202b8-9a21-487e-b344-080a6693cbcd) object to define a list of one or more days to target your ads.

> [!NOTE]
>If you had previously set up your version 9 `Target` object with separate Day and Hour elements, you can get the version 10 `Target` and it will include the equivalent [DayTimeTargetBid](http://msdn.microsoft.com/library/a24eff53-fd03-4751-b28e-167754480121) objects which maintain the intent of your day and time bids. For more information, see [Migrating to Version 10 DayTime Target](#daytimemigration).

### <a name="deviceostarget"></a>DeviceOS Target
When you target by device, you choose to show ads to potential customers when they're using desktops and tablets or smartphones. Use the [DeviceOSTarget](http://msdn.microsoft.com/library/37ae15ef-8d7d-47d0-bae4-eacba08b7e76) object to define a list of one or more devices to target your ads.

### <a name="gendertarget"></a>Gender Target
You can target customers by gender so that your ads are displayed more frequently to people who will be interested in them. Use the [GenderTarget](http://msdn.microsoft.com/library/4732ef06-6621-40ec-a448-fd16de3a82cb) object to define a list of one or both genders to target your ads.

### <a name="locationtarget"></a>Location Target
When you target by location, you can choose to show ads to potential customers in, searching for, or viewing pages about:

-   All available countries/regions

-   Selected cities, zip codes, metro areas, states/provinces, and countries/regions

-   A specified radius around a zip code, coordinates, landmark, or area

Use the [LocationTarget](http://msdn.microsoft.com/library/4349d964-0553-4d68-a53e-5011ff51a8f9) object to define a list of one or more locations to target your ads. The [LocationTarget](http://msdn.microsoft.com/library/4349d964-0553-4d68-a53e-5011ff51a8f9) object includes elements that can contain one or more of the following granular target bids.

> [!NOTE]
> Although location targeting is most often used to designate the specific locations where you want to show your ads, [!INCLUDE[brand](../../concepts/guides/includes/brand.md)] also lets you target locations you specifically want to exclude from seeing your ads. To exclude a target set the `IsExcluded` element to true within any of the following target bids except `RadiusTargetBid`. The default value for `IsExcluded` is False.

-   [CityTargetBid](http://msdn.microsoft.com/library/5ddec602-5502-4ccb-ac73-2f3a78068b52)

-   [CountryTargetBid](http://msdn.microsoft.com/library/a66ee965-4501-4b1b-980f-47433a9dd3c6)

-   [MetroAreaTargetBid](http://msdn.microsoft.com/library/f82c7df7-c89c-43df-a81d-0f1aaa1aa24d)

-   [PostalCodeTargetBid](http://msdn.microsoft.com/library/fda3134a-6d02-4867-9b12-6566f8678ea6)

    > [!NOTE]
    > To get postal code target bids, you must specify the LocationTargetVersion element as 2 or Latest when calling [GetTargetsByIds](http://msdn.microsoft.com/library/96f88bfa-f850-47b4-a788-51a54a390a94).

-   [RadiusTargetBid](http://msdn.microsoft.com/library/2f15a842-4266-463f-b8ec-dff27adf733f)

-   [StateTargetBid](http://msdn.microsoft.com/library/63b931d3-d22f-4e99-82cb-d3e30b8081b1)

For information on location codes to use for each target bid value, see [Geographical Location Codes](../../concepts/api-reference/geographical-location-codes.md).

#### Location Intent Options
Set `IntentOption` to `PeopleInOrSearchingForOrViewingPages` if you want to show ads to people in, searching for, or viewing pages about your targeted location. For example if the [LocationTarget](http://msdn.microsoft.com/library/4349d964-0553-4d68-a53e-5011ff51a8f9) includes London and `IntentOption` is `PeopleInOrSearchingForOrViewingPages`, then someone physically located in Florida searching for London hotels will see the ad.

Set `IntentOption` to `PeopleIn` if you only want to show ads to people in your targeted location. For example if the [LocationTarget](http://msdn.microsoft.com/library/4349d964-0553-4d68-a53e-5011ff51a8f9) is set to London and `IntentOption` is `PeopleIn`, then someone physically located in Florida searching for London hotels will not see the ad.

Set `IntentOption` to `PeopleSearchingForOrViewingPages` if you want to show ads to people searching for or viewing pages about your targeted location. For example if the [LocationTarget](http://msdn.microsoft.com/library/4349d964-0553-4d68-a53e-5011ff51a8f9) includes London and `IntentOption` is `PeopleSearchingForOrViewingPages`, then someone physically located in Florida searching for London hotels will see the ad. Someone located in London who searches for your keywords, but does not search for or about the targeted location will not see the ads.

For more information and examples, please see [How can I get my ads in front of my customers?](https://help.bingads.microsoft.com/#apex/3/en/51029/0-500).

## <a name="defaulttargets"></a>Default Target Settings
For campaigns and ad groups created using the [!INCLUDE[brand](../../concepts/guides/includes/brand.md)] API, there is no associated target defined by default. For example if you call [GetTargetsByCampaignIds](http://msdn.microsoft.com/library/379faa2e-6f20-4674-9fc2-466b4b3d6ac5), the response would include a nil target as follows.

```xml
\<Targets xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  \<Target i:nil="true"/>
</Targets>
```
This is the effective equivalent of targeting all ages, days, genders, hours, and locations worldwide.

As a best practice you should consider at minimum adding a location target corresponding to the customer market country. For example, by default in the [!INCLUDE[brand](../../concepts/guides/includes/brand.md)] web application, **All locations worldwide** is not the default setting. If your [Customer](http://msdn.microsoft.com/library/a4c8e03e-e494-4fb7-9dbb-3bea2f095249) market country is set to  US, then by default when creating a new campaign in the [!INCLUDE[brand](../../concepts/guides/includes/brand.md)] web application your campaign will target the United States within **Selected cities, metro areas, states/provinces, and countries/regions**. When getting targets the service will return the corresponding [LocationTarget](http://msdn.microsoft.com/library/4349d964-0553-4d68-a53e-5011ff51a8f9) as follows.

```xml
\<Targets xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
   <Target>
     \<Age i:nil="true"/>
     \<DayTime i:nil="true"/>
     \<ForwardCompatibilityMap xmlns:a="http://schemas.datacontract.org/2004/07/System.Collections.Generic"/>
     \<Gender i:nil="true"/>
     <Id>TargetIdGoesHere</Id>
     <IsLibraryTarget>true</IsLibraryTarget>
     <Location>
        \<CityTarget i:nil="true"/>
        <CountryTarget>
          <Bids>
           <CountryTargetBid>
              <BidAdjustment>0</BidAdjustment>
              <CountryAndRegion>US</CountryAndRegion>
              <IsExcluded>false</IsExcluded>
           </CountryTargetBid>
        </Bids>
        </CountryTarget>
        <IntentOption>PeopleInOrSearchingForOrViewingPages</IntentOption>
        \<MetroAreaTarget i:nil="true"/>
        \<PostalCodeTarget i:nil="true"/>
        \<RadiusTarget i:nil="true"/>
        \<StateTarget i:nil="true"/>
     </Location>
     <Name>targetgroup1</Name>
  </Target>
</Targets>
```

## <a name="Adding_Targets"></a>Adding Targets
To create a target that you can associate with an ad group or campaign, complete the following steps.

1.  Create an instance of the object that represents the desired target and assign it to the appropriate element of the [Target](http://msdn.microsoft.com/library/800bab2c-7d1d-4f05-9ec2-e1f799667a88) object. For example to target users in a specific country, create an instance of the [CountryTarget](http://msdn.microsoft.com/library/3615a843-e24c-4c54-bf7c-7022dc1c6c1b) object within the [LocationTarget](http://msdn.microsoft.com/library/4349d964-0553-4d68-a53e-5011ff51a8f9) and assign it to the target's `Location` element. Specify the target country and bid adjustment percentage by creating an instance of the [CountryTargetBid](http://msdn.microsoft.com/library/a66ee965-4501-4b1b-980f-47433a9dd3c6) object, and then assign it to the `Bids` element of the `CountryTarget`.

    > [!NOTE]
    > For information on location codes to use for each target bid value, see [Geographical Location Codes](../../concepts/api-reference/geographical-location-codes.md).

2.  To add the `Target` object to your target library, call the [AddTargetsToLibrary](http://msdn.microsoft.com/library/6e709477-2b67-420e-b865-8df78cb8f388) operation. Save or keep track of the target identifier that [AddTargetsToLibrary](http://msdn.microsoft.com/library/6e709477-2b67-420e-b865-8df78cb8f388) returns.

3.  To associate the target with a campaign, call the [SetTargetToCampaign](http://msdn.microsoft.com/library/fa0c52a0-00eb-4405-9907-54eae12eba0d) operation, passing the campaign identifier and the target identifier.

4.  To associate the target with an ad group, call the [SetTargetToAdGroup](http://msdn.microsoft.com/library/f5b73d73-fa73-4df3-828e-378a5e9bdc94) operation, passing the ad group identifier and the target identifier.

An ad group and campaign can be associated with only one target. If you try to associate more than one target with an ad group or campaign, the `SetTargetToAdGroup` and `SetTargetToCampaign` operations will throw an exception.

## <a name="Get_Target"></a>Getting Targets
You can get information about the targets that are in your library by using the [GetTargetsInfoFromLibrary](http://msdn.microsoft.com/library/6d07eda9-cb8a-4720-900d-87cf0c138763) operation. This operation returns an array of [TargetInfo](http://msdn.microsoft.com/library/378b1534-2e4d-405b-a642-f720aac5b2cb) objects for all targets in your library. The `TargetInfo` object contains only basic information, such as the identifier of the target.

To obtain more detailed information about one or more targets, use the [GetTargetsByIds](http://msdn.microsoft.com/library/96f88bfa-f850-47b4-a788-51a54a390a94) operation. This operation takes an array of target identifiers and returns the full set of information about the specified targets.

To get the targets that are associated with one or more ad groups, use the [GetTargetsByAdGroupIds](http://msdn.microsoft.com/library/98af7172-f2ac-4972-b4bb-8b87e7debc26) operation. Similarly, use the [GetTargetsByCampaignIds](http://msdn.microsoft.com/library/379faa2e-6f20-4674-9fc2-466b4b3d6ac5) operation to get the targets that are associated with one or more campaigns.

## <a name="Update_Targets"></a>Updating Targets
To update one or more targets, call the [UpdateTargetsInLibrary](http://msdn.microsoft.com/library/52b6e364-48ff-4c42-a308-f311b6093dcf) operation. Because the update operation performs a complete overwrite of the existing target, you typically call the [GetTargetsByIds](http://msdn.microsoft.com/library/96f88bfa-f850-47b4-a788-51a54a390a94) operation to get the target, modify the target as appropriate, and then call [UpdateTargetsInLibrary](http://msdn.microsoft.com/library/52b6e364-48ff-4c42-a308-f311b6093dcf).

> [!IMPORTANT]
> Partial update is not supported for targets. Any optional elements which are not sent with the update request will in effect be deleted from the target. For example, if the target contains the `DayTime` and `Location` target types and you create a [Target](http://msdn.microsoft.com/library/800bab2c-7d1d-4f05-9ec2-e1f799667a88) object and specify only the `DayTime` target type with the updated day and time, the target will contain only the `DayTime` target type after the update.

## <a name="Delete_Targets"></a>Deleting Targets
To remove the target association for an ad group, call the [DeleteTargetFromAdGroup](http://msdn.microsoft.com/library/bf1c5c8d-073d-497b-b73c-8ff8ae8e74f5) operation. To remove the target association for a campaign, call the [DeleteTargetFromCampaign](http://msdn.microsoft.com/library/69011571-86e6-4fa4-991e-95f3aed82c68) operation. These operations remove only the association between the entity and the target. The target is still retained in the library even if there is no association.

To remove a target from your library, call the [DeleteTargetsFromLibrary](http://msdn.microsoft.com/library/fc67ac37-779d-4068-afb1-99c37ffcc970) operation.

## <a name="bidadjust"></a>Bid Adjustments
The ad group or keyword bid is used as the default or base bid. When you define a target, you can choose to adjust the base bid by a specified percentage. For example, if your business sells pet supplies on the Internet, and you also have a storefront in Seattle, you can set your base bid for the "pet supplies" keyword to $1, and create a location target for your campaign that adjusts the bid by 50% for users in the Seattle metropolitan area. If a user in Los Angeles searches for "pet supplies", your bid for that keyword will be the base bid of $1.00. If a user in Seattle searches for "pet supplies", your bid is adjusted by 50% to $1.50. Placing a bid adjustment increases the likelihood that your ad is displayed in a better position for customers who meet your targeting criteria.

### <a name="multiplicativebids"></a>Multiplicative Bid Adjustments
The base bid is adjusted by multipliers of the bid adjustment percentage values that you specify for each target type that applies to the search user. For example, say you specify a day target for Saturday with a 20% bid adjustment, and a Seattle metropolitan area target with a 30% bid adjustment. If the user resides in Seattle and searches on a Saturday, the service increases the base bid by 56%. The example is calculated as follows.

`1.00` (base bid default) `* 1.20` (day bid adjustment) `* 1.30` (location bid adjustment)`= 1.56` (56 percent adjustment)

> [!NOTE]
> After calculation, bid adjustments are rounded to two decimals of precision. For example, 1.1749 is rounded to 1.17 (17%), or 1.175 is rounded to 1.18 (18%).

### Target Bid Adjustments
To adjust the bid for a target, set the corresponding `BidAdjustment` element in the following target bid objects.

> [!NOTE]
> Multiple bid adjustments across location targets are not combined. If you specify geographically-related combinations of country/region, state/province, metropolitan area, or city targets, the bid adjustment of the most refined target would apply.
> 
> For example, if the search user is located in Redmond and country is set to `US` with a 10% bid adjustment, state is set to `US-WA` with a 20% bid adjustment, metro area is set to `Seattle-Tacoma, WA, WA US` with a 30% bid adjustment, and city is set to `Redmond, Seattle-Tacoma, WA WA US` with a 40% bid adjustment, then the bid would be adjusted by 40%. If the user is located elsewhere within the Seattle-Tacoma metropolitan area, for example in Bellevue, the bid would be increased by 30%.

-   [AgeTargetBid](http://msdn.microsoft.com/library/5f791579-3d7a-40c5-8985-d34585f792fa)

-   [CityTargetBid](http://msdn.microsoft.com/library/5ddec602-5502-4ccb-ac73-2f3a78068b52)

-   [CountryTargetBid](http://msdn.microsoft.com/library/a66ee965-4501-4b1b-980f-47433a9dd3c6)

-   [DayTimeTargetBid](http://msdn.microsoft.com/library/a24eff53-fd03-4751-b28e-167754480121)

-   [DeviceOSTargetBid](http://msdn.microsoft.com/library/174af9c5-dc08-4d94-8aa5-fbc5a4e830c9)

-   [GenderTargetBid](http://msdn.microsoft.com/library/24e4e220-a6b6-4ac0-a63d-4fb3068f20e0)

-   [MetroAreaTargetBid](http://msdn.microsoft.com/library/f82c7df7-c89c-43df-a81d-0f1aaa1aa24d)

-   [PostalCodeTargetBid](http://msdn.microsoft.com/library/fda3134a-6d02-4867-9b12-6566f8678ea6)

-   [RadiusTargetBid](http://msdn.microsoft.com/library/2f15a842-4266-463f-b8ec-dff27adf733f)

-   [StateTargetBid](http://msdn.microsoft.com/library/63b931d3-d22f-4e99-82cb-d3e30b8081b1)

## <a name="daytimemigration"></a>Migrating to Version 10 DayTime Target
If you had previously set up your version 9 `Target` object with separate Day and Hour elements, you can get the version 10 `Target` and it will include the equivalent [DayTimeTargetBid](http://msdn.microsoft.com/library/a24eff53-fd03-4751-b28e-167754480121) objects which maintain the intent of your day and time bids. Let's consider the following examples where the version 9 `Monday` (day) bid adjustment is `10` percent and the version 9 `ThreeAMToSevenAM` (hour) bid adjustment is `20` percent, the number of bids will vary depending on whether you set TargetAllDays or TargetAllHours in version 9. 

If you had set `TargetAllDays=false` and `TargetAllHours=false` in version 9, then version 10 will return only 1 DayTime target that contains a bid adjustment of 32 corresponding to the [multiplied bids](#multiplicativebids) (union) of the specified v9 day and hour bids. The DayTime target bid contains: `Day` set to Monday; `FromHour` set to 3; `FromMinute` set to 0; `ToHour` set to 7; `ToMinute` set to 0. 

If you had set `TargetAllDays=true` and `TargetAllHours=false` in version 9, then version 10 will return 7 DayTime target bids. 
* 1 DayTime target will contain a bid adjustment of 32 corresponding to the [multiplied bids](#multiplicativebids) (union) of the specified v9 day and hour bids. The DayTime target bid contains: `Day` set to Monday; `FromHour` set to 3; `FromMinute` set to 0; `ToHour` set to 7; `ToMinute` set to 0. 
* 6 DayTime targets will contain a bid adjustment of 20 where only the hour matched the version 9 hour, for example where the DayTime target bid contains: `Day` set to Sunday; `FromHour` set to 3; `FromMinute` set to 0; `ToHour` set to 7; `ToMinute` set to 0.

If you had set `TargetAllDays=false` and `TargetAllHours=true` in version 9, then version 10 will return 7 DayTime target bids. 
* 1 DayTime target will contain a bid adjustment of 32 corresponding to the [multiplied bids](#multiplicativebids) (union) of the specified v9 day and hour bids. The DayTime target bid contains: `Day` set to Monday; `FromHour` set to 3; `FromMinute` set to 0; `ToHour` set to 7; `ToMinute` set to 0. 
* 6 DayTime targets will contain a bid adjustment of 10 where only the day matched the version 9 day, for example where the DayTime target bid contains: `Day` set to Monday; `FromHour` set to 0; `FromMinute` set to 0; `ToHour` set to 3; `ToMinute` set to 0.

If you had set `TargetAllDays=true` and `TargetAllHours=true` in version 9, then version 10 will return 49 DayTime target bids which represent all possible combinations of days and hour ranges. 
* 1 DayTime target will contain a bid adjustment of 32 corresponding to the [multiplied bids](#multiplicativebids) (union) of the specified v9 day and hour bids. The DayTime target bid contains: `Day` set to Monday; `FromHour` set to 3; `FromMinute` set to 0; `ToHour` set to 7; `ToMinute` set to 0. 
* 6 DayTime targets will contain a bid adjustment of 10 where only the day matched the version 9 day, for example where the DayTime target bid contains: `Day` set to Monday; `FromHour` set to 0; `FromMinute` set to 0; `ToHour` set to 3; `ToMinute` set to 0.
* 6 DayTime targets will contain a bid adjustment of 20 where only the hour matched the version 9 hour, for example where the DayTime target bid contains: `Day` set to Sunday; `FromHour` set to 3; `FromMinute` set to 0; `ToHour` set to 7; `ToMinute` set to 0.
* 36 DayTime targets will contain a bid adjustment of 0 where neither the day or hour matched the version 9 day or hour bids, for example where the DayTime target bid contains: `Day` set to Sunday; `FromHour` set to 0; `FromMinute` set to 0; `ToHour` set to 3; `ToMinute` set to 0.

> [!IMPORTANT]
> Once you or another application set the version 10 DayTime target, then the version 9 Day and Hour targets will be nil when retrieved. Any subsequent Day and Hour target updates via the version 9 [UpdateTargetsInLibrary](http://msdn.microsoft.com/library/52b6e364-48ff-4c42-a308-f311b6093dcf) operation will be accepted and overwrite a previously specified DayTime target.

> [!NOTE]
> If your ad group uses either the version 9 `DayTarget` or version 9 `HourTarget` (not both types), and then you set a version 10 [DayTimeTarget](http://msdn.microsoft.com/library/661202b8-9a21-487e-b344-080a6693cbcd) for the campaign, the [!INCLUDE[brand](../../concepts/guides/includes/brand.md)] system adds the missing `DayTarget` or `HourTarget` to the ad group.
> 
> Remember that when a target type is not specified at the ad group level, that type is effectively inherited from the campaign if it exists in the campaign. For example if you had a campaign hour target from 11am - 3pm and an ad group day target on Monday, the effective ad group delivery time is Monday, 11am - 3pm. If you then changed the campaign target to a day and time range from 1pm - 1:15pm on Tuesday, [!INCLUDE[brand](../../concepts/guides/includes/brand.md)] helps preserve your original effective delivery range of Monday, 11am - 3pm by adding an hour target of 11am - 3pm to the ad group target.

## See Also
[Campaign Management Service Reference](http://msdn.microsoft.com/library/5f50ed8a-6bca-4d30-8340-7290bc074f0e)
[Bing Ads Web Service Addresses](../../concepts/api-reference/bing-ads-web-service-addresses.md)

