---
title: "UpdateCampaigns Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ec8e857-9273-49d1-8097-9253348fabda
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateCampaigns Service Operation
Updates specified campaigns in a specified account.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>UpdateCampaignsRequest Message

### Request Body
The *UpdateCampaignsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account that contains the campaign to update.|*long*|
|*Campaigns*|An array that can contain a maximum of 100 [Campaign](../campaign-api/campaign-data-object.md) objects to update.|[Campaign](../campaign-api/campaign-data-object.md) array|

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
    <Action mustUnderstand="1">UpdateCampaigns</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateCampaignsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      <Campaigns i:nil="false">
        <Campaign>
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
          <BudgetType i:nil="false"></BudgetType>
          <DailyBudget i:nil="false"></DailyBudget>
          <DaylightSaving i:nil="false"></DaylightSaving>
          <Description i:nil="false"></Description>
          <ForwardCompatibilityMap xmlns:e180="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e180:KeyValuePairOfstringstring>
              <e180:key i:nil="false"></e180:key>
              <e180:value i:nil="false"></e180:value>
            </e180:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id i:nil="false"></Id>
          <Name i:nil="false"></Name>
          <NativeBidAdjustment i:nil="false"></NativeBidAdjustment>
          <Status i:nil="false"></Status>
          <TimeZone i:nil="false"></TimeZone>
          <TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e181="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            <e181:Parameters i:nil="false">
              <e181:CustomParameter>
                <e181:Key i:nil="false"></e181:Key>
                <e181:Value i:nil="false"></e181:Value>
              </e181:CustomParameter>
            </e181:Parameters>
          </UrlCustomParameters>
          <CampaignType i:nil="false"></CampaignType>
          <Settings i:nil="false">
            <Setting i:type="-- specify derived type here with the appropriate prefix --">
              <Type i:nil="false"></Type>
              <!--Keep these fields if you set the i:type attribute to ShoppingSetting-->
              <Priority i:nil="false"></Priority>
              <SalesCountryCode i:nil="false"></SalesCountryCode>
              <StoreId i:nil="false"></StoreId>
              <!--Keep these fields if you set the i:type attribute to DynamicSearchAdsSetting-->
              <DomainName i:nil="false"></DomainName>
              <Language i:nil="false"></Language>
            </Setting>
          </Settings>
          <BudgetId i:nil="false"></BudgetId>
          <Languages i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </Languages>
        </Campaign>
      </Campaigns>
    </UpdateCampaignsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateCampaignsResponse Message

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
    <UpdateCampaignsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e182="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e182:KeyValuePairOfstringstring>
              <e182:key p4:nil="false"></e182:key>
              <e182:value p4:nil="false"></e182:value>
            </e182:KeyValuePairOfstringstring>
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
    </UpdateCampaignsResponse>
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
[GetCampaignsByIds](../campaign-api/getcampaignsbyids-service-operation.md)  

