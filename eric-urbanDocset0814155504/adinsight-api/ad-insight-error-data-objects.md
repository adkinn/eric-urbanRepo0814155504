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
[!INCLUDE[brand](../adinsight-api/includes/brand.md)] Ad Insight service operations may throw fault exceptions that include one or more error objects. The error objects contain the details of why the service operation failed.

## Fault Objects
The following fault objects may be thrown by the Ad Insight service, and should be caught within your application.

|Fault Object|Description|
|----------------|---------------|
|[AdApiFaultDetail](../adinsight-api/adapifaultdetail-data-object.md)|Defines a fault object that operations return when generic errors occur, such as an authentication error.|
|[ApiFaultDetail](../adinsight-api/apifaultdetail-data-object.md)|Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.|
|[ApplicationFault](../adinsight-api/applicationfault-data-object.md)|Defines the base object from which all fault detail objects derive.<br /><br />**Note:** Do not catch [ApplicationFault](../adinsight-api/applicationfault-data-object.md), and instead catch one or more of the derived faults such as [AdApiFaultDetail](../adinsight-api/adapifaultdetail-data-object.md).|

## Error Objects
The following error objects may be returned within Ad Insight fault objects, and contain the details of why the service operation failed.

|Error Object|Description|
|----------------|---------------|
|[AdApiError](../adinsight-api/adapierror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
|[BatchError](../adinsight-api/batcherror-data-object.md)|Defines an error object that identifies the item within the batch of items in the request message that caused the operation to fail, and the reason for the failure.|
|[OperationError](../adinsight-api/operationerror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|

## See Also
[Handling Service Errors and Exceptions](~/concepts/handling-service-errors-and-exceptions.md)

