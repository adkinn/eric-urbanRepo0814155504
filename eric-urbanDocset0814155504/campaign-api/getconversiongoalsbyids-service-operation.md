---
title: "GetConversionGoalsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88100c2e-3681-4228-b836-5bd9492d56b9
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetConversionGoalsByIds Service Operation
Gets the specified conversion goals. 

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetConversionGoalsByIdsRequest Message

### Request Body
The *GetConversionGoalsByIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*ConversionGoalTypes*|One or more types of conversion goals to return. |[ConversionGoalType](../campaign-api/conversiongoaltype-value-set.md)|Yes|
|*ConversionGoalIds*|A maximum of 100 identifiers of the conversion goals that you want to get. <br /><br />If *ConversionGoalIds* is null or empty, then you are effectively requesting all conversion goals of the specified types for the account. |*long* array|No|

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
    <Action mustUnderstand="1">GetConversionGoalsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetConversionGoalsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ConversionGoalIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </ConversionGoalIds>
      <ConversionGoalTypes></ConversionGoalTypes>
    </GetConversionGoalsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetConversionGoalsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionGoals*|An array of [ConversionGoal](../campaign-api/conversiongoal-data-object.md) objects that corresponds directly to the conversion goal identifiers that you specified in the request. Items of the array may be returned as null. For each array index where a conversion goal was not retrieved, the corresponding element will be null.|[ConversionGoal](../campaign-api/conversiongoal-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]

### <a name="response_soap"></a>Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetConversionGoalsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ConversionGoals p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <ConversionGoal p4:type="-- specify derived type here with the appropriate prefix --">
          <ConversionWindowInMinutes p4:nil="false"></ConversionWindowInMinutes>
          <CountType p4:nil="false"></CountType>
          <Id p4:nil="false"></Id>
          <Name p4:nil="false"></Name>
          <Revenue p4:nil="false">
            <CurrencyCode p4:nil="false"></CurrencyCode>
            <Type p4:nil="false"></Type>
            <Value p4:nil="false"></Value>
          </Revenue>
          <Scope p4:nil="false"></Scope>
          <Status p4:nil="false"></Status>
          <TagId p4:nil="false"></TagId>
          <TrackingStatus p4:nil="false"></TrackingStatus>
          <Type p4:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to UrlGoal-->
          <UrlExpression p4:nil="false"></UrlExpression>
          <UrlOperator p4:nil="false"></UrlOperator>
          <!--Keep these fields if you set the i:type attribute to DurationGoal-->
          <MinimumDurationInSeconds p4:nil="false"></MinimumDurationInSeconds>
          <!--Keep these fields if you set the i:type attribute to PagesViewedPerVisitGoal-->
          <MinimumPagesViewed p4:nil="false"></MinimumPagesViewed>
          <!--Keep these fields if you set the i:type attribute to EventGoal-->
          <ActionExpression p4:nil="false"></ActionExpression>
          <ActionOperator p4:nil="false"></ActionOperator>
          <CategoryExpression p4:nil="false"></CategoryExpression>
          <CategoryOperator p4:nil="false"></CategoryOperator>
          <LabelExpression p4:nil="false"></LabelExpression>
          <LabelOperator p4:nil="false"></LabelOperator>
          <Value p4:nil="false"></Value>
          <ValueOperator p4:nil="false"></ValueOperator>
          <!--Keep these fields if you set the i:type attribute to AppInstallGoal-->
          <AppPlatform p4:nil="false"></AppPlatform>
          <AppStoreId p4:nil="false"></AppStoreId>
          <!--Keep these fields if you set the i:type attribute to OfflineConversionGoal-->
          <!--Keep these fields if you set the i:type attribute to InStoreTransactionGoal-->
        </ConversionGoal>
      </ConversionGoals>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e118="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e118:KeyValuePairOfstringstring>
              <e118:key p4:nil="false"></e118:key>
              <e118:value p4:nil="false"></e118:value>
            </e118:KeyValuePairOfstringstring>
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
    </GetConversionGoalsByIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[AddConversionGoals](../campaign-api/addconversiongoals-service-operation.md)  
[GetConversionGoalsByTagIds](../campaign-api/getconversiongoalsbytagids-service-operation.md)  
[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)  
