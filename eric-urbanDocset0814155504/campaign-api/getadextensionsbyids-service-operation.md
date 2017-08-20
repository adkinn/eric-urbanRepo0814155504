---
title: "GetAdExtensionsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 487f54cc-83d2-41b7-87f4-cdf7d3a0b397
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAdExtensionsByIds Service Operation
Gets the specified ad extensions from the account’s ad extension library.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAdExtensionsByIdsRequest Message

### Request Body
The *GetAdExtensionsByIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AccountId*|The identifier of the account that owns the ad extensions.|*long*|Required|
|*AdExtensionIds*|A list of ad extension identifiers. You can specify a maximum of 100 identifiers.|*long* array|Required|
|*AdExtensionType*|The types of ad extensions that the list of identifiers contains.|[AdExtensionsTypeFilter](../campaign-api/adextensionstypefilter-value-set.md)|Required|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">GetAdExtensionsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAdExtensionsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      <AdExtensionIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </AdExtensionIds>
      <AdExtensionType></AdExtensionType>
    </GetAdExtensionsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAdExtensionsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdExtensions*|A list of [AdExtension](../campaign-api/adextension-data-object.md) objects. The list corresponds directly to the list of identifiers in the request. If an ad extension ID in the request is not valid or the extension is not of the type specified, the corresponding item in this list is null.|[AdExtension](../campaign-api/adextension-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetAdExtensionsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdExtensions p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <AdExtension p4:type="-- specify derived type here with the appropriate prefix --">
          <DevicePreference p4:nil="false"></DevicePreference>
          <ForwardCompatibilityMap xmlns:e83="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e83:KeyValuePairOfstringstring>
              <e83:key p4:nil="false"></e83:key>
              <e83:value p4:nil="false"></e83:value>
            </e83:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <Scheduling p4:nil="false">
            <DayTimeRanges p4:nil="false">
              <DayTime>
                <Day></Day>
                <EndHour></EndHour>
                <EndMinute></EndMinute>
                <StartHour></StartHour>
                <StartMinute></StartMinute>
              </DayTime>
            </DayTimeRanges>
            <EndDate p4:nil="false">
              <Day></Day>
              <Month></Month>
              <Year></Year>
            </EndDate>
            <StartDate p4:nil="false">
              <Day></Day>
              <Month></Month>
              <Year></Year>
            </StartDate>
            <UseSearcherTimeZone p4:nil="false"></UseSearcherTimeZone>
          </Scheduling>
          <Status p4:nil="false"></Status>
          <Type p4:nil="false"></Type>
          <Version p4:nil="false"></Version>
          <!--Keep these fields if you set the i:type attribute to SiteLinksAdExtension-->
          <SiteLinks p4:nil="false">
            <SiteLink>
              <Description1 p4:nil="false"></Description1>
              <Description2 p4:nil="false"></Description2>
              <DestinationUrl p4:nil="false"></DestinationUrl>
              <DevicePreference p4:nil="false"></DevicePreference>
              <DisplayText p4:nil="false"></DisplayText>
              <FinalAppUrls xmlns:e84="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                <e84:AppUrl>
                  <e84:OsType p4:nil="false"></e84:OsType>
                  <e84:Url p4:nil="false"></e84:Url>
                </e84:AppUrl>
              </FinalAppUrls>
              <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                <a1:string></a1:string>
              </FinalMobileUrls>
              <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                <a1:string></a1:string>
              </FinalUrls>
              <Scheduling p4:nil="false">
                <DayTimeRanges p4:nil="false">
                  <DayTime>
                    <Day></Day>
                    <EndHour></EndHour>
                    <EndMinute></EndMinute>
                    <StartHour></StartHour>
                    <StartMinute></StartMinute>
                  </DayTime>
                </DayTimeRanges>
                <EndDate p4:nil="false">
                  <Day></Day>
                  <Month></Month>
                  <Year></Year>
                </EndDate>
                <StartDate p4:nil="false">
                  <Day></Day>
                  <Month></Month>
                  <Year></Year>
                </StartDate>
                <UseSearcherTimeZone p4:nil="false"></UseSearcherTimeZone>
              </Scheduling>
              <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
              <UrlCustomParameters xmlns:e85="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                <e85:Parameters p4:nil="false">
                  <e85:CustomParameter>
                    <e85:Key p4:nil="false"></e85:Key>
                    <e85:Value p4:nil="false"></e85:Value>
                  </e85:CustomParameter>
                </e85:Parameters>
              </UrlCustomParameters>
            </SiteLink>
          </SiteLinks>
          <!--Keep these fields if you set the i:type attribute to LocationAdExtension-->
          <Address p4:nil="false">
            <CityName p4:nil="false"></CityName>
            <CountryCode p4:nil="false"></CountryCode>
            <PostalCode p4:nil="false"></PostalCode>
            <ProvinceCode p4:nil="false"></ProvinceCode>
            <ProvinceName p4:nil="false"></ProvinceName>
            <StreetAddress p4:nil="false"></StreetAddress>
            <StreetAddress2 p4:nil="false"></StreetAddress2>
          </Address>
          <CompanyName p4:nil="false"></CompanyName>
          <GeoCodeStatus p4:nil="false"></GeoCodeStatus>
          <GeoPoint p4:nil="false">
            <LatitudeInMicroDegrees></LatitudeInMicroDegrees>
            <LongitudeInMicroDegrees></LongitudeInMicroDegrees>
          </GeoPoint>
          <IconMediaId p4:nil="false"></IconMediaId>
          <ImageMediaId p4:nil="false"></ImageMediaId>
          <PhoneNumber p4:nil="false"></PhoneNumber>
          <!--Keep these fields if you set the i:type attribute to CallAdExtension-->
          <CountryCode p4:nil="false"></CountryCode>
          <IsCallOnly p4:nil="false"></IsCallOnly>
          <IsCallTrackingEnabled p4:nil="false"></IsCallTrackingEnabled>
          <PhoneNumber p4:nil="false"></PhoneNumber>
          <RequireTollFreeTrackingNumber p4:nil="false"></RequireTollFreeTrackingNumber>
          <!--Keep these fields if you set the i:type attribute to ImageAdExtension-->
          <AlternativeText p4:nil="false"></AlternativeText>
          <Description p4:nil="false"></Description>
          <DestinationUrl p4:nil="false"></DestinationUrl>
          <FinalAppUrls xmlns:e86="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e86:AppUrl>
              <e86:OsType p4:nil="false"></e86:OsType>
              <e86:Url p4:nil="false"></e86:Url>
            </e86:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <ImageMediaIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </ImageMediaIds>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e87="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e87:Parameters p4:nil="false">
              <e87:CustomParameter>
                <e87:Key p4:nil="false"></e87:Key>
                <e87:Value p4:nil="false"></e87:Value>
              </e87:CustomParameter>
            </e87:Parameters>
          </UrlCustomParameters>
          <!--Keep these fields if you set the i:type attribute to AppAdExtension-->
          <AppPlatform p4:nil="false"></AppPlatform>
          <AppStoreId p4:nil="false"></AppStoreId>
          <DestinationUrl p4:nil="false"></DestinationUrl>
          <DisplayText p4:nil="false"></DisplayText>
          <FinalAppUrls xmlns:e88="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e88:AppUrl>
              <e88:OsType p4:nil="false"></e88:OsType>
              <e88:Url p4:nil="false"></e88:Url>
            </e88:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e89="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e89:Parameters p4:nil="false">
              <e89:CustomParameter>
                <e89:Key p4:nil="false"></e89:Key>
                <e89:Value p4:nil="false"></e89:Value>
              </e89:CustomParameter>
            </e89:Parameters>
          </UrlCustomParameters>
          <!--Keep these fields if you set the i:type attribute to ReviewAdExtension-->
          <IsExact></IsExact>
          <Source p4:nil="false"></Source>
          <Text p4:nil="false"></Text>
          <Url p4:nil="false"></Url>
          <!--Keep these fields if you set the i:type attribute to CalloutAdExtension-->
          <Text p4:nil="false"></Text>
          <!--Keep these fields if you set the i:type attribute to Sitelink2AdExtension-->
          <Description1 p4:nil="false"></Description1>
          <Description2 p4:nil="false"></Description2>
          <DestinationUrl p4:nil="false"></DestinationUrl>
          <DisplayText p4:nil="false"></DisplayText>
          <FinalAppUrls xmlns:e90="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e90:AppUrl>
              <e90:OsType p4:nil="false"></e90:OsType>
              <e90:Url p4:nil="false"></e90:Url>
            </e90:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e91="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e91:Parameters p4:nil="false">
              <e91:CustomParameter>
                <e91:Key p4:nil="false"></e91:Key>
                <e91:Value p4:nil="false"></e91:Value>
              </e91:CustomParameter>
            </e91:Parameters>
          </UrlCustomParameters>
          <!--Keep these fields if you set the i:type attribute to StructuredSnippetAdExtension-->
          <Header p4:nil="false"></Header>
          <Values p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </Values>
          <!--Keep these fields if you set the i:type attribute to PriceAdExtension-->
          <Language p4:nil="false"></Language>
          <PriceExtensionType></PriceExtensionType>
          <TableRows p4:nil="false">
            <PriceTableRow>
              <CurrencyCode p4:nil="false"></CurrencyCode>
              <Description p4:nil="false"></Description>
              <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                <a1:string></a1:string>
              </FinalMobileUrls>
              <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                <a1:string></a1:string>
              </FinalUrls>
              <Header p4:nil="false"></Header>
              <Price></Price>
              <PriceQualifier></PriceQualifier>
              <PriceUnit></PriceUnit>
              <TermsAndConditions p4:nil="false"></TermsAndConditions>
              <TermsAndConditionsUrl p4:nil="false"></TermsAndConditionsUrl>
            </PriceTableRow>
          </TableRows>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e92="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e92:Parameters p4:nil="false">
              <e92:CustomParameter>
                <e92:Key p4:nil="false"></e92:Key>
                <e92:Value p4:nil="false"></e92:Value>
              </e92:CustomParameter>
            </e92:Parameters>
          </UrlCustomParameters>
        </AdExtension>
      </AdExtensions>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e93="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e93:KeyValuePairOfstringstring>
              <e93:key p4:nil="false"></e93:key>
              <e93:value p4:nil="false"></e93:value>
            </e93:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          <Message p4:nil="false"></Message>
          <Type p4:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to EditorialError-->
          <Appealable p4:nil="false"></Appealable>
          <DisapprovedText p4:nil="false"></DisapprovedText>
          <Location p4:nil="false"></Location>
          <PublisherCountry p4:nil="false"></PublisherCountry>
          <ReasonCode></ReasonCode>
        </BatchError>
      </PartialErrors>
    </GetAdExtensionsByIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[DeleteAdExtensions](../campaign-api/deleteadextensions-service-operation.md)  
[DeleteAdExtensionsAssociations](../campaign-api/deleteadextensionsassociations-service-operation.md)  
[GetAdExtensionIdsByAccountId](../campaign-api/getadextensionidsbyaccountid-service-operation.md)  
[GetAdExtensionsAssociations](../campaign-api/getadextensionsassociations-service-operation.md)  
[GetAdExtensionsEditorialReasons](../campaign-api/getadextensionseditorialreasons-service-operation.md)  
[SetAdExtensionsAssociations](../campaign-api/setadextensionsassociations-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  

