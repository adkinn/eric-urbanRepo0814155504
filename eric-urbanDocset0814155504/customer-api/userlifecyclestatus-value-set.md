---
title: "UserLifeCycleStatus Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a80dd9c6-4a0c-4c90-99cd-e7daf5ff9d53
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UserLifeCycleStatus Value Set
Defines the possible status values of a user.

## Syntax

```xml
\<xs:simpleType name="UserStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Pending" />
    \<xs:enumeration value="Active" />
    \<xs:enumeration value="Inactive" />
    \<xs:enumeration value="Deleted" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The user is active.|
|Deleted|Reserved for internal use. The user was deleted.|
|Inactive|Reserved for internal use. The user was disabled by the system.|
|Pending|The user is a new user who has not been activated. The user is sent notification about how to activate the account. After the user activates the account, the status changes to Active.<br/><br/>**Note:** This status is deprecated and is only applicable for managed user credentials, and not for Microsoft account (MSA) users. |

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]