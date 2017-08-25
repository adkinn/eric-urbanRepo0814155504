---
title: "SuggestKeywordsForUrl Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08de288d-5469-49e2-968f-910359f54a91
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SuggestKeywordsForUrl Service Operation
Suggests the possible keywords for the content located at the specified URL.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>SuggestKeywordsForUrlRequest Message

### Request Body
The *SuggestKeywordsForUrlRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*ExcludeBrand*|A value that determines whether the results exclude brand keywords. To exclude brand keywords in the result, set to true. The default is false.|*boolean*|No|
|*Language*|The language used by the website.<br /><br />For possible values, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).<br /><br />The default is English.|*string*|No|
|*MaxKeywords*|A positive integer value that specifies the maximum number of keywords to return. The maximum value that you can specify is 200.<br /><br />The default is 10.|*int*|No|
|*MinConfidenceScore*|A filter value that limits the keywords that the service returns to those that have a confidence score that is greater than or equal to the specified score. For example, you can specify that you want the operation to return only keywords that have a confidence score of at least 80 percent (0.8).<br /><br />If null, the confidence score is not used to limit the results.|*double*|No|
|*Url*|The URL of the webpage to scan for possible keywords. The URL can contain a maximum of 2,000 characters.|*string*|Yes|

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
    <Action mustUnderstand="1">SuggestKeywordsForUrl</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SuggestKeywordsForUrlRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Url i:nil="false"></Url>
      <Language i:nil="false"></Language>
      <MaxKeywords i:nil="false"></MaxKeywords>
      <MinConfidenceScore i:nil="false"></MinConfidenceScore>
      <ExcludeBrand i:nil="false"></ExcludeBrand>
    </SuggestKeywordsForUrlRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SuggestKeywordsForUrlResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keywords*|An array of [KeywordAndConfidence](../adinsight-api/keywordandconfidence-data-object.md) objects that contains the possible keywords found in the content of the specified URL. In addition, the object includes a score that indicates the probability that using the keyword would result in the URL being included in the results of a search query.<br /><br />The results are sorted in order from keywords with the highest confidence score to those with the lowest confidence score.|[KeywordAndConfidence](../adinsight-api/keywordandconfidence-data-object.md) array|

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
    <SuggestKeywordsForUrlResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Keywords xmlns:e39="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e39:KeywordAndConfidence>
          <e39:SuggestedKeyword p5:nil="false"></e39:SuggestedKeyword>
          <e39:ConfidenceScore></e39:ConfidenceScore>
        </e39:KeywordAndConfidence>
      </Keywords>
    </SuggestKeywordsForUrlResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
