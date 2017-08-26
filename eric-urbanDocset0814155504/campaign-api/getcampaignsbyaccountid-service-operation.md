---
title: "GetCampaignsByAccountId Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2cd78bd9-0397-4fcc-8ebb-40f72b987a96
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetCampaignsByAccountId Service Operation
Gets the campaigns within an account.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetCampaignsByAccountIdRequest Message

### Request Body
The *GetCampaignsByAccountIdRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AccountId*|The identifier of the account that contains the campaigns to get.|*long*|Required|
|*CampaignType*|The type of campaign to get, for example *SearchAndContent*, *Shopping*, or *DynamicSearchAds*. You can specify one or more types.|[CampaignType](../campaign-api/campaigntype-value-set.md)|Required|

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
    <Action mustUnderstand="1">GetCampaignsByAccountId</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetCampaignsByAccountIdRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      <CampaignType></CampaignType>
    </GetCampaignsByAccountIdRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetCampaignsByAccountIdResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Campaigns*|The list of campaigns that were retrieved. If no campaigns exist, an empty array is returned.|[Campaign](../campaign-api/campaign-data-object.md) array|

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
    <GetCampaignsByAccountIdResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Campaigns p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Campaign>
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
          </BiddingScheme>
          <BudgetType p4:nil="false"></BudgetType>
          <DailyBudget p4:nil="false"></DailyBudget>
          <Description p4:nil="false"></Description>
          <ForwardCompatibilityMap xmlns:e121="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e121:KeyValuePairOfstringstring>
              <e121:key p4:nil="false"></e121:key>
              <e121:value p4:nil="false"></e121:value>
            </e121:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <Name p4:nil="false"></Name>
          <NativeBidAdjustment p4:nil="false"></NativeBidAdjustment>
          <Status p4:nil="false"></Status>
          <TimeZone p4:nil="false"></TimeZone>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e122="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e122:Parameters p4:nil="false">
              <e122:CustomParameter>
                <e122:Key p4:nil="false"></e122:Key>
                <e122:Value p4:nil="false"></e122:Value>
              </e122:CustomParameter>
            </e122:Parameters>
          </UrlCustomParameters>
          <CampaignType p4:nil="false"></CampaignType>
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
          <BudgetId p4:nil="false"></BudgetId>
          <Languages p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </Languages>
        </Campaign>
      </Campaigns>
    </GetCampaignsByAccountIdResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddCampaigns](../campaign-api/addcampaigns-service-operation.md)  
[DeleteCampaigns](../campaign-api/deletecampaigns-service-operation.md)  
[GetCampaignsByIds](../campaign-api/getcampaignsbyids-service-operation.md)  
[UpdateCampaigns](../campaign-api/updatecampaigns-service-operation.md)  

