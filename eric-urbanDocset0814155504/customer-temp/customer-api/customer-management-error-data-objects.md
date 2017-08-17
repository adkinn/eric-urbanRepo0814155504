---
title: "Customer Management Error Data Objects"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94ad73a8-9060-4b0a-afa8-78cd114092cc
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Customer Management Error Data Objects
[!INCLUDE[brand](../customer-api/includes/brand.md)] customer management service operations may throw fault exceptions that include one or more error objects. The error objects contain the details of why the service operation failed. For more information, see [Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx).

## Fault Objects
The following fault objects may be thrown by the customer management service, and should be caught within your application.

|Fault Object|Description|
|----------------|---------------|
|[AdApiFaultDetail](../customer-api/adapifaultdetail-data-object.md)|Defines a fault object that operations return when generic errors occur, such as an authentication error.|
|[ApiFault](../customer-api/apifault-data-object.md)|Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.|
|[ApplicationFault](../customer-api/applicationfault-data-object.md)|Defines the base object from which all fault detail objects derive.<br /><br />**Note:** Do not catch *ApplicationFault*, and instead catch one or more of the derived faults such as *AdApiFaultDetail*.|

## Error Objects
The following error objects may be returned within customer management fault objects, and contain the details of why the service operation failed.

|Error Object|Description|
|----------------|---------------|
|[AdApiError](../customer-api/adapierror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
|[OperationError](../customer-api/operationerror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
