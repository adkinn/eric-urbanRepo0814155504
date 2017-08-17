---
title: "ClientLink Data Object"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e48370d-9a37-44d0-9a88-bf3595c74b46
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ClientLink Data Object
Defines a client link object. Acceptance of a client link invitation enables an agency to  manage the corresponding client accounts. To send an invitation to manage a client account, call the [AddClientLinks](../customer-api/addclientlinks-service-operation.md) operation and specify one client link per account to manage. For more information about the client link lifecycle, see [Link to Client Accounts](https://msdn.microsoft.com/library/bing-ads-agency-management-model-guide.aspx#clientlink).

> [!NOTE]
> This object does not have a system defined identifier. To uniquely identify a client link, use either the *ClientAccountId* or *ClientAccountNumber* paired with either the *ManagingCustomerId* or *ManagingCustomerNumber*.

## Syntax

```xml
\<xs:complexType name="ClientLink">
  \<xs:sequence>
    \<xs:element name="ClientAccountId" type="xs:int" nillable="true" minOccurs="0"/>
    \<xs:element name="ClientAccountNumber" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="ManagingCustomerId" type="xs:int" nillable="true" minOccurs="0"/>
    \<xs:element name="ManagingCustomerNumber" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="Note" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="Name" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="InviterEmail" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="InviterName" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="InviterPhone" type="xs:string" nillable="true" minOccurs="0"/>
    \<xs:element name="IsBillToClient" type="xs:boolean" minOccurs="0"/>
    \<xs:element name="StartDate" type="xs:dateTime" nillable="true" minOccurs="0"/>
    \<xs:element name="Status" type="tns:ClientLinkStatus" nillable="true" minOccurs="0"/>
    \<xs:element name="SuppressNotification" type="xs:boolean" minOccurs="0"/>
    \<xs:element name="LastModifiedDateTime" type="xs:dateTime" minOccurs="0"/>
    \<xs:element name="LastModifiedByUserId" type="xs:int" minOccurs="0"/>
    \<xs:element name="Timestamp" type="xs:base64Binary" nillable="true" minOccurs="0"/>
    \<xs:element name="ForwardCompatibilityMap" type="q4:ArrayOfKeyValuePairOfstringstring" nillable="true" minOccurs="0" xmlns:q4="http://schemas.datacontract.org/2004/07/System.Collections.Generic"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ClientAccountId*|The identifier of the client account to manage.<br /><br />When adding a client link, either the *ClientAccountId* or *ClientAccountNumber* is required, but specifying both will cause the operation to fail.<br/><br/>**Add:** Optional<br/>**Update:** Read-only and Required|*long*|
|*ClientAccountNumber*|The number of the client account to manage.<br /><br />When adding a client link, either the *ClientAccountId* or *ClientAccountNumber* is required, but specifying both will cause the operation to fail.<br/><br/>**Add:** Optional<br/>**Update:** Read-only and Required|*string*|
|*ForwardCompatibilityMap*|The list of key and value strings for forward compatibility. This element can be used to avoid otherwise breaking changes when new elements are added in future releases.<br /><br />**Note:** Forward compatibility changes will be noted here in future releases. There are currently no forward compatibility changes for the *ClientLink* object.|*KeyValuePairOfstringstring* array|
|*IsBillToClient*|Determines whether the owner of the client account or the managing customer is responsible for billing payments.<br /><br />If set to true the client will be responsible and otherwise, since the default value is false, the managing customer is responsible for billing.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|*boolean*|
|*InviterEmail*|The email of the user who created the client link request.<br /><br />This value does not need to be the same as, nor is it used to modify, the email already stored in [!INCLUDE[brand](../customer-api/includes/brand.md)] for the current authenticated user.<br /><br />If not specified, the service will set this value to the email already stored in [!INCLUDE[brand](../customer-api/includes/brand.md)] for the current authenticated user.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|*string*|
|*InviterName*|The name of the parent customer of the user who  created the client link request.<br /><br />This value does not need to be the same as, nor is it used to modify, the customer name already stored in [!INCLUDE[brand](../customer-api/includes/brand.md)].<br /><br />If not specified, the service will set this value to the parent customer name already stored in [!INCLUDE[brand](../customer-api/includes/brand.md)] for the current authenticated user.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|*string*|
|*InviterPhone*|The phone number of the user who created the client link request.<br /><br />This value does not need to be the same as, nor is it used to modify, the phone number already stored in [!INCLUDE[brand](../customer-api/includes/brand.md)] for the current authenticated user.<br /><br />If not specified, the service will set this value to the phone number already stored in [!INCLUDE[brand](../customer-api/includes/brand.md)] for the current authenticated user.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|*string*|
|*LastModifiedByUserId*|The identifier of the last user to update the client link’s information.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*long*|
|*LastModifiedDateTime*|The date and time that the client link was last updated. The value is in Coordinated Universal Time (UTC).<br /><br />**Note:** The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](http://msdn.microsoft.com/library/ms256220.aspx).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*dateTime*|
|*ManagingCustomerId*|The identifier of the customer who manages or is requesting to manage the client account.<br /><br />When adding a client link, either the *ManagingCustomerId* or *ManagingCustomerNumber* is required, but specifying both will cause the operation to fail.<br/><br/>**Add:** Optional<br/>**Update:** Read-only and Required|*long*|
|*ManagingCustomerNumber*|The number of the customer who manages or is requesting to manage the client account.<br /><br />When adding a client link, either the *ManagingCustomerId* or *ManagingCustomerNumber* is required, but specifying both will cause the operation to fail.<br/><br/>**Add:** Optional<br/>**Update:** Read-only and Required|*string*|
|*Name*|The friendly name that can be used to reference this client link.<br /><br />The name can contain a maximum of 40 characters.<br /><br />A default name will be provided if none is specified. The name does not need to be unique compared to other client links for the user.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|*string*|
|*Note*|Optional message from the requestor providing context and details about the client link invitation.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*string*|
|*StartDate*|The date when the status would update. For an accepted link request the status would transition towards Active on this date, and for an unlink request the status would transition towards Inactive on this date.<br /><br />If not specified, this value will be set to the current date and time.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|*dateTime*|
|*Status*|Determines the life cycle status of the client link, for example whether the client link has been accepted or declined.<br /><br />When adding a client link this element cannot be specified, and the service sets the effective status to LinkPending.<br/><br/>**Add:** Read-only<br/>**Update:** Required|[ClientLinkStatus Value Set](../customer-api/clientlinkstatus-value-set.md)|
|*SuppressNotification*|Determines whether or not to send email notification of the client link invitation to the primary user of the client account.<br /><br />If set to true the client will not receive an email and otherwise, since the default value is false, the client will receive an email notification.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|*boolean*|
|*TimeStamp*|The time-stamp value that the system uses internally to reconcile updates when you call the [UpdateClientLinks](../customer-api/updateclientlinks-service-operation.md) operation.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*base64Binary*|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[AddClientLinks](../customer-api/addclientlinks-service-operation.md)  
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)  
[UpdateClientLinks](../customer-api/updateclientlinks-service-operation.md)  

