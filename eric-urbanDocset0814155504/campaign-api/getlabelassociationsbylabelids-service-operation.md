---
title: "GetLabelAssociationsByLabelIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9282c02d-e93a-4b1d-9a44-76eec1f5c47d
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
---
# GetLabelAssociationsByLabelIds Service Operation
Gets label associations by label identifiers.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetLabelAssociationsByLabelIdsRequest Message

### Request Body
The *GetLabelAssociationsByLabelIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*PageInfo*|Determines the index and size of label association results per page.<br/><br/>Up to 1,000 label associations will be returned per page, so you might need to request multiple pages to get all of the label associations.<br /><br />If this element is not specified, the defaut page Index is *0* and the default Size is *1,000*.|[Paging](../campaign-api/paging-data-object.md)|Optional|
|*EntityType*|Filters the returned associations by entity type.<br/><br/>The supported entity type values are *Campaign*, *AdGroup*, *Ad*, and *Keyword*.|[EntityType](../campaign-api/entitytype-value-set.md)|Required|
|*LabelIds*|The list of label identifiers used to request label associations.<br/><br/>If the list of label identifiers is null or empty then all label associations for the account will be returned page by page. See the *PageInfo* element for more information.<br /><br />The maximum size of the list is 1 item per service request.|*long* array|Optional|

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
    <Action mustUnderstand="1">GetLabelAssociationsByLabelIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetLabelAssociationsByLabelIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <EntityType></EntityType>
      <LabelIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </LabelIds>
      <PageInfo i:nil="false">
        <Index></Index>
        <Size></Size>
      </PageInfo>
    </GetLabelAssociationsByLabelIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetLabelAssociationsByLabelIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|LabelAssociation|An array of label associations.<br /><br />For each label identifier specified in the request, zero or more [LabelAssociation](../campaign-api/labelassociation-data-object.md) objects are returned. Whereas the order of the returned [LabelAssociation](../campaign-api/labelassociation-data-object.md) objects is guaranteed in the order of the requested label identifiers, please note that multiple [LabelAssociation](../campaign-api/labelassociation-data-object.md) objects can be returned for the same label identifier. The entity identifiers are in ascending order for a given label's associations.<br/><br/>It is possible to receive duplicate associations across multiple pages, so you should check for duplicate results.|[LabelAssociation](../campaign-api/labelassociation-data-object.md) array|
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
    <GetLabelAssociationsByLabelIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <LabelAssociations p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <LabelAssociation>
          <EntityId></EntityId>
          <LabelId></LabelId>
        </LabelAssociation>
      </LabelAssociations>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e146="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e146:KeyValuePairOfstringstring>
              <e146:key p4:nil="false"></e146:key>
              <e146:value p4:nil="false"></e146:value>
            </e146:KeyValuePairOfstringstring>
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
    </GetLabelAssociationsByLabelIdsResponse>
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
[SetLabelAssociations](../campaign-api/setlabelassociations-service-operation.md)  
