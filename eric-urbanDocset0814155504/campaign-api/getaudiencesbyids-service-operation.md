---
title: "GetAudiencesByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6eb86de5-c924-4b22-bb91-b36260675023
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# GetAudiencesByIds Service Operation
Retrieves the specified audiences from the specified account.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAudiencesByIdsRequest Message

### Request Body
The *GetAudiencesByIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AudienceIds*|A maximum of 100 identifiers of the requested audiences.<br/><br/>If this element is null or empty, then you are effectively requesting all customer and account scoped audiences for the specified account.<br/><br/>**Note**: If the audience identifiers do not match the requested audience types, then the operation will return a batch error for each requested audience ID.|*long* array|No|
|*Type*|One or more types of audiences to return.|[AudienceType](../campaign-api/audiencetype-value-set.md) array|Yes|

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
    <Action mustUnderstand="1">GetAudiencesByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAudiencesByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AudienceIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </AudienceIds>
      <Type></Type>
    </GetAudiencesByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAudiencesByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Audiences*|The list of audiences that corresponds directly to the audience identifiers that you specified in the request. Items of the list may be returned as null. For each list index where an audience was not retrieved, the corresponding element will be null.|[Audience](../campaign-api/audience-data-object.md) array|
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
    <GetAudiencesByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Audiences p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Audience p4:type="-- specify derived type here with the appropriate prefix --">
          <Description p4:nil="false"></Description>
          <ForwardCompatibilityMap xmlns:e113="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e113:KeyValuePairOfstringstring>
              <e113:key p4:nil="false"></e113:key>
              <e113:value p4:nil="false"></e113:value>
            </e113:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <MembershipDuration p4:nil="false"></MembershipDuration>
          <Name p4:nil="false"></Name>
          <ParentId p4:nil="false"></ParentId>
          <Scope p4:nil="false"></Scope>
          <Type></Type>
          <!--Keep these fields if you set the i:type attribute to RemarketingList-->
          <Rule xmlns:e114="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
            <e114:Type p4:nil="false"></e114:Type>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsRule-->
            <e114:RuleItemGroups p4:nil="false">
              <e114:RuleItemGroup>
                <e114:Items p4:nil="false">
                  <e114:RuleItem p4:type="-- specify derived type here with the appropriate prefix --">
                    <e114:Type p4:nil="false"></e114:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e114:Operand p4:nil="false"></e114:Operand>
                    <e114:Operator></e114:Operator>
                    <e114:Value p4:nil="false"></e114:Value>
                  </e114:RuleItem>
                </e114:Items>
              </e114:RuleItemGroup>
            </e114:RuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsWhoVisitedAnotherPageRule-->
            <e114:AnotherRuleItemGroups p4:nil="false">
              <e114:RuleItemGroup>
                <e114:Items p4:nil="false">
                  <e114:RuleItem p4:type="-- specify derived type here with the appropriate prefix --">
                    <e114:Type p4:nil="false"></e114:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e114:Operand p4:nil="false"></e114:Operand>
                    <e114:Operator></e114:Operator>
                    <e114:Value p4:nil="false"></e114:Value>
                  </e114:RuleItem>
                </e114:Items>
              </e114:RuleItemGroup>
            </e114:AnotherRuleItemGroups>
            <e114:RuleItemGroups p4:nil="false">
              <e114:RuleItemGroup>
                <e114:Items p4:nil="false">
                  <e114:RuleItem p4:type="-- specify derived type here with the appropriate prefix --">
                    <e114:Type p4:nil="false"></e114:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e114:Operand p4:nil="false"></e114:Operand>
                    <e114:Operator></e114:Operator>
                    <e114:Value p4:nil="false"></e114:Value>
                  </e114:RuleItem>
                </e114:Items>
              </e114:RuleItemGroup>
            </e114:RuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to PageVisitorsWhoDidNotVisitAnotherPageRule-->
            <e114:ExcludeRuleItemGroups p4:nil="false">
              <e114:RuleItemGroup>
                <e114:Items p4:nil="false">
                  <e114:RuleItem p4:type="-- specify derived type here with the appropriate prefix --">
                    <e114:Type p4:nil="false"></e114:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e114:Operand p4:nil="false"></e114:Operand>
                    <e114:Operator></e114:Operator>
                    <e114:Value p4:nil="false"></e114:Value>
                  </e114:RuleItem>
                </e114:Items>
              </e114:RuleItemGroup>
            </e114:ExcludeRuleItemGroups>
            <e114:IncludeRuleItemGroups p4:nil="false">
              <e114:RuleItemGroup>
                <e114:Items p4:nil="false">
                  <e114:RuleItem p4:type="-- specify derived type here with the appropriate prefix --">
                    <e114:Type p4:nil="false"></e114:Type>
                    <!--Keep these fields if you set the i:type attribute to StringRuleItem-->
                    <e114:Operand p4:nil="false"></e114:Operand>
                    <e114:Operator></e114:Operator>
                    <e114:Value p4:nil="false"></e114:Value>
                  </e114:RuleItem>
                </e114:Items>
              </e114:RuleItemGroup>
            </e114:IncludeRuleItemGroups>
            <!--Keep these fields if you set the i:type attribute to CustomEventsRule-->
            <e114:Action p4:nil="false"></e114:Action>
            <e114:ActionOperator></e114:ActionOperator>
            <e114:Category p4:nil="false"></e114:Category>
            <e114:CategoryOperator></e114:CategoryOperator>
            <e114:Label p4:nil="false"></e114:Label>
            <e114:LabelOperator></e114:LabelOperator>
            <e114:Value p4:nil="false"></e114:Value>
            <e114:ValueOperator></e114:ValueOperator>
          </Rule>
          <TagId p4:nil="false"></TagId>
          <!--Keep these fields if you set the i:type attribute to CustomAudience-->
          <!--Keep these fields if you set the i:type attribute to InMarketAudience-->
        </Audience>
      </Audiences>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e115="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e115:KeyValuePairOfstringstring>
              <e115:key p4:nil="false"></e115:key>
              <e115:value p4:nil="false"></e115:value>
            </e115:KeyValuePairOfstringstring>
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
    </GetAudiencesByIdsResponse>
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
[UpdateAudiences](../campaign-api/updateaudiences-service-operation.md)  

