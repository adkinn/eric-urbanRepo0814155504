---
title: "MigrationStatusInfo Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 756c62df-2e83-4d31-842b-5dd33fa0e962
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# MigrationStatusInfo Data Object
Defines an object that contains the migration type and status for an account.

## Syntax

```xml
<xs:complexType name="MigrationStatusInfo">
  <xs:sequence>
    <xs:element name="MigrationType" nillable="true" type="xs:string"/>
    <xs:element minOccurs="0" name="StartTimeInUtc" nillable="true" type="xs:dateTime"/>
    <xs:element name="Status" type="tns:MigrationStatus"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MigrationType*|The migration type.|*string*|
|*StartTimeInUtc*|The date and time when the migration began. The value is in Coordinated Universal Time (UTC).<br/><br/>**Note:** The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](https://msdn.microsoft.com/library/ms256220.aspx).|*dateTime*|
|*Status*|The migration status.|[MigrationStatus](../campaign-api/migrationstatus-value-set.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetAccountMigrationStatuses](../campaign-api/getaccountmigrationstatuses-service-operation.md)  
[AccountMigrationStatusesInfo](../campaign-api/accountmigrationstatusesinfo-data-object.md)  
