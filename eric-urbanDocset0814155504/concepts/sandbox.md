---
title: "Sandbox"
ms.custom: ""
ms.date: "07/20/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 388750c8-c64c-4e39-a2bf-ec23d87077bf
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Sandbox
[!INCLUDE[brand](../concepts/guides/includes/brand.md)] provides an API sandbox environment where you can test your application before deploying it to the production environment. Ads that you create in sandbox are not served.

Supported services in sandbox vary from production. To get the web service addresses for supported services, see [Bing Ads Web Service Addresses](../concepts/api-reference/bing-ads-web-service-addresses.md).

> [!NOTE]
> Sandbox may be down for maintenance, with or without prior notification. Efforts will be made to notify users before sandbox downtime. Notifications are posted in the [Bing Ads Developer Blog](http://go.microsoft.com/fwlink/?LinkId=269628).

-   [Getting Access](#access)  
-   [Sandbox Best Practices](#bestpractices)  
-   [Ad Insight Service](#adinsight)  
-   [Bulk Service](#bulk)  
-   [Campaign Management Service](#campaign)  
-   [Customer Management Service](#customer)  
-   [Customer Billing Service](#billing)  
-   [Reporting Service](#reporting)  

## <a name="access"></a>Getting Access
The sandbox and production environments use separate credentials. To get access to sandbox, go to the sandbox’s [Bing Ads](https://sandbox.bingads.microsoft.com) web application and click **Sign up** to get a sandbox account. You will use the same username and password to call the API.

When you sign up for an account, append _sbx to the username that you choose, for example contosoapi_sbx. In addition, do not specify a payment instrument.

All [!INCLUDE[brand](../concepts/guides/includes/brand.md)] customers may use the following multi-user developer token in sandbox: **BBD37VB98**

> [!NOTE]
> Authentication with a Microsoft Account is not supported in sandbox. You can test your sandbox application with the *UserName* and *Password* legacy header elements, and then with the *AuthenticationToken* element verify authentication of a Microsoft account via OAuth in production. For more information, see [Managing User Authentication with OAuth](../concepts/guides/authentication-with-oauth.md).

## <a name="bestpractices"></a>Sandbox Best Practices
Sandbox should not be used in the same capacity as production.

-   Make sure that when you deploy your application to the production environment, you use the production WSDLs and your production credentials.  
-   Sandbox contains the current production release, and will be updated with feature previews with or without prior notification.  
-   Capacity of the sandbox is less than that of production, and you should not use it to perform stress or capacity testing.  
-   Please do not use more than one thread.    

## <a name="adinsight"></a>Ad Insight Service
Opportunities are updated daily in sandbox for existing campaigns, ad groups, and keywords to test the end to end coding workflow. You may get test opportunities for up to 1,000 keywords across all accounts per [!INCLUDE[brand](../concepts/guides/includes/brand.md)] customer. You should not use the test data to infer or expect similar performance for your campaigns, ad groups, or keywords in production.

> [!NOTE]
> Sandbox opportunity data is refreshed and updated each weekend, and is available by Monday.

-   [Supported Keywords](#supportedkeywords)  
-   [Service Operations](#adintel_serviceops)  

### <a name="supportedkeywords"></a>Supported Keywords
Sandbox supports a limited set of keywords for testing Ad Insight service operations. You should not use the test data to infer or expect similar estimates for your keywords in production. You may use the following set of keywords to test your application.

|Supported Keywords for Ad Insight Sandbox|
|---------------------------------------------|
|air|
|auto|
|best deals|
|booking|
|car information|
|care|
|deal of the day|
|discounts|
|entertainment|
|finances|
|games|
|hotel reviews|
|insurance comparison|
|sport|
|the hotel|

### <a name="adintel_serviceops"></a>Service Operations
Ad Insight service operations differ from production, and limitations are described in the following table.

|Service Operation|Sandbox Limitations|
|---------------------|-----------------------|
|[GetBidLandscapeByKeywordIds](https://msdn.microsoft.com/library/bing-ads-ad-insight-getbidlandscapebykeywordids.aspx)|Not supported. You can call the operation with existing keyword identifiers, but no data is returned.|
|[GetEstimatedBidByKeywordIds](https://msdn.microsoft.com/library/bing-ads-ad-insight-getestimatedbidbykeywordids.aspx)|A limited set of keywords are supported. For more information, see [Supported Keywords](#supportedkeywords).|
|[GetEstimatedBidByKeywords](https://msdn.microsoft.com/library/bing-ads-ad-insight-getestimatedbidbykeywords.aspx)|A limited set of keywords are supported. For more information, see [Supported Keywords](#supportedkeywords).|
|[GetEstimatedPositionByKeywordIds](https://msdn.microsoft.com/library/bing-ads-ad-insight-getestimatedpositionbykeywordids.aspx)|A limited set of keywords are supported. For more information, see [Supported Keywords](#supportedkeywords).<br /><br />To increase chance of getting an estimate, the *MaxBid* element should be more than or equal to 5 US Dollar, or the equivalent in other currencies.|
|[GetEstimatedPositionByKeywords](https://msdn.microsoft.com/library/bing-ads-ad-insight-getestimatedpositionbykeywords.aspx)|A limited set of keywords are supported. For more information, see [Supported Keywords](#supportedkeywords).<br /><br />To increase chance of getting an estimate, the *MaxBid* element should be more than or equal to 5 US Dollar, or the equivalent in other currencies.|
|[GetHistoricalKeywordPerformance](https://msdn.microsoft.com/library/bing-ads-ad-insight-gethistoricalkeywordperformance.aspx)|A limited set of keywords are supported. For more information, see [Supported Keywords](#supportedkeywords).<br /><br />The *MatchType* and *AdPosition* elements must be set to *Aggregate*.<br /><br />The *Devices* element must be set to *Computers* or left nil.|
|[GetHistoricalSearchCount](https://msdn.microsoft.com/library/bing-ads-ad-insight-gethistoricalsearchcount.aspx)|A limited set of keywords are supported. For more information, see [Supported Keywords](#supportedkeywords).<br /><br />The *EndMonthAndYear* element must be set to the previous month. For example if today's date is June 10, 2013, the end month should be May 2013.<br /><br />The *Devices* element must be set to *Computers* or left nil.|
|[GetKeywordCategories](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordcategories.aspx)|There should be no difference in sandbox versus production.|
|[GetKeywordDemographics](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeyworddemographics.aspx)|A limited set of keywords are supported. For more information, see [Supported Keywords](#supportedkeywords).<br /><br />The *Devices* element must be set to *Computers* or left nil.|
|[GetKeywordLocations](https://msdn.microsoft.com/library/bing-ads-ad-insight-getkeywordlocations.aspx)|A limited set of keywords are supported. For more information, see [Supported Keywords](#supportedkeywords).<br /><br />The *Devices* element must be set to *Computers* or left nil.|
|[SuggestKeywordsForUrl](https://msdn.microsoft.com/library/bing-ads-ad-insight-suggestkeywordsforurl.aspx)|There should be no difference in sandbox versus production.|
|[SuggestKeywordsFromExistingKeywords](https://msdn.microsoft.com/library/bing-ads-ad-insight-suggestkeywordsfromexistingkeywords.aspx)|If the SuggestionType is set to 1, there should be no difference in behavior compared to production.<br /><br />For suggestion type values 2, 3, and 4, the results are limited to the set of keywords provided in sandbox. For more information, see [Supported Keywords](#supportedkeywords).|

## <a name="bulk"></a>Bulk Service
The file size limit for upload in production is 100MB or 2.5 million rows. For sandbox the limit is 20K rows. For more information, see [Bulk Download and Upload](../concepts/guides/bulk-download-and-upload.md).

## <a name="campaign"></a>Campaign Management Service

-   [Editorial Support](#editorialsupport)  
-   [Product Ads](#productads)  

### <a name="editorialsupport"></a>Editorial Support
Sandbox supports limited editorial reviews and appeals.

> [!NOTE]
> Sandbox does not support testing of editorial rejections reason operations, for example [GetEditorialReasonsByIds](https://msdn.microsoft.com/library/bing-ads-campaign-management-geteditorialreasonsbyids.aspx).

#### Magic Terms
If you know of editorial terms that will fail editorial review, you can use them. Otherwise, to test your application’s editorial logic, use the following format to construct a *magic* term that determines, by country, whether editorial will approve or reject the ad or keyword, or put it in a pending state. These magic terms are supported in sandbox only.

{*MatchType*}{*Language*}{*FlagArea*}{m}{*StatusPerCountry*}{m1}

You must specify a value for each component of the term.

|Component|Description|
|-------------|---------------|
|*MatchType*|Determines whether the magic term is the only word in the keyword. The following are the possible match-type values (not case sensitive) that you can specify.<br /><br />e – Exact. The keyword must contain only the magic term.<br /><br />p – Phrase. The keyword can contain other words in addition to the magic term.|
|*Language*|Determines the editorial guidelines to apply. You should specify the same language that the ad group specifies. The following are the possible language values (not case sensitive) that you can specify.<br /><br />EN - English<br /><br />FR - French<br /><br />DE - German|
|*FlagArea*|Determines the area of the editorial guidelines to apply to the term. The following are the possible guideline areas that you can specify.<br /><br />3 - Alcohol<br /><br />15 - Gambling<br /><br />97 – Adult Erotica<br /><br />To specify more than one flag area for a keyword, specify multiple phrase magic terms. For example, pen3m569m1 pen15m569m1.|
|m|Literal. Must be m.|
|*StatusPerCountry*|Determines the editorial status to return for each language. The integer is broken down into 2-bit fields. Each 2-bit field represents the editorial status to apply for the country.<br /><br />The following shows each country’s position in the integer for each *Language* value. The *Language* value determines the countries that you can include in the integer. For example, for English, United States (US) is in the most significant position and Ireland (IE) is in the least significant position.<br /><br />EN - IESGINCAGBUS<br /><br />FR - FRCA<br /><br />DE - DECHAT<br /><br />You can set each country’s 2-bit value to one of the following values.<br /><br />00 - Approved<br /><br />01 - Rejected<br /><br />10 - Pending inactive<br /><br />11 - Pending active<br /><br />For example, to specify that you want the term rejected for US and pending inactive for CA, you would set the integer’s bit fields to 000000100001 (or decimal 33).|
|m1|Literal. Must be m1.|

##### Where to use the magic term
You can use magic terms in the following locations.

-   A text ad’s *Title* element.  
-   A text ad’s *Description* element.  
-   A keyword’s *Text* element.  

##### Example magic term
If you specified a term using the following components, the resulting term would be pen3m569m1.

-   Match type: Phrase 
-   Language: English   
-   Flag area: Alcohol  
-   Editorial status per country: 569 (001000111001), which is broken out as follows.
    -   Rejected in US  
    -   Pending inactive in GB  
    -   Pending active in CA  
    -   Approved in IN  
    -   Pending inactive in SG  
    -   Approved in IE

### <a name="productads"></a>Product Ads
Product ads are supported in sandbox in the United States. To be auto-approved you must create a catalog and a [!INCLUDE[storebrand](../concepts/guides/includes/storebrand.md)] store that ends with "sandbox" as follows.

1.  In the [!INCLUDE[brand](../concepts/guides/includes/brand.md)] web application click on **Tools**.

2.  Under **Management Tools**, click on **Bing Merchant Center**.

3.  Click **Create store**, and enter a store name that ends with "**sandbox**" (case-insensitive).

4.  Add your store info, select **Product Ads** under **Catalog settings**, and click **Finish**.

5.  In your new store, click **Catalog management**, and then click **Create catalog**.

6.  Add your catalog name, select **Manually upload file later** under **Catalog feed file**, and click **Save**.

## <a name="billing"></a>Customer Billing Service
The Customer Billing service is not supported in sandbox.

## <a name="customer"></a>Customer Management Service
Most customer management service operations are supported in sandbox. Unsupported features include [AddClientLinks](https://msdn.microsoft.com/library/bing-ads-customer-management-addclientlinks.aspx) and [UpdateClientLinks](https://msdn.microsoft.com/library/bing-ads-customer-management-updateclientlinks.aspx).

## <a name="reporting"></a>Reporting Service
When you create a keyword, test performance data should be generated within a few hours. The data is provided to test generating, retrieving, and parsing reports in the sandbox. For a given keyword identifier, the test data is not updated over time. The data will show example performance for one month prior to the creation of your keyword by design. You should not use the test data to infer or expect similar performance for your keywords in production. 

The following reports can return performance data in sandbox.

-   [AccountPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-accountperformancereportrequest.aspx)
-   [AdDynamicTextPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-addynamictextperformancereportrequest.aspx)
-   [AdGroupPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adgroupperformancereportrequest.aspx)
-   [AdPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-adperformancereportrequest.aspx)
-   [CallDetailReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-calldetailreportrequest.aspx)
-   [CampaignPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-campaignperformancereportrequest.aspx)
-   [DestinationUrlPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-destinationurlperformancereportrequest.aspx)
-   [GeographicalLocationReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-geographicallocationreportrequest.aspx)
-   [KeywordPerformanceReportRequest](https://msdn.microsoft.com/library/bing-ads-reporting-keywordperformancereportrequest.aspx)

> [!NOTE]
> All other report types can be submitted successfully, and the sandbox service will return an empty report.

