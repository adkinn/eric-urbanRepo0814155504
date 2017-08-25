---
title: "UpdateAudiences Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63a01a0f-d355-4388-b8ee-1d22a30584f0
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# UpdateAudiences Service Operation
Updates the specified audiences.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>UpdateAudiencesRequest Message

### Request Body
The *UpdateAudiencesRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Audiences*|A list of audiences to update.<br /><br />The maximum size of the array is 100.<br/><br/>You can only update [RemarketingList](../campaign-api/remarketinglist-data-object.md) and [CustomAudience](../campaign-api/customaudience-data-object.md) objects. You cannot update [InMarketAudience](../campaign-api/inmarketaudience-data-object.md) objects.|[Audience](../campaign-api/audience-data-object.md) array|

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
    <Action mustUnderstand="1">UpdateAudiences</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateAudiencesRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Audiences i:nil="false">
        <Audience i:type="-- specify derived type here with the appropriate prefix --">
          <Description i:nil="false"></Description>
          <ForwardCompatibilityMap xmlns:e172="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e172:KeyValuePairOfstringstring>
              <e172:key i:nil="false"></e172:key>
              <e172:value i:nil="false"></e172:value>
            </e172:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id i:nil="false"></Id>
          <MembershipDuration i:nil="false"></MembershipDuration>
          <Name i:nil="false"></Name>
          <ParentId i:nil="false"></ParentId>
          <Scope i:nil="false"></Scope>
          <Type></Type>
          <!--Keep these fields if you set the i:type attribute to RemarketingList-->
          <Rule xmlns:e173="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
            <e173:Type i:nil="false"></e173:Type>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsRule-->
            <e173:RuleItemGroups i:nil="false">
              <e173:RuleItemGroup>
                <e173:Items i:nil="false">
                  <e173:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e173:Type i:nil="false"></e173:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e173:Operand i:nil="false"></e173:Operand>
                    <e173:Operator></e173:Operator>
                    <e173:Value i:nil="false"></e173:Value>
                  </e173:RuleItem>
                </e173:Items>
              </e173:RuleItemGroup>
            </e173:RuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsWhoVisitedAnotherPageRule-->
            <e173:AnotherRuleItemGroups i:nil="false">
              <e173:RuleItemGroup>
                <e173:Items i:nil="false">
                  <e173:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e173:Type i:nil="false"></e173:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e173:Operand i:nil="false"></e173:Operand>
                    <e173:Operator></e173:Operator>
                    <e173:Value i:nil="false"></e173:Value>
                  </e173:RuleItem>
                </e173:Items>
              </e173:RuleItemGroup>
            </e173:AnotherRuleItemGroups>
            <e173:RuleItemGroups i:nil="false">
              <e173:RuleItemGroup>
                <e173:Items i:nil="false">
                  <e173:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e173:Type i:nil="false"></e173:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e173:Operand i:nil="false"></e173:Operand>
                    <e173:Operator></e173:Operator>
                    <e173:Value i:nil="false"></e173:Value>
                  </e173:RuleItem>
                </e173:Items>
              </e173:RuleItemGroup>
            </e173:RuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsWhoDidNotVisitAnotherPageRule-->
            <e173:ExcludeRuleItemGroups i:nil="false">
              <e173:RuleItemGroup>
                <e173:Items i:nil="false">
                  <e173:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e173:Type i:nil="false"></e173:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e173:Operand i:nil="false"></e173:Operand>
                    <e173:Operator></e173:Operator>
                    <e173:Value i:nil="false"></e173:Value>
                  </e173:RuleItem>
                </e173:Items>
              </e173:RuleItemGroup>
            </e173:ExcludeRuleItemGroups>
            <e173:IncludeRuleItemGroups i:nil="false">
              <e173:RuleItemGroup>
                <e173:Items i:nil="false">
                  <e173:RuleItem i:type="-- specify derived type here with the appropriate prefix --">
                    <e173:Type i:nil="false"></e173:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e173:Operand i:nil="false"></e173:Operand>
                    <e173:Operator></e173:Operator>
                    <e173:Value i:nil="false"></e173:Value>
                  </e173:RuleItem>
                </e173:Items>
              </e173:RuleItemGroup>
            </e173:IncludeRuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to CustomEventsRule-->
            <e173:Action i:nil="false"></e173:Action>
            <e173:ActionOperator></e173:ActionOperator>
            <e173:Category i:nil="false"></e173:Category>
            <e173:CategoryOperator></e173:CategoryOperator>
            <e173:Label i:nil="false"></e173:Label>
            <e173:LabelOperator></e173:LabelOperator>
            <e173:Value i:nil="false"></e173:Value>
            <e173:ValueOperator></e173:ValueOperator>
          </Rule>
          <TagId i:nil="false"></TagId>
          <!--Keep these fields if you set the i:type attribute to CustomAudience-->
          <!--Keep these fields if you set the i:type attribute to InMarketAudience-->
        </Audience>
      </Audiences>
    </UpdateAudiencesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateAudiencesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
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
    <UpdateAudiencesResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e174="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e174:KeyValuePairOfstringstring>
              <e174:key p4:nil="false"></e174:key>
              <e174:value p4:nil="false"></e174:value>
            </e174:KeyValuePairOfstringstring>
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
    </UpdateAudiencesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Audiences Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddAudiences](../campaign-api/addaudiences-service-operation.md)  
[DeleteAudiences](../campaign-api/deleteaudiences-service-operation.md)  
[GetAudiencesByIds](../campaign-api/getaudiencesbyids-service-operation.md)  

