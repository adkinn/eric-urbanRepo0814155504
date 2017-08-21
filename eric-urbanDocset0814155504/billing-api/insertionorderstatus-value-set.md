---
title: "InsertionOrderStatus Value Set"
ms.custom: ""
ms.date: "06/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b29b792f-3398-4b33-905a-c05240da6592
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# InsertionOrderStatus Value Set
Defines the possible status values of an [InsertionOrder](../billing-api/insertionorder-data-object.md).

## Syntax

```xml
<xs:simpleType name="InsertionOrderStatus">
  <xs:restriction base="xs:string">
    <xs:enumeration value="Active" />
    <xs:enumeration value="Exhausted" />
    <xs:enumeration value="Expired" />
    <xs:enumeration value="Pending" />
    <xs:enumeration value="PendingSystemReview" />
    <xs:enumeration value="PendingUserReview" />
    <xs:enumeration value="Declined" />
    <xs:enumeration value="Canceled" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|You have an approved insertion order, and your ads are eligible to run.|
|Canceled|You have canceled an order that you created or that was created by Bing Ads. A canceled order cannot be reactivated. |
|Declined|You have declined an order created by Bing Ads, or the order you created has been declined. Submit a new order, contact your Bing Ads account manager, or [contact support](http://go.microsoft.com/fwlink?LinkId=398371).|
|Exhausted|Your balance has been depleted and the order is no longer active.<br/><br/>**Note**: This status is read-only and only the system can set the status to Exhausted.|
|Expired|Your order has reached its end date and is no longer valid.<br/><br/>**Note**: This status is read-only and only the system can set the status to Expired.|
|Pending|You have an approved order that has not reached its start date yet.<br/><br/>**Note**: This status is read-only and only the system can set the status to Pending.|
|PendingSystemReview|This value is deprecated.<br/><br/>**Note**: Previously this read-only status indicated that you created a new order and submitted it for approval. The process used to take up to 48 hours. Beginning in calendar Q2 2017, insertion orders that you create are immediately set to Active, Pending, or Declined.|
|PendingUserReview|You need to approve or decline an order that Bing Ads created for your account.<br/><br/>**Note**: This status is read-only and only the system can set the status to PendingUserReview.|

## Requirements
[!INCLUDE[reqbilling](../billing-api/includes/reqbilling.md)]
## See Also
[InsertionOrder](../billing-api/insertionorder-data-object.md)

