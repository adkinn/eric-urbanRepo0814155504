---
title: "GetAccountMonthlySpend Service Operation"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3eba2e20-10e0-4075-acd8-d8901939376c
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAccountMonthlySpend Service Operation
Gets the amount spent by the account in the specified month.

||
|-|
|[!INCLUDE[bill_navigation_noremarks](../billing-api/includes/bill-navigation-noremarks.md)]|

## <a name="request"></a>GetAccountMonthlySpendRequest Message

### Request Body
The *GetAccountMonthlySpendRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

||||
|-|-|-|
|*AccountId*|The identifier of the account that contains the spend information to get.<br /><br />The account must use the invoice payment method; credit card accounts are not supported.<br /><br />The account must be a Yahoo!-managed account.<br /><br />If the account identifier belongs to a reseller, the operation sums the account balances for all the accounts of all the customers that the reseller manages. If the reseller has ten customers and each customer has ten accounts, the operation returns the sum of the monthly spend of all 100 accounts. To get the monthly spend of a single account of a customer that the reseller manages, set the *AccountId* element to the specified account identifier. To get the monthly spend of all the accounts of a customer that the reseller manages, call this operation for each account, and then sum the monthly spend amounts.|*long*|
|*MonthYear*|The month and year for which you want to get the monthly spend information (the operation ignores the day and time values).  **Note**: The service uses the month and year components corresponding to the specified *dateTime*. For example 2013-06-15T00:00:00 and 2013-06 are both valid and will return the same results.<br /><br />If you specify the current month, the operation returns the month-to-date spend amount. For example, if the current date is June 15, 2013 and you set *MonthYear* to June 2013, the operation returns the spend amount for June 1 to June 15, inclusively.<br /><br />You cannot specify a future month and year. If you specify a prior month for which there is no data, the call returns 0 (zero).<br /><br />The spend amount can span multiple insertion orders (IOs). If the credits are greater than the actual spend, the returned monthly spend amount is a negative value.|*dateTime*|

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
    <Action mustUnderstand="1">GetAccountMonthlySpend</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAccountMonthlySpendRequest xmlns="https://bingads.microsoft.com/Billing/v11">
      <AccountId></AccountId>
      <MonthYear></MonthYear>
    </GetAccountMonthlySpendRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAccountMonthlySpendResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Amount*|The amount spent by the account in the specified period.<br /><br />The account must be Yahoo!-managed.<br /><br />If the account is not Yahoo!-managed, the return value is 0.|*double*|

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
    <GetAccountMonthlySpendResponse xmlns="https://bingads.microsoft.com/Billing/v11">
      <Amount></Amount>
    </GetAccountMonthlySpendResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[billingerror](../billing-api/includes/billingerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
