---
title: "PaymentMethodType Value Set"
ms.custom: ""
ms.date: "07/20/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 493f3a76-4a67-4cbc-8ac6-d2b0240a2afc
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# PaymentMethodType Value Set
Defines possible payment methods for a [!INCLUDE[brand](../customer-api/includes/brand.md)] account.

> [!NOTE]
> Reserved for internal use.

## Syntax

```xml
\<xs:simpleType name="PaymentMethodType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="CreditCard" />
    \<xs:enumeration value="Invoice" />
    \<xs:enumeration value="Check" />
    \<xs:enumeration value="ElectronicFundsTransfer" />
    \<xs:enumeration value="PayPal" />
    \<xs:enumeration value="ELV" />
    \<xs:enumeration value="OfflinePaymentMethod" />
    \<xs:enumeration value="VBA" />
    \<xs:enumeration value="Boleto" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Boleto|Boleto is a form of payment used widely in Brazil. [!INCLUDE[brand](../customer-api/includes/brand.md)] allows customers to use Boleto to fund their prepay accounts by giving them the ability to print a payment slip that they can use to make payment at various locations in Brazil (e.g. Post offices and banks). This payment method is only supported in Brazil and activity must be billed in BRL currency.|
|Check|The payments are made with a check.|
|CreditCard|The payments are made with a credit card.<br /><br />If you use a credit card, the card is charged when the account balance (the amount of accrued advertising charges) reaches an internally defined threshold.|
|ElectronicFundsTransfer|The payments are made with an electronic funds transfer.|
|ELV|The ELV value represents the SEPA payment method. SEPA is a form of a direct debit in Europe. With SEPA [!INCLUDE[brand](../customer-api/includes/brand.md)] validates a customer’s bank account by making a small deposit that needs to be verified in [!INCLUDE[brand](../customer-api/includes/brand.md)]. This process takes some time but helps ensure the security of a customer’s SEPA account. SEPA is currently only supported in Germany and activity must be billed in EUR currency. SEPA is only allowed to be used to fund prepay accounts.|
|Invoice|An invoice is sent to the customer requesting payment.<br /><br />If you use the invoice method, the customer specified in the `BillToCustomerId` element of the [AdvertiserAccount](../customer-api/advertiseraccount-data-object.md) is invoiced at the end of the each month.|
|OfflinePaymentMethod|Meant to signal when a customer is funding a prepay account by making payment via a check or a bank transfer. When using such a payment method customers must include their [!INCLUDE[brand](../customer-api/includes/brand.md)] account number for us to process the payment.|
|PayPal|A payment service that allows customers to pay for their [!INCLUDE[brand](../customer-api/includes/brand.md)] transactions online. A verified PayPal account is needed, meaning that it needs a valid payment method backing it up for it to be used within [!INCLUDE[brand](../customer-api/includes/brand.md)].|
|VBA|Virtual Bank Account is a form of payment used widely in Taiwan. [!INCLUDE[brand](../customer-api/includes/brand.md)] allows customers to use VBA to fund their prepay accounts by giving them the ability to print a payment slip that they can use to make payment at various locations in Taiwan (e.g. Post offices and banks). This payment method is only supported in Taiwan and activity must be billed in TWD currency.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]