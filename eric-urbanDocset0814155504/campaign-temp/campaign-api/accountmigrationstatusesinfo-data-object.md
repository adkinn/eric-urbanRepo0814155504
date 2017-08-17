---
title: "AccountMigrationStatusesInfo Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49f4e8b4-e270-4a3d-bf94-23f9a681d87e
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AccountMigrationStatusesInfo Data Object
Defines an object that contains migration status for an account.

## Syntax

```xml
\<xs:complexType name="AccountMigrationStatusesInfo">
  \<xs:sequence>
    \<xs:element name="AccountId" type="xs:long"/>
    \<xs:element minOccurs="0" name="MigrationStatusInfo" nillable="true" type="tns:ArrayOfMigrationStatusInfo"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The Bing Ads identifier of the account.|*long*|
|*MigrationStatusInfo*|The list of migration status info for the corresponding account.|[MigrationStatusInfo](../campaign-api/migrationstatusinfo-data-object.md) array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetAccountMigrationStatuses](../campaign-api/getaccountmigrationstatuses-service-operation.md)

