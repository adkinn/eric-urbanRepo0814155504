---
title: "OAuth C# Example"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb73f222-90e2-4b45-a334-0c67ffa06719
caps.latest.revision: 2
author: "eric-urban"
ms.author: "scottwhi"
---
# OAuth C# Example
The following topics break out a simple desktop implementation used to get an access and refresh token. The example does not support the recommended state query parameter.

If you use the Bing Ads C# SDK, you should use it to get your OAuth access and refresh tokens. For information, see [Getting Started](../hotel-api/getting-started.md).

|Module|Description
|-|-
|[CodeGrantFlow](../hotel-api/codegrantflow-csharp-example.md)|A browser control that gets the user's credentials, requests permissions for your application to access their resources, and returns the access and refresh tokens.
|[Call CodeGrantFlow](../hotel-api/call-codegrantflow-in-csharp-example.md)|A test app that shows how to call the CodeGrantFlow DLL to get an access and refresh token.