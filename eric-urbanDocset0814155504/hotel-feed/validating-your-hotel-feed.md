---
title: "Validating your Hotel Feed"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d5d7c49-834b-4b27-be5b-4dcee71dbf24
caps.latest.revision: 2
author: "eric-urban"
ms.author: "scottwhi"
---
# Validating your Hotel Feed
Bing provides the [Hotel XSD](https://bhacstatic.blob.core.windows.net/schemas/hotel.xsd) that you use to validate your hotels feed before sending it to Bing. This saves time and round trips by catching document syntax errors. You should always validate your feed file before sending it to Bing.

The following example shows using xmllint to validate the SampleHotelsFeed.xml feed file.

```
xmllint.exe --schema hotel.xsd SampleHotelsFeed.xml
```
