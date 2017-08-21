---
title: "GetAccount Service Operation"
ms.custom: ""
ms.date: "06/28/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d2dfca9-8ff2-47a7-a717-5fad90566155
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAccount Service Operation
Gets the details of an account.

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>GetAccountRequest Message

### Request Body
The *GetAccountRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account to get.|*long*|


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
    <Action mustUnderstand="1">GetAccount</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAccountRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <AccountId></AccountId>
    </GetAccountRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAccountResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Account*|An account object that contains information about the account, such as payment method, account type, and parent customer.|[Account](../customer-api/account-data-object.md)|

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
    <GetAccountResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <Account xmlns:e15="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" p5:type="-- specify derived type here with the appropriate prefix --" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e15:AccountType></e15:AccountType>
        <e15:BillToCustomerId p5:nil="false"></e15:BillToCustomerId>
        <e15:CountryCode p5:nil="false"></e15:CountryCode>
        <e15:CurrencyType p5:nil="false"></e15:CurrencyType>
        <e15:AccountFinancialStatus p5:nil="false"></e15:AccountFinancialStatus>
        <e15:Id p5:nil="false"></e15:Id>
        <e15:Language p5:nil="false"></e15:Language>
        <ForwardCompatibilityMap xmlns:e16="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false">
          <e16:KeyValuePairOfstringstring>
            <e16:key p5:nil="false"></e16:key>
            <e16:value p5:nil="false"></e16:value>
          </e16:KeyValuePairOfstringstring>
        </ForwardCompatibilityMap>
        <e15:LastModifiedByUserId p5:nil="false"></e15:LastModifiedByUserId>
        <e15:LastModifiedTime p5:nil="false"></e15:LastModifiedTime>
        <e15:Name p5:nil="false"></e15:Name>
        <e15:Number p5:nil="false"></e15:Number>
        <e15:ParentCustomerId></e15:ParentCustomerId>
        <e15:PaymentMethodId p5:nil="false"></e15:PaymentMethodId>
        <e15:PaymentMethodType p5:nil="false"></e15:PaymentMethodType>
        <e15:PrimaryUserId p5:nil="false"></e15:PrimaryUserId>
        <e15:AccountLifeCycleStatus p5:nil="false"></e15:AccountLifeCycleStatus>
        <e15:TimeStamp p5:nil="false"></e15:TimeStamp>
        <e15:TimeZone p5:nil="false"></e15:TimeZone>
        <e15:PauseReason p5:nil="false"></e15:PauseReason>
        <!--Keep these fields if you set the i:type attribute to AdvertiserAccount-->
        <e15:LinkedAgencies p5:nil="false">
          <e15:CustomerInfo>
            <e15:Id p5:nil="false"></e15:Id>
            <e15:Name p5:nil="false"></e15:Name>
          </e15:CustomerInfo>
        </e15:LinkedAgencies>
        <e15:SalesHouseCustomerId p5:nil="false"></e15:SalesHouseCustomerId>
        <TaxInformation xmlns:e17="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false">
          <e17:KeyValuePairOfstringstring>
            <e17:key p5:nil="false"></e17:key>
            <e17:value p5:nil="false"></e17:value>
          </e17:KeyValuePairOfstringstring>
        </TaxInformation>
        <e15:BackUpPaymentInstrumentId p5:nil="false"></e15:BackUpPaymentInstrumentId>
        <e15:BillingThresholdAmount p5:nil="false"></e15:BillingThresholdAmount>
        <e15:BusinessAddress p5:nil="false">
          <e15:City p5:nil="false"></e15:City>
          <e15:CountryCode p5:nil="false"></e15:CountryCode>
          <e15:Id p5:nil="false"></e15:Id>
          <e15:Line1 p5:nil="false"></e15:Line1>
          <e15:Line2 p5:nil="false"></e15:Line2>
          <e15:Line3 p5:nil="false"></e15:Line3>
          <e15:Line4 p5:nil="false"></e15:Line4>
          <e15:PostalCode p5:nil="false"></e15:PostalCode>
          <e15:StateOrProvince p5:nil="false"></e15:StateOrProvince>
          <e15:TimeStamp p5:nil="false"></e15:TimeStamp>
        </e15:BusinessAddress>
      </Account>
    </GetAccountResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Code|
|--------|
|105|
|108|
