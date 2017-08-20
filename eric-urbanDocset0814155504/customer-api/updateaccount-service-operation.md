---
title: "UpdateAccount Service Operation"
ms.custom: ""
ms.date: "07/20/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c97848c0-73c6-4c72-86c0-349eaa7d0e6d
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateAccount Service Operation
Updates the details of the specified account.

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>UpdateAccountRequest Message

### Request Body
The *UpdateAccountRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Account*|An *AdvertiserAccount* object that contains the updated account information.<br /><br />This operation overwrites the existing account data with the contents of the account object that you pass. This operation performs a full update, and not a partial update. The *Account* object must contain the time stamp value from the last time that the *Account* object was written to. To ensure that the time stamp contains the correct value, call the [GetAccount](../customer-api/getaccount-service-operation.md) operation. You can then update the account data as appropriate, and call *UpdateAccount*.|[AdvertiserAccount](../customer-api/advertiseraccount-data-object.md)|

### Request Headers
[!INCLUDE[header_intro](../customer-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[cusman_header_oauth](../customer-api/includes/cusman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[cusman_header_password](../customer-api/includes/cusman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <Action mustUnderstand="1">UpdateAccount</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateAccountRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <Account xmlns:e51="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
        <e51:AccountType></e51:AccountType>
        <e51:BillToCustomerId i:nil="false"></e51:BillToCustomerId>
        <e51:CountryCode i:nil="false"></e51:CountryCode>
        <e51:CurrencyType i:nil="false"></e51:CurrencyType>
        <e51:AccountFinancialStatus i:nil="false"></e51:AccountFinancialStatus>
        <e51:Id i:nil="false"></e51:Id>
        <e51:Language i:nil="false"></e51:Language>
        <ForwardCompatibilityMap xmlns:e52="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e52:KeyValuePairOfstringstring>
            <e52:key i:nil="false"></e52:key>
            <e52:value i:nil="false"></e52:value>
          </e52:KeyValuePairOfstringstring>
        </ForwardCompatibilityMap>
        <e51:LastModifiedByUserId i:nil="false"></e51:LastModifiedByUserId>
        <e51:LastModifiedTime i:nil="false"></e51:LastModifiedTime>
        <e51:Name i:nil="false"></e51:Name>
        <e51:Number i:nil="false"></e51:Number>
        <e51:ParentCustomerId></e51:ParentCustomerId>
        <e51:PaymentMethodId i:nil="false"></e51:PaymentMethodId>
        <e51:PaymentMethodType i:nil="false"></e51:PaymentMethodType>
        <e51:PrimaryUserId i:nil="false"></e51:PrimaryUserId>
        <e51:AccountLifeCycleStatus i:nil="false"></e51:AccountLifeCycleStatus>
        <e51:TimeStamp i:nil="false"></e51:TimeStamp>
        <e51:TimeZone i:nil="false"></e51:TimeZone>
        <e51:PauseReason i:nil="false"></e51:PauseReason>
        <!--Keep these fields if you set the i:type attribute to AdvertiserAccount-->
        <e51:LinkedAgencies i:nil="false">
          <e51:CustomerInfo>
            <e51:Id i:nil="false"></e51:Id>
            <e51:Name i:nil="false"></e51:Name>
          </e51:CustomerInfo>
        </e51:LinkedAgencies>
        <e51:SalesHouseCustomerId i:nil="false"></e51:SalesHouseCustomerId>
        <TaxInformation xmlns:e53="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e53:KeyValuePairOfstringstring>
            <e53:key i:nil="false"></e53:key>
            <e53:value i:nil="false"></e53:value>
          </e53:KeyValuePairOfstringstring>
        </TaxInformation>
        <e51:BackUpPaymentInstrumentId i:nil="false"></e51:BackUpPaymentInstrumentId>
        <e51:BillingThresholdAmount i:nil="false"></e51:BillingThresholdAmount>
        <e51:BusinessAddress i:nil="false">
          <e51:City i:nil="false"></e51:City>
          <e51:CountryCode i:nil="false"></e51:CountryCode>
          <e51:Id i:nil="false"></e51:Id>
          <e51:Line1 i:nil="false"></e51:Line1>
          <e51:Line2 i:nil="false"></e51:Line2>
          <e51:Line3 i:nil="false"></e51:Line3>
          <e51:Line4 i:nil="false"></e51:Line4>
          <e51:PostalCode i:nil="false"></e51:PostalCode>
          <e51:StateOrProvince i:nil="false"></e51:StateOrProvince>
          <e51:TimeStamp i:nil="false"></e51:TimeStamp>
        </e51:BusinessAddress>
      </Account>
    </UpdateAccountRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateAccountResponse Message

### <a name="Body_Elements"></a>Response Body
The response does not contain additional body elements.

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[cusman_response_header_table](../customer-api/includes/cusman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <UpdateAccountResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <LastModifiedTime></LastModifiedTime>
    </UpdateAccountResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Code|
|--------|
|105|
|192|
