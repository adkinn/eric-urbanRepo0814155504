---
title: "SetLabelAssociations Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7245c1c8-93ae-451b-a549-92213251e904
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
---
# SetLabelAssociations Service Operation
Sets label associations.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>SetLabelAssociationsRequest Message

### Request Body
The *SetLabelAssociationsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*EntityType*|Indicates the entity type associated with the label.<br/><br/>The supported entity type values are *Campaign*, *AdGroup*, *Ad*, and *Keyword*.|[EntityType](../campaign-api/entitytype-value-set.md)|Required|
|*LabelAssociations*|The list of label associations to set.<br/><br/>Each label association includes label and entity identifiers.<br /><br />The maximum size of the list is 100 items per service request.<br/><br/>Each entity can be associated with a maximum of 50 labels. For example *Campaign A* can be associated with up to 50 labels.|[LabelAssociation](../campaign-api/labelassociation-data-object.md) array|Required|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The response does not contain additional body elements.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">SetLabelAssociations</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SetLabelAssociationsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <EntityType></EntityType>
      <LabelAssociations i:nil="false">
        <LabelAssociation>
          <EntityId></EntityId>
          <LabelId></LabelId>
        </LabelAssociation>
      </LabelAssociations>
    </SetLabelAssociationsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SetLabelAssociationsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any associations that were not successfully retrieved.<br /><br />The list of errors corresponds directly to the list of associations in the request. Items of the list may be returned as null. For each list index where an association was successfully retrieved, the corresponding error element will be null. Ideally all associations are retrieved successfully and all elements in this list are null.|[BatchError](../campaign-api/batcherror-data-object.md) array|

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
    <SetLabelAssociationsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e159="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e159:KeyValuePairOfstringstring>
              <e159:key p4:nil="false"></e159:key>
              <e159:value p4:nil="false"></e159:value>
            </e159:KeyValuePairOfstringstring>
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
    </SetLabelAssociationsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteLabelAssociations](../campaign-api/deletelabelassociations-service-operation.md)  
[GetLabelAssociationsByEntityIds](../campaign-api/getlabelassociationsbyentityids-service-operation.md)  
[GetLabelAssociationsByLabelIds](../campaign-api/getlabelassociationsbylabelids-service-operation.md)  
