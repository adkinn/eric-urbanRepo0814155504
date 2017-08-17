---
title: "GetKeywordIdeaCategories Service Operation"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e49f267-10f8-4751-9fd5-bcf8854a2a7e
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordIdeaCategories Service Operation
Gets the list of keyword idea categories.

You can use the *CategoryId* element of a [KeywordCategory](../Ad Insight Version 11/keywordcategory-data-object.md) as a part of the [CategorySearchParameter](../Ad Insight Version 11/categorysearchparameter-data-object.md) when calling the [GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md) operation.

||
|-|
|[!INCLUDE[adint_navigation_noremarks](../Ad Insight Version 11/includes/adint-navigation-noremarks.md)]|

## <a name="request"></a>GetKeywordIdeaCategoriesRequest Message

### Request Body
The request does not contain additional body elements.

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
    <Action mustUnderstand="1">GetKeywordIdeaCategories</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetKeywordIdeaCategoriesRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11" />
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetKeywordIdeaCategoriesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordIdeaCategories*|The list of keyword idea categories.|[KeywordIdeaCategory](../Ad Insight Version 11/keywordideacategory-data-object.md) array|

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
    <GetKeywordIdeaCategoriesResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<KeywordIdeaCategories xmlns:e21="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e21:KeywordIdeaCategory>
          \<e21:CategoryId>\</e21:CategoryId>
          \<e21:CategoryName p5:nil="false">\</e21:CategoryName>
        \</e21:KeywordIdeaCategory>
      </KeywordIdeaCategories>
    </GetKeywordIdeaCategoriesResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../Ad Insight Version 11/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
