---
title: "Bulk Service Reference"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 893b4696-c081-473c-b726-08f9ccce4cf7
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Bulk Service Reference
The Bulk [service](https://msdn.microsoft.com/library/bing-ads-overview-web-service-addresses.aspx) defines the following Application Programming Interface (API) that you can use to download and upload campaign entity data in the background.

|Interface|Description|
|---------|---------|
|[Bulk Service Operations](../bulk-api/bulk-service-operations.md)|Service operations such as [DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md) and [GetBulkUploadUrl](../bulk-api/getbulkuploadurl-service-operation.md) can be used to download and upload campaign entity data in the background.|
|[Bulk Data Objects](../bulk-api/bulk-data-objects.md)|If want to include performance report data in the Bulk download, you can use the [Date](../bulk-api/date-data-object.md) and [PerformanceStatsDateRange](../bulk-api/performancestatsdaterange-data-object.md) objects.|
|[Bulk Error Data Objects](../bulk-api/bulk-error-data-objects.md)|Be sure to [handle](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx) errors, for example [OperationError](../bulk-api/operationerror-data-object.md) would be returned if the user credentials cannot be authenticated.|
|[Bulk Value Sets](../bulk-api/bulk-value-sets.md)|Choose which data is downloaded with the [DataScope ](../bulk-api/datascope-value-set.md) and [DownloadEntity](../bulk-api/downloadentity-value-set.md) value sets.|
|[Bulk File Schema](../bulk-api/bulk-file-schema.md)|The bulk schema defines the contents of the file for download or upload with the [!INCLUDE[brand](../bulk-api/includes/brand.md)] Bulk service. For both download and upload, the Bulk service supports the file types and corresponding schemas in the [DownloadEntity](../bulk-api/downloadentity-value-set.md) value set. For more information about using the Bulk service to manage your campaigns, see [Bulk Download and Upload](https://msdn.microsoft.com/library/bing-ads-bulk-download-and-upload-guide.aspx). |

## See Also
[Getting Started With the Bing Ads API](https://msdn.microsoft.com/library/bing-ads-getting-started.aspx)  
[Bing Ads Technical Guides](https://msdn.microsoft.com/library/bing-ads-technical-guides.aspx)  
[Bing Ads Web Service Addresses](https://msdn.microsoft.com/library/bing-ads-overview-web-service-addresses.aspx)  
[Bing Ads API Error Codes](https://msdn.microsoft.com/library/bing-ads-operation-error-codes.aspx)  

