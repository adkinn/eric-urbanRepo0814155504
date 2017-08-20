---
title: "DeleteCampaignCriterions Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 116e5b0c-515c-46e6-9fc2-61b2c77d5836
caps.latest.revision: 18
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeleteCampaignCriterions Service Operation
Deletes one or more campaign criterions.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>DeleteCampaignCriterionsRequest Message

### Request Body
The *DeleteCampaignCriterionsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignCriterionIds*|A list of unique system identifiers corresponding to the campaign criterions that you want to delete.<br/><br/>You can include up to 100 campaign criterion identifiers per request.|*long* array|
|*CampaignId*|The identifier of the campaign that owns the criterions to delete.|*long*|
|*CriterionType*|The type of criterion to delete, for example *Webpage*. You can specify only one criterion type value per call.<br/><br/>To add, delete, or update target criterions i.e., age, day and time, device, gender, location, location intent, and radius criterions, you must specify the *CriterionType* value as *Targets*. You can add, delete, and update multiple target criterion types in the same operation. To retrieve these target criterions via [GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md) you must request the specific type individually i.e., *Age*, *DayTime*, *Device*, *Gender*, *Location*, *LocationIntent*, and *Radius*. |[CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md)|

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
    <Action mustUnderstand="1">DeleteCampaignCriterions</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <DeleteCampaignCriterionsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <CampaignCriterionIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </CampaignCriterionIds>
      <CampaignId></CampaignId>
      <CriterionType></CriterionType>
    </DeleteCampaignCriterionsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>DeleteCampaignCriterionsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*IsMigrated*|Indicates whether or not the campaign where you deleted target criterions previously shared target criterions with another campaign or ad group. In that case this operation migrates the shared target associations and assigns new campaign criterion IDs.<br/><br/>If this value is true and if you already have criterion IDs for targets such as age, day and time, device, gender, and location, then you should replace those IDs with all of the new IDs returned by the [GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md) operation (specify *TargetCriterions* as the *CriterionType*). You only need to sync target criterion IDs, and this is not applicable for other criterion types such as webpage criterions. For more information, see [Upgrading Targets to Criterions](https://msdn.microsoft.com/library/bing-ads-target-to-criterions.aspx)|*boolean*|
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
    <DeleteCampaignCriterionsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <IsMigrated></IsMigrated>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e60="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e60:KeyValuePairOfstringstring>
              <e60:key p4:nil="false"></e60:key>
              <e60:value p4:nil="false"></e60:value>
            </e60:KeyValuePairOfstringstring>
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
    </DeleteCampaignCriterionsResponse>
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
[GetCampaignCriterionsByIds](../campaign-api/getcampaigncriterionsbyids-service-operation.md)  
[UpdateCampaignCriterions](../campaign-api/updatecampaigncriterions-service-operation.md)    
[CampaignCriterion](../campaign-api/campaigncriterion-data-object.md)  
[NegativeCampaignCriterion](../campaign-api/negativecampaigncriterion-data-object.md)  
[CampaignCriterionType](../campaign-api/campaigncriteriontype-value-set.md)  

