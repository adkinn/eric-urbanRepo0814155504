---
title: "Can I Use the API and FTP?"
ms.custom: ""
ms.date: "03/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 75940754-4dc8-4e42-a7ac-9f1fcf57265d
caps.latest.revision: 5
author: "eric-urban"
ms.author: "scottwhi"
---
# Can I Use the API and FTP?
Yes, in the following, very limited cases you may use the API and FTP together without conflicts occurring.

- You use FTP and the API to update different catalogs. For example, you use the API to update catalog A and FTP to update catalog B. 

- You use the API to only get products or determine the status of a product. For example, if you use FTP to update catalog A, you may use the API only to get products from catalog A.


You are strongly discouraged from updating the same catalog using FTP and the API. If you use FTP and the API to update the same catalog, you must wait until the FTP process completes before using the API to update the catalog. The FTP process can take several hours to complete. To determine whether the FTP process is complete, you'd use the verification report in the UI; there is no programmatic way to determine whether it's complete. 

If you don't wait for the FTP update to complete before using the API to update the catalog, the FTP and API updates may overwrite one another, and it's undetermined which will win. 

The only exception to using FTP and the API to update the same catalog at the same time is if you use the API to update only the `price`, `salePrice`, and `salePriceEffectiveDate` fields of the catalog. For example, if you use FTP to update products in catalog A, you may use the API to update only the price fields of products in catalog A without worry about whether the FTP update is complete.
