---
title: "Geographical Location Codes"
ms.custom: na
ms.date: "07/10/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 6403f8c8-7332-4219-ade0-c7a7dcd02cee
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Geographical Location Codes
Geographical locations data can be used to for [Location Targeting](../docset-overview/show-ads-to-your-target-audience.md#locationtarget). You can call the [GetGeoLocationsFileUrl](http://msdn.microsoft.com/library/bing-ads-campaign-management-getgeolocationsfileurl.aspx) operation to get a temporary file URL that can be used to download the latest geographical locations data. You can also get the data from the [Bing Ads Developer Portal](https://developers.azure.bingads.microsoft.com/Account). You must be signed in to the developer portal with a Microsoft account user who has Bing Ads credentials. 

> [!IMPORTANT]
> As a best practice you should download the file instead of opening it directly through an application such as Microsoft Excel. If you view the locations data in a text editor, be sure to use UTF-8 encoding instead of ANSI, otherwise some characters will not be displayed accurately.

## <a name="fileformat"></a>Location Codes File Format
The comma separated value (CSV) file contains data organized in the following non-localized column headings. Only the Display Name and Descriptor columns are localized depending on the file URL used above.

> [!IMPORTANT]
> New columns may be added at any time, so your implementation must ignore unknown columns.
> 
> The order of locations is not guaranteed, so you should not take dependencies on any perceived column sort order or hierarchy.

|Column Name|Description|
|---------------|---------------|
|ID|The unique [!INCLUDE[brand](../api-reference/includes/brand.md)] system identifier for the location.|
|Code|This value can be used to set the location target.<br /><br />**Note:** If this field itself contains commas the enclosed data will be surrounded by quotes, but you should not use the quotes when setting a location target bid. For example *Seattle, Seattle-Tacoma, WA WA US* is a valid city code.|
|Display Name|The optional name that you can use to display the locations data, for example to users of your application. Vertical bars are used to separate the location components from most to least specific. For example given Seattle&#124;Washington&#124;United States the most specific component is the city of Seattle within the state of Washington of the United States.<br/><br/>**Note**: Multiple location codes can have the same display name. You must not use the display name for anything other than presentation, for example do not assume any hierarchy or take any dependencies on the display name.|
|Descriptor|The optional friendly name corresponding to the Target Type column. There is not necessarily a one to one relationship between this value and the Target Type column. You should not assume any hierarchy or take any dependencies on the descriptor.|
|Target Type|Determines the type of location target can accept the value in the Code column.|
|Replaces|Reserved for future use to indicate which location or locations are replaced by the location in this row.|
|Status|Reserved for future use to indicate whether the location in this row is active or deprecated. Currently there are no deprecated locations provided in the CSV file.|
|AdWords Location ID|The *Google AdWords*Location Criterion Id corresponding to the [!INCLUDE[brand](../api-reference/includes/brand.md)] geographical location code. You can use this for mapping [!INCLUDE[brand](../api-reference/includes/brand.md)] locations to the estimated AdWords locations.<br /><br />**Note:** This value is a heuristic estimate that can be used for mapping AdWords and [!INCLUDE[brand](../api-reference/includes/brand.md)] geographical locations.|

## <a name="codeformat"></a>Code Format
If you are constructing the codes for location targeting without using the [Location Codes File](#fileformat), please note that the value of each code is constructed using the country code as the base sub code. More specific target locations contain the sub code of its parent geographic location. You do not need to build each code using this format, and it is not recommended, since all codes are available in the [Location Codes File](#fileformat). 

Target Type  |Code Format  |Example  
---------|---------|---------
Country     |CountryCode         |US (ID 190)         
State     |StateSubCode-CountryCode         |US-WA (ID 4132)         
MetroArea (Outside of the United States)     |MetroName, MetroSubCode CountryCode         |Brest, E FR (ID 4150)         
MetroArea (United States)     |MetroName, MetroSubCode, MetroSubCode CountryCode         |Seattle-Tacoma, WA, WA US (ID 71287)         
City (Outside of Australia)     |CityName, MetroAreaCode         |Chelan, Seattle-Tacoma, WA WA US (ID 67386)         
City (Australia)     |CityName, StateSubCode CountryCode         |Sydney, NS AU (ID 112363)         
PostalCode     |PostalSubCode, StateSubCode CountryCode         |98052, WA US (ID 71326)         


## See Also
[Show Ads to Your Target Audience](../docset-overview/show-ads-to-your-target-audience.md)  

