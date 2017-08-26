---
title: "GetLabelsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41c38711-66ab-4255-a49c-77abb672b2eb
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
---
# GetLabelsByIds Service Operation
Gets labels by label identifiers.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetLabelsByIdsRequest Message

### Request Body
The *GetLabelsByIdsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*PageInfo*|Determines the index and size of label results per page.<br /><br />If this element is not specified, the defaut page Index is *0* and the default Size is *1,000*.|[Paging](../campaign-api/paging-data-object.md)|Optional|
|*LabelIds*|The identifiers of the labels to get.<br /><br />The maximum size of the list is 1,000 items per service request. If this element is not specified, the operation will return all active labels in the account (1,000 results per page).|*long* array|Optional|

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
    <Action mustUnderstand="1">GetLabelsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetLabelsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <LabelIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </LabelIds>
      <PageInfo i:nil="false">
        <Index></Index>
        <Size></Size>
      </PageInfo>
    </GetLabelsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetLabelsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Labels*|An array of [Label](../campaign-api/label-data-object.md) objects that corresponds directly to the label identifiers that you specified in the request. Items of the list may be returned as null. For each list index where a label was not retrieved, the corresponding element will be null.|[Label](../campaign-api/label-data-object.md) array|
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
    <GetLabelsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Labels p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Label>
          <ColorCode p4:nil="false"></ColorCode>
          <Description p4:nil="false"></Description>
          <Id p4:nil="false"></Id>
          <Name p4:nil="false"></Name>
        </Label>
      </Labels>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e147="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e147:KeyValuePairOfstringstring>
              <e147:key p4:nil="false"></e147:key>
              <e147:value p4:nil="false"></e147:value>
            </e147:KeyValuePairOfstringstring>
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
    </GetLabelsByIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddLabels](../campaign-api/addlabels-service-operation.md)  
[DeleteLabels](../campaign-api/deletelabels-service-operation.md)  
[UpdateLabels](../campaign-api/updatelabels-service-operation.md)  

