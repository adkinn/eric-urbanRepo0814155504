---
title: "GetHistoricalKeywordPerformance Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57c7f905-17bb-45e6-9bfc-0005726b25de
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetHistoricalKeywordPerformance Service Operation
Gets the historical performance of the normalized search term. The results are aggregated by device type.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetHistoricalKeywordPerformanceRequest Message

### Request Body
The *GetHistoricalKeywordPerformanceRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Devices*|A list of one or more of the following device types: Computers, NonSmartphones, Smartphones, Tablets. The default is Computers.<br /><br />The response includes keyword performance data for the device types that you specify only, if available.<br />Used to determine a keyword?s performance on the specified device types.|*string* array|No|
|*Keywords*|An array of keywords for which you want to get historical performance statistics. The array can contain a maximum of 1,000 keywords, and each keyword can contain a maximum of 100 characters.|*string* array|Yes|
|*Language*|The language in which the keywords are written.<br /><br />The countries/regions that you specify in the *PublisherCountries* element must support the specified language.<br /><br />For possible values, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).|*string*|Yes|
|*MatchTypes*|The match types for which you want to get historical data.<br /><br />You may not specify the Content match type.|[MatchType](../adinsight-api/matchtype-value-set.md) array|Yes|
|*PublisherCountries*|The country codes of the countries/regions to use as the source of the historical data.<br /><br />You can specify one or more country codes. Each country/region that you specify must support the language specified in the *Language* element.<br /><br />For possible values, see [Geographical Location Codes](http://go.microsoft.com/fwlink/?LinkId=691115).<br /><br />If Null, the default is all countries/regions that support the specified language.|*string* array|No|
|*TargetAdPosition*|The position of the search results for which you want to get performance data.<br /><br />For example, to get performance data when ads appeared in the first position of the mainline by using the keyword and match type, set this element to MainLine1. To get performance data when ads appeared in any position of the search results by using the keyword and match type, set this element to All.<br /><br />The default value is *All*.<br /><br />**Note:** If you specify *All* for this element, the service will return multiple results per keyword for  each supported ad position. If you specify Aggregate, the service will return one aggregated result.|[AdPosition](../adinsight-api/adposition-value-set.md)|No|
|*TimeInterval*|The time period that identifies the data to use to determine the key performance index of the specified keywords. For example, use data from the previous seven days or previous 30 days to determine the keyword performance.<br /><br />The default value is *Last7Days*.|[TimeInterval](../adinsight-api/timeinterval-value-set.md)|No|

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
    <Action mustUnderstand="1">GetHistoricalKeywordPerformance</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetHistoricalKeywordPerformanceRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </Keywords>
      <TimeInterval i:nil="false"></TimeInterval>
      <TargetAdPosition i:nil="false"></TargetAdPosition>
      <MatchTypes i:nil="false">
        <MatchType></MatchType>
      </MatchTypes>
      <Language i:nil="false"></Language>
      <PublisherCountries i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </PublisherCountries>
      <Devices i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </Devices>
    </GetHistoricalKeywordPerformanceRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetHistoricalKeywordPerformanceResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordHistoricalPerformances*|An array of [KeywordHistoricalPerformance](../adinsight-api/keywordhistoricalperformance-data-object.md) data objects. The array contains an item for each keyword, device, match type, and ad position specified in the request. If the keyword is not valid or has no data available, the corresponding item in the array will be null.|[KeywordHistoricalPerformance](../adinsight-api/keywordhistoricalperformance-data-object.md) array|

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
    <GetHistoricalKeywordPerformanceResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordHistoricalPerformances xmlns:e15="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e15:KeywordHistoricalPerformance>
          <e15:Keyword p5:nil="false"></e15:Keyword>
          <e15:KeywordKPIs p5:nil="false">
            <e15:KeywordKPI>
              <e15:Device p5:nil="false"></e15:Device>
              <e15:MatchType></e15:MatchType>
              <e15:AdPosition></e15:AdPosition>
              <e15:Clicks></e15:Clicks>
              <e15:Impressions></e15:Impressions>
              <e15:AverageCPC></e15:AverageCPC>
              <e15:CTR></e15:CTR>
              <e15:TotalCost></e15:TotalCost>
              <e15:AverageBid></e15:AverageBid>
            </e15:KeywordKPI>
          </e15:KeywordKPIs>
        </e15:KeywordHistoricalPerformance>
      </KeywordHistoricalPerformances>
    </GetHistoricalKeywordPerformanceResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
