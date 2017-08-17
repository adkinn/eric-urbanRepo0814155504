---
title: "Reporting Error Data Objects"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19cc8a4f-b974-44dd-a498-51cee175f547
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Reporting Error Data Objects
[!INCLUDE[brand](../reporting-api/includes/brand.md)] reporting service operations may throw fault exceptions that include one or more error objects. The error objects contain the details of why the service operation failed.

## Fault Objects
The following fault objects may be thrown by the reporting service, and should be caught within your application.

|Fault Object|Description|
|----------------|---------------|
|[AdApiFaultDetail](../reporting-api/adapifaultdetail-data-object.md)|Defines a fault object that operations return when generic errors occur, such as an authentication error.|
|[ApiFaultDetail](../reporting-api/apifaultdetail-data-object.md)|Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.|
|[ApplicationFault](../reporting-api/applicationfault-data-object.md)|Defines the base object from which all fault detail objects derive.<br /><br />**Note**: Do not catch *ApplicationFault*, and instead catch one or more of the derived faults such as *AdApiFaultDetail*.|

## Error Objects
The following error objects may be returned within reporting fault objects, and contain the details of why the service operation failed.

|Error Object|Description|
|----------------|---------------|
|[AdApiError](../reporting-api/adapierror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
|[BatchError](../reporting-api/batcherror-data-object.md)|Defines an error object that identifies the item within the batch of items in the request message that caused the operation to fail, and the reason for the failure.|
|[OperationError](../reporting-api/operationerror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|

## See Also
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)

