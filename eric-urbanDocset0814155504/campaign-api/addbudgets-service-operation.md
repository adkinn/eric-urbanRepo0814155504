---
title: "AddBudgets Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4494965-a460-408b-8705-9ed9558e4863
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddBudgets Service Operation
Adds new budgets to the account's shared budget library.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddBudgetsRequest Message

### Request Body
The *AddBudgetsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Budgets*|An array of [Budget](../campaign-api/budget-data-object.md) objects to add to the account's shared budget library.<br /><br />You can add a maximum of 100 budgets in a single call. Each account's shared budget library can have up to 11,000 shared budgets.<br/><br/>The account is determined by the required *CustomerAccountId* header element.|[Budget](../campaign-api/budget-data-object.md) array|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">AddBudgets</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <AddBudgetsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<Budgets i:nil="false">
        <Budget>
          \<Amount i:nil="false"></Amount>
          \<AssociationCount i:nil="false"></AssociationCount>
          \<BudgetType i:nil="false"></BudgetType>
          \<Id i:nil="false"></Id>
          \<Name i:nil="false"></Name>
        </Budget>
      </Budgets>
    </AddBudgetsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>AddBudgetsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BudgetIds*|A list of unique system identifiers corresponding to the budgets that were added.<br /><br />The list of identifiers corresponds directly to the list of budgets in the request. Items of the list may be returned as null. For each list index where a budget was not added, the corresponding element will be null.|*long* array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <AddBudgetsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<BudgetIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<a1:long>\</a1:long>
      </BudgetIds>
      \<PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          \<Details p4:nil="false"></Details>
          \<ErrorCode p4:nil="false"></ErrorCode>
          \<FieldPath p4:nil="false"></FieldPath>
          \<ForwardCompatibilityMap xmlns:e28="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e28:KeyValuePairOfstringstring>
              \<e28:key p4:nil="false">\</e28:key>
              \<e28:value p4:nil="false">\</e28:value>
            \</e28:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          \<Message p4:nil="false"></Message>
          \<Type p4:nil="false"></Type>
          \<!--Keep these fields if you set the i:type attribute to EditorialError-->
          \<Appealable p4:nil="false"></Appealable>
          \<DisapprovedText p4:nil="false"></DisapprovedText>
          \<Location p4:nil="false"></Location>
          \<PublisherCountry p4:nil="false"></PublisherCountry>
          <ReasonCode></ReasonCode>
        </BatchError>
      </PartialErrors>
    </AddBudgetsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[Budget](../campaign-api/budget-data-object.md)  
[DeleteBudgets](../campaign-api/deletebudgets-service-operation.md)  
[GetBudgetsByIds](../campaign-api/getbudgetsbyids-service-operation.md)  
[GetCampaignIdsByBudgetIds](../campaign-api/getcampaignidsbybudgetids-service-operation.md)  
[UpdateBudgets](../campaign-api/updatebudgets-service-operation.md)  

