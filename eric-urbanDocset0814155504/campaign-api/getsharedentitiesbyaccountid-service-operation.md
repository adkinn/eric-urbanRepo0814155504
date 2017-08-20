---
title: "GetSharedEntitiesByAccountId Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5939b0c3-ecc3-4c52-9471-a3114eec78f3
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetSharedEntitiesByAccountId Service Operation
Gets the negative keyword lists from the account's library.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>GetSharedEntitiesByAccountIdRequest Message

### Request Body
The *GetSharedEntitiesByAccountIdRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*SharedEntityType*|The type of shared entity to get from the account's library.<br /><br />Currently the only supported value is NegativeKeywordList.|*string*|

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
    <Action mustUnderstand="1">GetSharedEntitiesByAccountId</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetSharedEntitiesByAccountIdRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<SharedEntityType i:nil="false"></SharedEntityType>
    </GetSharedEntitiesByAccountIdRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetSharedEntitiesByAccountIdResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*SharedEntities*|The shared entities from the account's shared library, for example negative keyword lists.|[SharedEntity](../campaign-api/sharedentity-data-object.md) array|

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
    <GetSharedEntitiesByAccountIdResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<SharedEntities p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<SharedEntity p4:type="-- specify derived type here with the appropriate prefix --">
          \<AssociationCount p4:nil="false"></AssociationCount>
          \<ForwardCompatibilityMap xmlns:e138="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e138:KeyValuePairOfstringstring>
              \<e138:key p4:nil="false">\</e138:key>
              \<e138:value p4:nil="false">\</e138:value>
            \</e138:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          \<Id p4:nil="false"></Id>
          \<Name p4:nil="false"></Name>
          \<Type p4:nil="false"></Type>
          \<!--Keep these fields if you set the i:type attribute to SharedList-->
          \<ItemCount p4:nil="false"></ItemCount>
        </SharedEntity>
      </SharedEntities>
    </GetSharedEntitiesByAccountIdResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddSharedEntity](../campaign-api/addsharedentity-service-operation.md)  
[DeleteSharedEntities](../campaign-api/deletesharedentities-service-operation.md)  
[DeleteSharedEntityAssociations](../campaign-api/deletesharedentityassociations-service-operation.md)  
[GetSharedEntityAssociationsByEntityIds](../campaign-api/getsharedentityassociationsbyentityids-service-operation.md)  
[GetSharedEntityAssociationsBySharedEntityIds](../campaign-api/getsharedentityassociationsbysharedentityids-service-operation.md)  
[SetSharedEntityAssociations](../campaign-api/setsharedentityassociations-service-operation.md)  
[UpdateSharedEntities](../campaign-api/updatesharedentities-service-operation.md)  

