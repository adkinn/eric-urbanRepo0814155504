---
title: "Bing Ads Client Libraries"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a82f547-d755-4c44-813f-7df9151150ed
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Bing Ads Client Libraries
You can develop [!INCLUDE[brand](../concepts/includes/brand.md)] applications with any programming language that supports web services. The Bing Ads Software Development Kits (SDK) enhance the experience of developing [!INCLUDE[brand](../concepts/includes/brand.md)] applications with .NET, Java, and Python languages. Each SDK includes a proxy to all [!INCLUDE[brand](../concepts/includes/brand.md)] API web services and abstracts low level details of authentication with OAuth. You can use the high level *BulkServiceManager* and *ReportingServiceManager* interfaces to abstract and execute operations in the low level Bulk and Reporting services. For example instead of calling *SubmitGenerateReport* and *PollGenerateReport* to download a report, you download a report using one method with the *ReportingServiceManager* class.

> [!NOTE]
> The PHP SDK does not include *BulkServiceManager* and *ReportingServiceManager* interfaces as described for the other three SDKs.

## <a name="repositories"></a>SDK Repositories

|SDK|Documentation|Source|Distribution|Code Examples|License|
|-------|-----------------|----------|----------------|-----------------|-----------|
|Bing Ads .NET SDK|[Getting Started](../concepts/getting-started-using-csharp-with-bing-ads-services.md)|[GitHub](https://github.com/BingAds/BingAds-dotNet-SDK)|[NuGet](https://www.nuget.org/packages/Microsoft.BingAds.SDK/)|[GitHub](http://go.microsoft.com/fwlink/?LinkId=525447) &#124; [MSDN](../concepts/csharp-examples-for-bing-ads.md)|[Bing Ads .NET SDK License](https://github.com/BingAds/BingAds-dotNet-SDK/blob/master/LICENSE.md)|
|Bing Ads Java SDK|[Getting Started](../concepts/getting-started-using-java-with-bing-ads-services.md) |[GitHub](https://github.com/BingAds/BingAds-Java-SDK)|[Maven](https://github.com/BingAds/BingAds-Java-SDK#Maven-Artifact)|[GitHub](http://go.microsoft.com/fwlink/?LinkId=525443) &#124; [MSDN](../concepts/java-examples-for-bing-ads.md)|[Bing Ads Java SDK License](https://github.com/BingAds/BingAds-Java-SDK/blob/master/LICENSE)|
|Bing Ads Python SDK|[Getting Started](../concepts/getting-started-using-python-with-bing-ads-services.md) |[GitHub](https://github.com/BingAds/BingAds-Python-SDK)|[PyPi](https://pypi.python.org/pypi/bingads)|[GitHub](http://go.microsoft.com/fwlink/?LinkId=529184) &#124; [MSDN](../concepts/python-examples-for-bing-ads.md)|[Bing Ads Python SDK License](https://github.com/BingAds/BingAds-Python-SDK/blob/master/LICENSE)|
|Bing Ads PHP SDK|[Getting Started](../concepts/getting-started-using-php-with-bing-ads-services.md)|[GitHub](https://github.com/BingAds/BingAds-PHP-SDK)|[Packagist](https://packagist.org/packages/microsoft/bingads)|[GitHub](http://go.microsoft.com/fwlink/?LinkId=838593) &#124; [MSDN](../concepts/php-examples-for-bing-ads.md)|[Bing Ads PHP SDK License](https://github.com/BingAds/BingAds-PHP-SDK/blob/master/LICENSE.md)|

## <a name="namespaces"></a>Namespaces

### <a name="latestnamespaces"></a>Latest Namespaces
The SDKs support all active [Bing Ads Web Service Addresses](../concepts/bing-ads-web-service-addresses.md) in sandbox and production. 

You should use the following namespaces corresponding to the latest version of each service. These are the supported high level public namespaces. Internal and lower level namespaces are not documented here. You can find out more information about internal namespaces within the GitHub [SDK Repositories](#repositories) for each SDK.

|Namespace|Description|
|-------------|---------------|
|*Microsoft.BingAds*|Provides classes related to authentication that can be used to access any Bing Ads Web Service.<br/>**Note:** [Bing Ads Content API](https://msdn.microsoft.com/library/bing-ads-content-api(v=msads.90).aspx) clients can use the authentication classes provided with the SDK; however, the SDK does not include classes for calling the Content API.|
|*Microsoft.BingAds.V11.AdInsight*|Provides proxy classes to the service operations, data objects, and value sets defined for version 11 of the [Ad Insight](https://msdn.microsoft.com/library/bing-ads-ad-insight-reference(v=msads.100).aspx) service.|
|*Microsoft.BingAds.V11.Bulk*|Provides proxy classes to the service operations, data objects, and value sets defined for version 11 of the [Bulk](https://msdn.microsoft.com/library/bing-ads-bulk-reference(v=msads.100).aspx) service.<br />Provides classes to accelerate productivity for downloading and uploading entities. For example an instance of the *BulkServiceManager* class can submit your download request to the bulk service, poll the service until completed, and download the file to the local directory that you specified in the request. Use the *BulkFileReader* class instead of writing a file parser to read the download results. The *BulkFileReader* provides access to the bulk file records in *BulkEntity* derived classes, which contain the familiar data objects and value sets in version 11 of the [Campaign Management](https://msdn.microsoft.com/library/bing-ads-campaign-management-reference(v=msads.100).aspx) service.|
|*Microsoft.BingAds.V11.CampaignManagement*|Provides proxy classes to the service operations, data objects, and value sets defined for version 11 of the [Campaign Management](https://msdn.microsoft.com/library/bing-ads-campaign-management-reference(v=msads.100).aspx) service.|
|*Microsoft.BingAds.V11.CustomerBilling*|Provides proxy classes to the service operations, data objects, and value sets defined for version 11 of the [Customer Billing](https://msdn.microsoft.com/library/bing-ads-customer-billing-api-reference(v=msads.90).aspx) service.|
|*Microsoft.BingAds.V11.CustomerManagement*|Provides proxy classes to the service operations, data objects, and value sets defined for version 11 of the [Customer Management](https://msdn.microsoft.com/library/bing-ads-customer-management-api-reference(v=msads.90).aspx) service.|
|*Microsoft.BingAds.V11.Reporting*|Provides proxy classes to the service operations, data objects, and value sets defined for version 11 of the [Reporting](https://msdn.microsoft.com/library/bing-ads-reporting-reference(v=msads.90).aspx) service.<br />Provides classes to accelerate productivity for downloading reports. For example an instance of the *ReportingServiceManager* class can submit your download request to the reporting service, poll the service until completed, and download the file to the local directory that you specified in the request.|

## See Also
[Bing Ads Web Service Addresses](../concepts/bing-ads-web-service-addresses.md)  

