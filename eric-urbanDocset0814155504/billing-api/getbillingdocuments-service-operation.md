---
title: "GetBillingDocuments Service Operation"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 15af9e5c-2937-4b0d-8abc-7458a13369c2
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBillingDocuments Service Operation
Gets the specified billing documents.

> [!NOTE]
> This operation will not return billing documents associated with Yahoo!-managed accounts.

[!INCLUDE[billing_service_namespace](../billing-api/includes/billing-service-namespace.md)]

## <a name="request"></a>GetBillingDocumentsRequest Message

### Request Body
The *GetBillingDocumentsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*DocumentIds*|A list of identifiers of the billing documents to get. To get a list of identifiers, call the [GetBillingDocumentsInfo](../billing-api/getbillingdocumentsinfo-service-operation.md) operation.|*long* array|
|*Type*|The format to use to generate the billing document. For example, you can generate the billing document in PDF or XML format.|[DataType](../billing-api/datatype-value-set.md)|

### Request Headers
[!INCLUDE[header_intro](../billing-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[billing_header_oauth](../billing-api/includes/billing-header-oauth.md)]
#### Password Authentication
[!INCLUDE[billing_header_password](../billing-api/includes/billing-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Billing/v11">
    <Action mustUnderstand="1">GetBillingDocuments</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBillingDocumentsRequest xmlns="https://bingads.microsoft.com/Billing/v11">
      <DocumentIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </DocumentIds>
      <Type></Type>
    </GetBillingDocumentsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBillingDocumentsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|BillingDocuments|The list of billing documents that were retrieved.|[BillingDocument](../billing-api/billingdocument-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[bill_response_header_table](../billing-api/includes/bill-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Billing/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetBillingDocumentsResponse xmlns="https://bingads.microsoft.com/Billing/v11">
      <BillingDocuments xmlns:e2="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e2:BillingDocument>
          <e2:Data p5:nil="false"></e2:Data>
          <e2:Id></e2:Id>
          <e2:Type></e2:Type>
        </e2:BillingDocument>
      </BillingDocuments>
    </GetBillingDocumentsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[billingerror](../billing-api/includes/billingerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[GetBillingDocumentsInfo](../billing-api/getbillingdocumentsinfo-service-operation.md)

