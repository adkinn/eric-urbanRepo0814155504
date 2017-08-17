---
title: "UpdateCampaignCriterions Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5909f8f-bc63-488a-bb9f-9a385cc1525d
caps.latest.revision: 19
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateCampaignCriterions Service Operation
Updates one or more campaign criterions.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>UpdateCampaignCriterionsRequest Message

### Request Body
The *UpdateCampaignCriterionsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignCriterions*|The list of campaign criterions to update.<br/><br/>You can include up to 100 campaign criterions per request.<br /><br />Within each [CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) object, you must specify the criterion’s ID and the ID of the campaign that it belongs to.|[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md) array|
|*CriterionType*|The type of criterion to update, for example *Webpage*. You can specify only one criterion type value per call.<br/><br/>To add, delete, or update target criterions i.e., age, day and time, device, gender, location, location intent, and radius criterions, you must specify the *CriterionType* value as *Targets*. You can add, delete, and update multiple target criterion types in the same operation. To retrieve these target criterions via [GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md) you must request the specific type individually i.e., *Age*, *DayTime*, *Device*, *Gender*, *Location*, *LocationIntent*, and *Radius*.|[CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md)|

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
    <Action mustUnderstand="1">UpdateCampaignCriterions</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateCampaignCriterionsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <CampaignCriterions i:nil="false">
        <CampaignCriterion i:type="-- specify derived type here with the appropriate prefix --">
          <CampaignId></CampaignId>
          <Criterion i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
            <Type i:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to ProductScope-->
            <Conditions i:nil="false">
              <ProductCondition>
                <Attribute i:nil="false"></Attribute>
                <Operand i:nil="false"></Operand>
              </ProductCondition>
            </Conditions>
            <!--Keep these fields if you set the i:type attribute to AgeCriterion-->
            <AgeRange i:nil="false"></AgeRange>
            <!--Keep these fields if you set the i:type attribute to DeviceCriterion-->
            <DeviceName i:nil="false"></DeviceName>
            <OSName i:nil="false"></OSName>
            <!--Keep these fields if you set the i:type attribute to DayTimeCriterion-->
            <Day i:nil="false"></Day>
            <FromHour i:nil="false"></FromHour>
            <FromMinute i:nil="false"></FromMinute>
            <ToHour i:nil="false"></ToHour>
            <ToMinute i:nil="false"></ToMinute>
            <!--Keep these fields if you set the i:type attribute to GenderCriterion-->
            <GenderType i:nil="false"></GenderType>
            <!--Keep these fields if you set the i:type attribute to RadiusCriterion-->
            <LatitudeDegrees i:nil="false"></LatitudeDegrees>
            <LongitudeDegrees i:nil="false"></LongitudeDegrees>
            <Name i:nil="false"></Name>
            <Radius i:nil="false"></Radius>
            <RadiusUnit i:nil="false"></RadiusUnit>
            <!--Keep these fields if you set the i:type attribute to LocationCriterion-->
            <DisplayName i:nil="false"></DisplayName>
            <EnclosedLocationIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
              <a1:long></a1:long>
            </EnclosedLocationIds>
            <LocationId i:nil="false"></LocationId>
            <LocationType i:nil="false"></LocationType>
            <!--Keep these fields if you set the i:type attribute to LocationIntentCriterion-->
            <IntentOption i:nil="false"></IntentOption>
            <!--Keep these fields if you set the i:type attribute to AudienceCriterion-->
            <AudienceId i:nil="false"></AudienceId>
            <AudienceType i:nil="false"></AudienceType>
            <!--Keep these fields if you set the i:type attribute to Webpage-->
            <Parameter xmlns:e176="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
              <e176:Conditions i:nil="false">
                <e176:WebpageCondition>
                  <e176:Argument i:nil="false"></e176:Argument>
                  <e176:Operand></e176:Operand>
                </e176:WebpageCondition>
              </e176:Conditions>
              <e176:CriterionName i:nil="false"></e176:CriterionName>
            </Parameter>
          </Criterion>
          <ForwardCompatibilityMap xmlns:e177="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e177:KeyValuePairOfstringstring>
              <e177:key i:nil="false"></e177:key>
              <e177:value i:nil="false"></e177:value>
            </e177:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id i:nil="false"></Id>
          <Status i:nil="false"></Status>
          <Type i:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to NegativeCampaignCriterion-->
          <!--Keep these fields if you set the i:type attribute to BiddableCampaignCriterion-->
          <CriterionBid i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
            <Type i:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to FixedBid-->
            <Amount></Amount>
            <!--Keep these fields if you set the i:type attribute to BidMultiplier-->
            <Multiplier></Multiplier>
          </CriterionBid>
        </CampaignCriterion>
      </CampaignCriterions>
      <CriterionType></CriterionType>
    </UpdateCampaignCriterionsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateCampaignCriterionsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*IsMigrated*|Indicates whether or not the campaign where you updated target criterions previously shared target criterions with another campaign or ad group. In that case this operation migrates the shared target associations and assigns new campaign criterion IDs.<br/><br/>If this value is true and if you already have criterion IDs for targets such as age, day and time, device, gender, and location, then you should replace those IDs with all of the new IDs returned by the [GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md) operation (specify *TargetCriterions* as the *CriterionType*). You only need to sync target criterion IDs, and this is not applicable for other criterion types such as webpage criterions. For more information, see [Upgrading Targets to Criterions](https://msdn.microsoft.com/library/bing-ads-target-to-criterions.aspx)|*boolean*|
|*NestedPartialErrors*|An array of [BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) objects that contain details for any criterion that were not successfully updated. The top level error within each [BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) object corresponds to potential criterion errors. The nested list of [BatchError](../campaign-api/batcherror-data-object.md) objects would include any errors specific to the list of items a criterion can have, for example a list of product conditions.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) array|

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
    <UpdateCampaignCriterionsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <IsMigrated></IsMigrated>
      <NestedPartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchErrorCollection>
          <BatchErrors p4:nil="false">
            <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
              <Code></Code>
              <Details p4:nil="false"></Details>
              <ErrorCode p4:nil="false"></ErrorCode>
              <FieldPath p4:nil="false"></FieldPath>
              <ForwardCompatibilityMap xmlns:e178="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
                <e178:KeyValuePairOfstringstring>
                  <e178:key p4:nil="false"></e178:key>
                  <e178:value p4:nil="false"></e178:value>
                </e178:KeyValuePairOfstringstring>
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
          </BatchErrors>
          <Code p4:nil="false"></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e179="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e179:KeyValuePairOfstringstring>
              <e179:key p4:nil="false"></e179:key>
              <e179:value p4:nil="false"></e179:value>
            </e179:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          <Message p4:nil="false"></Message>
          <Type p4:nil="false"></Type>
        </BatchErrorCollection>
      </NestedPartialErrors>
    </UpdateCampaignCriterionsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddCampaignCriterions](../campaign-api/addcampaigncriterions-service-operation.md)  
[DeleteCampaignCriterions](../campaign-api/deletecampaigncriterions-service-operation.md)  
[GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md)  
[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md)  
[NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md)  
[CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md)  

