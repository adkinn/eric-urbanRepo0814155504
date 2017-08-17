---
title: "Campaign Management Error Data Objects"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c47d3439-76f1-428d-8c3d-e922f12b0998
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Campaign Management Error Data Objects
[!INCLUDE[brand](../campaign-api/includes/brand.md)] campaign management service operations may throw fault exceptions that include one or more error objects. The error objects contain the details of why the service operation failed.

## Fault Objects
The following fault objects may be thrown by the campaign management service, and should be caught within your application.

|Fault Object|Description|
|----------------|---------------|
|[AdApiFaultDetail](../campaign-api/adapifaultdetail-data-object.md)|Defines a fault object that operations return when generic errors occur, such as an authentication error.|
|[ApiFaultDetail](../campaign-api/apifaultdetail-data-object.md)|Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.|
|[ApplicationFault](../campaign-api/applicationfault-data-object.md)|Defines the base object from which all fault detail objects derive.<br /><br />**Note:** Do not catch [ApplicationFault](../campaign-api/applicationfault-data-object.md), and instead catch one or more of the derived faults such as [AdApiFaultDetail](../campaign-api/adapifaultdetail-data-object.md).|
|[EditorialApiFaultDetail](../campaign-api/editorialapifaultdetail-data-object.md)|Defines a fault object that operations return when one or more entity elements in your request message fail editorial review.|

## Error Objects
The following error objects may be returned within campaign management fault objects, and contain the details of why the service operation failed.

|Error Object|Description|
|----------------|---------------|
|[AdApiError](../campaign-api/adapierror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
|[BatchError](../campaign-api/batcherror-data-object.md)|Defines an error object that identifies the item within the batch of items in the request message that caused the operation to fail, and the reason for the failure.<br /><br />**Note:** May also be returned in the `PartialErrors` element of some operation responses, for example [AddKeywords](../campaign-api/addkeywords-service-operation.md).|
|[BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md)|Defines an error object that contains batch error details for the top level list index and a list of batch errors corresponding to the  nested list index.<br /><br />**Note:** May be returned in the `NestedPartialErrors` element of some operation responses, for example [AddNegativeKeywordsToEntities](../campaign-api/addnegativekeywordstoentities-service-operation.md).|
|[EditorialError](../campaign-api/editorialerror-data-object.md)|Defines an error object that identifies the entity element that failed editorial review.|
|[OperationError](../campaign-api/operationerror-data-object.md)|Defines an error object that contains the details of why the service operation failed.|
