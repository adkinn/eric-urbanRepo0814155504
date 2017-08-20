---
title: "GetCampaignCriterionsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8da2b953-82f4-4bb4-b8e5-d072e493dad6
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetCampaignCriterionsByIds Service Operation
Gets the specified campaign criterions.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>GetCampaignCriterionsByIdsRequest Message

### Request Body
The *GetCampaignCriterionsByIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*CampaignCriterionIds*|A list of unique identifiers that identify the campaign criterions to get.<br/><br/>You can include up to 100 campaign criterion identifiers per request.<br /><br />If this element is null, all criterions for the specified *CampaignId* will be retrieved.|*long* array|No|
|*CampaignId*|The unique identifier of the campaign whose criterions you want to get.|*long*|Yes|
|*CriterionType*|The type of criterion to get, for example *Webpage*. You can specify only one type. The *Targets* value is not allowed for this operation.|[CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md)|Yes|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">GetCampaignCriterionsByIds</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetCampaignCriterionsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<CampaignCriterionIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:long>\</a1:long>
      </CampaignCriterionIds>
      <CampaignId></CampaignId>
      <CriterionType></CriterionType>
    </GetCampaignCriterionsByIdsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetCampaignCriterionsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignCriterions*|The list of campaign criterions that correspond directly to the identifiers specified in the request. Items of the list may be returned as null. For each list index where a criterion was not retrieved, the corresponding element will be null.|[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <GetCampaignCriterionsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<CampaignCriterions p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<CampaignCriterion p4:type="-- specify derived type here with the appropriate prefix --">
          <CampaignId></CampaignId>
          \<Criterion p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
            \<Type p4:nil="false"></Type>
            \<!--Keep these fields if you set the i:type attribute to ProductScope-->
            \<Conditions p4:nil="false">
              <ProductCondition>
                \<Attribute p4:nil="false"></Attribute>
                \<Operand p4:nil="false"></Operand>
              </ProductCondition>
            </Conditions>
            \<!--Keep these fields if you set the i:type attribute to AgeCriterion-->
            \<AgeRange p4:nil="false"></AgeRange>
            \<!--Keep these fields if you set the i:type attribute to DeviceCriterion-->
            \<DeviceName p4:nil="false"></DeviceName>
            \<OSName p4:nil="false"></OSName>
            \<!--Keep these fields if you set the i:type attribute to DayTimeCriterion-->
            \<Day p4:nil="false"></Day>
            \<FromHour p4:nil="false"></FromHour>
            \<FromMinute p4:nil="false"></FromMinute>
            \<ToHour p4:nil="false"></ToHour>
            \<ToMinute p4:nil="false"></ToMinute>
            \<!--Keep these fields if you set the i:type attribute to GenderCriterion-->
            \<GenderType p4:nil="false"></GenderType>
            \<!--Keep these fields if you set the i:type attribute to RadiusCriterion-->
            \<LatitudeDegrees p4:nil="false"></LatitudeDegrees>
            \<LongitudeDegrees p4:nil="false"></LongitudeDegrees>
            \<Name p4:nil="false"></Name>
            \<Radius p4:nil="false"></Radius>
            \<RadiusUnit p4:nil="false"></RadiusUnit>
            \<!--Keep these fields if you set the i:type attribute to LocationCriterion-->
            \<DisplayName p4:nil="false"></DisplayName>
            \<EnclosedLocationIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
              \<a1:long>\</a1:long>
            </EnclosedLocationIds>
            \<LocationId p4:nil="false"></LocationId>
            \<LocationType p4:nil="false"></LocationType>
            \<!--Keep these fields if you set the i:type attribute to LocationIntentCriterion-->
            \<IntentOption p4:nil="false"></IntentOption>
            \<!--Keep these fields if you set the i:type attribute to AudienceCriterion-->
            \<AudienceId p4:nil="false"></AudienceId>
            \<AudienceType p4:nil="false"></AudienceType>
            \<!--Keep these fields if you set the i:type attribute to Webpage-->
            \<Parameter xmlns:e109="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
              \<e109:Conditions p4:nil="false">
                \<e109:WebpageCondition>
                  \<e109:Argument p4:nil="false">\</e109:Argument>
                  \<e109:Operand>\</e109:Operand>
                \</e109:WebpageCondition>
              \</e109:Conditions>
              \<e109:CriterionName p4:nil="false">\</e109:CriterionName>
            </Parameter>
          </Criterion>
          \<ForwardCompatibilityMap xmlns:e110="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e110:KeyValuePairOfstringstring>
              \<e110:key p4:nil="false">\</e110:key>
              \<e110:value p4:nil="false">\</e110:value>
            \</e110:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          \<Id p4:nil="false"></Id>
          \<Status p4:nil="false"></Status>
          \<Type p4:nil="false"></Type>
          \<!--Keep these fields if you set the i:type attribute to NegativeCampaignCriterion-->
          \<!--Keep these fields if you set the i:type attribute to BiddableCampaignCriterion-->
          \<CriterionBid p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
            \<Type p4:nil="false"></Type>
            \<!--Keep these fields if you set the i:type attribute to FixedBid-->
            <Amount></Amount>
            \<!--Keep these fields if you set the i:type attribute to BidMultiplier-->
            <Multiplier></Multiplier>
          </CriterionBid>
        </CampaignCriterion>
      </CampaignCriterions>
      \<PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          \<Details p4:nil="false"></Details>
          \<ErrorCode p4:nil="false"></ErrorCode>
          \<FieldPath p4:nil="false"></FieldPath>
          \<ForwardCompatibilityMap xmlns:e111="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e111:KeyValuePairOfstringstring>
              \<e111:key p4:nil="false">\</e111:key>
              \<e111:value p4:nil="false">\</e111:value>
            \</e111:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          \<Message p4:nil="false"></Message>
          \<Type p4:nil="false"></Type>
          \<!--Keep these fields if you set the i:type attribute to EditorialError-->
          \<Appealable p4:nil="false"></Appealable>
          \<DisapprovedText p4:nil="false"></DisapprovedText>
          \<Location p4:nil="false"></Location>
          \<PublisherCountry p4:nil="false"></PublisherCountry>
          <ReasonCode></ReasonCode>
        </BatchError>
      </PartialErrors>
    </GetCampaignCriterionsByIdsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddCampaignCriterions](../campaign-api/addcampaigncriterions-service-operation.md)  
[DeleteCampaignCriterions](../campaign-api/deletecampaigncriterions-service-operation.md)  
[UpdateCampaignCriterions](../campaign-api/updatecampaigncriterions-service-operation.md)  
[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md)  
[NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md)  
[CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md)  

