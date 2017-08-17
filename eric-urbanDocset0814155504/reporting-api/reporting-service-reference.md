---
title: "Reporting Service Reference"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6609bc0f-0054-481b-ba59-a62a65104041
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Reporting Service Reference
The Reporting [service](https://msdn.microsoft.com/library/bing-ads-overview-web-service-addresses.aspx) defines the following Application Programming Interface (API) that you can use to request and download reports.

|Interface|Description|
|---------|---------|
|[Reporting Service Operations](../reporting-api/reporting-service-operations.md)|Use the [SubmitGenerateReport](../reporting-api/submitgeneratereport-service-operation.md) and [PollGenerateReport](../reporting-api/pollgeneratereport-service-operation.md) operations to specify the type of report that you want to download, and get the download URL. For an overview, see [Request and Download a Report](https://msdn.microsoft.com/library/bing-ads-reporting-request-and-download-a-report.aspx).|
|[Reporting Data Objects](../reporting-api/reporting-data-objects.md)|You'll find most of the same reports that are available in the Bing Ads web application, for example the [CampaignPerformanceReportRequest](../reporting-api/campaignperformancereportrequest-data-object.md) and [SearchCampaignChangeHistoryReportRequest](../reporting-api/searchcampaignchangehistoryreportrequest-data-object.md).|
|[Reporting Error Data Objects](../reporting-api/reporting-error-data-objects.md)|Be sure to [handle](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx) errors, for example [OperationError](../reporting-api/operationerror-data-object.md) would be returned if the user credentials cannot be authenticated.|
|[Reporting Value Sets](../reporting-api/reporting-value-sets.md)|Use the reporting value sets to specify the [attributes and performance statistics](https://msdn.microsoft.com/library/bing-ads-report-attributes-performance-statistics-guide.aspx) you want to download.|

## See Also
[Getting Started With the Bing Ads API](https://msdn.microsoft.com/library/bing-ads-getting-started.aspx)  
[Bing Ads Technical Guides](https://msdn.microsoft.com/library/bing-ads-technical-guides.aspx)  
[Bing Ads Web Service Addresses](https://msdn.microsoft.com/library/bing-ads-overview-web-service-addresses.aspx)  
[Bing Ads API Error Codes](https://msdn.microsoft.com/library/bing-ads-operation-error-codes.aspx)  

