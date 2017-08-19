---
title: "GetKeywordDemographics Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 435ca0ff-bd7d-40c5-9aa8-3c8cceeae6b6
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordDemographics Service Operation
Gets the age and gender of users who have searched for the specified keywords.

[!INCLUDE[adint-service-namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetKeywordDemographicsRequest Message

### Request Body
The *GetKeywordDemographicsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Device*|A list of one or more of the following device types: Computers, NonSmartphones, Smartphones, Tablets. The default is Computers.<br /><br />The response includes keyword demographics data for the device types that you specify only, if available.|*string* array|No|
|*Keywords*|An array of keywords for which you want to get demographics data. The data is broken out by device type. The array can contain a maximum of 1,000 keywords, and each keyword can contain a maximum of 100 characters.|*string* array|Yes|
|*Language*|The language in which the keywords are written.<br /><br />For possible values, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).|*string*|Yes|
|*PublisherCountry*|The country code of the country/region to use as the source of the demographics data.<br /><br />The country/region that you specify must support the language specified in the *Language* element.<br /><br />For possible values, see [Geographical Location Codes](http://go.microsoft.com/fwlink/?LinkId=691115).<br /><br />If null, the specified language determines the default publisher country. For a list of default publisher countries by language, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).|*string*|No|

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
    <Action mustUnderstand="1">GetKeywordDemographics</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetKeywordDemographicsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </Keywords>
      <Language i:nil="false"></Language>
      <PublisherCountry i:nil="false"></PublisherCountry>
      <Device i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </Device>
    </GetKeywordDemographicsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetKeywordDemographicsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordDemographicResult*|An array of [KeywordDemographicResult](../adinsight-api/keyworddemographicresult-data-object.md) data objects. The order of the items corresponds directly to the keywords specified in the request. If there is no demographic data available for a keyword, the keyword will be included in the list, but the *KeywordDemographics* element of the corresponding [KeywordDemographicResult](../adinsight-api/keyworddemographicresult-data-object.md) will be null.<br /><br />Each [KeywordDemographicResult](../adinsight-api/keyworddemographicresult-data-object.md)  contains an array of [KeywordDemographic](../adinsight-api/keyworddemographic-data-object.md) data objects.  The array contains an item for each device specified in the request. Each [KeywordDemographic](../adinsight-api/keyworddemographic-data-object.md) contains the percentage of time that users of a certain age and gender searched for the specified keyword.|[KeywordDemographicResult](../adinsight-api/keyworddemographicresult-data-object.md) array|

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
    <GetKeywordDemographicsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordDemographicResult xmlns:e20="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e20:KeywordDemographicResult>
          <e20:Keyword p5:nil="false"></e20:Keyword>
          <e20:KeywordDemographics p5:nil="false">
            <e20:KeywordDemographic>
              <e20:Device p5:nil="false"></e20:Device>
              <e20:Age18_24></e20:Age18_24>
              <e20:Age25_34></e20:Age25_34>
              <e20:Age35_49></e20:Age35_49>
              <e20:Age50_64></e20:Age50_64>
              <e20:Age65Plus></e20:Age65Plus>
              <e20:AgeUnknown></e20:AgeUnknown>
              <e20:Female></e20:Female>
              <e20:Male></e20:Male>
              <e20:GenderUnknown></e20:GenderUnknown>
            </e20:KeywordDemographic>
          </e20:KeywordDemographics>
        </e20:KeywordDemographicResult>
      </KeywordDemographicResult>
    </GetKeywordDemographicsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
