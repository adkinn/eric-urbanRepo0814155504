---
title: "UpdateAdGroups Service Operation"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 222be3c0-da10-448f-984c-55d4a1deeca1
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateAdGroups Service Operation
Updates the specified ad groups in a campaign.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>UpdateAdGroupsRequest Message

### Request Body
The *UpdateAdGroupsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroups*|An array that can contain a maximum of 1,000 [AdGroup](../campaign-api/adgroup-data-object.md) objects to update.|[AdGroup](../campaign-api/adgroup-data-object.md) array|
|*CampaignId*|The identifier of the campaign that owns the ad groups to update.|*long*|
|*UpdateNativeBidAdjustment*|Determines whether or not the service should use the *NativeBidAdjustment* element of each specified [AdGroup](../campaign-api/adgroup-data-object.md) during update.  If set to True, the *NativeBidAdjustment* will be used, and otherwise it will be ignored and your existing native bid adjustment setting will be retained during update.<br /><br />The default value is False if  this element is not set.|*boolean*|

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
    <Action mustUnderstand="1">UpdateAdGroups</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateAdGroupsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
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
          <ForwardCompatibilityMap xmlns:e180="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e180:KeyValuePairOfstringstring>
              <e180:key i:nil="false"></e180:key>
              <e180:value i:nil="false"></e180:value>
            </e180:KeyValuePairOfstringstring>
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
          <UrlCustomParameters xmlns:e181="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            <e181:Parameters i:nil="false">
              <e181:CustomParameter>
                <e181:Key i:nil="false"></e181:Key>
                <e181:Value i:nil="false"></e181:Value>
              </e181:CustomParameter>
            </e181:Parameters>
          </UrlCustomParameters>
        </AdGroup>
      </AdGroups>
      <UpdateNativeBidAdjustment></UpdateNativeBidAdjustment>
    </UpdateAdGroupsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateAdGroupsResponse Message

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
    <UpdateAdGroupsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e167="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e167:KeyValuePairOfstringstring>
              <e167:key p4:nil="false"></e167:key>
              <e167:value p4:nil="false"></e167:value>
            </e167:KeyValuePairOfstringstring>
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
    </UpdateAdGroupsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddAdGroups](../campaign-api/addadgroups-service-operation.md)  
[DeleteAdGroups](../campaign-api/deleteadgroups-service-operation.md)  
[GetAdGroupsByCampaignId](../campaign-api/getadgroupsbycampaignid-service-operation.md)  
[GetAdGroupsByIds](../campaign-api/getadgroupsbyids-service-operation.md)  

