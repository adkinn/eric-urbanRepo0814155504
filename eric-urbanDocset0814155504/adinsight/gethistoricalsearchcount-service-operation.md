---
title: "GetHistoricalSearchCount Service Operation"
ms.custom: ""
ms.date: "06/21/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6ce7ede-5c61-489c-9d75-68f7bd713a4d
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetHistoricalSearchCount Service Operation
Gets the number of times the normalized term was used in a search during the specified time period. The results are aggregated by device type.

||
|-|
|[!INCLUDE[adint_navigation_noremarks](../Ad Insight Version 11/includes/adint-navigation-noremarks.md)]|

## <a name="request"></a>GetHistoricalSearchCountRequest Message

### Request Body
The *GetHistoricalSearchCountRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Devices*|A list of one or more of the following device types: Computers, NonSmartphones, Smartphones, Tablets. The default is Computers.<br /><br />The response includes search counts for the device types that you specify only, if available.|*string* array|No|
|*EndDate*|The end date of the date range that identifies the data that you want to use to determine the historical search count.<br /><br />The date cannot be later than today’s date, and must be later than or the same as the specified start date.<br /><br />The effective *EndDate* may be adjusted if the specified *TimePeriodRollup* is Weekly or Monthly.|[DayMonthAndYear](../Ad Insight Version 11/daymonthandyear-data-object.md)|Yes|
|*Keywords*|An array of keywords for which you want to determine the number of times that the keyword was used in a search query. The array can contain a maximum of 1,000 keywords, and each keyword can contain a maximum of 100 characters.|*string* array|Yes|
|*Language*|The language in which the keywords are written.<br /><br />The countries/regions that you specify in the *PublisherCountries* element must support the specified language.<br /><br />For possible values, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).|*string*|Yes|
|*PublisherCountries*|The country codes of the countries/regions to use as the source of the historical data.<br /><br />You can specify one or more country codes. Each country/region that you specify must support the language specified in the *Language* element.<br /><br />For possible values, see [Geographical Location Codes](http://go.microsoft.com/fwlink/?LinkId=691115).<br /><br />If Null, the default is all countries/regions that support the specified language.|*string* array|No|
|*StartDate*|The start date of the date range that identifies the data that you want to use to determine the historical search count.<br /><br />This date must be earlier than or the same as the specified end date. The date should be later than the maximum available historical data range corresponding to the specified *TimePeriodRollup* element.<br /><br />The effective *StartDate* may be adjusted if the specified *TimePeriodRollup* is Weekly or Monthly.|[DayMonthAndYear](../Ad Insight Version 11/daymonthandyear-data-object.md)|Yes|
|*TimePeriodRollup*|You may specify whether to return data aggregated daily, weekly, or monthly.<br /><br />For a list of supported values, see [Historical Data By Time Period](#timeperiodrollup).|*string*|No|

#### <a name="timeperiodrollup"></a>Historical Data By Time Period
The following case-sensitive values may be specified, and data will be returned as far back as the corresponding maximum available historical data range.

|TimePeriodRollup|Available Historical Data|
|--------------------|-----------------------------|
|Daily|Up to 45 days prior to the most recent completed day.|
|Weekly|Up to 15 weeks prior to the most recent completed week.<br /><br />**Note:** The specified *StartDate* is adjusted back to the nearest Sunday, and the *EndDate* is adjusted forward to the nearest Saturday.|
|Monthly|Up to 24 months prior to the most recent completed month.<br /><br />**Note:** The specified *StartDate* is adjusted back to the beginning of the month, and the *EndDate* is adjusted forward to the end of the month.|

### Request Headers
[!INCLUDE[header_intro](../Ad Insight Version 11/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[adint_header_oauth](../Ad Insight Version 11/includes/adint-header-oauth.md)]
#### Password Authentication
[!INCLUDE[adint_header_password](../Ad Insight Version 11/includes/adint-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <Action mustUnderstand="1">GetHistoricalSearchCount</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetHistoricalSearchCountRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:string>\</a1:string>
      </Keywords>
      \<Language i:nil="false"></Language>
      \<PublisherCountries i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:string>\</a1:string>
      </PublisherCountries>
      \<StartDate xmlns:e16="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" i:nil="false">
        \<e16:Day>\</e16:Day>
        \<e16:Month>\</e16:Month>
        \<e16:Year>\</e16:Year>
      </StartDate>
      \<EndDate xmlns:e17="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" i:nil="false">
        \<e17:Day>\</e17:Day>
        \<e17:Month>\</e17:Month>
        \<e17:Year>\</e17:Year>
      </EndDate>
      \<TimePeriodRollup i:nil="false"></TimePeriodRollup>
      \<Devices i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:string>\</a1:string>
      </Devices>
    </GetHistoricalSearchCountRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetHistoricalSearchCountResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordSearchCounts*|An array of [KeywordSearchCount](../Ad Insight Version 11/keywordsearchcount-data-object.md) data objects. The array contains an item for each keyword specified in the request. If the keyword is not valid, the corresponding item in the array will be null.<br /><br />Each [KeywordSearchCount](../Ad Insight Version 11/keywordsearchcount-data-object.md) contains an array of [SearchCountsByAttributes](../Ad Insight Version 11/searchcountsbyattributes-data-object.md).  The array contains an item for each unique device specified in the request.|[KeywordSearchCount](../Ad Insight Version 11/keywordsearchcount-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[adint_response_header_table](../Ad Insight Version 11/includes/adint-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <GetHistoricalSearchCountResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<KeywordSearchCounts xmlns:e18="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e18:KeywordSearchCount>
          \<e18:Keyword p5:nil="false">\</e18:Keyword>
          \<e18:SearchCountsByAttributes p5:nil="false">
            \<e18:SearchCountsByAttributes>
              \<e18:Device p5:nil="false">\</e18:Device>
              \<e18:HistoricalSearchCounts p5:nil="false">
                \<e18:HistoricalSearchCountPeriodic>
                  \<e18:SearchCount>\</e18:SearchCount>
                  \<e18:DayMonthAndYear p5:nil="false">
                    \<e18:Day>\</e18:Day>
                    \<e18:Month>\</e18:Month>
                    \<e18:Year>\</e18:Year>
                  \</e18:DayMonthAndYear>
                \</e18:HistoricalSearchCountPeriodic>
              \</e18:HistoricalSearchCounts>
            \</e18:SearchCountsByAttributes>
          \</e18:SearchCountsByAttributes>
        \</e18:KeywordSearchCount>
      </KeywordSearchCounts>
    </GetHistoricalSearchCountResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../Ad Insight Version 11/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
