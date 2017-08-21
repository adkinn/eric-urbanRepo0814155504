---
title: "overview with french"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be5fb821-4f23-4cd4-bc84-60332114868b
caps.latest.revision: 2
author: "eric-urban"
ms.author: "scottwhi"
---
# overview with french
To provide Bing your points of sale data, create an XML document that contains a point of sale (POS) for each booking site you support. A POS describes the POS's display name, URL, and criteria for matching the user to a POS.


The document must use UTF-8 encoding and must conform to the [pointsofsale XSD](#). 

> [!NOTE]
> Bing does not support all XSD elements. Bing ignores any element or attribute in the document that it does not support. The [Points of Sale Reference](../hotel-api/points-of-sale-reference.md) includes only those elements and attributes that Bing supports. 

> [!NOTE]
> The document must specify the elements in the order defined in the pointsofsale XSD (or as shown in the reference).

## The top-level element in your feed

The points of sale feed contains a single, top-level [pointsofsale](../hotel-api/points-of-sale-reference.md#pointsofsale) element. 

```xml
\<pointsofsale xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="http://www.gstatic.com/localfeed/local_feed.xsd">
```

The `pointsofsale` element requires a [PointOfSale](../hotel-api/points-of-sale-reference.md#pointofsaletype) child element. Specify a `PointOfSale` element for each site that users can use to book a room. 

```xml
<pointsofsale>
  <PointOfSale>
    . . .
  </PointOfSale>
  ...
</pointsofsale>
```


The `PointOfSale` element describes the POS's display name, URL, and criteria for matching the user to a POS. For information about defining a POS, see [Defining a point of sale).

## Defining a point of sale

The `pointsofsale` element contains a list of [PointOfSale](../hotel-api/points-of-sale-reference.md#pointofsaletype) elements, one for each POS site that users can use to book rooms. The list must contain points of sale for a single partner.

The following shows a `PointOfSale` element that defines a POS for English or French speaking end-users in the US or France. The POS URL includes details about the transaction, such as the check-in and check-out dates, hotel ID, and user language. Bing uses the display name and POS URL to create a hyperlink that's added to the ad. When the user clicks the link, they're taken to the booking site.

```xml
  <PointOfSale id="English-French">
    <DisplayNames display_text="ContosoTravel.com" display_language="en" />
    <DisplayNames display_text="ContosoTravel.com.fr" display_language="fr" />
    <Match status="yes" language="en" country="US" currency="USD" />
    <Match status="yes" language="fr" country="FR" currency="EUR" />
    <URL>http://partner.com/landing?hid=(PARTNER-HOTEL-ID)&amp;checkin=(CHECKINYEAR)-(CHECKINMONTH)-(CHECKINDAY)&amp;checkout=(CHECKOUTYEAR)-(CHECKOUTMONTH)-(CHECKOUTDAY)&amp;language=(USER-LANGUAGE)</URL>
  </PointOfSale>
```

For information about how Bing matches users to a POS, see [Matching points of sale](#Matching points of sale).

The following shows a complete points of sale XML document.

```xml
\<?xml version="1.0" encoding="UTF-8"?>
\<pointsofsale xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="http://www.gstatic.com/localfeed/local_feed.xsd">
  <PointOfSale id="English-French">
    <DisplayNames display_text="ContosoTravel.com" display_language="en" />
    <DisplayNames display_text="ContosoTravel.com.fr" display_language="fr" />
    <Match status="yes" language="en" country="US" currency="USD" />
    <Match status="yes" language="fr" country="FR" currency="EUR" />
    <URL>http://partner.com/landing?hid=(PARTNER-HOTEL-ID)&amp;checkin=(CHECKINYEAR)-(CHECKINMONTH)-(CHECKINDAY)&amp;checkout=(CHECKOUTYEAR)-(CHECKOUTMONTH)-(CHECKOUTDAY)&amp;language=(USER-LANGUAGE)</URL>
  </PointOfSale>
</pointsofsale>
```


## Matching points of sale

Points of sale include a `Match` element that contains the criteria used by Bing to match a user to a POS. Bing uses the following rules to find the best POS match.

- The following lists the criterion that Bing uses to match users to points of sale. 
  - country
  - currency
  - language
  - device
  
- The list is in order of preference&mdash;Bing gives the highest preference to country matches and the least preference to device matches. 

- If `Match` does not specify a criterion, Bing implicitly matches all values. For example, if `Match` specifies language and currency, Bing implicitly matches any country and device. 
  
- If `Match` specifies one or more criterion, Bing uses the POS with the most explicit matches.  
   
- If the user matches multiple points of sale, Bing uses the POS with the best match quality. If multiple points of sale have the same match quality, Bing uses the first POS that it found with that match quality. Match quality is based on:  
  - Criterion preferred order. For example, if one POS matches only on the user's currency and another matches only on the user's device, Bing uses the POS that matches the user's currency because it's higher in the preferred order.  
  - Explicit match is preferred over an implicit match. For example, if one POS matches explicitly to the user's country and another matches only implicitly to the user's country, Bing uses the POS that explicitly matches.


The `Match` element's status attribute determines whether to include or exclude the POS based on matching. If status is *never* and Bing matches all criterion, Bing will not use the POS. To exclude a POS, all criterion must match. In the following example, Bing explicitly excludes the POS if the user is from the United States or France, and implicitly includes it if the user is from any other country.

```
\<PointOfSale id='exclude-example'>
  . . .
  \<Match status='never' country='US' />
  \<Match status='never' country='FR' />
  . . .
</PointOfSale>
``` 

If status is *yes*, Bing will not eliminate any points of sale from consideration that do not explicitly match all criterion, but preference is given to the POS that matches the most criterion. In the following example, Bing explicitly matches the user to the POS if the user's country is France.

```
\<PointOfSale id='exclude-example'>
  . . .
  \<Match status='yes' country='FR' />
  . . .
</PointOfSale>
``` 

If the user's country is not France, the POS will still be considered until a better match is found. If a better match is not found, Bind will use the URL.


Bing recommends using the same matching criteria for each POS. This minimizes the complexity in determining why one POS matched over another.


## Using dynamic query parameters

A point of sale (POS) contains a `URL` element that identifies the site where users can book rooms. The URL may contain dynamic query parameters, which are parameters that contain a predefined token for its value. Bing then substitutes the token with a value before adding the URL to the ad. By using dynamic query parameters, you can include the hotel's ID, check-in date, length of stay, and more in the URL.

The following shows the syntax that you use to specify dynamic query parameters in your POS URL.

```
http://domain.com/path?param-name=(dynamic-varible-name)
```

The following are the possible dynamic variable names that you may specify in the URL.

|Name|Description
|-|-
|ADVANCE‑BOOKING‑WINDOW|The number of days in advance of the check-in date that the booking took place. For example, 36.
|CHECKINDAY|The two-digit day specified in the `Checkin` element of the Transaction Message. For example, 20.
|CHECKINDAY-OF-WEEK|The day of the week that the check-in takes place. Bing uses digits 0 through 6 to represent Monday through Sunday. For example, 1 is Tuesday.
|CHECKINMONTH|The two-digit month specified in the `Checkin` element of the Transaction Message. For example, 06.
|CHECKINYEAR|The four-digit year specified in the `Checkin` element of the Transaction Message. For example, 2017.
|CHECKOUTDAY|The two-digit day that the user checks out. Bing use the `Nights` and `Checkin` elements of the TransactionMessage to calculated the day. For example, 23.
|CHECKOUTMONTH|The two-digit month that the user checks out. Bing uses the `Nights` and `Checkin` elements of the Transaction Message to calculate the month. For example, 07.
|CHECKOUTYEAR|The four-digit year that the user checks out. Bing uses the `Nights` and `Checkin` elements of the Transaction Message to calculate the year. For example, 2017.
|CLICK-TYPE|Indicates whether the user clicked on a hotel ad or a room bundle ad. The following are the possible values.<ul><li>hotel&mdash;The user clicked on a hotel ad.</li><li>room&mdash;The user clicked on a room bundle ad.</li></ul> **NOTE:** Bing does not support the room option.
|CUSTOM[1-5]|The values of the custom fields (for example, Custom1) specified in `Result` element of the Transaction message.
|DATE-TYPE|Indicates whether the user selected the default date or specified a date when searching. The following are the possible values.<ul><li>default&mdash;The user clicked on a hotel ad that used default dates.</li><li>selected&mdash;The user clicked on a hotel ad with specified dates.</li></ul>
|BING-SITE|The Bing property that originated the ad request. The following are the possible values.<ul><li>localuniversal&mdash;The ad originated from a search results page.</li><li>mapresults&mdash;The ad originated from a maps site.</li><li>unknown&mdash;The ad originated from an undetermined source.</li></ul>
|LENGTH|The length of stay specified in the `Nights` element of the Transaction Message. For example, 3.
|NUM-ADULTS|The number of adults occupying the room. The default value is 2.
|PARTNER-CURRENCY|The three-letter currency code specified in the currency attribute of the `Baserate` element in the Transaction Message. For example, USD.
|PARTNER-HOTEL-ID|The hotel's ID specified in the `id` element of the Hotel Feed.
|PRICE-DISPLAYED-TAX|The amount of tax in the user's local currency. The tax amount is based on the `Tax` element specified in the Transaction Message. For example, 3.14. 
|PRICE‑DISPLAYED‑TOTAL|The total cost of the room in the user's local currency. The amount is based on the sum of the `Baserate`, `Tax`, and `OtherFees` elements specified in the Transaction Message. For example, 152.13.
|USER-COUNTRY|Two-letter country code of the country where the user is located. The value is extracted from the end-user's client settings. For example, US.
|USER-CURRENCY|Three-letter currency code of the local currency used by the user. The value is inferred from the end-user's client settings. For example, USD.
|USER-DEVICE|The end-user's device type. The following are the possible values.<ul><li>mobile</li><li>tablet</li><li>desktop</li><li>unknown</li></ul>The value is inferred from the end-user's client settings.
|USER-LANGUAGE|The two-letter language code that specifies the display language of the ad. The value is inferred from the end-user's client settings. For example, en.
|VERIFICATION|A Boolean that indicates whether the Bing generated the link. If Bing generated the link, the value is **true**. Otherwise, **false**.


All dates, such as CHECKINDAY, are in the hotel's timezone.

The following shows an example URL that contains dynamic query parameters and encoded entities.

```
<URL>http://www.partnerdomain.com?hotelID=(PARTNER-HOTEL-ID)
  &amp;checkinDay=(CHECKINDAY)&amp;checkinMonth=(CHECKINMONTH)
  &amp;checkinYear=(CHECKINYEAR)&amp;nights=(LENGTH)</URL>
```

Before Bing uses the URL in the ad, it substitutes values for the dynamic variable names. For example, if the user books a room for 6 nights starting on 6/7/2017 for hotel #42, Bing renders the URL as:

```
http://www.partnerdomain.com?hotelID=42&checkinDay=07&checkinMonth=06&checkinYear=2016&nights=6
```

Bing gets values for the dynamic parameters from your Transaction Message and Hotel Feed, as well as user-specific settings. For example, the value of the LENGTH variable comes from the `Nights` element in the Transaction Message, and the value of the PARTNER-HOTEL-ID variable comes from the `id` element in the Hotel Feed.

Some variables are subsets of Transaction Message elements. For example, the CHECKINDAY, CHECKINMONTH, and CHECKINYEAR variables are extracted from the `Checkin` element. Other variables are calculated based on the user's locale and other client settings.


### General URL rules

The following are general rules to follow when using dynamic variables.

- All dynamic parameters are optional. You are not required to insert any dynamic parameters in your POS URL. However, using variables to pass itinerary- and user-specific information generally creates a better experience for the end-user.
  
- Surround dynamic variable names with open and close parentheses.

- Use encoded entities for special characters. For example, replace ampersands (&amp;) with \&amp;, space with %20, and forward slash (/) with %2F.

- Values for a single parameter may be constructed from multiple variables. For example, you may construct the value of a checkinDate query parameter from the CHECKINDAY, CHECKINMONTH, and CHECKINYEAR variables.  
  ```  
  <URL>http://www.partnerdomain.com?checkinDate=(CHECKINDAY)%2F;(CHECKINMONTH)%2F;(CHECKINYEAR)</URL>  
  ```
  
- For dynamic variables that Bing recognized but does not support, Bing replaces the variable string with an empty string.
  
  
### Using conditional directives

In addition to the variables listed above, you can also use the following directives to create conditional logic.

- IF-DEFAULT-DATE&mdash;Resolves to **true** if the user clicked on a hotel ad that used default dates (the user did not pick the dates). If **true**, Bing inserts the values that follow this directive into the URL. Otherwise, Bing inserts the values following the ELSE directive.  
  
- ELSE&mdash;If the previous condition is not met, then the values that follow this directive are inserted into the URL.  
  
- ENDIF&mdash;Ends the conditional block.

For example, the following URL sets the popup_datepicker query parameter to **true** if the user used default dates instead of specifying dates.

```
<URL>http://partner.com?hotelID=(PARTNER-HOTEL-ID)
&amp;checkinDay=(CHECKINDAY)&amp;checkinMonth=(CHECKINMONTH)&amp;checkinYear=(CHECKINYEAR)
&amp;nights=(LENGTH)(IF-DEFAULT-DATE)&amp;popup_datepicker=true(ELSE)
&amp;popup_datepicker=false(ENDIF)</URL>
```

If **true**, Bing renders the URL as:

```
http://partner.com?hotelID=123&checkinDay=01&checkinMonth=07&checkinYear=2017&nights=1&popup_datepicker=true
```

Otherwise, Bing renders the URL as:

```
http://partner.com?hotelID=123&checkinDay=23&checkinMonth=07&checkinYear=2017&nights=2&popup_datepicker=false
```
