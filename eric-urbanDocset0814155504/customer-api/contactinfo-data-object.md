---
title: "ContactInfo Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40cc65a4-90cb-4f2c-9ee8-0d2307160603
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ContactInfo Data Object
Defines the contact information for a user.

## Syntax

```xml
<xs:complexType name="ContactInfo">
  <xs:sequence>
    <xs:element minOccurs="0" name="Address" nillable="true" type="tns:string" />
    <xs:element minOccurs="0" name="ContactByPhone" nillable="true" type="xsd:boolean" />
    <xs:element minOccurs="0" name="ContactByPostalMail" nillable="true" type=" xsd:boolean " />
    <xs:element minOccurs="0" name="Email" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="EmailFormat" nillable="true" type="tns:EmailFormat" />
    <xs:element minOccurs="0" name="Fax" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="HomePhone" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="Id" nillable="true" type="xsd:long" />
    <xs:element minOccurs="0" name="Mobile" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="Phone1" nillable="true" type="xsd:string" />
    <xs:element minOccurs="0" name="Phone2" nillable="true" type="xsd:string" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Address*|The address of the user.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|[Address](../customer-api/address-data-object.md)|
|*ContactByPhone*|A value that determines whether the user should be contacted by telephone. If **true**, the telephone number specified in the *Phone1* element is used to contact the user.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*boolean*|
|*ContactByPostalMail*|A value that determines whether the user should be contacted by postal mail. If **true**, correspondence is sent to the address specified in the *Address* element.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*boolean*|
|*Email*|The email address is used to send the account activation notification to the user, and can contain a maximum of 100 characters.<br /><br />If the user should be contacted by email, set the *EmailFormat* element to a valid format value.<br /><br />**Note:** The contact info email address may differ from the email address corresponding to the authenticated Microsoft Account. For more information, see the *IsMigratedToMicrosoftAccount* and *UserName* elements of the [User](../customer-api/user-data-object.md).<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*EmailFormat*|The format of the body of an email message to use when correspondence is sent to the user (this does not apply to the activation notification email message).<br /><br />You must set this element if you want the user contacted via email.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|[EmailFormat Value Set](../customer-api/emailformat-value-set.md)|
|*Fax*|The fax telephone number of the user. The telephone number can contain a maximum of 100 characters.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*HomePhone*|The home telephone number of the user. The telephone number can contain a maximum of 100 characters.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Id*|The system generated identifier of the object.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Mobile*|The mobile telephone number of the user. The telephone number can contain a maximum of 100 characters.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Phone1*|The primary telephone number of the user. The telephone number can contain a maximum of 100 characters.<br/><br/>**Add:** Required<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*Phone2*|An alternate telephone number for the user. The telephone number can contain a maximum of 100 characters.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[User](../customer-api/user-data-object.md)

