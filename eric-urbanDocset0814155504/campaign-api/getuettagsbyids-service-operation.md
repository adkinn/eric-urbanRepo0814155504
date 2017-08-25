---
title: "GetUetTagsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 879b726f-b167-4a2b-a8e0-e0590113ae1b
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetUetTagsByIds Service Operation
Gets the specified Universal Event Tracking (UET) tags.

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetUetTagsByIdsRequest Message

### Request Body
The *GetUetTagsByIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the customer identifier in the *CustomerId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TagIds*|A maximum of 100 identifiers of the UET tags that you want to get. <br /><br />If *TagIds* is null or empty, then you are effectively requesting all UET tags that are available for the customer.|[UetTag](../campaign-api/uettag-data-object.md) array|

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
    <Action mustUnderstand="1">GetUetTagsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetUetTagsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <TagIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </TagIds>
    </GetUetTagsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetUetTagsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*UetTags*|An array of [UetTag](../campaign-api/uettag-data-object.md) objects that corresponds directly to the UET tag identifiers that you specified in the request. Items of the array may be returned as null. For each array index where a UET tag was not retrieved, the corresponding element will be null.|[UetTag](../campaign-api/uettag-data-object.md) array|
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
    <GetUetTagsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <UetTags p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <UetTag>
          <Description p4:nil="false"></Description>
          <Id p4:nil="false"></Id>
          <Name p4:nil="false"></Name>
          <TrackingNoScript p4:nil="false"></TrackingNoScript>
          <TrackingScript p4:nil="false"></TrackingScript>
          <TrackingStatus p4:nil="false"></TrackingStatus>
        </UetTag>
      </UetTags>
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
    </GetUetTagsByIdsResponse>
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
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  
[UetTag](../campaign-api/uettag-data-object.md)  
[AddUetTags](../campaign-api/adduettags-service-operation.md)  
[UpdateUetTags](../campaign-api/updateuettags-service-operation.md)  
