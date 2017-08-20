---
title: "UpdateClientLinks Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ebfb01a9-56d5-4acb-a0c4-28b964a188ef
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateClientLinks Service Operation
Updates the status of the specified client links. To update a client link, the *TimeStamp* element is required for validation, so you must first call the [SearchClientLinks](../customer-api/searchclientlinks-service-operation.md) to get the existing *ClientLink* object. Then modify the *Status* element of the returned *ClientLink*, and include the updated *ClientLink* object  in a subsequent call to the *UpdateClientLinks* operation. For more information about the client link lifecycle, see [Link to Client Accounts](http://go.microsoft.com/fwlink/?LinkId=691023).

If your user is within an agency, then the operation may be used to update the client link status of any account that you manage or have invited to manage. For more information about becoming an agency, see the [Resources for agency partners](https://advertise.bingads.microsoft.com/en-us/resources/bing-partner-program/agency-resources).

If your user is within a client customer that has one or more accounts managed or invited to be managed by an agency, then you may only use this operation to update the status as *LinkAccepted* or *LinkDeclined*. A  client may also accept or decline the link request via the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application. For more information, see [How to have an agency manage your Bing Ads account](http://help.bingads.microsoft.com/#apex/3/en/52004/3).

The role of the user calling this operation must be Super Admin. For more information, see [User Roles and Available Service Operations](http://go.microsoft.com/fwlink/?LinkId=691022).

There is no set limit to the amount of client accounts that can be linked to an agency.


> [!NOTE]
>[!INCLUDE[sandbox_clientlink](../customer-api/includes/sandbox-clientlink.md)]

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>UpdateClientLinksRequest Message

### Request Body
The *UpdateClientLinksRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ClientLinks*|The list of client links to update.<br /><br />You should limit your request to 10 client links per call.|[ClientLink](../customer-api/clientlink-data-object.md) array|

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
    <Action mustUnderstand="1">UpdateClientLinks</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateClientLinksRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <ClientLinks xmlns:e48="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e48:ClientLink>
          <e48:ClientAccountId i:nil="false"></e48:ClientAccountId>
          <e48:ClientAccountNumber i:nil="false"></e48:ClientAccountNumber>
          <e48:ManagingCustomerId i:nil="false"></e48:ManagingCustomerId>
          <e48:ManagingCustomerNumber i:nil="false"></e48:ManagingCustomerNumber>
          <e48:Note i:nil="false"></e48:Note>
          <e48:Name i:nil="false"></e48:Name>
          <e48:InviterEmail i:nil="false"></e48:InviterEmail>
          <e48:InviterName i:nil="false"></e48:InviterName>
          <e48:InviterPhone i:nil="false"></e48:InviterPhone>
          <e48:IsBillToClient></e48:IsBillToClient>
          <e48:StartDate i:nil="false"></e48:StartDate>
          <e48:Status i:nil="false"></e48:Status>
          <e48:SuppressNotification></e48:SuppressNotification>
          <e48:LastModifiedDateTime></e48:LastModifiedDateTime>
          <e48:LastModifiedByUserId></e48:LastModifiedByUserId>
          <e48:Timestamp i:nil="false"></e48:Timestamp>
          <ForwardCompatibilityMap xmlns:e49="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e49:KeyValuePairOfstringstring>
              <e49:key i:nil="false"></e49:key>
              <e49:value i:nil="false"></e49:value>
            </e49:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
        </e48:ClientLink>
      </ClientLinks>
    </UpdateClientLinksRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateClientLinksResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*OperationErrors*|A list of one or more reasons why the service operation failed, and no client links were added.|[OperationError](../customer-api/operationerror-data-object.md) array|
|*PartialErrors*|An array of *OperationError* lists that contain details for any client links that were not successfully added.<br /><br />Results are returned in the same order corresponding to the requested client links. The number of first dimension list elements is equal to the requested client links count. For successfully added client links, the *OperationError* element at the corresponding index is null.|[OperationError](../customer-api/operationerror-data-object.md) [][]|

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
    <UpdateClientLinksResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <OperationErrors xmlns:e50="https://bingads.microsoft.com/Customer/v11/Exception" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e50:OperationError>
          <e50:Code></e50:Code>
          <e50:Details p5:nil="false"></e50:Details>
          <e50:Message p5:nil="false"></e50:Message>
        </e50:OperationError>
      </OperationErrors>
      <PartialErrors xmlns:e51="https://bingads.microsoft.com/Customer/v11/Exception" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e51:ArrayOfOperationError>
          <e51:OperationError>
            <e51:Code></e51:Code>
            <e51:Details p5:nil="false"></e51:Details>
            <e51:Message p5:nil="false"></e51:Message>
          </e51:OperationError>
        </e51:ArrayOfOperationError>
      </PartialErrors>
    </UpdateClientLinksResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddClientLinks](../customer-api/addclientlinks-service-operation.md)  
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)  

