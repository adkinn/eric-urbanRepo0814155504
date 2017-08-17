---
title: "Bulk Error Data Objects"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cfcee3a3-b33a-4928-b7c6-6876f2be5859
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Bulk Error Data Objects
[!INCLUDE[brand](../bulk-api/includes/brand.md)] bulk service operations may throw fault exceptions that include one or more error objects. The error objects contain the details of why the service operation failed.

## Fault Objects
The following fault objects may be thrown by the bulk service, and should be caught within your application.

|Fault Object|Description|
|----------------|---------------|
|[AdApiFaultDetail](../bulk-api/adapifaultdetail-data-object.md)|Defines a fault object that operations return when generic errors occur, such as an authentication error.|
|[ApiFaultDetail](../bulk-api/apifaultdetail-data-object.md)|Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.|
|[ApplicationFault](../bulk-api/applicationfault-data-object.md)|Defines the base object from which all fault detail objects derive.<br /><br />**Note:** Do not catch [ApplicationFault](../bulk-api/applicationfault-data-object.md), and instead catch one or more of the derived faults such as [AdApiFaultDetail](../bulk-api/adapifaultdetail-data-object.md).|

## Error Objects
The following error objects may be returned within bulk fault objects, and contain the details of why the service operation failed.

|Error Object|Description|
|----------------|---------------|
|[AdApiError](../bulk-api/adapierror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
|[BatchError](../bulk-api/batcherror-data-object.md)|Defines an error object that identifies the item within the batch of items in the request message that caused the operation to fail, and the reason for the failure.|
|[EditorialError](../bulk-api/editorialerror-data-object.md)|Defines an error object that identifies the entity with the batch of entities that failed editorial review.|
|[OperationError](../bulk-api/operationerror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
