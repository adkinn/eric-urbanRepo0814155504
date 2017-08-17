---
title: "Customer Billing Service Operations"
ms.custom: ""
ms.date: "05/27/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59bef3fc-dbac-43f0-8600-73394b61d3a8
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Customer Billing Service Operations
The Customer Billing Service defines the following service operations.

> [!NOTE]
> Operations reserved for internal use are not documented.

|Service Operation|Description|Request Limits|
|---------------------|---------------|------------------|
|[AddInsertionOrder](../billing-api/addinsertionorder-service-operation.md)|Adds an insertion order to the specified account.|1 *AccountId*<br /><br />1 *InsertionOrder*|
|[GetAccountMonthlySpend](../billing-api/getaccountmonthlyspend-service-operation.md)|Gets the amount spent by the account in the specified month.<br /><br />**Note**: This operation will return a value of 0 for accounts that are not Yahoo!-managed.|1 *AccountId*|
|[GetBillingDocuments](../billing-api/getbillingdocuments-service-operation.md)|Gets the specified billing documents.<br /><br />**Note**: This operation will not return billing documents associated with Yahoo!-managed accounts.|Not applicable.|
|[GetBillingDocumentsInfo](../billing-api/getbillingdocumentsinfo-service-operation.md)|Gets a list of objects that contains billing document identification information, for example, the billing document identifier, billing document amount, and account identifier.<br /><br />**Note**: This operation will not return billing documents associated with Yahoo!-managed accounts.|Not applicable.|
|[GetInsertionOrdersByAccount](../billing-api/getinsertionordersbyaccount-service-operation.md)|Gets a list of insertion orders for the specified account.<br /><br />**Note**: This operation is deprecated and will be removed in a future API version. To get insertion orders, you should use [SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md).|1 *AccountId*|
|[SearchInsertionOrders](../billing-api/searchinsertionorders-service-operation.md)|Searches for insertion orders that match a specified criteria.|6 *Predicates*|
|[UpdateInsertionOrder](../billing-api/updateinsertionorder-service-operation.md)|Updates an insertion order within the specified account.|1 *AccountId*<br /><br />1 *InsertionOrder*|
