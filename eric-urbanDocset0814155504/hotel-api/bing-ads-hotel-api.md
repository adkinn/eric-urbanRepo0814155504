---
title: "Bing Ads Hotel API"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b56e3c9-1ad4-475f-b3dd-f2dfc1a2890d
caps.latest.revision: 9
author: "eric-urban"
ms.author: "scottwhi"
---
# Bing Ads Hotel API
> [!NOTE]
> Hotel Ads is now under pilot and available to pilot participants only. Please contact your account manager for details.
>
> The Hotel Ads components and documentation are subject to change.

Hotel Ads enables advertisers to showcase their hotels on Bing.com across devices. Travelers can see hotel ads when they are actively looking to book a hotel.

To use Hotel Ads, you need to work with your account manager to import your hotel and points of sale data. For details about creating your hotel and points of sale feed files, see [Hotel Feed](../hotel-api/hotel-feed.md) and [Points of Sale Feed](../hotel-api/points-of-sale-feed.md). 

The hotel feed is an XML document that describes the hotels that you want to advertise. The feed provides the hotel's name, address, telephone number, and geographical coordinates. The points of sale feed is an XML document that describes the sites that users use to book rooms. The feed provides a point of sale (POS) for each booking site you support. A POS describes the POS's display name, URL, and criteria for matching the user to a POS. 

After importing your hotel and points of sale feeds into Bing, you need to send Bing your pricing and availability data for your hotel properties. For details about sending this information, see [Transaction Message](../hotel-api/transaction-message.md).

Lastly, you need to specify create hotel ad campaigns and specifying bids for your hotel ads. For information, see [Travel API](../hotel-api/travel-api.md).