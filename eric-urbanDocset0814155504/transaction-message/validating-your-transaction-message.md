---
title: "Validating your Transaction Message"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3921428d-d5bd-495d-830e-f82280d6bfa9
caps.latest.revision: 4
author: "eric-urban"
ms.author: "scottwhi"
---
# Validating your Transaction Message
Bing provides the [Transaction XSD](https://bhacstatic.blob.core.windows.net/schemas/transaction.xsd) that you use to validate your transaction message before sending it to Bing. This saves time and round trips by catching document syntax errors. You should always validate your transaction messages before sending them to Bing.

The following example shows using xmllint to validate the message contained in SampleTransaction.xml.

```
xmllint.exe --schema transaction.xsd SampleTransaction.xml
```
