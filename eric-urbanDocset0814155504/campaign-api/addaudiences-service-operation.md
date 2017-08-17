---
title: "AddAudiences Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7700ed5-4bde-4caa-91fe-1fe2efc1c7fa
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddAudiences Service Operation
Adds one or more audiences.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddAudiencesRequest Message

### Request Body
The *AddAudiencesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Audiences*|The list of audiences to add.<br/><br/>The maximum size of the list is 100.<br/><br/>You can only add [RemarketingList](../campaign-api/remarketinglist-data-object.md) objects. You cannot add [CustomAudience](../campaign-api/customaudience-data-object.md) or [InMarketAudience](../campaign-api/inmarketaudience-data-object.md) objects. |[Audience](../campaign-api/audience-data-object.md) array|

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
    <Action mustUnderstand="1">AddAudiences</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <AddAudiencesRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Audiences i:nil="false">
        <Audience i:type="-- specify derived type here with the appropriate prefix --">
          <Description i:nil="false"></Description>
          <ForwardCompatibilityMap xmlns:e25="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e25:KeyValuePairOfstringstring>
              <e25:key i:nil="false"></e25:key>
              <e25:value i:nil="false"></e25:value>
            </e25:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id i:nil="false"></Id>
          <MembershipDuration i:nil="false"></MembershipDuration>
          <Name i:nil="false"></Name>
          <ParentId i:nil="false"></ParentId>
          <Scope i:nil="false"></Scope>
          <Type></Type>
          <!--Keep these fields if you set the i:type attribute to RemarketingList-->
          <Rule xmlns:e26="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
            <e26:Type i:nil="false"></e26:Type>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsRule-->
            <e26:RuleItemGroups i:nil="false">
              <e26:RuleItemGroup>
                <e26:Items i:nil="false">
                  <e26:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e26:Type i:nil="false"></e26:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e26:Operand i:nil="false"></e26:Operand>
                    <e26:Operator></e26:Operator>
                    <e26:Value i:nil="false"></e26:Value>
                  </e26:RuleItem>
                </e26:Items>
              </e26:RuleItemGroup>
            </e26:RuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsWhoVisitedAnotherPageRule-->
            <e26:AnotherRuleItemGroups i:nil="false">
              <e26:RuleItemGroup>
                <e26:Items i:nil="false">
                  <e26:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e26:Type i:nil="false"></e26:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e26:Operand i:nil="false"></e26:Operand>
                    <e26:Operator></e26:Operator>
                    <e26:Value i:nil="false"></e26:Value>
                  </e26:RuleItem>
                </e26:Items>
              </e26:RuleItemGroup>
            </e26:AnotherRuleItemGroups>
            <e26:RuleItemGroups i:nil="false">
              <e26:RuleItemGroup>
                <e26:Items i:nil="false">
                  <e26:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e26:Type i:nil="false"></e26:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e26:Operand i:nil="false"></e26:Operand>
                    <e26:Operator></e26:Operator>
                    <e26:Value i:nil="false"></e26:Value>
                  </e26:RuleItem>
                </e26:Items>
              </e26:RuleItemGroup>
            </e26:RuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsWhoDidNotVisitAnotherPageRule-->
            <e26:ExcludeRuleItemGroups i:nil="false">
              <e26:RuleItemGroup>
                <e26:Items i:nil="false">
                  <e26:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e26:Type i:nil="false"></e26:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e26:Operand i:nil="false"></e26:Operand>
                    <e26:Operator></e26:Operator>
                    <e26:Value i:nil="false"></e26:Value>
                  </e26:RuleItem>
                </e26:Items>
              </e26:RuleItemGroup>
            </e26:ExcludeRuleItemGroups>
            <e26:IncludeRuleItemGroups i:nil="false">
              <e26:RuleItemGroup>
                <e26:Items i:nil="false">
                  <e26:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e26:Type i:nil="false"></e26:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e26:Operand i:nil="false"></e26:Operand>
                    <e26:Operator></e26:Operator>
                    <e26:Value i:nil="false"></e26:Value>
                  </e26:RuleItem>
                </e26:Items>
              </e26:RuleItemGroup>
            </e26:IncludeRuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to CustomEventsRule-->
            <e26:Action i:nil="false"></e26:Action>
            <e26:ActionOperator></e26:ActionOperator>
            <e26:Category i:nil="false"></e26:Category>
            <e26:CategoryOperator></e26:CategoryOperator>
            <e26:Label i:nil="false"></e26:Label>
            <e26:LabelOperator></e26:LabelOperator>
            <e26:Value i:nil="false"></e26:Value>
            <e26:ValueOperator></e26:ValueOperator>
          </Rule>
          <TagId i:nil="false"></TagId>
          <!--Keep these fields if you set the i:type attribute to CustomAudience-->
          <!--Keep these fields if you set the i:type attribute to InMarketAudience-->
        </Audience>
      </Audiences>
    </AddAudiencesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>AddAudiencesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AudienceIds*|A list of unique system identifiers corresponding to the audiences that were added.<br /><br />The list of identifiers corresponds directly to the list of audiences in the request. Items of the list may be returned as null. For each list index where an audience was not added, the corresponding element will be null.|*long* array|
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
    <AddAudiencesResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AudienceIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </AudienceIds>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e27="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e27:KeyValuePairOfstringstring>
              <e27:key p4:nil="false"></e27:key>
              <e27:value p4:nil="false"></e27:value>
            </e27:KeyValuePairOfstringstring>
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
    </AddAudiencesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteAudiences](../campaign-api/deleteaudiences-service-operation.md)  
[GetAudiencesByIds](../campaign-api/getaudiencesbyids-service-operation.md)  
[UpdateAudiences](../campaign-api/updateaudiences-service-operation.md)  

