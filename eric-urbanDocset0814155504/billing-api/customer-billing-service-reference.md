---
title: "Customer Billing Service Reference"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe095f08-c490-44b2-8019-c6dabb5c469a
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Customer Billing Service Reference
The Customer Billing [service](~/concepts/bing-ads-web-service-addresses.md) defines the following Application Programming Interface (API) that you can use to get billing documents, insertion orders, and monthly spend for an account.

|Interface|Description|
|---------|---------|
|[Customer Billing Service Operations](../billing-api/customer-billing-service-operations.md)|Service operations include [GetAccountMonthlySpend](../billing-api/getaccountmonthlyspend-service-operation.md) and [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md).|
|[Customer Billing Data Objects](../billing-api/customer-billing-data-objects.md)|To add, get, and update an insertion order, use the [InsertionOrder](../billing-api/insertionorder-data-object.md) object.|
|[Customer Billing Error Data Objects](../billing-api/customer-billing-error-data-objects.md)|Be sure to [handle](~/concepts/handling-service-errors-and-exceptions.md) errors, for example [OperationError](../billing-api/operationerror-data-object.md) would be returned if the user credentials cannot be authenticated.|
|[Customer Billing Value Sets](../billing-api/customer-billing-value-sets.md)|Value sets include [InsertionOrderStatus](../billing-api/insertionorderstatus-value-set.md) and more.|

## See Also
[Getting Started With the Bing Ads API](~/concepts/getting-started-with-the-https://msdn.microsoft.com/library/bing-ads-api.md)  
[Bing Ads Technical Guides](~/concepts/bing-ads-technical-guides.md)  
[Bing Ads Web Service Addresses](~/concepts/bing-ads-web-service-addresses.md)  
[Bing Ads API Error Codes](~/concepts/bing-ads-operation-error-codes.md)  
