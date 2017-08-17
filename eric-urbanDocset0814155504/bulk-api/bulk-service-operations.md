---
title: "Bulk Service Operations"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3dc09043-a7cd-4d5a-b752-218eaf945a61
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Bulk Service Operations
The Bulk service defines the following operations.

|Operation|Description|Request Limits|
|-------------|---------------|------------------|
|[DownloadCampaignsByAccountIds](../bulk-api/downloadcampaignsbyaccountids-service-operation.md)|Downloads settings and performance data for all of the account's campaigns.|1 *Account*|
|[DownloadCampaignsByCampaignIds](../bulk-api/downloadcampaignsbycampaignids-service-operation.md)|Downloads settings and performance data for the specified campaigns.|1,000 *Campaigns*|
|[GetBulkDownloadStatus](../bulk-api/getbulkdownloadstatus-service-operation.md)|Gets the status and completion percentage of a bulk download request.|1 *DownloadRequestId*|
|[GetBulkUploadStatus](../bulk-api/getbulkuploadstatus-service-operation.md)|Gets the status and completion percentage of a bulk upload request.|1 *RequestId*|
|[GetBulkUploadUrl](../bulk-api/getbulkuploadurl-service-operation.md)|Submits a request for a URL where a bulk upload file may be posted.|1 *AccountId*|

## See Also
[Bulk Data Objects](../bulk-api/bulk-data-objects.md)  
[Bulk Value Sets](../bulk-api/bulk-value-sets.md)

