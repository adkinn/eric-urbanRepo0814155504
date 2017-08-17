---
title: "AddAdGroups Service Operation"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10bbda9a-f0e2-41b8-b5cc-14c75e638633
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddAdGroups Service Operation
Adds new ad groups to a specified campaign.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddAdGroupsRequest Message

### Request Body
The *AddAdGroupsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroups*|An array of [AdGroup](../campaign-api/adgroup-data-object.md) objects to add to the specified campaign.<br /><br />You can add a maximum of 1,000 ad groups in a single call. Each campaign can have up to 20,000 ad groups.|[AdGroup](../campaign-api/adgroup-data-object.md) array|
|*CampaignId*|The identifier of the campaign to add the ad groups to.|*long*|

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
    <Action mustUnderstand="1">AddAdGroups</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <AddAdGroupsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <CampaignId></CampaignId>
      <AdGroups i:nil="false">
        <AdGroup>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdRotation i:nil="false">
            <EndDate i:nil="false"></EndDate>
            <StartDate i:nil="false"></StartDate>
            <Type i:nil="false"></Type>
          </AdRotation>
          <BiddingScheme i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
            <Type i:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to MaxClicksBiddingScheme-->
            <MaxCpc i:nil="false">
              <Amount i:nil="false"></Amount>
            </MaxCpc>
            <!--Keep these fields if you set the i:type attribute to MaxConversionsBiddingScheme-->
            <MaxCpc i:nil="false">
              <Amount i:nil="false"></Amount>
            </MaxCpc>
            <!--Keep these fields if you set the i:type attribute to TargetCpaBiddingScheme-->
            <MaxCpc i:nil="false">
              <Amount i:nil="false"></Amount>
            </MaxCpc>
            <TargetCpa i:nil="false"></TargetCpa>
            <!--Keep these fields if you set the i:type attribute to ManualCpcBiddingScheme-->
            <!--Keep these fields if you set the i:type attribute to EnhancedCpcBiddingScheme-->
            <!--Keep these fields if you set the i:type attribute to InheritFromParentBiddingScheme-->
            <InheritedBidStrategyType i:nil="false"></InheritedBidStrategyType>
          </BiddingScheme>
          <ContentMatchBid i:nil="false">
            <Amount i:nil="false"></Amount>
          </ContentMatchBid>
          <EndDate i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </EndDate>
          <ForwardCompatibilityMap xmlns:e18="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e18:KeyValuePairOfstringstring>
              <e18:key i:nil="false"></e18:key>
              <e18:value i:nil="false"></e18:value>
            </e18:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id i:nil="false"></Id>
          <Language i:nil="false"></Language>
          <Name i:nil="false"></Name>
          <NativeBidAdjustment i:nil="false"></NativeBidAdjustment>
          <Network i:nil="false"></Network>
          <PricingModel i:nil="false"></PricingModel>
          <RemarketingTargetingSetting i:nil="false"></RemarketingTargetingSetting>
          <SearchBid i:nil="false">
            <Amount i:nil="false"></Amount>
          </SearchBid>
          <StartDate i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </StartDate>
          <Status i:nil="false"></Status>
          <TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e19="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            <e19:Parameters i:nil="false">
              <e19:CustomParameter>
                <e19:Key i:nil="false"></e19:Key>
                <e19:Value i:nil="false"></e19:Value>
              </e19:CustomParameter>
            </e19:Parameters>
          </UrlCustomParameters>
        </AdGroup>
      </AdGroups>
    </AddAdGroupsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>AddAdGroupsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupIds*|A list of unique system identifiers corresponding to the ad groups that were added.<br /><br />The list of identifiers corresponds directly to the list of ad groups in the request. Items of the list may be returned as null. For each list index where an ad group was not added, the corresponding element will be null.|*long* array|
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
    <AddAdGroupsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </AdGroupIds>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e20="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e20:KeyValuePairOfstringstring>
              <e20:key p4:nil="false"></e20:key>
              <e20:value p4:nil="false"></e20:value>
            </e20:KeyValuePairOfstringstring>
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
    </AddAdGroupsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteAdGroups](../campaign-api/deleteadgroups-service-operation.md)  
[GetAdGroupsByCampaignId](../campaign-api/getadgroupsbycampaignid-service-operation.md)  
[GetAdGroupsByIds](../campaign-api/getadgroupsbyids-service-operation.md)  
[UpdateAdGroups](../campaign-api/updateadgroups-service-operation.md)  

