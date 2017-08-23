---
title: "ref copy with all defined"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1c5b363-1812-4e70-869d-d317dd238dc8
caps.latest.revision: 2
author: "eric-urban"
ms.author: "scottwhi"
---
# ref copy with all defined
If you create hotel ads in Bing, you use transaction messages to provide Bing your itinerary data. This section describes the elements of a transaction message defined by the [Transaction XSD](../transaction-message/transaction-message-schemas.md). 

For information about creating a transaction message, see [Creating a Transaction Message](../Topic/Creating%20an%20Itinerary%20Transaction%20Message.md).

> [!NOTE]
> Bing does not support all Transaction XSD elements. Bing ignores any element or attribute in the message that it does not support. To determine which elements and attributes that Bing does not support, see [Transaction Message Reference](../transaction-message/transaction-message-reference.md) (the elements and attributes are marked as *Not supported*). 

> [!NOTE]
> The elements must be specified in the order defined in the Transaction XSD.

----

The following are the top-level elements that the [Transaction Schema](../transaction-message/transaction-message-schemas.md) defines.

|Type|Description
|-|-
|[Transaction](#transaction)|Defines the top-level element of the transaction message.


The following are the complex types that the [Transaction Schema](../transaction-message/transaction-message-schemas.md) defines.

|Type|Description
|-|-
|[allowablePointsOfSaleType](#allowablepointsofsaletype)|Defines a list of points of sale where the room may be sold.
|[localizedText](#localizedtext)|Defines a text string in a localized language.
|[multipleRatesType](#multipleratestype)|Defines a list of room rates.
|[photoUrlType](#photourltype)|Defines a photo.
|[roomPriceDataType](#roompricedatatype)|Defines the details of a hotel room, package, or bundle, depending on the context where the type is used.



The following are the simple types that the [Transaction Schema](../transaction-message/transaction-message-schemas.md) defines.

|Type|Description
|-|-
|[chargeCurrencyType](#chargecurrencytype)|Defines the possible values .



The following are the groups that the [Transaction Schema](../transaction-message/transaction-message-schemas.md) defines.

|Type|Description
|-|-
|[basicRateInfoGroup](#basicrateinfogroup)|Defines the rate, taxes, and fees of a room.
|[packageInfoGroup](#packageinfogroup)|Defines the available amenities for a room.
|[customFieldsGroup](#customfieldsgroup)|Defines custom fields for user-defined metadata.
|[hotelRateGroup](#hotelrategroup)|Defines rate metadata for a room.
|[roomRateGroup](#roomrategroup)|Defines rate metadata for a room bundle.
 
 
<a name="basicrateinfogroup" /> 
## BasicRateInfoGroup
Defines the rate, taxes, and fees of a room.  

|Element|Description|Type
|-|-|-
|Baserate|**Required**<br /><br />The room rate. This is the rate of the room for the entire stay&mdash;not the per night rate. If the rate includes fees and taxes, see the `all_inclusive` attribute.<br /><br />**Attributes**:<ul><li>all_inclusive&mdash;Optional. If the base rate includes taxes and fees, set to **true**; otherwise, **false**. The default is **false**.<br /><br />If **true**, `Tax` and `OtherFees` must be set to 0.00.<br /><br />If the hotel is located in the US or Canada, you should not set this attribute to **true**. For information, see ???.</li><li>currency&mdash;Required. The three-character currency code that the rate is specified in. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the rate from the fractional portion (for example, 150.00).</li><li>Do not use a thousands separator in the integer portion of the rate. Instead of 1,150.00, use 1150.00</li></ul>|Decimal
|ExpirationTime|**Optional**<br /><br />???|DateTime
|OtherFees|**Required**<br /><br />Any fee not covered by base rate and taxes (for example, a parking fee or portable bed fee).<br /><br />**Attributes**:<ul><li>currency&mdash;Required. The three-character currency code that the fee is specified in (for example, USD for US Dollar). For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the fee from the fractional portion (for example, 50.00).</li><li>Do not use a thousands separator in the integer portion of the fee. Instead of 1,000.00, use 1000.00</li><li>If the base rate's `all_inclusive` attribute is **true**, set this field to 0.00.</li></ul>|Decimal
|Tax|**Required**<br /><br />The tax amount.<br /><br />**Attributes**:<ul><li>currency&mdash;Required. The three-character currency code that the fee is specified in. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the tax from the fractional portion (for example, 50.00).</li><li>Do not use a thousands separator in the integer portion of the tax. Instead of 1,000.00, use 1000.00</li><li>If the base rate's `all_inclusive` attribute is **true**, set this field to 0.00.</li></ul>|Decimal



 
<a name="allowablepointsofsale" /> 
## allowablePointsOfSaleType
Defines a point of sale where the room may be sold.

|Element|Description|Type
|-|-|-
|PointOfSale|<br /><br />**Attributes**:<ul><li>id&mdash;Required. An opaque, user-defined ID that uniquely defines a POS location. This ID must match the ID of a POS defined in you Points of Sale feed file.</li></ul> |None

 
<a name="localizedtext" /> 
## localizedText
Defines a text string in a localized language.

|Element|Description|Type
|-|-|-
|Text|The localized text string.<br /><br />**Attributes**:<ul><li>language&mdash;Required. The ISO 639-1 two-character language code that the text is specified in. For example, en for English.</li><li>text&mdash;Required. The localized text string.</li></ul>|None



 
<a name="multipleratestype" /> 
## multipleRatesType
Defines a list of room rates.

|Element|Description|Type
|-|-|-
|Rate|<br /><br />**Attributes**:<ul><li>rate_rule_id&mdash;Required. An opaque, user-defined ID that identities the rule that determines whether the rate applies.</li></ul> |[roomRateGroup Type](#roomrategroup)


<a name="photourltype" /> 
## photoUrlType
Defines a photo.

|Element|Description|Type
|-|-|-
|Caption| |[localizedText](#localizedtext)
|URL| |String

 
<a name="roompricedatatype" /> 
## roomPriceDataType
Defines the details of a hotel room, package, or bundle, depending on the context where the type is used.

|Element|Description|Type
|-|-|-
|RoomData| |roomPriceDataType
|PackageData| |roomPriceDataType
|Tagline1| |[localizedText](#localizedtext)
|Tagline2| |[localizedText](#localizedtext)
|RoomID| |String
|RatePlanID| |String
|PackageID| |String
|Name| |[localizedText](#localizedtext)
|Description| |[localizedText](#localizedtext)
|PhotoURL| |[photoUrlType](#photourltype)
|Capacity|The maximum number of people that the room may hold.<br /><br />**Notes**:<ul><li>The value must be in the range 1 through 30.</li><li>The value must not be less than `Occupancy`.</li></ul>|Unsigned Integer
|Occupancy|The number of people registered to stay in the room.<br /><br />**Notes**:<ul><li>The value must be in the range 1 through 30.</li><li>The value must not be greater than `Capacity`.</li></ul>|Unsigned Integer
|ChargeCurrency|The following are the possible values.<ul><li>deposit</li><li>hotel</li><li>installment</li><li>web</li></ul>|String
|Refundable|Determines whether the room charge (for example, a deposit) is refundable. the default is any time prior to occupancy.<br /><br />**Attributes**:<ul><li>available&mdash;Required. A Boolean value that determines whether a room charge prior to occupancy is refundable. If the charge is refundable, set to **true**; otherwise, **false**.</li><li>refundable_until_days&mdash;Optional. The number of days prior to occupancy that the room charge is refundable. If not specified, the room charge is refundable any time prior to occupancy.</li><li>refundable_until_time&mdash;Optional. The time of day of the last day  that the room charge is refundable. If not specified and `refundable_until_days` is not specified, the room charge is refundable any time prior to occupancy. If not specified and `refundable_until_days` is specified, the room charge is refundable up until 11:59 PM of the last refundable day.</li></ul>|None
BreakfastIncluded|A Boolean value that determines whether the room includes breakfast. If the room includes some form of breakfast (for example, a continental breakfast), set to **true**; otherwise, **false**. The default is **false**.|Boolean
ParkingIncluded|A Boolean value that determines whether the room includes parking. If the room includes parking, set to **true**; otherwise, **false**. The default is **false**.|Boolean
InternetIncluded|A Boolean value that determines whether the room includes Internet access. If the room includes Internet access, set to **true**; otherwise, **false**. The default is **false**.|Boolean
|Baserate|**Required**<br /><br />The room rate. This is the rate of the room for the entire stay&mdash;not the per night rate. If the rate includes fees and taxes, see the `all_inclusive` attribute.<br /><br />**Attributes**:<ul><li>all_inclusive&mdash;Optional. If the base rate includes taxes and fees, set to **true**; otherwise, **false**. The default is **false**.<br /><br />If **true**, `Tax` and `OtherFees` must be set to 0.00.<br /><br />If the hotel is located in the US or Canada, you should not set this attribute to **true**. For information, see ???.</li><li>currency&mdash;Required. The three-character currency code that the rate is specified in. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the rate from the fractional portion (for example, 150.00).</li><li>Do not use a thousands separator in the integer portion of the rate. Instead of 1,150.00, use 1150.00</li></ul>|Decimal
|Tax|**Required**<br /><br />The tax amount.<br /><br />**Attributes**:<ul><li>currency&mdash;Required. The three-character currency code that the fee is specified in. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the tax from the fractional portion (for example, 50.00).</li><li>Do not use a thousands separator in the integer portion of the tax. Instead of 1,000.00, use 1000.00</li><li>If the base rate's `all_inclusive` attribute is **true**, set this field to 0.00.</li></ul>|Decimal
|OtherFees|**Required**<br /><br />Any fee not covered by base rate and taxes (for example, a parking fee or portable bed fee).<br /><br />**Attributes**:<ul><li>currency&mdash;Required. The three-character currency code that the fee is specified in (for example, USD for US Dollar). For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the fee from the fractional portion (for example, 50.00).</li><li>Do not use a thousands separator in the integer portion of the fee. Instead of 1,000.00, use 1000.00</li><li>If the base rate's `all_inclusive` attribute is **true**, set this field to 0.00.</li></ul>|Decimal
|ExpirationTime|**Optional**<br /><br />???|DateTime
|Custome1| |String
|Custome2| |String
|Custome3| |String
|Custome4| |String
|Custome5| |String
|AllowablePointsOfSale|A list of points of sale where users can book the room.|[allowablePointsOfSaleType](#allowablepointsofsaletype)
|Rates|A list of |[multipleRatesType](#multipleratestype)


 
<a name="roomrategroup" /> 
## roomRateGroup Type
Defines the rate and metadata for a room.

|Element|Description|Type
|-|-|-
|ChargeCurrency|The following are the possible values.<ul><li>deposit</li><li>hotel</li><li>installment</li><li>web</li></ul>|String
|Refundable|Determines whether the room charge (for example, a deposit) is refundable. the default is any time prior to occupancy.<br /><br />**Attributes**:<ul><li>available&mdash;Required. A Boolean value that determines whether a room charge prior to occupancy is refundable. If the charge is refundable, set to **true**; otherwise, **false**.</li><li>refundable_until_days&mdash;Optional. The number of days prior to occupancy that the room charge is refundable. If not specified, the room charge is refundable any time prior to occupancy.</li><li>refundable_until_time&mdash;Optional. The time of day of the last day  that the room charge is refundable. If not specified and `refundable_until_days` is not specified, the room charge is refundable any time prior to occupancy. If not specified and `refundable_until_days` is specified, the room charge is refundable up until 11:59 PM of the last refundable day.</li></ul>|None
BreakfastIncluded|A Boolean value that determines whether the room includes breakfast. If the room includes some form of breakfast (for example, a continental breakfast), set to **true**; otherwise, **false**. The default is **false**.|Boolean
ParkingIncluded|A Boolean value that determines whether the room includes parking. If the room includes parking, set to **true**; otherwise, **false**. The default is **false**.|Boolean
InternetIncluded|A Boolean value that determines whether the room includes Internet access. If the room includes Internet access, set to **true**; otherwise, **false**. The default is **false**.|Boolean
|Baserate|**Required**<br /><br />The room rate. This is the rate of the room for the entire stay&mdash;not the per night rate. If the rate includes fees and taxes, see the `all_inclusive` attribute.<br /><br />**Attributes**:<ul><li>all_inclusive&mdash;Optional. If the base rate includes taxes and fees, set to **true**; otherwise, **false**. The default is **false**.<br /><br />If **true**, `Tax` and `OtherFees` must be set to 0.00.<br /><br />If the hotel is located in the US or Canada, you should not set this attribute to **true**. For information, see ???.</li><li>currency&mdash;Required. The three-character currency code that the rate is specified in. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the rate from the fractional portion (for example, 150.00).</li><li>Do not use a thousands separator in the integer portion of the rate. Instead of 1,150.00, use 1150.00</li></ul>|Decimal
|Tax|**Required**<br /><br />The tax amount.<br /><br />**Attributes**:<ul><li>currency&mdash;Required. The three-character currency code that the fee is specified in. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the tax from the fractional portion (for example, 50.00).</li><li>Do not use a thousands separator in the integer portion of the tax. Instead of 1,000.00, use 1000.00</li><li>If the base rate's `all_inclusive` attribute is **true**, set this field to 0.00.</li></ul>|Decimal
|OtherFees|**Required**<br /><br />Any fee not covered by base rate and taxes (for example, a parking fee or portable bed fee).<br /><br />**Attributes**:<ul><li>currency&mdash;Required. The three-character currency code that the fee is specified in (for example, USD for US Dollar). For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>**Notes**:<ul><li>To remove the room from inventory, set this field to -1.00. You should remove the room from inventory whenever someone books the room.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the fee from the fractional portion (for example, 50.00).</li><li>Do not use a thousands separator in the integer portion of the fee. Instead of 1,000.00, use 1000.00</li><li>If the base rate's `all_inclusive` attribute is **true**, set this field to 0.00.</li></ul>|Decimal
|ExpirationTime|**Optional**<br /><br />???|DateTime
|Custome1| |String
|Custome2| |String
|Custome3| |String
|Custome4| |String
|Custome5| |String
|AllowablePointsOfSale|A list of points of sale where users can book the room.|[allowablePointsOfSaleType](#allowablepointsofsaletype)


 
<a name="transaction" /> 
## Transaction
Defines the top-level element of a transaction message.

|Element|Description|Type
|-|-|-
|Transaction|The top-level element in a transaction message.<br /><br />**Attributes**:<ul><li>timestamp&mdash;Required. The UTC date and time that you sent the message. The time stamp format is: YYYY-MM-DDThh:mm:ss[+/-hh:mm]. The UTC offset is optional. For example, 2017-06-14T08:00:34 or 2017-06-14T01:00:34+07:00.<br />The time stamp applies to each record in the message. Bing processes a record only if the record's time stamp is later than the time stamp of the same record currently in Bing. For example, if Bing processes a message with time stamp 14:10 and then processes a message with time stamp 14:09, only those records not included in the 14:10 message are processed.<br />Messages with a time stamp older than 24 hours are not processed. </li><li>id&mdash;Optional. An opaque, user-defined ID that advertisers use to identify the message.</li><li>partner&mdash;Not supported. An ID that uniquely identifies a partner.</li></ul> |[Transaction Type](#transactiontype)


 
<a name="transactiontype" /> 
## Transaction Type
Defines the transaction message.

|Element|Description|Type
|-|-|-
|PartnerData|**Not supported**. |[roomPriceDataType](#roompricedatatype)
|PropertyDataSet|**Not supported**. |[PropertyDataSet Type](#propertydataset)
|Result|A  |Array of [Result Type](#resulttype)


 
<a name="propertydataset" /> 
## PropetyDataSet Type
Defines the property's metadata.

|Element|Description|Type
|-|-|-
|Property| |String
|PropertyData| |[roomPriceDataType](#roompricedatatype)
|RoomData| |[roomPriceDataType](#roompricedatatype)
|PackageData| |[roomPriceDataType](#roompricedatatype)


 
<a name="resulttype" /> 
## Result Type
Defines the room's metadata.

|Element|Description|Type
|-|-|-
|Property|Required.<br /><br />The ID of the hotel property. This ID must match the ID of the hotel in your Hotel Feed file that you submitted to Bing. |String
|Checkin|Required.<br /><br />The check-in date in the form: YYYY-MM-DD.<br /><br />Notes:<ul><li>The date cannot be earlier that message's `timestamp` date.</li><li>The check in dates within the message must be sequential&mdash;you cannot skip dates.</li></ul> |Date
|Nights|Required.<br /><br />The number of nights to book.|Unsigned Integer
|RoomID|Not supported.<br /><br />An ID that uniquely identifies the room in the context of the property (for example, the room number). Specify this ID if you specified room metadata in a prior transaction message using `PropertyDataSet`.|String
|Baserate|Required.<br /><br />The room rate. This is the rate of the room for the entire stay&mdash;not the per night rate. If the rate includes fees and taxes, see the `all_inclusive` attribute.<br /><br />Attributes:<ul><li>all_inclusive&mdash;Optional. If the base rate includes taxes and fees, set to **true**; otherwise, **false**. The default is **false**.<br /><br />If **true**, `Tax` and `OtherFees` must be set to 0.00.<br /><br />If the hotel is located in the US or Canada, you should not set this attribute to **true**. For information, see ???.</li><li>currency&mdash;Required. The three-character currency code that the rate is specified in. For example, USD for US Dollar. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>Notes:<ul><li>To remove the itinerary from inventory, set this field, `Tax`, and `OtherFees` to -1.00. You should remove the itinerary from inventory whenever there are no more rooms available to satisfy the stay.</li><li>All currencies must use a decimal point (.) to separate the integer portion of the rate from the fractional portion (for example, 150.00).</li><li>Do not use a thousands separator in the integer portion of the rate. Instead of 1,150.00, use 1150.00</li></ul>|Decimal
|Tax|Required.<br /><br />The tax amount based on `Baserate`.<br /><br />Attributes:<ul><li>currency&mdash;Required. The three-character currency code that the fee is specified in. For example, USD for US Dollar. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>Notes:<ul><li>All currencies must use a decimal point (.) to separate the integer portion of the tax from the fractional portion (for example, 50.00).</li><li>Do not use a thousands separator in the integer portion of the tax. Instead of 1,000.00, use 1000.00</li><li>If the base rate's `all_inclusive` attribute is **true**, set this field to 0.00.</li></ul>|Decimal
|OtherFees|Required.<br /><br />Any fee not covered by base rate and taxes (for example, a parking fee or portable bed fee).<br /><br />Attributes:<ul><li>currency&mdash;Required. The three-character currency code that the fee is specified in. For example, USD for US Dollar. For a list of codes, see [ISO 4217](http://www.xe.com/iso4217.php).</li></ul>Notes:<ul><li>All currencies must use a decimal point (.) to separate the integer portion of the fee from the fractional portion (for example, 50.00).</li><li>Do not use a thousands separator in the integer portion of the fee. Instead of 1,000.00, use 1000.00</li><li>If the base rate's `all_inclusive` attribute is **true**, set this field to 0.00.</li></ul>|Decimal
|ExpirationTime|Not supported.<br /><br />???|DateTime
|ChargeCurrency|Optional.<br /><br />Defines when the user pays for a booking. The following are the possible values.<ul><li>deposit&mdash;The user is charged a portion of the booking immediately and the remainder is charged at a later point in time, typically when the user checks out of the hotel.</li><li>hotel&mdash;The user is charged when checking in at the hotel. If payment must always be made in the hotel's currency, set the value of \<ChargeCurrency\> to hotel. The actual point of sale is not affected by the user's currency.</li><li>installment&mdash;Not supported.</li><li>web&mdash;The user is charged online at the time of booking. This is the default value. The actual point of sale is defined by the Points of Sale file, and can be affected by the user's currency, location, language, or other factors.</li></ul>|String
|Custom1|Optional.<br /><br />A user-defined string. Bing uses the string as a substitution value of a simarly named dynamic query parameter in a point of sale URL. For example, http://www.partnerdomain.com?promo=(CUSTOM1). For more information, see ???.|String
|Custom2|Optional.<br /><br />A user-defined string. Bing uses the string as a substitution value of a simarly named dynamic query parameter in a point of sale URL. For example, http://www.partnerdomain.com?promo=(CUSTOM1). For more information, see ???.|String
|Custom3|Optional.<br /><br />A user-defined string. Bing uses the string as a substitution value of a simarly named dynamic query parameter in a point of sale URL. For example, http://www.partnerdomain.com?promo=(CUSTOM1). For more information, see ???.|String
|Custom4|Optional.<br /><br />A user-defined string. Bing uses the string as a substitution value of a simarly named dynamic query parameter in a point of sale URL. For example, http://www.partnerdomain.com?promo=(CUSTOM1). For more information, see ???.|String
|Custom5|Optional.<br /><br />A user-defined string. Bing uses the string as a substitution value of a simarly named dynamic query parameter in a point of sale URL. For example, http://www.partnerdomain.com?promo=(CUSTOM1). For more information, see ???.|String
|AllowablePointsOfSale|A list of points of sale (POS) where users can book the room. A POS is a website where the user can book the room. By default, the user can use any POS defined in the Points of Sale feed file. Specify this element only if you want to limit the points of sale. |Array of [allowablePointsOfSaleType](#allowablepointsofsaletype)
|Rates|Not supported.|[multipleRatesType](#multipleratestype)
|RoomBundle|Not supported.|[roomPriceDataType](#roompricedatatype)



