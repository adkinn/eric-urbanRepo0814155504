---
title: "GetBudgetsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21bd4bef-f7d5-46cd-a0bc-493b578a755a
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBudgetsByIds Service Operation
Gets the specified budgets from the account's shared budget library.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetBudgetsByIdsRequest Message

### Request Body
The *GetBudgetsByIdsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*BudgetIds*|A list of unique budget identifiers that identify the budgets to get. You can specify a maximum of 100 IDs. <br/><br/>The budget IDs must be in the same account that you specified in the required *CustomerAccountId* header element.<br/><br/>If you leave this element nil or empty, then the operation will return all budgets that are available to be shared with campaigns in the account.|*long* array|Optional|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">GetBudgetsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBudgetsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <BudgetIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </BudgetIds>
    </GetBudgetsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBudgetsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Budgets*|An array of [Budget](../campaign-api/budget-data-object.md) objects that corresponds directly to the budget identifiers that you specified in the request. Items of the list may be returned as null. For each list index where a budget was not retrieved, the corresponding element will be null.|[Budget](../campaign-api/budget-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetBudgetsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Budgets p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Budget>
          <Amount p4:nil="false"></Amount>
          <AssociationCount p4:nil="false"></AssociationCount>
          <BudgetType p4:nil="false"></BudgetType>
          <Id p4:nil="false"></Id>
          <Name p4:nil="false"></Name>
        </Budget>
      </Budgets>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e108="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e108:KeyValuePairOfstringstring>
              <e108:key p4:nil="false"></e108:key>
              <e108:value p4:nil="false"></e108:value>
            </e108:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          <Message p4:nil="false"></Message>
          <Type p4:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to EditorialError-->
          <Appealable p4:nil="false"></Appealable>
          <DisapprovedText p4:nil="false"></DisapprovedText>
          <Location p4:nil="false"></Location>
          <PublisherCountry p4:nil="false"></PublisherCountry>
          <ReasonCode></ReasonCode>
        </BatchError>
      </PartialErrors>
    </GetBudgetsByIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[Budget](../campaign-api/budget-data-object.md)  
[AddBudgets](../campaign-api/addbudgets-service-operation.md)  
[DeleteBudgets](../campaign-api/deletebudgets-service-operation.md)  
[GetCampaignIdsByBudgetIds](../campaign-api/getcampaignidsbybudgetids-service-operation.md)  
[UpdateBudgets](../campaign-api/updatebudgets-service-operation.md)  

