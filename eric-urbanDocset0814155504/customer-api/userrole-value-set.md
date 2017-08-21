---
title: "UserRole Value Set"
ms.custom: ""
ms.date: "04/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 187736e8-bfa0-44c7-80b4-f5a09b22d492
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UserRole Value Set
Defines the possible roles of a user.

## Syntax

```xml
<xs:simpleType name="UserRole">
  <xs:restriction base="xs:string">
    <xs:enumeration value="AdvertiserCampaignManager" />
    <xs:enumeration value="SuperAdmin" />
    <xs:enumeration value="ClientViewer" />
    <xs:enumeration value="ClientManager" />
    <xs:enumeration value="PublisherAdmin" />
    <xs:enumeration value="PublisherAccountManager" />
    <xs:enumeration value="PublisherReportUser" />
    <xs:enumeration value="PublisherListManager" />
    <xs:enumeration value="PublisherAdViewer" />
    <xs:enumeration value="ClientAdmin" />
    <xs:enumeration value="Standard" />
  </xs:restriction>
</xs:simpleType>
```

## Values
You can specify the string values with the [SendUserInvitation](../customer-api/senduserinvitation-service-operation.md) service operation. The integer value can be specified within the [UpdateUserRoles](../customer-api/updateuserroles-service-operation.md) service operation, and is returned when calling [GetUser](../customer-api/getuser-service-operation.md).

> [!NOTE]
> The value set defines additional user roles which are internal only. The following user roles are supported.

|Value|Description|Integer Value|Level|
|---------|---------------|-----------------|---------|
|AdvertiserCampaignManager|This role has permissions to view selected accounts and add, edit, or delete campaigns within the selected accounts. The Advertiser Campaign Manager can view payment methods, but cannot manage any billing and payment tasks.|16|Account|
|StandardUser|This role has permissions to manage campaigns and perform some billing activities on specific accounts. This role cannot add, edit, or delete payment methods or other users; create or delete accounts; or link to or unlink from clients.|203|Account|
|SuperAdmin|This role has full permissions for all accounts. A Super Admin can manage everything related to billing and payments, account details, and other users (including other Super Admins). The Super Admin can specify which accounts other users have access to. When signing up as a new customer, the first user is the Super Admin.|41|Customer|
|Viewer|This role has read-only permissions. Write operations are not allowed.|100|Account|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[UserInvitation](../customer-api/userinvitation-data-object.md)

