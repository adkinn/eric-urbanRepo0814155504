---
title: "AddUetTags Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31ed1ffd-5725-43d9-9f6f-0ac86a7d321f
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddUetTags Service Operation
Adds new Universal Event Tracking (UET) tags that you can add to your website to allow Bing Ads to collect actions people take on your website.

After you create a UET tag, the next step is to add the UET tag tracking code to your website. We recommend that you, or your website administrator, add it to your entire website in either the head or body sections. If your website has a master page, then that is the best place to add it because you add it once and it is included on all pages. For more information, see [How do I add the UET tag to my website?](https://help.bingads.microsoft.com/#apex/3/en/56688/2).

You can use one UET tag with all of your conversion goals and remarketing lists. Before you create multiple UET tags, see [Reasons for creating more than one UET tag](https://help.bingads.microsoft.com/#apex/3/en/56685/2).

[!INCLUDE[guide_uet](../campaign-api/includes/guide-uet.md)]

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddUetTagsRequest Message

### Request Body
The *AddUetTagsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the customer identifier in the *CustomerId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*UetTags*|An array of [UetTag](../campaign-api/uettag-data-object.md) objects to add to the customer's shared UET tag library.<br/><br/>The customer is determined by the required *CustomerId* header element.<br /><br />You can add a maximum of 100 UET tags in a single call, although please note that you can use one UET tag with all of your conversion goals and remarketing lists. Before you create multiple UET tags, see [Reasons for creating more than one UET tag](https://help.bingads.microsoft.com/#apex/3/en/56685/2).<br/><br/>**Note:** If the call is successful, the tracking script that you should add to your website is included in a corresponding [UetTag](../campaign-api/uettag-data-object.md) within the response message.|[UetTag](../campaign-api/uettag-data-object.md) array|

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
    <Action mustUnderstand="1">AddUetTags</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <AddUetTagsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<UetTags i:nil="false">
        <UetTag>
          \<Description i:nil="false"></Description>
          \<Id i:nil="false"></Id>
          \<Name i:nil="false"></Name>
          \<TrackingNoScript i:nil="false"></TrackingNoScript>
          \<TrackingScript i:nil="false"></TrackingScript>
          \<TrackingStatus i:nil="false"></TrackingStatus>
        </UetTag>
      </UetTags>
    </AddUetTagsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>AddUetTagsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*UetTag*|An array of [UetTag](../campaign-api/uettag-data-object.md) objects that corresponds directly to the [UetTag](../campaign-api/uettag-data-object.md) objects that you specified in the request. Items of the array may be returned as null. For each array index where a UET tag was not added, the corresponding element will be null.|[RemarketingList](../campaign-api/remarketinglist-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]

### <a name="response_soap"></a>Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <AddUetTagsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<UetTags p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <UetTag>
          \<Description p4:nil="false"></Description>
          \<Id p4:nil="false"></Id>
          \<Name p4:nil="false"></Name>
          \<TrackingNoScript p4:nil="false"></TrackingNoScript>
          \<TrackingScript p4:nil="false"></TrackingScript>
          \<TrackingStatus p4:nil="false"></TrackingStatus>
        </UetTag>
      </UetTags>
      \<PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          \<Details p4:nil="false"></Details>
          \<ErrorCode p4:nil="false"></ErrorCode>
          \<FieldPath p4:nil="false"></FieldPath>
          \<ForwardCompatibilityMap xmlns:e46="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e46:KeyValuePairOfstringstring>
              \<e46:key p4:nil="false">\</e46:key>
              \<e46:value p4:nil="false">\</e46:value>
            \</e46:KeyValuePairOfstringstring>
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
    </AddUetTagsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[RemarketingList](../campaign-api/remarketinglist-data-object.md)  
[UetTag](../campaign-api/uettag-data-object.md)  
[GetUetTagsByIds](../campaign-api/getuettagsbyids-service-operation.md)  
[UpdateUetTags](../campaign-api/updateuettags-service-operation.md)  