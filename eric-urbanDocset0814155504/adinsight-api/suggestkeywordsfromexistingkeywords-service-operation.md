---
title: "SuggestKeywordsFromExistingKeywords Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ea9c8b7-43dd-4c73-ab02-f50cd3938842
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SuggestKeywordsFromExistingKeywords Service Operation
Suggests keywords that could perform better than the specified keywords.

||
|-|
|[!INCLUDE[adint_navigation](../adinsight-api/includes/adint-navigation.md)]|

## <a name="request"></a>SuggestKeywordsFromExistingKeywordsRequest Message

### Request Body
The *SuggestKeywordsFromExistingKeywordsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdGroupId*|The identifier of the ad group for suggested keywords.<br /><br />**Note:** This element is not yet supported and may be used to influence keyword suggestions in a future release|*string*|No|
|*CampaignId*|The identifier of the campaign for suggested keywords.<br /><br />**Note:** This element is not yet supported and may be used to influence keyword suggestions in a future release|*string*|No|
|*ExcludeBrand*|A value that determines whether the results exclude brand keywords. To exclude brand keywords in the result, set to true. The default is false.|*boolean*|No|
|*Keywords*|An array of keywords for which you want to get suggested keywords that could perform better. The array can contain a maximum of 1,000 keywords, and each keyword can contain a maximum of 100 characters.|*string* array|Yes|
|*Language*|The language in which the keyword is written.<br /><br />For possible values, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113). See the [Remarks](#remarks) section below for a list of providers that are supported for each language.<br /><br />The default is English.|*string*|No|
|*MaxSuggestionsPerKeyword*|The maximum number of keyword suggestions to return per specified keyword. If *SuggestionType* is set to 4, you can request a maximum of 200 suggestions per keyword; otherwise the maximum suggestions that you can request is 100.<br /><br />The default is 50.|*int*|No|
|*PublisherCountries*|The country codes of the countries/regions to use as the source of data for determining the suggested keywords.<br /><br />You can specify one or more country codes. Each country that you specify must support the language that you specified in the *Language* element.<br /><br />For supported values, see the [Remarks](#remarks) section below.<br /><br />The default is all countries/regions that support the specified language.|*string* array|No|
|*RemoveDuplicates*|A Boolean value that determines whether to remove duplicate keywords from the list of suggested keywords. To remove duplicates, set to true. The default is false.|*boolean*|No|
|*SuggestionType*|The provider to use to generate the keyword suggestions. For a list of possible providers, the language and country restrictions of each provider, and the default provider by country, see the [Remarks](#remarks) section below.|*int*|No|

### Request Headers
[!INCLUDE[header_intro](../adinsight-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[adint_header_oauth](../adinsight-api/includes/adint-header-oauth.md)]
#### Password Authentication
[!INCLUDE[adint_header_password](../adinsight-api/includes/adint-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <Action mustUnderstand="1">SuggestKeywordsFromExistingKeywords</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <SuggestKeywordsFromExistingKeywordsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:string>\</a1:string>
      </Keywords>
      \<Language i:nil="false"></Language>
      \<PublisherCountries i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:string>\</a1:string>
      </PublisherCountries>
      \<MaxSuggestionsPerKeyword i:nil="false"></MaxSuggestionsPerKeyword>
      \<SuggestionType i:nil="false"></SuggestionType>
      \<RemoveDuplicates i:nil="false"></RemoveDuplicates>
      \<ExcludeBrand i:nil="false"></ExcludeBrand>
      \<AdGroupId i:nil="false"></AdGroupId>
      \<CampaignId i:nil="false"></CampaignId>
    </SuggestKeywordsFromExistingKeywordsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>SuggestKeywordsFromExistingKeywordsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordSuggestions*|An array of [KeywordSuggestion](../adinsight-api/keywordsuggestion-data-object.md) data objects. The array contains an item for each keyword specified in the request. The object contains a list of suggested keywords that may perform better than the specified keyword.<br /><br />For each suggested keyword, the object includes a score that indicates the probability that using the keyword would result in an ad being included in the results of a search query. If there are no suggestions for a keyword, the *SuggestionsAndConfidence* element will be null.|[KeywordSuggestion](../adinsight-api/keywordsuggestion-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[adint_response_header_table](../adinsight-api/includes/adint-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <SuggestKeywordsFromExistingKeywordsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<KeywordSuggestions xmlns:e40="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e40:KeywordSuggestion>
          \<e40:Keyword p5:nil="false">\</e40:Keyword>
          \<e40:SuggestionsAndConfidence p5:nil="false">
            \<e40:KeywordAndConfidence>
              \<e40:SuggestedKeyword p5:nil="false">\</e40:SuggestedKeyword>
              \<e40:ConfidenceScore>\</e40:ConfidenceScore>
            \</e40:KeywordAndConfidence>
          \</e40:SuggestionsAndConfidence>
        \</e40:KeywordSuggestion>
      </KeywordSuggestions>
    </SuggestKeywordsFromExistingKeywordsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## <a name="remarks"></a>Remarks
The following are the possible suggestion providers that you can specify.

|Suggestion Type|Description|
|-------------------|---------------|
|1|Returns search queries that include the keyword.|
|2|Returns keywords from other ad groups that include the specified keyword.|
|3|Returns search queries that are related to the specified keyword.|
|4|Returns the best suggestions from the other providers.|
The following are the providers that each country supports.

### 

|Country (Country Code)|Language|Type 1|Type 2|Type 3|Type 4|Default Provider|
|--------------------------|------------|----------|----------|----------|----------|--------------------|
|Argentina (AR)|Spanish|No|Yes|Yes|No|2|
|Australia (AU)|English|No|Yes|Yes|Yes|4|
|Brazil (BR)|Portuguese|No|Yes|Yes|No|2|
|Canada (CA)|English|Yes|Yes|Yes|No|2|
|Canada (CA)|French|No|Yes|Yes|No|2|
|Chile (CL)|Spanish|No|Yes|Yes|No|2|
|Colombia (CO)|Spanish|No|Yes|Yes|No|2|
|Denmark (DK)|Danish|No|Yes|No|No|2|
|Finland (FI)|Finnish|No|Yes|No|No|2|
|France|French|Yes|Yes|Yes|Yes|4|
|Germany (DE)|German|No|Yes|Yes|Yes|4|
|Hong Kong (HK)|Traditional Chinese|No|Yes|No|No|2|
|India (IN)|English|No|Yes|Yes|No|2|
|Indonesia (ID)|English|No|Yes|No|No|2|
|Ireland (IE)|English|No|Yes|No|No|2|
|Italy (IT)|Italian|No|Yes|Yes|No|2|
|Malaysia (MY)|English|No|Yes|No|No|2|
|Mexico (MX)|Spanish|No|Yes|Yes|No|2|
|Netherlands (NL)|Dutch|No|Yes|Yes|No|2|
|New Zealand (NZ)|English|No|Yes|No|No|2|
|Norway (NO)|Norwegian|No|Yes|Yes|No|2|
|Peru (PE)|Spanish|No|Yes|Yes|No|2|
|Philippines (PH)|English|No|Yes|No|No|2|
|Singapore (SG)|English|No|Yes|No|No|2|
|Spain (ES)|Spanish|No|Yes|Yes|No|2|
|Sweden (SE)|Swedish|No|Yes|No|No|2|
|Taiwan (TW)|Traditional Chinese|No|Yes|No|Yes|4|
|Thailand (TH)|English|No|Yes|Yes|No|2|
|United Kingdom (GB)|English|Yes|Yes|Yes|Yes|4|
|United States (US)|English|Yes|Yes|Yes|Yes|4|
|Venezuela (VE)|Spanish|No|Yes|Yes|No|2|
|Vietnam (VN)|English|No|Yes|No|No|2|
