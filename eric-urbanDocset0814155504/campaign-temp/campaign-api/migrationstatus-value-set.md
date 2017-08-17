---
title: "MigrationStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6881b58-9d2a-465c-b68d-4f9ca9b43d53
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MigrationStatus Value Set
Defines the possible migration status values.

## Syntax

```xml
\<xs:simpleType name="MigrationStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="NotInPilot" />
    \<xs:enumeration value="NotStarted" />
    \<xs:enumeration value="InProgress" />
    \<xs:enumeration value="Completed" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Completed|The migration is complete, or migration is not needed because the account was created after all of the customer's other accounts were added to the pilot queue for the corresponding migration type.|
|InProgress|The migration is in progress.|
|NotInPilot|None of the accounts for the customer are in the queue for the corresponding migration type. All of a customer's accounts are added to pilot at the same time. A customer cannot have a subset of their accounts in pilot.|
|NotStarted|The account is in the queue for the corresponding migration type, but the migration has not yet begun.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[GetAccountMigrationStatuses](../campaign-api/getaccountmigrationstatuses-service-operation.md)  
[AccountMigrationStatusesInfo](../campaign-api/accountmigrationstatusesinfo-data-object.md)  
[MigrationStatusInfo](../campaign-api/migrationstatusinfo-data-object.md)  
