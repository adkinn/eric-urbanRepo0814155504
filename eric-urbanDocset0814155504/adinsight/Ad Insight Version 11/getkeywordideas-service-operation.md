---
title: "GetKeywordIdeas Service Operation"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72bd0248-ca14-436b-a33f-2fce0edfe2da
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordIdeas Service Operation
Gets the list of keyword ideas.

Suggests new ad groups and keywords based on your existing keywords, website, and product category. You can also request historical statistics for keywords e.g., monthly searches, competition, average CPC, and ad impression share. You can use the returned suggested keyword bids as input to the [GetKeywordTrafficEstimates](../Ad Insight Version 11/getkeywordtrafficestimates-service-operation.md) operation.

||
|-|
|[!INCLUDE[adint_navigation_noremarks](../Ad Insight Version 11/includes/adint-navigation-noremarks.md)]|

## <a name="request"></a>GetKeywordIdeasRequest Message

### Request Body
The *GetKeywordIdeasRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*ExpandIdeas*|Determines whether you want new keyword ideas, or if you only want keyword attributes for the set of keywords that you specified in the *SearchParameters* list. If you set this element false, the [QuerySearchParameter](../Ad Insight Version 11/querysearchparameter-data-object.md) object must be included in the *SearchParameters* list. |*boolean*|Optional|
|*IdeaAttributes*|The keyword idea attributes that you want included in the response e.g., *Keyword*, *Competition*, *MonthlySearchCounts*, and *SuggestedBid*.<br/><br/>The *Keyword* attribute will always be returned for each returned [KeywordIdea](../Ad Insight Version 11/keywordidea-data-object.md) whether or not you include the *Keyword* value in the requested list of idea attributes.|[KeywordIdeaAttribute](../Ad Insight Version 11/keywordideaattribute-value-set.md) array|Optional|
|*SearchParameters*|The search parameters define your criteria and filters for the requested keyword ideas.<br/><br/>Do not try to instantiate a [SearchParameter](../Ad Insight Version 11/searchparameter-data-object.md). You can include one or more the following objects that derive from it: [CategorySearchParameter](../Ad Insight Version 11/categorysearchparameter-data-object.md), [CompetitionSearchParameter](../Ad Insight Version 11/competitionsearchparameter-data-object.md), [DateRangeSearchParameter](../Ad Insight Version 11/daterangesearchparameter-data-object.md), [DeviceSearchParameter](../Ad Insight Version 11/devicesearchparameter-data-object.md), [ExcludeAccountKeywordsSearchParameter](../Ad Insight Version 11/excludeaccountkeywordssearchparameter-data-object.md), [IdeaTextSearchParameter](../Ad Insight Version 11/ideatextsearchparameter-data-object.md), [ImpressionShareSearchParameter](../Ad Insight Version 11/impressionsharesearchparameter-data-object.md), [LanguageSearchParameter](../Ad Insight Version 11/languagesearchparameter-data-object.md), [LocationSearchParameter](../Ad Insight Version 11/locationsearchparameter-data-object.md), [NetworkSearchParameter](../Ad Insight Version 11/networksearchparameter-data-object.md), [QuerySearchParameter](../Ad Insight Version 11/querysearchparameter-data-object.md), [SearchVolumeSearchParameter](../Ad Insight Version 11/searchvolumesearchparameter-data-object.md), [SuggestedBidSearchParameter](../Ad Insight Version 11/suggestedbidsearchparameter-data-object.md) and [UrlSearchParameter](../Ad Insight Version 11/urlsearchparameter-data-object.md).<br/><br/>You cannot include duplicates of any search parameter type.<br/><br/>The list must include all of these search parameters: [LanguageSearchParameter](../Ad Insight Version 11/languagesearchparameter-data-object.md), [LocationSearchParameter](../Ad Insight Version 11/locationsearchparameter-data-object.md), and [NetworkSearchParameter](../Ad Insight Version 11/networksearchparameter-data-object.md).<br/><br/>The list must include one or more of these search parameters: [CategorySearchParameter](../Ad Insight Version 11/categorysearchparameter-data-object.md), [QuerySearchParameter](../Ad Insight Version 11/querysearchparameter-data-object.md), or [UrlSearchParameter](../Ad Insight Version 11/urlsearchparameter-data-object.md). If the *ExpandIdeas* element is false, then the [QuerySearchParameter](../Ad Insight Version 11/querysearchparameter-data-object.md) is required whether or not you included additional search parameters.|[SearchParameter](../Ad Insight Version 11/searchparameter-data-object.md) array|Required|

### Request Headers
[!INCLUDE[header_intro](../Ad Insight Version 11/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[adint_header_oauth](../Ad Insight Version 11/includes/adint-header-oauth.md)]
#### Password Authentication
[!INCLUDE[adint_header_password](../Ad Insight Version 11/includes/adint-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <Action mustUnderstand="1">GetKeywordIdeas</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetKeywordIdeasRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<ExpandIdeas i:nil="false"></ExpandIdeas>
      \<IdeaAttributes i:nil="false">
        <KeywordIdeaAttribute></KeywordIdeaAttribute>
      </IdeaAttributes>
      \<SearchParameters xmlns:e22="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.SearchParameters" i:nil="false">
        \<e22:SearchParameter i:type="-- specify derived type here with the appropriate prefix --">
          \<!--Keep these fields if you set the i:type attribute to QuerySearchParameter-->
          \<e22:Queries i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          \</e22:Queries>
          \<!--Keep these fields if you set the i:type attribute to UrlSearchParameter-->
          \<e22:Url i:nil="false">\</e22:Url>
          \<!--Keep these fields if you set the i:type attribute to CategorySearchParameter-->
          \<e22:CategoryId>\</e22:CategoryId>
          \<!--Keep these fields if you set the i:type attribute to SearchVolumeSearchParameter-->
          \<e22:Maximum i:nil="false">\</e22:Maximum>
          \<e22:Minimum i:nil="false">\</e22:Minimum>
          \<!--Keep these fields if you set the i:type attribute to SuggestedBidSearchParameter-->
          \<e22:Maximum i:nil="false">\</e22:Maximum>
          \<e22:Minimum i:nil="false">\</e22:Minimum>
          \<!--Keep these fields if you set the i:type attribute to IdeaTextSearchParameter-->
          \<Excluded xmlns:e23="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" i:nil="false">
            \<e23:Keyword>
              \<e23:Id i:nil="false">\</e23:Id>
              \<e23:MatchType>\</e23:MatchType>
              \<e23:Text i:nil="false">\</e23:Text>
            \</e23:Keyword>
          </Excluded>
          \<Included xmlns:e24="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" i:nil="false">
            \<e24:Keyword>
              \<e24:Id i:nil="false">\</e24:Id>
              \<e24:MatchType>\</e24:MatchType>
              \<e24:Text i:nil="false">\</e24:Text>
            \</e24:Keyword>
          </Included>
          \<!--Keep these fields if you set the i:type attribute to ExcludeAccountKeywordsSearchParameter-->
          \<e22:ExcludeAccountKeywords>\</e22:ExcludeAccountKeywords>
          \<!--Keep these fields if you set the i:type attribute to ImpressionShareSearchParameter-->
          \<e22:Maximum i:nil="false">\</e22:Maximum>
          \<e22:Minimum i:nil="false">\</e22:Minimum>
          \<!--Keep these fields if you set the i:type attribute to LocationSearchParameter-->
          \<Locations xmlns:e25="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" i:nil="false">
            \<e25:LocationCriterion>
              \<e25:LocationId>\</e25:LocationId>
            \</e25:LocationCriterion>
          </Locations>
          \<!--Keep these fields if you set the i:type attribute to NetworkSearchParameter-->
          \<Network xmlns:e26="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" i:nil="false">
            \<e26:Network>\</e26:Network>
          </Network>
          \<!--Keep these fields if you set the i:type attribute to DeviceSearchParameter-->
          \<Device xmlns:e27="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" i:nil="false">
            \<e27:DeviceName i:nil="false">\</e27:DeviceName>
          </Device>
          \<!--Keep these fields if you set the i:type attribute to LanguageSearchParameter-->
          \<Languages xmlns:e28="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" i:nil="false">
            \<e28:LanguageCriterion>
              \<e28:Language i:nil="false">\</e28:Language>
            \</e28:LanguageCriterion>
          </Languages>
          \<!--Keep these fields if you set the i:type attribute to CompetitionSearchParameter-->
          \<e22:CompetitionLevels i:nil="false">
            <CompetitionLevel></CompetitionLevel>
          \</e22:CompetitionLevels>
          \<!--Keep these fields if you set the i:type attribute to DateRangeSearchParameter-->
          \<EndDate xmlns:e29="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" i:nil="false">
            \<e29:Day>\</e29:Day>
            \<e29:Month>\</e29:Month>
            \<e29:Year>\</e29:Year>
          </EndDate>
          \<StartDate xmlns:e30="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" i:nil="false">
            \<e30:Day>\</e30:Day>
            \<e30:Month>\</e30:Month>
            \<e30:Year>\</e30:Year>
          </StartDate>
        \</e22:SearchParameter>
      </SearchParameters>
    </GetKeywordIdeasRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetKeywordIdeasResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordIdeas*|The list of keyword ideas.|[KeywordIdea](../Ad Insight Version 11/keywordidea-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[adint_response_header_table](../Ad Insight Version 11/includes/adint-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <GetKeywordIdeasResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<KeywordIdeas xmlns:e29="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e29:KeywordIdea>
          \<e29:AdGroupId p5:nil="false">\</e29:AdGroupId>
          \<e29:AdGroupName p5:nil="false">\</e29:AdGroupName>
          \<e29:AdImpressionShare>\</e29:AdImpressionShare>
          \<e29:Competition>\</e29:Competition>
          \<e29:Keyword p5:nil="false">\</e29:Keyword>
          \<e29:MonthlySearchCounts p5:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:long>\</a1:long>
          \</e29:MonthlySearchCounts>
          \<e29:Relevance>\</e29:Relevance>
          \<e29:Source>\</e29:Source>
          \<e29:SuggestedBid>\</e29:SuggestedBid>
        \</e29:KeywordIdea>
      </KeywordIdeas>
    </GetKeywordIdeasResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../Ad Insight Version 11/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
