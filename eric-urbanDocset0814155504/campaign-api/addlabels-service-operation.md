---
title: "AddLabels Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 466634a8-004b-46ef-a6cc-696c090947e5
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
---
# AddLabels Service Operation
Adds one or more labels to an account.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>AddLabelsRequest Message

### Request Body
The *AddLabelsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Labels*|The list of labels to add to the account.<br /><br />The maximum size of the list is 100 items per service request.|[Label](../campaign-api/label-data-object.md) array|

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
    <Action mustUnderstand="1">AddLabels</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <AddLabelsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Labels i:nil="false">
        <Label>
          <ColorCode i:nil="false"></ColorCode>
          <Description i:nil="false"></Description>
          <Id i:nil="false"></Id>
          <Name i:nil="false"></Name>
        </Label>
      </Labels>
    </AddLabelsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>AddLabelsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*LabelIds*|A list of unique system identifiers corresponding to the labels that were added.<br /><br />The list of identifiers corresponds directly to the list of labels in the request. Items of the list may be returned as null. For each list index where a label was not added, the corresponding element will be null.|*long* array|
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
    <AddLabelsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <LabelIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </LabelIds>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e41="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e41:KeyValuePairOfstringstring>
              <e41:key p4:nil="false"></e41:key>
              <e41:value p4:nil="false"></e41:value>
            </e41:KeyValuePairOfstringstring>
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
    </AddLabelsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884)[Bing Ads Operation Error Codes](http://msdn.microsoft.com/library/bing-ads-operation-error-codes.aspx).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteLabels](../campaign-api/deletelabels-service-operation.md)  
[GetLabelsByIds](../campaign-api/getlabelsbyids-service-operation.md)  
[UpdateLabels](../campaign-api/updatelabels-service-operation.md)  

