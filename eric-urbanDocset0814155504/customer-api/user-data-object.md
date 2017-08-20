---
title: "User Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c99e55b-a4f1-4608-a9ff-4c0ddf795f4d
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# User Data Object
Defines a user.

## Syntax

```xml
<xs:complexType name="User">
  <xs:sequence>
    <xs:element minOccurs="0" name="ContactInfo" nillable="true" type="tns:ContactInfo" />
    <xs:element minOccurs="0" name="CustomerAppScope" nillable="true" type="tns:ApplicationType" />
    <xs:element minOccurs="0" name="CustomerId" nillable="true" type="xsd:long" />
    <xs:element minOccurs="0" name="Id" nillable="true" type="xss:long" />
    <xs:element minOccurs="0" name="JobTitle" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="LastModifiedByUserId" nillable="true" type="xsd:long" />
    <xs:element minOccurs="0" name="LastModifiedTime" nillable="true" type="xsd:dateTime" />
    <xs:element minOccurs="0" name="Lcid" nillable="true" type="tns:LCID" />
    <xs:element minOccurs="0" name="Name" nillable="true" type="tns:PersonName" />
    <xs:element minOccurs="0" name="Password" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="SecretAnswer" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="SecretQuestion" type="tns:SecretQuestion" />
    <xs:element minOccurs="0" name="UserLifeCycleStatus" nillable="true" type="tns:UserLifeCycleStatus" />
    <xs:element minOccurs="0" name="TimeStamp" nillable="true" type="xsd:base64Binary" />
    <xs:element minOccurs="0" name="UserName" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="IsMigratedToMicrosoftAccount" nillable="true" type="xsd:boolean" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ContactInfo*|The user’s contact information.<br/><br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|[ContactInfo](../customer-api/contactinfo-data-object.md)|
|*CustomerAppScope*|Confirms that the customer to whom this user belongs is an advertiser.<br/><br/>**Update:** Read-only|[ApplicationType](../customer-api/applicationtype-value-set.md)|
|*CustomerId*|The identifier of the customer to whom this user belongs.<br/><br/>**Update:** Read-only|*long*|
|*Id*|The system generated identifier of the user.<br/><br/>**Update:** Required|*long*|
|*IsMigratedToMicrosoftAccount*|If *true*, the user can be authenticated using  a Microsoft Account. For more information, see [Authentication with OAuth](https://msdn.microsoft.com/library/bing-ads-user-authentication-oauth-guide.aspx).<br/><br/>**Update:** Read-only|*boolean*|
|*JobTitle*|The user's job title. The title can contain a maximum of 50 characters.<br/><br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*LastModifiedByUserId*|The identifier of the last user to update the user’s information.<br/><br/>**Update:** Read-only|*long*|
|*LastModifiedTime*|The date and time that that the user information was last updated. The value is in Coordinated Universal Time (UTC).<br /><br />The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](http://msdn.microsoft.com/library/ms256220.aspx).<br/><br/>**Update:** Read-only|*dateTime*|
|*Lcid*|The locale to use when sending correspondence to the user by email or postal mail. The default is EnglishUS.<br/><br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|[LCID](../customer-api/lcid-value-set.md)|
|*Name*|The name of the user.<br/><br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|[PersonName](../customer-api/personname-data-object.md)|
|*Password*|The user’s [!INCLUDE[brand](../customer-api/includes/brand.md)] managed sign-in password.<br /><br />The [GetUser](../customer-api/getuser-service-operation.md) operation does not return the password.<br/><br/>**Update:** Read-only|*string*|
|*SecretAnswer*|The answer to the secret question that is specified in the *SecretQuestion* element. The answer must contain a minimum of five characters and a maximum of 64 characters.<br/><br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*SecretQuestion*|A question from a list of predefined questions that the user selects to use as his or her secret question. The *SecretAnswer* element contains the user’s answer to the question. The secret question and answer are used to validate the user in case the user forgets his or her password, and requests it.<br/><br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|[SecretQuestion](../customer-api/secretquestion-value-set.md)|
|*TimeStamp*|A time-stamp value that the system uses internally to reconcile updates when you call [UpdateUser](../customer-api/updateuser-service-operation.md) or [DeleteUser](../customer-api/deleteuser-service-operation.md).<br/><br/>**Update:** Required|*base64Binary*|
|*UserLifeCycleStatus*|The status of the user.<br/><br/>**Update:** Read-only|[UserLifeCycleStatus](../customer-api/userlifecyclestatus-value-set.md)|
|*UserName*|If the value of *IsMigratedToMicrosoftAccount* is false, this element contains the user's [!INCLUDE[brand](../customer-api/includes/brand.md)] managed sign-in user name. The name is case-insensitive.<br /><br />If the value of *IsMigratedToMicrosoftAccount* is true, this element contains the email address corresponding to the authenticated Microsoft Account.<br /><br />**Note:** The email address of the Microsoft Account may differ from the Email element of the [ContactInfo](../customer-api/contactinfo-data-object.md) object.<br/><br/>**Update:** Read-only|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[UserInfo](../customer-api/userinfo-data-object.md)  

