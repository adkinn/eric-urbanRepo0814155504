---
title: "AddAdExtensions Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09c3fd1a-99d9-401d-86e7-dcfe32c6301b
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddAdExtensions Service Operation
Adds one or more ad extensions to an account’s ad extension library.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddAdExtensionsRequest Message

### Request Body
The *AddAdExtensionsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account to add the extensions to.|*long*|
|*AdExtensions*|The list of ad extensions of any type to add to the account. You can specify a maximum of 100 extensions per call.|[AdExtension](../campaign-api/adextension-data-object.md) array|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">AddAdExtensions</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <AddAdExtensionsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      \<AdExtensions i:nil="false">
        \<AdExtension i:type="-- specify derived type here with the appropriate prefix --">
          \<DevicePreference i:nil="false"></DevicePreference>
          \<ForwardCompatibilityMap xmlns:e1="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            \<e1:KeyValuePairOfstringstring>
              \<e1:key i:nil="false">\</e1:key>
              \<e1:value i:nil="false">\</e1:value>
            \</e1:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          \<Id i:nil="false"></Id>
          \<Scheduling i:nil="false">
            \<DayTimeRanges i:nil="false">
              <DayTime>
                <Day></Day>
                <EndHour></EndHour>
                <EndMinute></EndMinute>
                <StartHour></StartHour>
                <StartMinute></StartMinute>
              </DayTime>
            </DayTimeRanges>
            \<EndDate i:nil="false">
              <Day></Day>
              <Month></Month>
              <Year></Year>
            </EndDate>
            \<StartDate i:nil="false">
              <Day></Day>
              <Month></Month>
              <Year></Year>
            </StartDate>
            \<UseSearcherTimeZone i:nil="false"></UseSearcherTimeZone>
          </Scheduling>
          \<Status i:nil="false"></Status>
          \<Type i:nil="false"></Type>
          \<Version i:nil="false"></Version>
          \<!--Keep these fields if you set the i:type attribute to SiteLinksAdExtension-->
          \<SiteLinks i:nil="false">
            <SiteLink>
              \<Description1 i:nil="false"></Description1>
              \<Description2 i:nil="false"></Description2>
              \<DestinationUrl i:nil="false"></DestinationUrl>
              \<DevicePreference i:nil="false"></DevicePreference>
              \<DisplayText i:nil="false"></DisplayText>
              \<FinalAppUrls xmlns:e2="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
                \<e2:AppUrl>
                  \<e2:OsType i:nil="false">\</e2:OsType>
                  \<e2:Url i:nil="false">\</e2:Url>
                \</e2:AppUrl>
              </FinalAppUrls>
              \<FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                \<a1:string>\</a1:string>
              </FinalMobileUrls>
              \<FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                \<a1:string>\</a1:string>
              </FinalUrls>
              \<Scheduling i:nil="false">
                \<DayTimeRanges i:nil="false">
                  <DayTime>
                    <Day></Day>
                    <EndHour></EndHour>
                    <EndMinute></EndMinute>
                    <StartHour></StartHour>
                    <StartMinute></StartMinute>
                  </DayTime>
                </DayTimeRanges>
                \<EndDate i:nil="false">
                  <Day></Day>
                  <Month></Month>
                  <Year></Year>
                </EndDate>
                \<StartDate i:nil="false">
                  <Day></Day>
                  <Month></Month>
                  <Year></Year>
                </StartDate>
                \<UseSearcherTimeZone i:nil="false"></UseSearcherTimeZone>
              </Scheduling>
              \<TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
              \<UrlCustomParameters xmlns:e3="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
                \<e3:Parameters i:nil="false">
                  \<e3:CustomParameter>
                    \<e3:Key i:nil="false">\</e3:Key>
                    \<e3:Value i:nil="false">\</e3:Value>
                  \</e3:CustomParameter>
                \</e3:Parameters>
              </UrlCustomParameters>
            </SiteLink>
          </SiteLinks>
          \<!--Keep these fields if you set the i:type attribute to LocationAdExtension-->
          \<Address i:nil="false">
            \<CityName i:nil="false"></CityName>
            \<CountryCode i:nil="false"></CountryCode>
            \<PostalCode i:nil="false"></PostalCode>
            \<ProvinceCode i:nil="false"></ProvinceCode>
            \<ProvinceName i:nil="false"></ProvinceName>
            \<StreetAddress i:nil="false"></StreetAddress>
            \<StreetAddress2 i:nil="false"></StreetAddress2>
          </Address>
          \<CompanyName i:nil="false"></CompanyName>
          \<GeoCodeStatus i:nil="false"></GeoCodeStatus>
          \<GeoPoint i:nil="false">
            <LatitudeInMicroDegrees></LatitudeInMicroDegrees>
            <LongitudeInMicroDegrees></LongitudeInMicroDegrees>
          </GeoPoint>
          \<IconMediaId i:nil="false"></IconMediaId>
          \<ImageMediaId i:nil="false"></ImageMediaId>
          \<PhoneNumber i:nil="false"></PhoneNumber>
          \<!--Keep these fields if you set the i:type attribute to CallAdExtension-->
          \<CountryCode i:nil="false"></CountryCode>
          \<IsCallOnly i:nil="false"></IsCallOnly>
          \<IsCallTrackingEnabled i:nil="false"></IsCallTrackingEnabled>
          \<PhoneNumber i:nil="false"></PhoneNumber>
          \<RequireTollFreeTrackingNumber i:nil="false"></RequireTollFreeTrackingNumber>
          \<!--Keep these fields if you set the i:type attribute to ImageAdExtension-->
          \<AlternativeText i:nil="false"></AlternativeText>
          \<Description i:nil="false"></Description>
          \<DestinationUrl i:nil="false"></DestinationUrl>
          \<FinalAppUrls xmlns:e4="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e4:AppUrl>
              \<e4:OsType i:nil="false">\</e4:OsType>
              \<e4:Url i:nil="false">\</e4:Url>
            \</e4:AppUrl>
          </FinalAppUrls>
          \<FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </FinalMobileUrls>
          \<FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </FinalUrls>
          \<ImageMediaIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:long>\</a1:long>
          </ImageMediaIds>
          \<TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          \<UrlCustomParameters xmlns:e5="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e5:Parameters i:nil="false">
              \<e5:CustomParameter>
                \<e5:Key i:nil="false">\</e5:Key>
                \<e5:Value i:nil="false">\</e5:Value>
              \</e5:CustomParameter>
            \</e5:Parameters>
          </UrlCustomParameters>
          \<!--Keep these fields if you set the i:type attribute to AppAdExtension-->
          \<AppPlatform i:nil="false"></AppPlatform>
          \<AppStoreId i:nil="false"></AppStoreId>
          \<DestinationUrl i:nil="false"></DestinationUrl>
          \<DisplayText i:nil="false"></DisplayText>
          \<FinalAppUrls xmlns:e6="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e6:AppUrl>
              \<e6:OsType i:nil="false">\</e6:OsType>
              \<e6:Url i:nil="false">\</e6:Url>
            \</e6:AppUrl>
          </FinalAppUrls>
          \<FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </FinalMobileUrls>
          \<FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </FinalUrls>
          \<TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          \<UrlCustomParameters xmlns:e7="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e7:Parameters i:nil="false">
              \<e7:CustomParameter>
                \<e7:Key i:nil="false">\</e7:Key>
                \<e7:Value i:nil="false">\</e7:Value>
              \</e7:CustomParameter>
            \</e7:Parameters>
          </UrlCustomParameters>
          \<!--Keep these fields if you set the i:type attribute to ReviewAdExtension-->
          <IsExact></IsExact>
          \<Source i:nil="false"></Source>
          \<Text i:nil="false"></Text>
          \<Url i:nil="false"></Url>
          \<!--Keep these fields if you set the i:type attribute to CalloutAdExtension-->
          \<Text i:nil="false"></Text>
          \<!--Keep these fields if you set the i:type attribute to Sitelink2AdExtension-->
          \<Description1 i:nil="false"></Description1>
          \<Description2 i:nil="false"></Description2>
          \<DestinationUrl i:nil="false"></DestinationUrl>
          \<DisplayText i:nil="false"></DisplayText>
          \<FinalAppUrls xmlns:e8="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e8:AppUrl>
              \<e8:OsType i:nil="false">\</e8:OsType>
              \<e8:Url i:nil="false">\</e8:Url>
            \</e8:AppUrl>
          </FinalAppUrls>
          \<FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </FinalMobileUrls>
          \<FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </FinalUrls>
          \<TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          \<UrlCustomParameters xmlns:e9="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e9:Parameters i:nil="false">
              \<e9:CustomParameter>
                \<e9:Key i:nil="false">\</e9:Key>
                \<e9:Value i:nil="false">\</e9:Value>
              \</e9:CustomParameter>
            \</e9:Parameters>
          </UrlCustomParameters>
          \<!--Keep these fields if you set the i:type attribute to StructuredSnippetAdExtension-->
          \<Header i:nil="false"></Header>
          \<Values i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </Values>
          \<!--Keep these fields if you set the i:type attribute to PriceAdExtension-->
          \<Language i:nil="false"></Language>
          <PriceExtensionType></PriceExtensionType>
          \<TableRows i:nil="false">
            <PriceTableRow>
              \<CurrencyCode i:nil="false"></CurrencyCode>
              \<Description i:nil="false"></Description>
              \<FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                \<a1:string>\</a1:string>
              </FinalMobileUrls>
              \<FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                \<a1:string>\</a1:string>
              </FinalUrls>
              \<Header i:nil="false"></Header>
              <Price></Price>
              <PriceQualifier></PriceQualifier>
              <PriceUnit></PriceUnit>
              \<TermsAndConditions i:nil="false"></TermsAndConditions>
              \<TermsAndConditionsUrl i:nil="false"></TermsAndConditionsUrl>
            </PriceTableRow>
          </TableRows>
          \<TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          \<UrlCustomParameters xmlns:e10="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e10:Parameters i:nil="false">
              \<e10:CustomParameter>
                \<e10:Key i:nil="false">\</e10:Key>
                \<e10:Value i:nil="false">\</e10:Value>
              \</e10:CustomParameter>
            \</e10:Parameters>
          </UrlCustomParameters>
        </AdExtension>
      </AdExtensions>
    </AddAdExtensionsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>AddAdExtensionsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdExtensionIdentities*|The identities of the extensions that were added. The list corresponds directly to the list of extensions specified in the request.|[AdExtensionIdentity](../campaign-api/adextensionidentity-data-object.md)|
|*NestedPartialErrors*|An array of [BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) objects that contain details for any ad extensions that were not successfully added. The top level error within each [BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) object corresponds to potential ad extension errors. The nested list of [BatchError](../campaign-api/batcherror-data-object.md) objects would include any errors specific to the list items within an ad extension (if applicable).<br/><br/>The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <AddAdExtensionsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<AdExtensionIdentities p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <AdExtensionIdentity>
          <Id></Id>
          \<Version p4:nil="false"></Version>
        </AdExtensionIdentity>
      </AdExtensionIdentities>
      \<NestedPartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchErrorCollection>
          \<BatchErrors p4:nil="false">
            \<BatchError p4:type="-- specify derived type here with the appropriate prefix --">
              <Code></Code>
              \<Details p4:nil="false"></Details>
              \<ErrorCode p4:nil="false"></ErrorCode>
              \<FieldPath p4:nil="false"></FieldPath>
              \<ForwardCompatibilityMap xmlns:e11="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
                \<e11:KeyValuePairOfstringstring>
                  \<e11:key p4:nil="false">\</e11:key>
                  \<e11:value p4:nil="false">\</e11:value>
                \</e11:KeyValuePairOfstringstring>
              </ForwardCompatibilityMap>
              <Index></Index>
              \<Message p4:nil="false"></Message>
              \<Type p4:nil="false"></Type>
              \<!--Keep these fields if you set the i:type attribute to EditorialError-->
              \<Appealable p4:nil="false"></Appealable>
              \<DisapprovedText p4:nil="false"></DisapprovedText>
              \<Location p4:nil="false"></Location>
              \<PublisherCountry p4:nil="false"></PublisherCountry>
              <ReasonCode></ReasonCode>
            </BatchError>
          </BatchErrors>
          \<Code p4:nil="false"></Code>
          \<Details p4:nil="false"></Details>
          \<ErrorCode p4:nil="false"></ErrorCode>
          \<FieldPath p4:nil="false"></FieldPath>
          \<ForwardCompatibilityMap xmlns:e12="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e12:KeyValuePairOfstringstring>
              \<e12:key p4:nil="false">\</e12:key>
              \<e12:value p4:nil="false">\</e12:value>
            \</e12:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          \<Message p4:nil="false"></Message>
          \<Type p4:nil="false"></Type>
        </BatchErrorCollection>
      </NestedPartialErrors>
    </AddAdExtensionsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteAdExtensions](../campaign-api/deleteadextensions-service-operation.md)  
[DeleteAdExtensionsAssociations](../campaign-api/deleteadextensionsassociations-service-operation.md)  
[GetAdExtensionIdsByAccountId](../campaign-api/getadextensionidsbyaccountid-service-operation.md)  
[GetAdExtensionsAssociations](../campaign-api/getadextensionsassociations-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[GetAdExtensionsEditorialReasons](../campaign-api/getadextensionseditorialreasons-service-operation.md)  
[SetAdExtensionsAssociations](../campaign-api/setadextensionsassociations-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  

