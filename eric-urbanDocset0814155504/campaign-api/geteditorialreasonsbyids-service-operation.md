---
title: "GetEditorialReasonsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6c8b301-c2d3-4f50-82a6-47fa74f59e22
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetEditorialReasonsByIds Service Operation
Gets the reasons why the specified entities failed editorial review and whether the rejection is appealable.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetEditorialReasonsByIdsRequest Message

### Request Body
The *GetEditorialReasonsByIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account that contains the specified entities.|*long*|
|*EntityIdToParentIdAssociations*|A list of  [EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md) objects that each contain the unique system identifier of an entity such as ad or keyword, and the identifier of its parent. An ad group is the parent of an ad or keyword.<br /><br />The list must include all ads or all keywords which failed editorial review ? the list cannot include a mix ads and keywords. The list can contain a maximum of 1,000 identifiers.|[EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md) array|
|*EntityType*|The type of entities that the entity list contains.|[EntityType](../campaign-api/entitytype-value-set.md)|

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
    <Action mustUnderstand="1">GetEditorialReasonsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetEditorialReasonsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      <EntityIdToParentIdAssociations xmlns:e120="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
        <e120:EntityIdToParentIdAssociation>
          <e120:EntityId></e120:EntityId>
          <e120:ParentId></e120:ParentId>
        </e120:EntityIdToParentIdAssociation>
      </EntityIdToParentIdAssociations>
      <EntityType></EntityType>
    </GetEditorialReasonsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetEditorialReasonsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EditorialReasons*|An array of [EditorialReasonCollection](../campaign-api/editorialreasoncollection-data-object.md) objects that corresponds directly to the [EntityIdToParentIdAssociation](../campaign-api/entityidtoparentidassociation-data-object.md) objects that you specified in the request. Each object identifies the reason for the failure and whether it is appealable. Items of the list may be returned as null. For each list index where an [EditorialReasonCollection](../campaign-api/editorialreasoncollection-data-object.md) was not retrieved, the corresponding element will be null.<br /><br />If the entity had not failed editorial review, the corresponding item in this collection is NULL. In addition, the item will be NULL if the specified ad or keyword identifier is not valid.|[EditorialReasonCollection](../campaign-api/editorialreasoncollection-data-object.md) array|
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
    <GetEditorialReasonsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <EditorialReasons p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <EditorialReasonCollection>
          <AdGroupId></AdGroupId>
          <AdOrKeywordId></AdOrKeywordId>
          <AppealStatus></AppealStatus>
          <Reasons p4:nil="false">
            <EditorialReason>
              <Location p4:nil="false"></Location>
              <PublisherCountries p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                <a1:string></a1:string>
              </PublisherCountries>
              <ReasonCode></ReasonCode>
              <Term p4:nil="false"></Term>
            </EditorialReason>
          </Reasons>
        </EditorialReasonCollection>
      </EditorialReasons>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e121="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e121:KeyValuePairOfstringstring>
              <e121:key p4:nil="false"></e121:key>
              <e121:value p4:nil="false"></e121:value>
            </e121:KeyValuePairOfstringstring>
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
    </GetEditorialReasonsByIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AppealEditorialRejections](../campaign-api/appealeditorialrejections-service-operation.md)

