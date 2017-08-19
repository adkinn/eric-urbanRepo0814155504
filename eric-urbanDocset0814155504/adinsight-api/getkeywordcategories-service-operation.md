---
title: "GetKeywordCategories Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 737b00ea-d159-4079-a7db-9c798e69b61d
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordCategories Service Operation
Gets the keyword categories to which the specified keywords belong.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetKeywordCategoriesRequest Message

### Request Body
The *GetKeywordCategoriesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*Keywords*|An array of keywords for which you want to determine the possible keyword categories that each keyword belongs to. The array can contain a maximum of 1,000 keywords, and each keyword can contain a maximum of 100 characters.|*string* array|Yes|
|*Language*|The language in which the keywords are written. You must set this element to English.|*string*|Yes|
|*MaxCategories*|The number of categories to include in the results. The maximum number of categories that you can request is 5.<br /><br />The default is 5.|*int*|No|
|*PublisherCountry*|The country code of the country/region to use as the source of the category data.<br /><br />**Note:** You must set this element to US.|*string*|Yes|

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
    <Action mustUnderstand="1">GetKeywordCategories</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetKeywordCategoriesRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </Keywords>
      <Language i:nil="false"></Language>
      <PublisherCountry i:nil="false"></PublisherCountry>
      <MaxCategories i:nil="false"></MaxCategories>
    </GetKeywordCategoriesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetKeywordCategoriesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Result*|An array of [KeywordCategoryResult](../adinsight-api/keywordcategoryresult-data-object.md) data objects. Each object contains the keyword and a list of categories to which it belongs.<br /><br />The list will include an item for each keyword that you specified in the request. If the keyword category cannot be determined, the *KeywordCategories* list will contain a single [KeywordCategory](../adinsight-api/keywordcategory-data-object.md). The value of *Category* will be Unknown Category and the value of *ConfidenceScore* will be 0.0.|[KeywordCategoryResult](../adinsight-api/keywordcategoryresult-data-object.md) array|

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
    <GetKeywordCategoriesResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Result xmlns:e19="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e19:KeywordCategoryResult>
          <e19:Keyword p5:nil="false"></e19:Keyword>
          <e19:KeywordCategories p5:nil="false">
            <e19:KeywordCategory>
              <e19:Category p5:nil="false"></e19:Category>
              <e19:ConfidenceScore></e19:ConfidenceScore>
            </e19:KeywordCategory>
          </e19:KeywordCategories>
        </e19:KeywordCategoryResult>
      </Result>
    </GetKeywordCategoriesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
