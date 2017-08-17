---
title: "Ad Insight Error Data Objects"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cec88ab-6cc6-444d-a96d-c9672ffe1626
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Insight Error Data Objects
[!INCLUDE[brand](../Ad Insight Version 11/includes/brand.md)] Ad Insight service operations may throw fault exceptions that include one or more error objects. The error objects contain the details of why the service operation failed.

## Fault Objects
The following fault objects may be thrown by the Ad Insight service, and should be caught within your application.

|Fault Object|Description|
|----------------|---------------|
|[AdApiFaultDetail](../Ad Insight Version 11/adapifaultdetail-data-object.md)|Defines a fault object that operations return when generic errors occur, such as an authentication error.|
|[ApiFaultDetail](../Ad Insight Version 11/apifaultdetail-data-object.md)|Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.|
|[ApplicationFault](../Ad Insight Version 11/applicationfault-data-object.md)|Defines the base object from which all fault detail objects derive.<br /><br />**Note:** Do not catch [ApplicationFault](../Ad Insight Version 11/applicationfault-data-object.md), and instead catch one or more of the derived faults such as [AdApiFaultDetail](../Ad Insight Version 11/adapifaultdetail-data-object.md).|

## Error Objects
The following error objects may be returned within Ad Insight fault objects, and contain the details of why the service operation failed.

|Error Object|Description|
|----------------|---------------|
|[AdApiError](../Ad Insight Version 11/adapierror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
|[BatchError](../Ad Insight Version 11/batcherror-data-object.md)|Defines an error object that identifies the item within the batch of items in the request message that caused the operation to fail, and the reason for the failure.|
|[OperationError](../Ad Insight Version 11/operationerror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|

## See Also
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)

