---
title: "Audience Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d158957-a49f-4c57-bd3f-95f0f7cb7528
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
---
# Audience Data Object
Defines the base object of an audience.

Do not try to instantiate an *Audience*. You can create one or more following objects that derive from it.
- [CustomAudience](../campaign-api/customaudience-data-object.md)  
- [InMarketAudience](../campaign-api/inmarketaudience-data-object.md)  
- [RemarketingList](../campaign-api/remarketinglist-data-object.md)  

## Syntax

```xml
\<xs:complexType name="Audience">
  \<xs:sequence>
    \<xs:element name="Description" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="ForwardCompatibilityMap" type="q105:ArrayOfKeyValuePairOfstringstring" nillable="true" minOccurs="0" xmlns:q105="http://schemas.datacontract.org/2004/07/System.Collections.Generic"/>
    \<xs:element name="Id" type="xs:long" nillable="true" minOccurs="0"/>
    \<xs:element name="MembershipDuration" type="xs:int" minOccurs="0"/>
    \<xs:element name="Name" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="ParentId" type="xs:long" minOccurs="0"/>
    \<xs:element name="Scope" type="tns:EntityScope" minOccurs="0"/>
    \<xs:element name="Type" nillable="true" type="tns:AudienceType" minOccurs="0"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Description*|The description of the audience. Use a description to help you remember what audience you are targeting.<br/><br/>The description can contain a maximum of 1,024 characters.|*string*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *Audience* object.|*KeyValuePairOfstringstring* array|
|*Id*|The Bing Ads identifier of the audience.|*long*|
|*MembershipDuration*|When you create an audience, you can specify how far back in time Bing Ads should look for actions that match your audience definition.<br/><br/>The mimimum duration is 1 day and the maximum duration allowed is 180 days.|*int*|
|*Name*|The name of the audience. The name can contain a maximum of 128 characters.|*string*|
|*ParentId*|The Bing Ads identifier of the account or customer. <br/><br/>If the *Scope* is set to *Account*, this is the account ID, and otherwise it is the customer ID.|*long*|
|*Scope*|Scope defines what accounts can use this audience.<br/><br/> If scope is set to *Account*, the audience can only be associated with ad groups within one specified account (*ParentId*). If scope is set to *Customer*, the audience can be associated with any ad groups across all of the customer's accounts.|[EntityScope](../campaign-api/entityscope-value-set.md)|
|*Type*|The type of the audience. For more information about audience types, see the [Remarks](#remarks).|[AudienceType](../campaign-api/audiencetype-value-set.md)|


## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by whether you instantiate a custom audience or another type of audience. If you generate the SOAP manually, use the *type* attribute of the *Audience* node as shown in the following example.

```xml
\<Audiences xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  \<Audience i:type="CustomAudience">
    \<Description i:nil="false">Custom Audience Description</Description>
    \<ForwardCompatibilityMap xmlns:e43="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
      \<e43:KeyValuePairOfstringstring>
        \<e43:key i:nil="false">\</e43:key>
        \<e43:value i:nil="false">\</e43:value>
      \</e43:KeyValuePairOfstringstring>
    </ForwardCompatibilityMap>
    \<Id i:nil="true" />
    \<MembershipDuration i:nil="false">30</MembershipDuration>
    \<Name i:nil="false">Custom Audience Name</Name>
    \<ParentId i:nil="false">ParentIdHere</ParentId>
    <Scope>Customer</Scope>
  </Audience>
</Audiences>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[AddAudiences](../campaign-api/addaudiences-service-operation.md)  
[DeleteAudiences](../campaign-api/deleteaudiences-service-operation.md)  
[GetAudiencesByIds](../campaign-api/getaudiencesbyids-service-operation.md)  
[UpdateAudiences](../campaign-api/updateaudiences-service-operation.md)  

