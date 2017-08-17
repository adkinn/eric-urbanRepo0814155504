---
title: "Format Version"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ead8e12f-6953-484e-9fec-05e821cacab5
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Format Version
Defines the format version of records in a bulk file.

## <a name="entitydata"></a>Attribute Fields in the Bulk File
For the *Format Version* record, the following attribute fields are available in the [Bulk File Schema](../bulk-api/bulk-file-schema.md). 

- [Name](#name)

The *Format Version* record is included in the Bulk download file automatically everytime you call the [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) or [DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md) service request. 

### <a name="name"></a>Name
This string represents the format version used for bulk download and upload. The format version differs from the Bing Ads API version. Currently for version 11 of the Bing Ads Bulk API, the only supported format version  is *5.0*. For more information, see [Format Versions](../bulk-api/bulk-file-schema.md#formatversions).

**Add:** Read-only  
**Update:** Read-only  
**Delete:** Read-only  
