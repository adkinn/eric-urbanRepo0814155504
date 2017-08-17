---
title: "GetCampaignIdsByBudgetIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f184b5ea-53f7-44c4-aabe-2803771e3b27
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetCampaignIdsByBudgetIds Service Operation
Gets the campaign identifiers that share each specified budget.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>GetCampaignIdsByBudgetIdsRequest Message

### Request Body
The *GetCampaignIdsByBudgetIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BudgetIds*|A list of unique budget identifiers that identify the campaign identifiers to get. You can specify a maximum of 1,000 IDs budget IDs, and each budget could be shared by up to 10,000 campaign identifiers. For each budget ID that you specify in the request, an [IdCollection](../campaign-api/idcollection-data-object.md) that contains between 1 and 10,000 campaign identifers will be returned. <br/><br/>The budget IDs must be in the same account that you specified in the required *CustomerAccountId* header element.|*long* array|

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
    <Action mustUnderstand="1">GetCampaignIdsByBudgetIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetCampaignIdsByBudgetIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <BudgetIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </BudgetIds>
    </GetCampaignIdsByBudgetIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetCampaignIdsByBudgetIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignIdCollection*|The list of campaign id collections that corresponds directly to the budget identifiers that you specified in the request. Items of the list may be returned as null. For each list index where an id collection was not retrieved, the corresponding element will be null.|[IdCollection](../campaign-api/idcollection-data-object.md) array|
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
    <GetCampaignIdsByBudgetIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <CampaignIdCollection p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <IdCollection>
          <Ids p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </Ids>
        </IdCollection>
      </CampaignIdCollection>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e112="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e112:KeyValuePairOfstringstring>
              <e112:key p4:nil="false"></e112:key>
              <e112:value p4:nil="false"></e112:value>
            </e112:KeyValuePairOfstringstring>
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
    </GetCampaignIdsByBudgetIdsResponse>
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
[GetBudgetsByIds](../campaign-api/getbudgetsbyids-service-operation.md)  
[UpdateBudgets](../campaign-api/updatebudgets-service-operation.md)  

