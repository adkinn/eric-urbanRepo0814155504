---
title: "ApplyOfflineConversions Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a85c5703-adba-4b23-a18f-df012d189868
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
---
# ApplyOfflineConversions Service Operation
Applies offline conversions for the account with Microsoft Click Id among other offline conversion data.

Let's say a customer sees your ad, clicks on it, but ends up calling you, leading to a sale that was taken offline. How can you track when your search ad leads to a conversion offline and outside of your website? You can import offline conversions, to better measure what happens after your ad was clicked.

After creating an [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md), you?ll need to wait two hours before sending Bing Ads any offline conversions. If you do not wait two hours, then your offline conversion data might not be applied. After you send Bing Ads the offline conversions, it can take up to five hours to view conversion data.

Each offline conversion needs to be associated to a single click ID. A single click ID can, however, be associated with multiple conversion goals and also be associated with the same goal multiple times, as long as the conversion time is different. Also, the same conversion can't be imported more than once. If more than one is attempted, the first instance will be used and the others will be ignored.

The value of the conversion can be included in the import file along with a custom currency. If no currency is stated, the conversion goal's default will be used.

For more information, see [Tracking offline conversions](https://help.bingads.microsoft.com/#apex/3/en/help:app54554/1/en-US/#ext:ConversionTracking_Load).

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>ApplyOfflineConversionsRequest Message

### Request Body
The *ApplyOfflineConversionsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*OfflineConversions*|The list of offline conversions for the account.<br /><br />You can add a maximum of 1,000 offline conversions per service request.<br/><br/>Each offline conversion needs to be associated to a single click ID. A single click ID can, however, be associated with multiple conversion goals and also be associated with the same goal multiple times, as long as the conversion time is different. Also, the same conversion can't be applied more than once. If you send Bing Ads duplicates, the first instance will be used and the others will be ignored.|[OfflineConversion](../campaign-api/offlineconversion-data-object.md) array|

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
    <Action mustUnderstand="1">ApplyOfflineConversions</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <ApplyOfflineConversionsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <OfflineConversions i:nil="false">
        <OfflineConversion>
          <ConversionCurrencyCode i:nil="false"></ConversionCurrencyCode>
          <ConversionName i:nil="false"></ConversionName>
          <ConversionTime></ConversionTime>
          <ConversionValue i:nil="false"></ConversionValue>
          <MicrosoftClickId i:nil="false"></MicrosoftClickId>
        </OfflineConversion>
      </OfflineConversions>
    </ApplyOfflineConversionsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>ApplyOfflineConversionsResponse Message

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
    <ApplyOfflineConversionsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e52="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e52:KeyValuePairOfstringstring>
              <e52:key p4:nil="false"></e52:key>
              <e52:value p4:nil="false"></e52:value>
            </e52:KeyValuePairOfstringstring>
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
    </ApplyOfflineConversionsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884)[Bing Ads Operation Error Codes](http://msdn.microsoft.com/library/bing-ads-operation-error-codes.aspx).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[OfflineConversion](../campaign-api/offlineconversion-data-object.md)  
[OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md)  

