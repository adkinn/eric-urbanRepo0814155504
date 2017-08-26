---
title: "GetConversionGoalsByTagIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e99e16c-6015-429f-84a0-779fa5c6d4a3
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetConversionGoalsByTagIds Service Operation
Gets the conversion goals that use the specified UET tags. 

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetConversionGoalsByTagIdsRequest Message

### Request Body
The *GetConversionGoalsByTagIdsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*ConversionGoalTypes*|One or more types of conversion goals to return. |[ConversionGoalType](../campaign-api/conversiongoaltype-value-set.md)|Yes|
|*TagIds*|A maximum of 100 tag identifiers that are used by the returned conversion goals. |*long* array|No|

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
    <Action mustUnderstand="1">GetConversionGoalsByTagIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetConversionGoalsByTagIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <TagIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </TagIds>
      <ConversionGoalTypes></ConversionGoalTypes>
    </GetConversionGoalsByTagIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetConversionGoalsByTagIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionGoals*|The list of conversion goals do not correspond directly to the tag identifiers specified in the request because there can be multiple conversion goals that use the same tag identifier specified in the request.|[ConversionGoal](../campaign-api/conversiongoal-data-object.md) array|
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
    <GetConversionGoalsByTagIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
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
          <ForwardCompatibilityMap xmlns:e119="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e119:KeyValuePairOfstringstring>
              <e119:key p4:nil="false"></e119:key>
              <e119:value p4:nil="false"></e119:value>
            </e119:KeyValuePairOfstringstring>
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
    </GetConversionGoalsByTagIdsResponse>
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
[GetConversionGoalsByIds](../campaign-api/getconversiongoalsbyids-service-operation.md)  
[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)  
