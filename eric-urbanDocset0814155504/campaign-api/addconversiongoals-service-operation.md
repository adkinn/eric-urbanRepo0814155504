---
title: "AddConversionGoals Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e187b5e5-6cbf-47fb-af11-8de1af4f22c4
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddConversionGoals Service Operation
Adds new conversion goals to the account's shared conversion goal library. 

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>AddConversionGoalsRequest Message

### Request Body
The *AddConversionGoalsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionGoals*|The list of conversion goals to add to the account's shared conversion goal library.<br /><br />You can add a maximum of 100 conversion goals per service request. <br/><br/>The account is determined by the required *CustomerAccountId* header element.|[ConversionGoal](../campaign-api/conversiongoal-data-object.md) array|

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
    <Action mustUnderstand="1">AddConversionGoals</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <AddConversionGoalsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ConversionGoals i:nil="false">
        <ConversionGoal i:type="-- specify derived type here with the appropriate prefix --">
          <ConversionWindowInMinutes i:nil="false"></ConversionWindowInMinutes>
          <CountType i:nil="false"></CountType>
          <Id i:nil="false"></Id>
          <Name i:nil="false"></Name>
          <Revenue i:nil="false">
            <CurrencyCode i:nil="false"></CurrencyCode>
            <Type i:nil="false"></Type>
            <Value i:nil="false"></Value>
          </Revenue>
          <Scope i:nil="false"></Scope>
          <Status i:nil="false"></Status>
          <TagId i:nil="false"></TagId>
          <TrackingStatus i:nil="false"></TrackingStatus>
          <Type i:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to UrlGoal-->
          <UrlExpression i:nil="false"></UrlExpression>
          <UrlOperator i:nil="false"></UrlOperator>
          <!--Keep these fields if you set the i:type attribute to DurationGoal-->
          <MinimumDurationInSeconds i:nil="false"></MinimumDurationInSeconds>
          <!--Keep these fields if you set the i:type attribute to PagesViewedPerVisitGoal-->
          <MinimumPagesViewed i:nil="false"></MinimumPagesViewed>
          <!--Keep these fields if you set the i:type attribute to EventGoal-->
          <ActionExpression i:nil="false"></ActionExpression>
          <ActionOperator i:nil="false"></ActionOperator>
          <CategoryExpression i:nil="false"></CategoryExpression>
          <CategoryOperator i:nil="false"></CategoryOperator>
          <LabelExpression i:nil="false"></LabelExpression>
          <LabelOperator i:nil="false"></LabelOperator>
          <Value i:nil="false"></Value>
          <ValueOperator i:nil="false"></ValueOperator>
          <!--Keep these fields if you set the i:type attribute to AppInstallGoal-->
          <AppPlatform i:nil="false"></AppPlatform>
          <AppStoreId i:nil="false"></AppStoreId>
          <!--Keep these fields if you set the i:type attribute to OfflineConversionGoal-->
          <!--Keep these fields if you set the i:type attribute to InStoreTransactionGoal-->
        </ConversionGoal>
      </ConversionGoals>
    </AddConversionGoalsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>AddConversionGoalsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ConversionGoalIds*|A list of unique system identifiers corresponding to the conversion goals that were added.<br /><br />The list of identifiers corresponds directly to the list of conversion goals in the request. Items of the list may be returned as null. For each list index where a conversion goal was not added, the corresponding element will be null.|*long* array|
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
    <AddConversionGoalsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ConversionGoalIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </ConversionGoalIds>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e36="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e36:KeyValuePairOfstringstring>
              <e36:key p4:nil="false"></e36:key>
              <e36:value p4:nil="false"></e36:value>
            </e36:KeyValuePairOfstringstring>
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
    </AddConversionGoalsResponse>
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
[GetConversionGoalsByIds](../campaign-api/getconversiongoalsbyids-service-operation.md)  
[GetConversionGoalsByTagIds](../campaign-api/getconversiongoalsbytagids-service-operation.md)  
[UpdateConversionGoals](../campaign-api/updateconversiongoals-service-operation.md)  
