---
title: "Reporting Data Retention Time Periods"
ms.custom: ""
ms.date: "07/10/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 468936d5-f707-468c-80ca-f728bd67a0b3
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Reporting Data Retention Time Periods
Reporting data is kept for specified periods of time. This topic provides the data retention time periods for Bing Ads performance data. Use this information to see how far back hourly, daily, weekly, monthly, yearly and summary aggregated data can be retrieved for a report.

Retention periods for reporting data is broken down into the following report categories.

-   [Performance](#performance)  
-   [Ad Extensions](#adextensions)  
-   [Product Ads](#productads)  
-   [Dynamic Search Ads](#dynamicsearchads)  
-   [Change History](#changehistory)  
-   [Targeting](#targeting)  
-   [Campaign Analytics](#analytics)  
-   [Billing and Budget](#budget)  

> [!NOTE]
> Retention periods are not applicable for the [Negative Keyword Conflict Report](http://msdn.microsoft.com/library/bing-ads-reporting-negativekeywordconflictreportrequest.aspx). The report is generated based on the current keywords and negative keywords.
> 
> It is possible to request and retrieve data outside of the published retention period, however the data outside of the retention period should be considered invalid or incomplete.

Unless otherwise noted, the **Hourly**, **Daily**, **Weekly**, **Monthly**, **Yearly** and **Summary** values are in *months*. For example, the last 6 months of hourly Keyword report data is available.

If the data aggregation is not available for a given report, it will be noted as *Not Applicable* in the table below.

## <a name="performance"></a>Performance

|API Report Name|Bing Ads Web Application Report Name|Hourly|Daily|Weekly|Monthly|Yearly|Summary|
|-------------------|----------------------------------------|----------|---------|----------|-----------|----------|-----------|
|[Account Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-accountperformancereportrequest.aspx)|Account|6|36|36|36|36|36|
|[Ad Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportrequest.aspx)|Ad|6|36|36|36|36|36|
|[Ad Dynamic Text Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-addynamictexxtperformancereportrequest.aspx)|Ad Dynamic Text|6|36|36|36|36|36|
|[Ad Group Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportrequest.aspx)|Ad Group|6|36|36|36|36|36|
|[Audience Performance Report](https://msdn.microsoft.com/library/bing-ads-reporting-audienceperformancereportrequest.aspx)|Audiences|6|36|36|36|36|36|
|[Campaign Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportrequest.aspx)|Campaign|6|36|36|36|36|36|
|[Destination Url Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportrequest.aspx)|Destination URL|6|36|36|36|36|36|
|[Keyword Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportrequest.aspx)|Keyword|6|36|36|36|36|36|
|[Search Query Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-searchqueryperformancereportrequest.aspx)|Search Term|1|36|36|36|36|36|
|[Share of Voice Report](http://msdn.microsoft.com/library/bing-ads-reporting-shareofvoicereportrequest.aspx)|Share of Voice|Not Applicable|3|3|6|6|6|

## <a name="adextensions"></a>Ad Extensions

|API Report Name|Bing Ads Web Application Report Name|Hourly|Daily|Weekly|Monthly|Yearly|Summary|
|-------------------|----------------------------------------|----------|---------|----------|-----------|----------|-----------|
|[Ad Extension By Ad Report](http://msdn.microsoft.com/library/bing-ads-reporting-adextensionbyadreportrequest.aspx)|Ad Extension by Ad|6|36|36|36|36|36|
|[Ad Extension Detail Report](http://msdn.microsoft.com/library/bing-ads-reporting-adextensiondetailreportrequest.aspx)|Ad Extension by Item|6|36|36|36|36|36|
|[Ad Extension By Keyword Report](http://msdn.microsoft.com/library/bing-ads-reporting-adextensionbykeywordreportrequest.aspx)|Ad Extension by Keyword|6|36|36|36|36|36|
|[Call Detail Report](http://msdn.microsoft.com/library/bing-ads-reporting-calldetailreportrequest.aspx)|Call Forwarding Detail|6|6|6|6|6|6|


## <a name="productads"></a>Product Ads

|API Report Name|Bing Ads Web Application Report Name|Hourly|Daily|Weekly|Monthly|Yearly|Summary|
|-------------------|----------------------------------------|----------|---------|----------|-----------|----------|-----------|
|[Product Dimension Performance Report](https://msdn.microsoft.com/library/bing-ads-reporting-productdimensionperformancereportrequest.aspx)|Product Dimension|6|36|36|36|36|36|
|[Product Partition Performance Report](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionperformancereportrequest.aspx)|Product Partition|6|36|36|36|36|36|
|[Product Partition Unit Performance Report](https://msdn.microsoft.com/library/bing-ads-reporting-productpartitionunitperformancereportrequest.aspx)|Product Partition Unit|6|36|36|36|36|36|
|[Product Search Query Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-searchqueryperformancereportrequest.aspx)|Product Search Term|1|36|36|36|36|36|


## <a name="dynamicsearchads"></a>Dynamic Search Ads

|API Report Name|Bing Ads Web Application Report Name|Hourly|Daily|Weekly|Monthly|Yearly|Summary|
|-------------------|----------------------------------------|----------|---------|----------|-----------|----------|-----------|
|[DSA Auto Target Performance Report](https://msdn.microsoft.com/library/bing-ads-reporting-dsaautotargetperformancereportrequest.aspx)|(Coming soon)|6|36|36|36|36|36|
|[DSA Category Performance Report](https://msdn.microsoft.com/library/bing-ads-reporting-dsacategoryperformancereportrequest.aspx)|(Coming soon)|6|36|36|36|36|36|
|[DSA Search Query Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-dsasearchqueryperformancereportrequest.aspx)|(Coming soon)|1|36|36|36|36|36|

## <a name="changehistory"></a>Change History

|API Report Name|Bing Ads Web Application Report Name|Hourly|Daily|Weekly|Monthly|Yearly|Summary|
|-------------------|----------------------------------------|----------|---------|----------|-----------|----------|-----------|
|[Search Campaign Change History Report](http://msdn.microsoft.com/library/bing-ads-reporting-searchcampaignchangehistoryreportrequest.aspx)|Campaign Change History|6|6|6|6|6|6|

## <a name="targeting"></a>Targeting

|API Report Name|Bing Ads Web Application Report Name|Hourly|Daily|Weekly|Monthly|Yearly|Summary|
|-------------------|----------------------------------------|----------|---------|----------|-----------|----------|-----------|
|[Age Gender Demographic Report](http://msdn.microsoft.com/library/bing-ads-reporting-agegenderdemographicreportrequest.aspx)|Age and Gender|6|36|36|36|36|36|
|[Geographic Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-geographicperformancereportrequest.aspx)|Geographic|14 **days**|36|36|36|36|36|
|[User Location Report](http://msdn.microsoft.com/library/bing-ads-reporting-userlocationperformancereportrequest.aspx)|User Location|14 **days**|36|36|36|36|36|

## <a name="analytics"></a>Campaign Analytics

|API Report Name|Bing Ads Web Application Report Name|Hourly|Daily|Weekly|Monthly|Yearly|Summary|
|-------------------|----------------------------------------|----------|---------|----------|-----------|----------|-----------|
|[Conversion Performance Report](http://msdn.microsoft.com/library/bing-ads-reporting-conversionperformancereportrequest.aspx)|Conversions|6|36|36|36|36|36|
|[Goals And Funnels Report](http://msdn.microsoft.com/library/bing-ads-reporting-goalsandfunnelsreportrequest.aspx)|Goals|1|36|36|36|36|36|
|Not applicable|Segments|1|36|36|36|36|36|


## <a name="budget"></a>Billing and Budget

|API Report Name|Bing Ads Web Application Report Name|Hourly|Daily|Weekly|Monthly|Yearly|Summary|
|-------------------|----------------------------------------|----------|---------|----------|-----------|----------|-----------|
|[Budget Summary Report](http://msdn.microsoft.com/library/bing-ads-reporting-budgetsummaryreportrequest.aspx)|Budget|Not Applicable|24|Not Applicable|Not Applicable|Not Applicable|Not Applicable|
|Not applicable|Billing Statement|Not Applicable|Not Applicable|Not Applicable|36|Not Applicable|Not Applicable|
