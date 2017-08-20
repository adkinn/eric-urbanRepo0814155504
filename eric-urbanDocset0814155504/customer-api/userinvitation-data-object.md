---
title: "UserInvitation Data Object"
ms.custom: ""
ms.date: "04/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02f9841b-ebf2-4f5a-9a58-350b059afedf
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UserInvitation Data Object
Defines a user invitation. When the invitation is accepted, the user's Microsoft account is linked to the specified [!INCLUDE[brand](../customer-api/includes/brand.md)] customer accounts.

It is possible to have multiple pending invitations sent to the same email address, which have not yet expired. It is also possible for those invitations to have specified different user roles, for example if you sent an invitation with an incorrect user role and then sent a second invitation with the correct user role. The recipient can accept any of the invitations. The Bing Ads API does not support any operations to delete pending user invitations. After you invite a user, the only way to cancel the invitation is through the Bing Ads web application. You can find both pending and accepted invitations in the Users section of Accounts & Billing.

Since a recipient can accept the invitation and sign into Bing Ads with a Microsoft account different than the invitation email address, you cannot determine with certainty the mapping from *UserInvitation* to accepted [User](../customer-api/user-data-object.md). You can search by the invitation ID (returned by [SendUserInvitation](../customer-api/senduserinvitation-service-operation.md)), only to the extent of finding out whether or not the invitation has been accepted or has expired. The [SearchUserInvitations](../customer-api/searchuserinvitations-service-operation.md) operation returns all pending invitations, whether or not they have expired. Accepted invitations are not included in the [SearchUserInvitations](../customer-api/searchuserinvitations-service-operation.md) response.  

After the invitation has been accepted, you can call [GetUsersInfo](../customer-api/getusersinfo-service-operation.md) and [GetUser](../customer-api/getuser-service-operation.md) to access the Bing Ads user details. Once again though, since a recipient can accept the invitation and sign into Bing Ads with a Microsoft account different than the invitation email address, you cannot determine with certainty the mapping from *UserInvitation* to accepted [User](../customer-api/user-data-object.md). With the user ID returned by [GetUsersInfo](../customer-api/getusersinfo-service-operation.md) or [GetUser](../customer-api/getuser-service-operation.md), you can call [DeleteUser](../customer-api/deleteuser-service-operation.md) to remove the user.

For more information about user authentication, see [Authentication with OAuth](https://msdn.microsoft.com/library/bing-ads-user-authentication-oauth-guide.aspx).


## Syntax

```xml
<xs:complexType name="UserInvitation">
  <xs:sequence>
    <xs:element minOccurs="0" name="Id" type="xs:long" />
    <xs:element minOccurs="0" name="FirstName" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="LastName" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="Email" nillable="true" type="xs:string" />
    <xs:element minOccurs="0" name="CustomerId" type="xs:long" />
    <xs:element minOccurs="0" name="Role" nillable="true" type="tns:UserRole" />
    <xs:element minOccurs="0" name="AccountIds" nillable="true" type="q5:ArrayOflong" xmlns:q5="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
    <xs:element minOccurs="0" name="ExpirationDate" type="xs:dateTime" />
    <xs:element minOccurs="0" name="Lcid" type="tns:LCID" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountIds*|An array of identifiers of the accounts that the user can manage. To specify that the user can manage all current and future accounts of the customer to which the user belongs, set to NULL.<br /><br />Users with account level roles such as Advertiser Campaign Manager can be restricted to specific accounts. Users with customer level roles such as Super Admin can access all accounts within the user’s customer, and their access cannot be restricted to specific accounts.<br /><br />**Note:** When attempting to restrict customer level user roles, for example attempting to restrict a Super Admin to specific accounts, the operation will not fail and the user will be granted access for all accounts within the specified customer.<br/><br/>**Send:** Optional|*long* array|
|*CustomerId*|The identifier of the customer this user is invited to manage. The *AccountIds* element determines which customer accounts the user can manage.<br/><br/>**Send:** Required|*long*|
|*Email*|The email address corresponding to the user's Microsoft account. The address can contain a maximum of 100 characters.<br/><br/>**Send:** Required|*string*|
|*ExpirationDate*|The date and time that the user invitation will expire. The value is in Coordinated Universal Time (UTC).<br /><br />**Note:** The duration of a user invitation is subject to change, and currently set at 30 days. You cannot set or update this value.<br/><br/>**Send:** Read-only|*dateTime*|
|*FirstName*|The first name of the user. The first name is limited to 40 characters.<br/><br/>**Send:** Required|*string*|
|*Id*|A system generated unique identifier for the user invitation.<br/><br/>**Send:** Read-only|*long*|
|*LastName*|The last name of the user. The last name is limited to 40 characters.<br/><br/>**Send:** Required|*string*|
|*Lcid*|The locale to use when sending correspondence to the user by email or postal mail. The default is EnglishUS.<br/><br/>**Send:** Required|[LCID](../customer-api/lcid-value-set.md)|
|*Role*|The user role, which determines the level of access that the user has to the accounts specified in the AccountIds element.<br/><br/>**Send:** Required|[UserRole](../customer-api/userrole-value-set.md)|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[SearchUserInvitations](../customer-api/searchuserinvitations-service-operation.md)  
[SendUserInvitation](../customer-api/senduserinvitation-service-operation.md)  

