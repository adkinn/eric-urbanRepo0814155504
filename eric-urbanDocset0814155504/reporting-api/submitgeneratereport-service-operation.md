---
title: "SubmitGenerateReport Service Operation"
ms.custom: ""
ms.date: "05/23/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d989277-fab3-429c-b888-752b7707aa9b
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SubmitGenerateReport Service Operation
Submits a report request.

> [!NOTE]
> You must use the same user credentials for the [SubmitGenerateReport](../reporting-api/submitgeneratereport-service-operation.md) and [PollGenerateReport](../reporting-api/pollgeneratereport-service-operation.md).

[!INCLUDE[reporting_service_namespace](../reporting-api/includes/reporting-service-namespace.md)]

## <a name="request"></a>SubmitGenerateReportRequest Message

### Request Body
The *SubmitGenerateReportRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ReportRequest*|The report request. The request must be an object that derives from [ReportRequest](../reporting-api/reportrequest-data-object.md). For a list of report request types, see [Report Types](http://go.microsoft.com/fwlink/?LinkId=691016).|[ReportRequest](../reporting-api/reportrequest-data-object.md)-derived object|

### Request Headers
[!INCLUDE[header_intro](../reporting-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[rep_header_oauth](../reporting-api/includes/rep-header-oauth.md)]
#### Password Authentication
[!INCLUDE[rep_header_password](../reporting-api/includes/rep-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Reporting/v11">
    <Action mustUnderstand="1">SubmitGenerateReport</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SubmitGenerateReportRequest xmlns="https://bingads.microsoft.com/Reporting/v11">
      <ReportRequest i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
        <ExcludeColumnHeaders i:nil="false"></ExcludeColumnHeaders>
        <ExcludeReportFooter i:nil="false"></ExcludeReportFooter>
        <ExcludeReportHeader i:nil="false"></ExcludeReportHeader>
        <Format i:nil="false"></Format>
        <Language i:nil="false"></Language>
        <ReportName i:nil="false"></ReportName>
        <ReturnOnlyCompleteData i:nil="false"></ReturnOnlyCompleteData>
        <!--Keep these fields if you set the i:type attribute to AccountPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AccountPerformanceReportColumn></AccountPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <DeviceOS i:nil="false"></DeviceOS>
          <DeviceType i:nil="false"></DeviceType>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to CampaignPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <CampaignPerformanceReportColumn></CampaignPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <DeviceOS i:nil="false"></DeviceOS>
          <DeviceType i:nil="false"></DeviceType>
          <Status i:nil="false"></Status>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to AdDynamicTextPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AdDynamicTextPerformanceReportColumn></AdDynamicTextPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <AdType i:nil="false"></AdType>
          <DeviceType i:nil="false"></DeviceType>
          <KeywordStatus i:nil="false"></KeywordStatus>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to AdGroupPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AdGroupPerformanceReportColumn></AdGroupPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceOS i:nil="false"></DeviceOS>
          <DeviceType i:nil="false"></DeviceType>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
          <Status i:nil="false"></Status>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to AdPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AdPerformanceReportColumn></AdPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <AdType i:nil="false"></AdType>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceType i:nil="false"></DeviceType>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to KeywordPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <KeywordPerformanceReportColumn></KeywordPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdRelevance i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:int></a1:int>
          </AdRelevance>
          <AdType i:nil="false"></AdType>
          <BidMatchType i:nil="false"></BidMatchType>
          <BidStrategyType i:nil="false"></BidStrategyType>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeliveredMatchType i:nil="false"></DeliveredMatchType>
          <DeviceType i:nil="false"></DeviceType>
          <ExpectedCtr i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:int></a1:int>
          </ExpectedCtr>
          <KeywordStatus i:nil="false"></KeywordStatus>
          <Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </Keywords>
          <LandingPageExperience i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:int></a1:int>
          </LandingPageExperience>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
          <QualityScore i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:int></a1:int>
          </QualityScore>
        </Filter>
        <MaxRows></MaxRows>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Sort i:nil="false">
          <KeywordPerformanceReportSort>
            <SortColumn></SortColumn>
            <SortOrder></SortOrder>
          </KeywordPerformanceReportSort>
        </Sort>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to DestinationUrlPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <DestinationUrlPerformanceReportColumn></DestinationUrlPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceType i:nil="false"></DeviceType>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to BudgetSummaryReportRequest-->
        <Columns i:nil="false">
          <BudgetSummaryReportColumn></BudgetSummaryReportColumn>
        </Columns>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to AgeGenderDemographicReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AgeGenderDemographicReportColumn></AgeGenderDemographicReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to UserLocationPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <UserLocationPerformanceReportColumn></UserLocationPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AdDistribution i:nil="false"></AdDistribution>
          <CountryCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </CountryCode>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to PublisherUsagePerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <PublisherUsagePerformanceReportColumn></PublisherUsagePerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to SearchQueryPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <SearchQueryPerformanceReportColumn></SearchQueryPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <AdType i:nil="false"></AdType>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeliveredMatchType i:nil="false"></DeliveredMatchType>
          <ExcludeZeroClicks></ExcludeZeroClicks>
          <KeywordStatus i:nil="false"></KeywordStatus>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
          <SearchQueries i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </SearchQueries>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to ConversionPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <ConversionPerformanceReportColumn></ConversionPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceType i:nil="false"></DeviceType>
          <KeywordStatus i:nil="false"></KeywordStatus>
          <Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </Keywords>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to GoalsAndFunnelsReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <GoalsAndFunnelsReportColumn></GoalsAndFunnelsReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceOS i:nil="false"></DeviceOS>
          <DeviceType i:nil="false"></DeviceType>
          <GoalIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </GoalIds>
          <KeywordStatus i:nil="false"></KeywordStatus>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to NegativeKeywordConflictReportRequest-->
        <Columns i:nil="false">
          <NegativeKeywordConflictReportColumn></NegativeKeywordConflictReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <KeywordStatus i:nil="false"></KeywordStatus>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <!--Keep these fields if you set the i:type attribute to SearchCampaignChangeHistoryReportRequest-->
        <Columns i:nil="false">
          <SearchCampaignChangeHistoryReportColumn></SearchCampaignChangeHistoryReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AdDistribution i:nil="false"></AdDistribution>
          <HowChanged i:nil="false"></HowChanged>
          <ItemChanged i:nil="false"></ItemChanged>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to AdExtensionByAdReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AdExtensionByAdReportColumn></AdExtensionByAdReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceOS i:nil="false"></DeviceOS>
          <DeviceType i:nil="false"></DeviceType>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to AdExtensionByKeywordReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AdExtensionByKeywordReportColumn></AdExtensionByKeywordReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceOS i:nil="false"></DeviceOS>
          <DeviceType i:nil="false"></DeviceType>
          <KeywordStatus i:nil="false"></KeywordStatus>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to AudiencePerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AudiencePerformanceReportColumn></AudiencePerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to AdExtensionDetailReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <AdExtensionDetailReportColumn></AdExtensionDetailReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceOS i:nil="false"></DeviceOS>
          <DeviceType i:nil="false"></DeviceType>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to ShareOfVoiceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <ShareOfVoiceReportColumn></ShareOfVoiceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <BidMatchType i:nil="false"></BidMatchType>
          <BidStrategyType i:nil="false"></BidStrategyType>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeliveredMatchType i:nil="false"></DeliveredMatchType>
          <DeviceType i:nil="false"></DeviceType>
          <KeywordStatus i:nil="false"></KeywordStatus>
          <Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </Keywords>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to ProductDimensionPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <ProductDimensionPerformanceReportColumn></ProductDimensionPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceType i:nil="false"></DeviceType>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to ProductPartitionPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <ProductPartitionPerformanceReportColumn></ProductPartitionPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceType i:nil="false"></DeviceType>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to ProductPartitionUnitPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <ProductPartitionUnitPerformanceReportColumn></ProductPartitionUnitPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <AdStatus i:nil="false"></AdStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <DeviceType i:nil="false"></DeviceType>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to CallDetailReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <CallDetailReportColumn></CallDetailReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
        <!--Keep these fields if you set the i:type attribute to GeographicPerformanceReportRequest-->
        <Aggregation></Aggregation>
        <Columns i:nil="false">
          <GeographicPerformanceReportColumn></GeographicPerformanceReportColumn>
        </Columns>
        <Filter i:nil="false">
          <AccountStatus i:nil="false"></AccountStatus>
          <AdDistribution i:nil="false"></AdDistribution>
          <AdGroupStatus i:nil="false"></AdGroupStatus>
          <CampaignStatus i:nil="false"></CampaignStatus>
          <CountryCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </CountryCode>
          <LanguageCode i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </LanguageCode>
        </Filter>
        <Scope i:nil="false">
          <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:long></a1:long>
          </AccountIds>
          <AdGroups i:nil="false">
            <AdGroupReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
              <AdGroupId></AdGroupId>
            </AdGroupReportScope>
          </AdGroups>
          <Campaigns i:nil="false">
            <CampaignReportScope>
              <AccountId></AccountId>
              <CampaignId></CampaignId>
            </CampaignReportScope>
          </Campaigns>
        </Scope>
        <Time i:nil="false">
          <CustomDateRangeEnd i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeEnd>
          <CustomDateRangeStart i:nil="false">
            <Day></Day>
            <Month></Month>
            <Year></Year>
          </CustomDateRangeStart>
          <PredefinedTime i:nil="false"></PredefinedTime>
        </Time>
      </ReportRequest>
    </SubmitGenerateReportRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SubmitGenerateReportResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ReportRequestId*|The identifier of the report request. Use this identifier when calling the [PollGenerateReport](../reporting-api/pollgeneratereport-service-operation.md) to determine the status of the report request. Once returned, the identifier is valid for two days.<br /><br />The *string* has a length up to 40 and can contain any character.|*string*|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[reporting_response_header_table](../reporting-api/includes/reporting-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Reporting/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <SubmitGenerateReportResponse xmlns="https://bingads.microsoft.com/Reporting/v11">
      <ReportRequestId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></ReportRequestId>
    </SubmitGenerateReportResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[reperror](../reporting-api/includes/reperror.md)]The following are example error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|ReportingServiceNullReportRequest|
|ReportingServiceUnknownReportType|
|ReportingServiceAccountNotAuthorized|
|ReportingServiceNoCompleteDataAvaliable|
|ReportingServiceInvalidDataAvailabilityAndTimePeriodCombination|
|ReportingServiceInvalidReportName|
|ReportingServiceInvalidReportAggregation|
|ReportingServiceInvalidReportTimeSelection|
|ReportingServiceInvalidCustomDateRangeStart|
|ReportingServiceInvalidCustomDateRangeEnd|
|ReportingServiceEndDateBeforeStartDate|
|ReportingServiceEmptyCustomDates|
|ReportingServiceCustomDatesOverlimit|
|ReportingServiceNullColumns|
|ReportingServiceRequiredColumnsNotSelected|
|ReportingServiceDuplicateColumns|
|ReportingServiceNoMeasureSelected|
|ReportingServiceInvalidAccountIdInCampaignReportScope|
|ReportingServiceInvalidCampaignIdInCampaignReportScope|
|ReportingServiceInvalidAccountIdInAdGroupReportScope|
|ReportingServiceInvalidCampaignIdInAdGroupReportScope|
|ReportingServiceInvalidAdGroupIdInAdGroupReportScope|
|ReportingServiceInvalidAccountIdInAccountReportScope|
|ReportingServiceNullCampaignReportScope|
|ReportingServiceNullAdGroupReportScope|
|ReportingServiceInvalidAccountReportScope|
|ReportingServiceInvalidAccountThruCampaignReportScope|
|ReportingServiceInvalidAccountThruAdGroupReportScope|
|ReportingServiceAccountsOverLimit|
|ReportingServiceMaximumCampaignsLimitReached|
|ReportingServiceAdGroupsOverLimit|
|ReportingServiceCrossSiteScriptNotAllowed|
|ReportingServiceInvalidKeywordFilterValue|
|ReportingServiceInvalidTimePeriodColumnForSummaryReport|
|ReportingServiceInvalidAccountIds|
|ReportingServiceSiteIdMaxArraySizeReached|
|ReportingServiceInvalidSiteIdValue|
|ReportingServiceInvalidCustomDateRange|
|ReportingServiceInvalidFutureStartDate|
|ReportingServiceInvalidSearchQueryFilterValue|
|ReportingServiceSearchQueryFilterValueLengthExceeded|
|ReportingServiceSearchQueryOverLimit|
|ReportingServiceKeywordFilterValueLengthExceeded|
|ReportingServiceKeywordOverLimit|
|ReportingServiceGoalIdMaxArraySizeReached|
|ReportingServiceTacticIdMaxArraySizeReached|
|ReportingServiceChannelIdMaxArraySizeReached|
|ReportingServiceThirdPartyCampaignIdMaxArraySizeReached|
|ReportingServiceThirdPartyAdGroupIdMaxArraySizeReached|
|ReportingServiceInvalidGrainForQualityScoreColumns|
|ReportingServiceInvalidGrainForImpressionShareColumns|
|ReportingServiceInvalidGrainForHistoricQualityScoreColumns|
|ReportingServiceFilterValueBatchSizeOverLimit|
|ReportingServiceFilterValueOverLimit|
|UnsuportedTimeGrain|
|InvalidFilterOrScopeValue|

## See Also
[PollGenerateReport](../reporting-api/pollgeneratereport-service-operation.md)  
[Request and Download a Report](https://msdn.microsoft.com/library/bing-ads-reporting-request-and-download-a-report.aspx)  

