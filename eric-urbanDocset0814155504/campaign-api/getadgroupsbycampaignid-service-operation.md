---
title: "GetAdGroupsByCampaignId Service Operation"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75b19dfe-6e48-40d4-bd5b-5d0cc7ae15fc
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAdGroupsByCampaignId Service Operation
Gets the ad groups within the specified campaign.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAdGroupsByCampaignIdRequest Message

### Request Body
The *GetAdGroupsByCampaignIdRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*CampaignId*|The identifier of the campaign that contains the ad groups to get.|*long*|Required|
|*ReturnAdditionalFields*|The list of additional properties that you want included within each returned [AdGroup](../campaign-api/adgroup-data-object.md) object. This set of flags enables you to get the latest features using the current version of Bing Ads Campaign Management API, and in the next version the corresponding elements will be included by default.|[AdGroupAdditionalField](../campaign-api/adgroupadditionalfield-value-set.md)|Optional|

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
    <Action mustUnderstand="1">GetAdGroupsByCampaignId</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAdGroupsByCampaignIdRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <CampaignId></CampaignId>
      <ReturnAdditionalFields i:nil="false"></ReturnAdditionalFields>
    </GetAdGroupsByCampaignIdRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAdGroupsByCampaignIdResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroups*|The list of ad groups within the specified campaign. If the campaign contains no ad groups, an empty array is returned.|[AdGroup](../campaign-api/adgroup-data-object.md) array|

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
    <GetAdGroupsByCampaignIdResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroups p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <AdGroup>
          <AdDistribution p4:nil="false"></AdDistribution>
          <AdRotation p4:nil="false">
            <EndDate p4:nil="false"></EndDate>
            <StartDate p4:nil="false"></StartDate>
            <Type p4:nil="false"></Type>
          </AdRotation>
          <BiddingScheme p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
            <Type p4:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to MaxClicksBiddingScheme-->
            <MaxCpc p4:nil="false">
              <Amount p4:nil="false"></Amount>
            </MaxCpc>
            <!--Keep these fields if you set the i:type attribute to MaxConversionsBiddingScheme-->
            <MaxCpc p4:nil="false">
              <Amount p4:nil="false"></Amount>
            </MaxCpc>
            <!--Keep these fields if you set the i:type attribute to TargetCpaBiddingScheme-->
            <MaxCpc p4:nil="false">
              <Amount p4:nil="false"></Amount>
            </MaxCpc>
            <TargetCpa p4:nil="false"></TargetCpa>
            <!--Keep these fields if you set the i:type attribute to ManualCpcBiddingScheme-->
            <!--Keep these fields if you set the i:type attribute to EnhancedCpcBiddingScheme-->
            <!--Keep these fields if you set the i:type attribute to InheritFromParentBiddingScheme-->
            <InheritedBidStrategyType p4:nil="false"></InheritedBidStrategyType>
          </BiddingScheme>
          <ContentMatchBid p4:nil="false">
            <Amount p4:nil="false"></Amount>
          </ContentMatchBid>
          <EndDate p4:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </EndDate>
          <ForwardCompatibilityMap xmlns:e103="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e103:KeyValuePairOfstringstring>
              <e103:key p4:nil="false"></e103:key>
              <e103:value p4:nil="false"></e103:value>
            </e103:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <Language p4:nil="false"></Language>
          <Name p4:nil="false"></Name>
          <NativeBidAdjustment p4:nil="false"></NativeBidAdjustment>
          <Network p4:nil="false"></Network>
          <PricingModel p4:nil="false"></PricingModel>
          <RemarketingTargetingSetting p4:nil="false"></RemarketingTargetingSetting>
          <SearchBid p4:nil="false">
            <Amount p4:nil="false"></Amount>
          </SearchBid>
          <Settings p4:nil="false">
            <Setting p4:type="-- specify derived type here with the appropriate prefix --">
              <Type p4:nil="false"></Type>
              <!--Keep these fields if you set the i:type attribute to ShoppingSetting-->
              <LocalInventoryAdsEnabled p4:nil="false"></LocalInventoryAdsEnabled>
              <Priority p4:nil="false"></Priority>
              <SalesCountryCode p4:nil="false"></SalesCountryCode>
              <StoreId p4:nil="false"></StoreId>
              <!--Keep these fields if you set the i:type attribute to DynamicSearchAdsSetting-->
              <DomainName p4:nil="false"></DomainName>
              <Language p4:nil="false"></Language>
            </Setting>
          </Settings>
          <StartDate p4:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </StartDate>
          <Status p4:nil="false"></Status>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e104="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e104:Parameters p4:nil="false">
              <e104:CustomParameter>
                <e104:Key p4:nil="false"></e104:Key>
                <e104:Value p4:nil="false"></e104:Value>
              </e104:CustomParameter>
            </e104:Parameters>
          </UrlCustomParameters>
        </AdGroup>
      </AdGroups>
    </GetAdGroupsByCampaignIdResponse>
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
[GetAdGroupsByIds](../campaign-api/getadgroupsbyids-service-operation.md)  
[UpdateAdGroups](../campaign-api/updateadgroups-service-operation.md)  

