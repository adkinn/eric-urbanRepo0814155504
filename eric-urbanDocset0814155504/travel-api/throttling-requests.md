---
title: "Throttling Requests"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8fcb337-6c9f-43a8-805e-1b19cb7f72b1
caps.latest.revision: 2
author: "eric-urban"
ms.author: "scottwhi"
---
# Throttling Requests
To ensure resources for everyone, the API limits the number of requests a customer ID may make per minute. The limit is not documented and is subject to change.

If you exceed the request per minute limit, the API returns HTTP status code 429. When you receive status code 429, you must wait 60 seconds before resubmitting the request.

Ensure your application contains the logic necessary to recover from status code 429.