---
title: "AppealEditorialRejections Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba87645c-f131-4a6a-addc-53e459f633a2
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AppealEditorialRejections Service Operation
Appeals the editorial rejections of one or more ads or keywords that failed editorial review.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AppealEditorialRejectionsRequest Message

### Request Body
The *AppealEditorialRejectionsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityIdToParentIdAssociations*|A list of unique identifiers of the ads or keywords that failed editorial review. The list can contain a maximum of 1,000 [EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md) objects.<br /><br />You submit each ad or keyword identifier with their respective ad group parent identifier in a [EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md) object. The list of [EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md) must include either ad identifiers or keyword identifiers – the list cannot include a mix ad and keyword entity identifiers.<br /><br />If an entity in the list has already been approved, the entity is ignored. If an entity in the list is not appealable, the call fails. If an entity in the list has an appeal pending, this request supersedes the pending request.|[EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md) array|
|*EntityType*|The type of entity that the entity to parent list contains. The supported values are *Ad* and *Keyword*.|[EntityType](../campaign-api/entitytype-value-set.md)|
|*JustificationText*|The justification for the appeal. The string can contain a maximum of 1,000 characters. The justification applies to all of the specified entities.<br /><br />**Note:** A useful justification should include reasons why the ad or keyword is compliant with editorial policy for example, *JustificationText = "my ads for paint guns are not firearms, they are painting tools"*.|*string*|

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
    <Action mustUnderstand="1">AppealEditorialRejections</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <AppealEditorialRejectionsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <EntityIdToParentIdAssociations xmlns:e47="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
        <e47:EntityIdToParentIdAssociation>
          <e47:EntityId></e47:EntityId>
          <e47:ParentId></e47:ParentId>
        </e47:EntityIdToParentIdAssociation>
      </EntityIdToParentIdAssociations>
      <EntityType></EntityType>
      <JustificationText i:nil="false"></JustificationText>
    </AppealEditorialRejectionsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>AppealEditorialRejectionsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any appeals that were not successfully submitted.<br /><br />The list of errors corresponds directly to the list of [EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md) in the request. Items of the list may be returned as null. For each list index where an appeal was successfully submitted, the corresponding error element will be null. Ideally all appeals are submitted successfully and all elements in this list are null.|[BatchError](../campaign-api/batcherror-data-object.md) array|

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
    <AppealEditorialRejectionsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e48="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e48:KeyValuePairOfstringstring>
              <e48:key p4:nil="false"></e48:key>
              <e48:value p4:nil="false"></e48:value>
            </e48:KeyValuePairOfstringstring>
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
    </AppealEditorialRejectionsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[GetEditorialReasonsByIds](../campaign-api/geteditorialreasonsbyids-service-operation.md)

