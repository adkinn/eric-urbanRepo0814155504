---
title: "GetCampaignsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5b47421-e856-4c94-8648-65eb226b7676
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetCampaignsByIds Service Operation
Gets the specified campaigns within an account.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetCampaignsByIdsRequest Message

### Request Body
The *GetCampaignsByIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AccountId*|The identifier of the account that contains the campaigns to get.|*long*|Required|
|*CampaignIds*|A maximum of 100 identifiers of the campaigns to get from the specified account.<br /><br />The identifiers must correspond to campaigns of the specified *CampaignType* or types, and otherwise the service will return error code *EntityIdFilterMismatch* (Code 516).|*long* array|Required|
|*CampaignType*|The type of campaigns to get, for example *SearchAndContent*, *Shopping*, or *DynamicSearchAds*. You can specify one or more types.|[CampaignType](../campaign-api/campaigntype-value-set.md)|Required|

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
    <Action mustUnderstand="1">GetCampaignsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetCampaignsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      <CampaignIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </CampaignIds>
      <CampaignType></CampaignType>
    </GetCampaignsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetCampaignsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Campaigns*|An array of [Campaign](../campaign-api/campaign-data-object.md) objects that corresponds directly to the campaign identifiers that you specified in the request. Items of the list may be returned as null. For each list index where a campaign was not retrieved, the corresponding element will be null.|[Campaign](../campaign-api/campaign-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any campaigns that were not successfully retrieved.<br /><br />The list of errors corresponds directly to the list of campaigns in the request. Items of the list may be returned as null. For each list index where a campaign was successfully retrieved, the corresponding error element will be null. Ideally all campaigns are retrieved successfully and all elements in this list are null.|[BatchError](../campaign-api/batcherror-data-object.md) array|

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
    <GetCampaignsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
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
          <ForwardCompatibilityMap xmlns:e123="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e123:KeyValuePairOfstringstring>
              <e123:key p4:nil="false"></e123:key>
              <e123:value p4:nil="false"></e123:value>
            </e123:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <Name p4:nil="false"></Name>
          <NativeBidAdjustment p4:nil="false"></NativeBidAdjustment>
          <Status p4:nil="false"></Status>
          <TimeZone p4:nil="false"></TimeZone>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e124="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e124:Parameters p4:nil="false">
              <e124:CustomParameter>
                <e124:Key p4:nil="false"></e124:Key>
                <e124:Value p4:nil="false"></e124:Value>
              </e124:CustomParameter>
            </e124:Parameters>
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
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e125="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e125:KeyValuePairOfstringstring>
              <e125:key p4:nil="false"></e125:key>
              <e125:value p4:nil="false"></e125:value>
            </e125:KeyValuePairOfstringstring>
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
    </GetCampaignsByIdsResponse>
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
[GetCampaignsByAccountId](../campaign-api/getcampaignsbyaccountid-service-operation.md)  
[UpdateCampaigns](../campaign-api/updatecampaigns-service-operation.md)  

