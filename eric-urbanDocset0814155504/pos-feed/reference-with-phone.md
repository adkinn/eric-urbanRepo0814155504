---
title: "reference with phone"
ms.custom: ""
ms.date: "08/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25820a31-cca7-409c-aae8-a5146b6d7dae
caps.latest.revision: 2
author: "eric-urban"
ms.author: "scottwhi"
---
# reference with phone
If you create hotel ads in Bing, you will use a Points of Sale feed to provide Bing the point of sale URLs to include in ads. You must define and import your points of sale feed prior to sending Bing [Transaction Messages](../hotel-api/transaction-message.md). 

For information about creating a points of sale feed, see [Creating a Poinsts of Sale Feed](../hotel-api/creating-a-points-of-sale-feed.md).

> [!NOTE]
> The elements must be specified in the order defined by the Points of Sale XSD (and as listed in this topic).

----

 
<a name="pointsofsale" /> 
## PointsOfSale
Defines the top-level element of a points of sale feed.

|Element|Description|Children
|-|-|-
|PointsOfSale|The top-level element in a points of sale feed.|[PointsOfSale Type](#pointsofsaletype)

 
<a name="pointsofsaletype" /> 
## PointsOfSale Type
Defines a list of points of sale.

|Element|Description|Children
|-|-|-
|PointOfSale|Defines a point of sale (POS) where users book rooms. Include a \<PointOfSale\> element for each POS you offer. You must define at least one POS, and all points of sale must be for a single partner.<br /><br />Attributes:<ul><li>id&mdash;Required. An opaque, user-defined ID that uniquely identifies the point of sale (POS). <br /><br />If you want to limit booking to specific POS for specific itineraries in your transaction message, use this ID in the `PointOfSale` element of your transaction message.</li></ul>|[PointOfSale Type](#pointofsaletype)


 
<a name="pointofsaletype" /> 
## PointOfSale Type
Defines a point of sale.

|Element|Description|Children
|-|-|-
|DisplayNames|Optional.<br /><br />The name of the partner or partner's domain to display in the ad. Specify a `DisplayNames` element for each language you support.<br /><br />Attributes:<ul><li>display_text&mdash;Required. The name of the partner to display in the ad.</li><li>display_language&mdash;Required. The language that the display name is specified in. Specify the language using the two-letter ISO 639 language code. For example, use **en** for English.</li></ul><br />Notes:<ul><li>Bing supports only English. The display_language attribute must be set to **en**.</li><li>Include `DisplayNames` only for online travel agencies. Don't include `DisplayNames` for central reservations system (CRS) suppliers (also known as integration partners) and direct suppliers (such as hotel owners or chains). For CRS suppliers and direct suppliers, Bing uses the hotel's name from the hotel feed.</li><li>The POS must specify a `Match` element with the same language that you specify for the display name.</li><li>Bing uses the display name and the URL in the `URL` element to create a hyperlink that Bing includes in the ad.</li></ul>|None
|Match|Required.<br />The criteria used to determine if the POS is used in the ad.<br /><br />Attributes:<ul><li>country&mdash;Optional. The country that the user or hotel must be in for the POS to be used in the ad. Specify the country using a two-letter ISO 3166 country code. For example, use **US** for United States.</li><li>language&mdash;Optional. The language that the user or hotel must use for the POS to be used in the ad. Specify the language using a two-letter ISO 639 language code. For example, use **en** for English.</li><li>currency&mdash;Optional. The currency that the user or hotel must be in for the POS to be used in the ad. Specify the currency using a three-character ISO 4217 currency code that the rate is specified in. For example, USD for US Dollar.</li><li>device&mdash;Optional. The user's device type. The following are the possible values.<ul><li>Desktop</li><li>Mobile</li><li>Tablet</li></ul></li><li>sitetype&mdash;Optional. The type of site where the ad request originated. The following are the possible values.<ul><li>LocalUniversal&mdash;The ad is being displayed as a result of a search request. </li><li>MapResults</li><li>PlacePage</li></ul></li><li>status&mdash;Optional. The condition used to match the criterion. The following are the possible values.<ul><li>Yes&mdash;Use the POS if the criteria matches.</li><li>Never&mdash;Don't use the POS if the criteria matches.</li></ul></li></ul>Notes:<ul><li>The language attribute must be set to **en**.</li><li>The country attribute must be set to **US**. </li><li>The currency attribute must be set to **USD**.</li></ul>For more information, see [POS Matching Rules](#).|None
|Phone|Optional.<br />Data type is string.<br /><br />The click-to-call telephone number to use in the ad.<br /><br />Attributes:<br /><ul><li>number&mdash;Required. The click-to-call telephone number to use in the ad. Include the "+" and country code, if applicable. </li></ul>Notes:<ul><li>The `Phone` and `URL` elements are mutually exclusive.</li><li>The POS may specify only one click-to-call telephone number.</li></ul>|[Phone Type](#phonetype)
|URL|Optional.<br />Data type is string.<br /><br/>The URL of the site where the user books the room.<br /><br /> Notes:<ul><li>The `Phone` and `URL` elements are mutually exclusive.</li><li>The POS may specify only one URL.</li><li>The URL may include five user-defined query parameters and one or more dynamic query parameters. For information about dynamic query parameters, see [Using Dynamic Query Parameters](#).</li></ul>|None

 
<a name="phonetype" /> 
## Phone Type
Defines the fees assessed by the advertiser for telephone bookings.

|Element|Description|Children
|-|-|-
|Fee|Optional.<br />Data type is decimal.<br /><br />The fee assessed by the advertiser if the user books the room by telephone. <br /><br />Attributes:<ul><li>type&mdash;Required. The type of fee charged. The following are the possible values:<br /><ul><li>booking&mdash;The fee is a flat fee for booking by phone.</li><li>per_minute&mdash;The fee is a per minute charge for booking by phone.</li></ul><li>value&mdash;The fee charged to the user for booking by phone. Depending on the fee's type, specify the flat fee or the per-minute rate. </li><li>currency&mdash;The currency that the fee is specified in. Specify the currency using a three-character ISO 4217 currency code that the rate is specified in. For example, USD for US Dollar.</li></ul>Notes:<ul><li>If there is no charge for booking by telephone, set the value attribute to 0.0.</li></ul> |None

