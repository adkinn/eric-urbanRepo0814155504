---
title: "GetDomainCategories Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 205f98de-5120-41de-b180-3efea58ec520
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetDomainCategories Service Operation
Gets the list of categories available for the website domain and language.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetDomainCategoriesRequest Message

### Request Body
The *GetDomainCategoriesRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*CategoryName*|The category name filter.<br/><br/>If you already know one or more of the categories, then you can optionally filter the list of results by sub-category. Up to three category levels can be specified, and must be separated by a forward slash ("/"). For example you can format the filter as *CategoryL1 / CategoryL2 / CategoryL3*.<br/><br/>If you do not include any category name, then all categories for the domain and language will be returned. |*string*|Optional|
|*DomainName*|The website name corresponding to the pages you want your ads to target.<br /><br />The maximum length of the domain is 2,048 characters. You do not need to include the *http*, *https*, or *www* prefix.|*string*|Required|
|*Language*|The language of the website domain. Currently only English is supported, so you must set this element to *EN*.|*string*|Required|

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
    <Action mustUnderstand="1">GetDomainCategories</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetDomainCategoriesRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <CategoryName i:nil="false"></CategoryName>
      <DomainName i:nil="false"></DomainName>
      <Language i:nil="false"></Language>
    </GetDomainCategoriesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetDomainCategoriesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Categories*|The list of domain categories.|[DomainCategory](../adinsight-api/domaincategory-data-object.md) array|

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
    <GetDomainCategoriesResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Categories xmlns:e8="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e8:DomainCategory>
          <e8:Bid></e8:Bid>
          <e8:CategoryName p5:nil="false"></e8:CategoryName>
          <e8:Coverage></e8:Coverage>
        </e8:DomainCategory>
      </Categories>
    </GetDomainCategoriesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
