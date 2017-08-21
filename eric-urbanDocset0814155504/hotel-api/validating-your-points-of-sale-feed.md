---
title: "Validating your Points of Sale Feed"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25c9fa33-b9e0-4cb7-b1db-6b378d4712ea
caps.latest.revision: 3
author: "eric-urban"
ms.author: "scottwhi"
---
# Validating your Points of Sale Feed
Bing provides the [PointsOfSale XSD](https://bhacstatic.blob.core.windows.net/schemas/point_of_sale.xsd) that you use to validate your points of sale feed before sending it to Bing. This saves time and round trips by catching document syntax errors. You should always validate your feed file before sending it to Bing.

The following example shows using xmllint to validate the SamplePointsOfSale.xml feed file.

```
xmllint.exe --schema point_of_sale.xsd SamplePointsOfSale.xml
```
