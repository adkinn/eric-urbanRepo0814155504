---
title: "GetAdExtensionsAssociations Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c972e9c-688a-4c72-8d19-41aeffaec383
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAdExtensionsAssociations Service Operation
Gets the respective ad extension associations by the specified campaign and ad group identifiers.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAdExtensionsAssociationsRequest Message

### Request Body
The *GetAdExtensionsAssociationsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AccountId*|The identifier of the account that owns the extensions.|*long*|Required|
|*AdExtensionType*|Filters the returned associations by ad extension type.|[AdExtensionsTypeFilter](../campaign-api/adextensionstypefilter-value-set.md)|Required|
|*AssociationType*|Filters the returned associations by entity type.|[AssociationType](../campaign-api/associationtype-value-set.md)|Required|
|*EntityIds*|The list of entity identifiers by which you may request the respective ad extension associations.|*long* array|Required|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The response does not contain additional body elements.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">GetAdExtensionsAssociations</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAdExtensionsAssociationsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      <AdExtensionType></AdExtensionType>
      <AssociationType></AssociationType>
      <EntityIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </EntityIds>
    </GetAdExtensionsAssociationsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAdExtensionsAssociationsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|AdExtensionAssociationCollection|An array of ad extension association collections.<br /><br />For each entity identifier specified in the request, an *AdExtensionAssociationCollection* is returned.|[AdExtensionAssociationCollection](../campaign-api/adextensionassociationcollection-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any associations that were not successfully retrieved.<br /><br />The list of errors corresponds directly to the list of associations in the request. Items of the list may be returned as null. For each list index where an association was successfully retrieved, the corresponding error element will be null. Ideally all associations are retrieved successfully and all elements in this list are null.|[BatchError](../campaign-api/batcherror-data-object.md) array|

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
    <GetAdExtensionsAssociationsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdExtensionAssociationCollection p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <AdExtensionAssociationCollection>
          <AdExtensionAssociations p4:nil="false">
            <AdExtensionAssociation>
              <AdExtension p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
                <DevicePreference p4:nil="false"></DevicePreference>
                <ForwardCompatibilityMap xmlns:e72="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
                  <e72:KeyValuePairOfstringstring>
                    <e72:key p4:nil="false"></e72:key>
                    <e72:value p4:nil="false"></e72:value>
                  </e72:KeyValuePairOfstringstring>
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
                    <FinalAppUrls xmlns:e73="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                      <e73:AppUrl>
                        <e73:OsType p4:nil="false"></e73:OsType>
                        <e73:Url p4:nil="false"></e73:Url>
                      </e73:AppUrl>
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
                    <UrlCustomParameters xmlns:e74="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                      <e74:Parameters p4:nil="false">
                        <e74:CustomParameter>
                          <e74:Key p4:nil="false"></e74:Key>
                          <e74:Value p4:nil="false"></e74:Value>
                        </e74:CustomParameter>
                      </e74:Parameters>
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
                <FinalAppUrls xmlns:e75="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                  <e75:AppUrl>
                    <e75:OsType p4:nil="false"></e75:OsType>
                    <e75:Url p4:nil="false"></e75:Url>
                  </e75:AppUrl>
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
                <UrlCustomParameters xmlns:e76="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                  <e76:Parameters p4:nil="false">
                    <e76:CustomParameter>
                      <e76:Key p4:nil="false"></e76:Key>
                      <e76:Value p4:nil="false"></e76:Value>
                    </e76:CustomParameter>
                  </e76:Parameters>
                </UrlCustomParameters>
                <!--Keep these fields if you set the i:type attribute to AppAdExtension-->
                <AppPlatform p4:nil="false"></AppPlatform>
                <AppStoreId p4:nil="false"></AppStoreId>
                <DestinationUrl p4:nil="false"></DestinationUrl>
                <DisplayText p4:nil="false"></DisplayText>
                <FinalAppUrls xmlns:e77="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                  <e77:AppUrl>
                    <e77:OsType p4:nil="false"></e77:OsType>
                    <e77:Url p4:nil="false"></e77:Url>
                  </e77:AppUrl>
                </FinalAppUrls>
                <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                  <a1:string></a1:string>
                </FinalMobileUrls>
                <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                  <a1:string></a1:string>
                </FinalUrls>
                <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
                <UrlCustomParameters xmlns:e78="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                  <e78:Parameters p4:nil="false">
                    <e78:CustomParameter>
                      <e78:Key p4:nil="false"></e78:Key>
                      <e78:Value p4:nil="false"></e78:Value>
                    </e78:CustomParameter>
                  </e78:Parameters>
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
                <FinalAppUrls xmlns:e79="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                  <e79:AppUrl>
                    <e79:OsType p4:nil="false"></e79:OsType>
                    <e79:Url p4:nil="false"></e79:Url>
                  </e79:AppUrl>
                </FinalAppUrls>
                <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                  <a1:string></a1:string>
                </FinalMobileUrls>
                <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
                  <a1:string></a1:string>
                </FinalUrls>
                <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
                <UrlCustomParameters xmlns:e80="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                  <e80:Parameters p4:nil="false">
                    <e80:CustomParameter>
                      <e80:Key p4:nil="false"></e80:Key>
                      <e80:Value p4:nil="false"></e80:Value>
                    </e80:CustomParameter>
                  </e80:Parameters>
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
                <UrlCustomParameters xmlns:e81="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
                  <e81:Parameters p4:nil="false">
                    <e81:CustomParameter>
                      <e81:Key p4:nil="false"></e81:Key>
                      <e81:Value p4:nil="false"></e81:Value>
                    </e81:CustomParameter>
                  </e81:Parameters>
                </UrlCustomParameters>
              </AdExtension>
              <AssociationType></AssociationType>
              <EditorialStatus p4:nil="false"></EditorialStatus>
              <EntityId></EntityId>
            </AdExtensionAssociation>
          </AdExtensionAssociations>
        </AdExtensionAssociationCollection>
      </AdExtensionAssociationCollection>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e82="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e82:KeyValuePairOfstringstring>
              <e82:key p4:nil="false"></e82:key>
              <e82:value p4:nil="false"></e82:value>
            </e82:KeyValuePairOfstringstring>
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
    </GetAdExtensionsAssociationsResponse>
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
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[GetAdExtensionsEditorialReasons](../campaign-api/getadextensionseditorialreasons-service-operation.md)  
[SetAdExtensionsAssociations](../campaign-api/setadextensionsassociations-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  

