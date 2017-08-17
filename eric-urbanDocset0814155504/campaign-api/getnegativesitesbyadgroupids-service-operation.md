---
title: "GetNegativeSitesByAdGroupIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e268244-40fa-4711-b034-3b3d70d06750
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetNegativeSitesByAdGroupIds Service Operation
Gets the negative site URLs of the specified ad groups.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>GetNegativeSitesByAdGroupIdsRequest Message

### Request Body
The *GetNegativeSitesByAdGroupIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupIds*|An array of identifiers of the ad groups that contain the negative site URLs that you want to get.<br /><br />The call fails if the sum of all negative site URLs defined in the specified list of ad groups exceeds 30,000 URLs. To ensure that the call succeeds, consider limiting the number of ad groups to 15.|*long* array|
|*CampaignId*|The identifier of the campaign that contains the ad groups.|*long*|

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
    <Action mustUnderstand="1">GetNegativeSitesByAdGroupIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetNegativeSitesByAdGroupIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <CampaignId></CampaignId>
      <AdGroupIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </AdGroupIds>
    </GetNegativeSitesByAdGroupIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetNegativeSitesByAdGroupIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupNegativeSites*|An array of [AdGroupNegativeSites](../campaign-api/adgroupnegativesites-data-object.md) that corresponds directly to the ad group identifiers that you specified in the request. Items of the list may be returned as null. For each list index where an [AdGroupNegativeSites](../campaign-api/adgroupnegativesites-data-object.md) was not retrieved, the corresponding element will be null.|[AdGroupNegativeSites](../campaign-api/adgroupnegativesites-data-object.md) array|
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
    <GetNegativeSitesByAdGroupIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupNegativeSites p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <AdGroupNegativeSites>
          <AdGroupId></AdGroupId>
          <NegativeSites p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </NegativeSites>
        </AdGroupNegativeSites>
      </AdGroupNegativeSites>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e136="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e136:KeyValuePairOfstringstring>
              <e136:key p4:nil="false"></e136:key>
              <e136:value p4:nil="false"></e136:value>
            </e136:KeyValuePairOfstringstring>
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
    </GetNegativeSitesByAdGroupIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[GetNegativeSitesByCampaignIds](../campaign-api/getnegativesitesbycampaignids-service-operation.md)  
[SetNegativeSitesToAdGroups](../campaign-api/setnegativesitestoadgroups-service-operation.md)  
[SetNegativeSitesToCampaigns](../campaign-api/setnegativesitestocampaigns-service-operation.md)  

