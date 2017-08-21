---
title: "ApplyProductPartitionActions Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a1cd474-5095-436c-a9ae-b372fbd30de8
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApplyProductPartitionActions Service Operation
Applies an add, update, or delete action to each of the specified [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md), which each contain a [ProductPartition](../campaign-api/productpartition-data-object.md).

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>ApplyProductPartitionActionsRequest Message

### Request Body
The *ApplyProductPartitionActionsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CriterionActions*|A list of up to 5,000 *AdGroupCriterionAction* objects that each contain an *Action* element and either a [BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md) or [NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md). <br/><br/>All of the ad group criterion actions must be for the same ad group. For more information including validation rules, please see [Create a Bing Shopping Campaign with the Campaign Management Service](~/concepts/product-ads.md#bingshopping_campaignservice).|[AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md) array|

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
    <Action mustUnderstand="1">ApplyProductPartitionActions</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <ApplyProductPartitionActionsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <CriterionActions i:nil="false">
        <AdGroupCriterionAction>
          <Action></Action>
          <AdGroupCriterion i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
            <AdGroupId></AdGroupId>
            <Criterion i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
              <Type i:nil="false"></Type>
              <!--Keep these fields if you set the i:type attribute to ProductPartition-->
              <Condition i:nil="false">
                <Attribute i:nil="false"></Attribute>
                <Operand i:nil="false"></Operand>
              </Condition>
              <ParentCriterionId i:nil="false"></ParentCriterionId>
              <PartitionType></PartitionType>
            </Criterion>
            <Id i:nil="false"></Id>
            <Status i:nil="false"></Status>
            <Type i:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to BiddableAdGroupCriterion-->
            <CriterionBid i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
              <Type i:nil="false"></Type>
              <!--Keep these fields if you set the i:type attribute to FixedBid-->
              <Amount></Amount>
            </CriterionBid>
            <DestinationUrl i:nil="false"></DestinationUrl>
            <EditorialStatus i:nil="false"></EditorialStatus>
            <FinalAppUrls xmlns:e50="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
              <e50:AppUrl>
                <e50:OsType i:nil="false"></e50:OsType>
                <e50:Url i:nil="false"></e50:Url>
              </e50:AppUrl>
            </FinalAppUrls>
            <FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
              <a1:string></a1:string>
            </FinalMobileUrls>
            <FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
              <a1:string></a1:string>
            </FinalUrls>
            <TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
            <UrlCustomParameters xmlns:e51="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
              <e51:Parameters i:nil="false">
                <e51:CustomParameter>
                  <e51:Key i:nil="false"></e51:Key>
                  <e51:Value i:nil="false"></e51:Value>
                </e51:CustomParameter>
              </e51:Parameters>
            </UrlCustomParameters>
            <!--Keep these fields if you set the i:type attribute to NegativeAdGroupCriterion-->
          </AdGroupCriterion>
        </AdGroupCriterionAction>
      </CriterionActions>
    </ApplyProductPartitionActionsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>ApplyProductPartitionActionsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupCriterionIds*|A list of identifiers that identify the criterion that had the action applied. The list of identifiers corresponds directly to the list of criterion in the request.<br /><br />**Note:** If any criterion action failed, then all remaining criterion actions will be rejected, and all elements in this list will be null.|*long* array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.<br /><br />**Note:** For criterion which failed due to user error, an actionable error code will be returned.<br /><br />**Note:** If any criterion action failed, then all remaining criterion actions will be rejected, and none of the elements in this list will be null. For criterion that might have otherwise succeeded,  a generic error will be returned which explains that a related entity failed.|[BatchError](../campaign-api/batcherror-data-object.md) array|

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
    <ApplyProductPartitionActionsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupCriterionIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </AdGroupCriterionIds>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e52="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e52:KeyValuePairOfstringstring>
              <e52:key p4:nil="false"></e52:key>
              <e52:value p4:nil="false"></e52:value>
            </e52:KeyValuePairOfstringstring>
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
    </ApplyProductPartitionActionsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md)  
[ProductPartition](../campaign-api/productpartition-data-object.md)  
[AdGroupCriterionAction](../campaign-api/adgroupcriterionaction-data-object.md)  
[BiddableAdGroupCriterion](../campaign-api/biddableadgroupcriterion-data-object.md)  
[NegativeAdGroupCriterion](../campaign-api/negativeadgroupcriterion-data-object.md)  

