---
title: "SetNegativeSitesToAdGroups Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b0e5125a-f4be-4bda-bc60-15a0c1847222
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SetNegativeSitesToAdGroups Service Operation
Sets the negative site URLs of the specified ad groups.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>SetNegativeSitesToAdGroupsRequest Message

### Request Body
The *SetNegativeSitesToAdGroupsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupNegativeSites*|An array of [AdGroupNegativeSites](../campaign-api/adgroupnegativesites-data-object.md) objects that identify the ad groups to update with the specified negative site URLs.<br /><br />The array can contain a maximum of 5,000 objects.<br /><br />The total number of URLs that you can specify per request for all ad groups combined is 30,000. For example, if you specify 2,500 URLs per ad group, the maximum number of [AdGroupNegativeSites](../campaign-api/adgroupnegativesites-data-object.md) objects that you should pass is 12.|[AdGroupNegativeSites](../campaign-api/adgroupnegativesites-data-object.md) array|
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
    <Action mustUnderstand="1">SetNegativeSitesToAdGroups</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SetNegativeSitesToAdGroupsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <CampaignId></CampaignId>
      <AdGroupNegativeSites i:nil="false">
        <AdGroupNegativeSites>
          <AdGroupId></AdGroupId>
          <NegativeSites i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </NegativeSites>
        </AdGroupNegativeSites>
      </AdGroupNegativeSites>
    </SetNegativeSitesToAdGroupsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SetNegativeSitesToAdGroupsResponse Message

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
    <SetNegativeSitesToAdGroupsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e148="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e148:KeyValuePairOfstringstring>
              <e148:key p4:nil="false"></e148:key>
              <e148:value p4:nil="false"></e148:value>
            </e148:KeyValuePairOfstringstring>
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
    </SetNegativeSitesToAdGroupsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884)[Bing Ads Operation Error Codes](http://msdn.microsoft.com/library/bing-ads-operation-error-codes.aspx).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[GetNegativeSitesByAdGroupIds](../campaign-api/getnegativesitesbyadgroupids-service-operation.md)  
[GetNegativeSitesByCampaignIds](../campaign-api/getnegativesitesbycampaignids-service-operation.md)  
[SetNegativeSitesToCampaigns](../campaign-api/setnegativesitestocampaigns-service-operation.md)  

