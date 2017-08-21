---
title: "Differences Between Google&#39;s and Bing&#39;s Transaction Message Usage"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 386821c5-2c20-4675-b5b5-823ca2f213a1
caps.latest.revision: 4
author: "eric-urban"
ms.author: "scottwhi"
---
# Differences Between Google&#39;s and Bing&#39;s Transaction Message Usage
The following are the differences between Google's Transaction Message implementation and Bing's.

- Bing supports the push model only. Bing does not support the pull model where your server is sent a request for transaction messages. Instead, you must send Bing a transaction message any time your rates and availability change.
  
- Bing does not support (and will ignore) the following `Transaction` elements:  
  
  - `PartnerData`
  - `PackageDataSet`
  
- Bing does not support (and will ignore) the following `Transaction` attributes:  
  
  - `id`
  - `partner`
  
- Bing does not support (and will ignore) the following `Result` elements:
  
  - `ExpirationTime`
  - `RoomID`
  - `Rates`
  - `RoomBundle`
  
- Bing does not support (and will ignore) the `all_inclusive` attribute of the `Baserate` element (see `Result`).
