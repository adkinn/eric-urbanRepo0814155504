---
title: "GetAdGroupCriterionsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 357a3026-ab8c-431c-b73c-7167a007dfeb
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAdGroupCriterionsByIds Service Operation
Gets ad group criterions by identifiers and types.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAdGroupCriterionsByIdsRequest Message

### Request Body
The *GetAdGroupCriterionsByIdsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdGroupCriterionIds*|A list of unique identifiers that identify the criterions to get.<br/><br/>You can include up to 1,000 ad group criterion identifiers per request. <br /><br />If this element is null, all criterions for the specified *AdGroupId* will be retrieved.|*long* array|No|
|*AdGroupId*|The identifier of the ad group that owns the criterions to get.|*long*|Yes|
|*CriterionType*|The type of criterion to get, for example *Webpage*. You can specify only one type. The *Targets* and *Audience* values are not allowed for this operation.|[AdGroupCriterionType](../campaign-api/adgroupcriteriontype-value-set.md)|Yes|

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
    <Action mustUnderstand="1">GetAdGroupCriterionsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAdGroupCriterionsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupCriterionIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </AdGroupCriterionIds>
      <AdGroupId></AdGroupId>
      <CriterionType></CriterionType>
    </GetAdGroupCriterionsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAdGroupCriterionsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupCriterions*|The list of criterions that correspond directly to the identifiers specified in the request. If an identifier in the list is not valid, the corresponding item in the response is set to null.|[AdGroupCriterion](../campaign-api/adgroupcriterion-data-object.md) array|

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
    <GetAdGroupCriterionsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupCriterions p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <AdGroupCriterion p4:type="-- specify derived type here with the appropriate prefix --">
          <AdGroupId></AdGroupId>
          <Criterion p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
            <Type p4:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to ProductPartition-->
            <Condition p4:nil="false">
              <Attribute p4:nil="false"></Attribute>
              <Operand p4:nil="false"></Operand>
            </Condition>
            <ParentCriterionId p4:nil="false"></ParentCriterionId>
            <PartitionType></PartitionType>
            <!--Keep these fields if you set the i:type attribute to AgeCriterion-->
            <AgeRange p4:nil="false"></AgeRange>
            <!--Keep these fields if you set the i:type attribute to DeviceCriterion-->
            <DeviceName p4:nil="false"></DeviceName>
            <OSName p4:nil="false"></OSName>
            <!--Keep these fields if you set the i:type attribute to DayTimeCriterion-->
            <Day p4:nil="false"></Day>
            <FromHour p4:nil="false"></FromHour>
            <FromMinute p4:nil="false"></FromMinute>
            <ToHour p4:nil="false"></ToHour>
            <ToMinute p4:nil="false"></ToMinute>
            <!--Keep these fields if you set the i:type attribute to GenderCriterion-->
            <GenderType p4:nil="false"></GenderType>
            <!--Keep these fields if you set the i:type attribute to RadiusCriterion-->
            <LatitudeDegrees p4:nil="false"></LatitudeDegrees>
            <LongitudeDegrees p4:nil="false"></LongitudeDegrees>
            <Name p4:nil="false"></Name>
            <Radius p4:nil="false"></Radius>
            <RadiusUnit p4:nil="false"></RadiusUnit>
            <!--Keep these fields if you set the i:type attribute to LocationCriterion-->
            <DisplayName p4:nil="false"></DisplayName>
            <EnclosedLocationIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
              <a1:long></a1:long>
            </EnclosedLocationIds>
            <LocationId p4:nil="false"></LocationId>
            <LocationType p4:nil="false"></LocationType>
            <!--Keep these fields if you set the i:type attribute to LocationIntentCriterion-->
            <IntentOption p4:nil="false"></IntentOption>
            <!--Keep these fields if you set the i:type attribute to AudienceCriterion-->
            <AudienceId p4:nil="false"></AudienceId>
            <AudienceType p4:nil="false"></AudienceType>
            <!--Keep these fields if you set the i:type attribute to Webpage-->
            <Parameter xmlns:e87="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
              <e87:Conditions p4:nil="false">
                <e87:WebpageCondition>
                  <e87:Argument p4:nil="false"></e87:Argument>
                  <e87:Operand></e87:Operand>
                </e87:WebpageCondition>
              </e87:Conditions>
              <e87:CriterionName p4:nil="false"></e87:CriterionName>
            </Parameter>
          </Criterion>
          <Id p4:nil="false"></Id>
          <Status p4:nil="false"></Status>
          <Type p4:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to BiddableAdGroupCriterion-->
          <CriterionBid p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
            <Type p4:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to FixedBid-->
            <Amount></Amount>
            <!--Keep these fields if you set the i:type attribute to BidMultiplier-->
            <Multiplier></Multiplier>
          </CriterionBid>
          <DestinationUrl p4:nil="false"></DestinationUrl>
          <EditorialStatus p4:nil="false"></EditorialStatus>
          <FinalAppUrls xmlns:e88="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e88:AppUrl>
              <e88:OsType p4:nil="false"></e88:OsType>
              <e88:Url p4:nil="false"></e88:Url>
            </e88:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e89="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e89:Parameters p4:nil="false">
              <e89:CustomParameter>
                <e89:Key p4:nil="false"></e89:Key>
                <e89:Value p4:nil="false"></e89:Value>
              </e89:CustomParameter>
            </e89:Parameters>
          </UrlCustomParameters>
          <!--Keep these fields if you set the i:type attribute to NegativeAdGroupCriterion-->
        </AdGroupCriterion>
      </AdGroupCriterions>
    </GetAdGroupCriterionsByIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddAdGroupCriterions](../campaign-api/addadgroupcriterions-service-operation.md)  
[ApplyProductPartitionActions](../campaign-api/applyproductpartitionactions-service-operation.md)  
[DeleteAdGroupCriterions](../campaign-api/deleteadgroupcriterions-service-operation.md)  
[UpdateAdGroupCriterions](../campaign-api/updateadgroupcriterions-service-operation.md)  

