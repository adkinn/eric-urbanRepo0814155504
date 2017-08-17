---
title: "GetKeywordLocations Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd61063e-f3c3-45d3-b672-6e7ef3c7cb2c
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordLocations Service Operation
Gets the geographical locations of users who have searched for the specified keywords.

||
|-|
|[!INCLUDE[adint_navigation_noremarks](../adinsight-api/includes/adint-navigation-noremarks.md)]|

## <a name="request"></a>GetKeywordLocationsRequest Message

### Request Body
The *GetKeywordLocationsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Device*|A list of one or more of the following device types: Computers, NonSmartphones, Smartphones, Tablets. The default is Computers.<br /><br />The response includes keyword locations data for only the device types that you specify, if available.|*string* array|No|
|*Keywords*|An array of keywords for which you want to get geographical location information. The data is broken out by device type. The array can contain a maximum of 1,000 keywords, and each keyword can contain a maximum of 100 characters.|*string* array|Yes|
|*Language*|The language in which the keywords are written.<br /><br />For possible values, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).|*string*|Yes|
|*Level*|The level at which to aggregate the geographical location data. The following are the possible values:<br /><br />0 - Country<br /><br />1 – State/Province<br /><br />2 – Metropolitan area<br /><br />3 - City<br /><br />The default value is 1 (State/Province).|*int*|No|
|*MaxLocations*|The maximum number of locations to return. You can request a maximum of 10 locations.<br /><br />The default value is 10.|*int*|No|
|*ParentCountry*|The country from which the search originated.<br /><br />For possible values, see [Geographical Location Codes](http://go.microsoft.com/fwlink/?LinkId=691115).<br /><br />The default is US.|*string*|No|
|*PublisherCountry*|The country code of the country/region to use as the source of the location data.<br /><br />The country/region that you specify must support the language specified in the *Language* element.<br /><br />For possible values, see [Geographical Location Codes](http://go.microsoft.com/fwlink/?LinkId=691115).<br /><br />If null, the specified language determines the default publisher country. For a list of default publisher countries by language, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).|*string*|No|

### Request Headers
[!INCLUDE[header_intro](../adinsight-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[adint_header_oauth](../adinsight-api/includes/adint-header-oauth.md)]
#### Password Authentication
[!INCLUDE[adint_header_password](../adinsight-api/includes/adint-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <Action mustUnderstand="1">GetKeywordLocations</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetKeywordLocationsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </Keywords>
      <Language i:nil="false"></Language>
      <PublisherCountry i:nil="false"></PublisherCountry>
      <Device i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </Device>
      <Level i:nil="false"></Level>
      <ParentCountry i:nil="false"></ParentCountry>
      <MaxLocations i:nil="false"></MaxLocations>
    </GetKeywordLocationsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetKeywordLocationsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordLocationResult*|An array of [KeywordLocationResult](../adinsight-api/keywordlocationresult-data-object.md) data objects. The order of the items corresponds directly to the keywords specified in the request. If there is no location data available for a keyword, the keyword will be included in the list, but the *KeywordLocations* element of the corresponding [KeywordLocationResult](../adinsight-api/keywordlocationresult-data-object.md) object will be null.<br /><br />Each [KeywordLocationResult](../adinsight-api/keywordlocationresult-data-object.md) data object contains an array of [KeywordLocation](../adinsight-api/keywordlocation-data-object.md).  The array contains an item for each device specified in the request. Each [KeywordLocation](../adinsight-api/keywordlocation-data-object.md) contains the geographical location and percentage of time that users in the geographical location searched for the specified keyword.|[KeywordLocationResult](../adinsight-api/keywordlocationresult-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[adint_response_header_table](../adinsight-api/includes/adint-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetKeywordLocationsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordLocationResult xmlns:e30="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e30:KeywordLocationResult>
          <e30:Keyword p5:nil="false"></e30:Keyword>
          <e30:KeywordLocations p5:nil="false">
            <e30:KeywordLocation>
              <e30:Device p5:nil="false"></e30:Device>
              <e30:Location p5:nil="false"></e30:Location>
              <e30:Percentage></e30:Percentage>
            </e30:KeywordLocation>
          </e30:KeywordLocations>
        </e30:KeywordLocationResult>
      </KeywordLocationResult>
    </GetKeywordLocationsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
