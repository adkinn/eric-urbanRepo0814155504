---
title: "Customer Billing Error Data Objects"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 307617c4-389e-4ac0-96e5-48f034ca600d
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Customer Billing Error Data Objects
[!INCLUDE[brand](../billing-api/includes/brand.md)] billing service operations may throw fault exceptions that include one or more error objects. The error objects contain the details of why the service operation failed.

## Fault Objects
The following fault objects may be thrown by the billing service, and should be caught within your application.

|Fault Object|Description|
|----------------|---------------|
|[AdApiFaultDetail](../billing-api/adapifaultdetail-data-object.md)|Defines a fault object that operations return when generic errors occur, such as an authentication error.|
|[ApiBatchFault](../billing-api/apibatchfault-data-object.md)|Defines a fault object that operations return when billing batch errors occur.|
|[ApiFault](../billing-api/apifault-data-object.md)|Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.|
|[ApplicationFault](../billing-api/applicationfault-data-object.md)|Defines the base object from which all fault detail objects derive.<br /><br />**Note**: Do not catch *ApplicationFault*, and instead catch one or more of the derived faults such as *AdApiFaultDetail*.|

## Error Objects
The following error objects may be returned within billing fault objects, and contain the details of why the service operation failed.

|Error Object|Description|
|----------------|---------------|
|[AdApiError](../billing-api/adapierror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
|[BatchError](../billing-api/batcherror-data-object.md)|Defines an error object that identifies the item within the batch of items in the request message that caused the operation to fail, and the reason for the failure.|
|[OperationError](../billing-api/operationerror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|

## See Also
[Handling Service Errors and Exceptions](~/concepts/handling-service-errors-and-exceptions.md)

