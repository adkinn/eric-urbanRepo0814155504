---
title: "AddClientLinks Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 83ed2a01-bbd1-40bb-91b3-1dc3a205d7fc
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddClientLinks Service Operation
Initiates the client link process to manage the account of another customer. Sends an invitation from an agency to a potential client.  For more information about the client link lifecycle, see [Link to Client Accounts](http://go.microsoft.com/fwlink/?LinkId=691023).

> [!NOTE]
> The client account must have a valid payment instrument set up for post-pay billing. Prepaid accounts are not supported for management by agencies.

Only an agency may call this service operation. For more information about becoming an agency, see the [Resources for agency partners](https://advertise.bingads.microsoft.com/en-us/resources/bing-partner-program/agency-resources).

The role of the user calling this operation must be Super Admin. For more information, see [User Roles and Available Service Operations](http://go.microsoft.com/fwlink/?LinkId=691022).

There is no set limit to the amount of client accounts that can be linked to an agency.

> [!NOTE]
>[!INCLUDE[sandbox_clientlink](../customer-api/includes/sandbox-clientlink.md)]

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>AddClientLinksRequest Message

### Request Body
The *AddClientLinksRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ClientLinks*|The list of client links to add.<br /><br />You should limit your request to 10 client links per call.|[ClientLink](../customer-api/clientlink-data-object.md) array|

### Request Headers
[!INCLUDE[header_intro](../customer-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[cusman_header_oauth](../customer-api/includes/cusman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[cusman_header_password](../customer-api/includes/cusman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <Action mustUnderstand="1">AddClientLinks</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <AddClientLinksRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      \<ClientLinks xmlns:e3="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        \<e3:ClientLink>
          \<e3:ClientAccountId i:nil="false">\</e3:ClientAccountId>
          \<e3:ClientAccountNumber i:nil="false">\</e3:ClientAccountNumber>
          \<e3:ManagingCustomerId i:nil="false">\</e3:ManagingCustomerId>
          \<e3:ManagingCustomerNumber i:nil="false">\</e3:ManagingCustomerNumber>
          \<e3:Note i:nil="false">\</e3:Note>
          \<e3:Name i:nil="false">\</e3:Name>
          \<e3:InviterEmail i:nil="false">\</e3:InviterEmail>
          \<e3:InviterName i:nil="false">\</e3:InviterName>
          \<e3:InviterPhone i:nil="false">\</e3:InviterPhone>
          \<e3:IsBillToClient>\</e3:IsBillToClient>
          \<e3:StartDate i:nil="false">\</e3:StartDate>
          \<e3:Status i:nil="false">\</e3:Status>
          \<e3:SuppressNotification>\</e3:SuppressNotification>
          \<e3:LastModifiedDateTime>\</e3:LastModifiedDateTime>
          \<e3:LastModifiedByUserId>\</e3:LastModifiedByUserId>
          \<e3:Timestamp i:nil="false">\</e3:Timestamp>
          \<ForwardCompatibilityMap xmlns:e4="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            \<e4:KeyValuePairOfstringstring>
              \<e4:key i:nil="false">\</e4:key>
              \<e4:value i:nil="false">\</e4:value>
            \</e4:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
        \</e3:ClientLink>
      </ClientLinks>
    </AddClientLinksRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>AddClientLinksResponse Message

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
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <AddClientLinksResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      \<OperationErrors xmlns:e5="https://bingads.microsoft.com/Customer/v11/Exception" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e5:OperationError>
          \<e5:Code>\</e5:Code>
          \<e5:Details p5:nil="false">\</e5:Details>
          \<e5:Message p5:nil="false">\</e5:Message>
        \</e5:OperationError>
      </OperationErrors>
      \<PartialErrors xmlns:e6="https://bingads.microsoft.com/Customer/v11/Exception" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e6:ArrayOfOperationError>
          \<e6:OperationError>
            \<e6:Code>\</e6:Code>
            \<e6:Details p5:nil="false">\</e6:Details>
            \<e6:Message p5:nil="false">\</e6:Message>
          \</e6:OperationError>
        \</e6:ArrayOfOperationError>
      </PartialErrors>
    </AddClientLinksResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)  
[UpdateClientLinks](../customer-api/updateclientlinks-service-operation.md)  

