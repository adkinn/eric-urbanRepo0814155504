---
title: "GetBillingDocumentsInfo Service Operation"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 659c89cc-c3c2-42dd-b501-62313d0a3975
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBillingDocumentsInfo Service Operation
Gets a list of objects that contains billing document identification information, for example the billing document identifier, amount, and account identifier.

> [!NOTE]
> This operation will not return billing documents associated with Yahoo!-managed accounts.

||
|-|
|[!INCLUDE[bill_navigation_noremarks](../billing-api/includes/bill-navigation-noremarks.md)]|

## <a name="request"></a>GetBillingDocumentsInfoRequest Message

### Request Body
The *GetBillingDocumentsInfoRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountIds*|A list of identifiers of the accounts whose billing document information you want to get.|*long* array|
|*StartDate*|The start date to use for specifying the billing documents to get.<br /><br />The start date cannot be later than the end date. You must specify the date in Coordinated Universal Time (UTC).|*dateTime*|
|*EndDate*|The end date to use for specifying the billing documents to get.<br /><br />To specify today’s date as the end date, set *EndDate* to NULL.<br /><br />The end date cannot be earlier than the start date. You must specify the date in Coordinated Universal Time (UTC).|*dateTime*|

### Request Headers
[!INCLUDE[header_intro](../billing-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[billing_header_oauth](../billing-api/includes/billing-header-oauth.md)]
#### Password Authentication
[!INCLUDE[billing_header_password](../billing-api/includes/billing-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Billing/v11">
    <Action mustUnderstand="1">GetBillingDocumentsInfo</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetBillingDocumentsInfoRequest xmlns="https://bingads.microsoft.com/Billing/v11">
      \<AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:long>\</a1:long>
      </AccountIds>
      <StartDate></StartDate>
      \<EndDate i:nil="false"></EndDate>
    </GetBillingDocumentsInfoRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetBillingDocumentsInfoResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BillingDocumentsInfo*|The list of billing document information objects that were retrieved.|[BillingDocumentInfo](../billing-api/billingdocumentinfo-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[bill_response_header_table](../billing-api/includes/bill-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Billing/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <GetBillingDocumentsInfoResponse xmlns="https://bingads.microsoft.com/Billing/v11">
      \<BillingDocumentsInfo xmlns:e3="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e3:BillingDocumentInfo>
          \<e3:AccountId>\</e3:AccountId>
          \<e3:AccountName p5:nil="false">\</e3:AccountName>
          \<e3:AccountNumber p5:nil="false">\</e3:AccountNumber>
          \<e3:Amount>\</e3:Amount>
          \<e3:CurrencyCode p5:nil="false">\</e3:CurrencyCode>
          \<e3:DocumentDate p5:nil="false">\</e3:DocumentDate>
          \<e3:DocumentId p5:nil="false">\</e3:DocumentId>
        \</e3:BillingDocumentInfo>
      </BillingDocumentsInfo>
    </GetBillingDocumentsInfoResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[billingerror](../billing-api/includes/billingerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[GetBillingDocuments](../billing-api/getbillingdocuments-service-operation.md)

