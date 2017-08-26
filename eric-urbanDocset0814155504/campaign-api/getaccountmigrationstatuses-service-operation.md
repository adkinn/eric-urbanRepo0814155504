---
title: "GetAccountMigrationStatuses Service Operation"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4f3711d-24b4-4aa6-9c56-bb694650ba8a
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAccountMigrationStatuses Service Operation
Gets the migration status info for the specified accounts.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAccountMigrationStatusesRequest Message

### Request Body
The *GetAccountMigrationStatusesRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountIds*|The identifiers of each account to request migration status.<br/><br/>**Required**: Yes|*long* array|
|*MigrationType*|Filters the returned migration status by migration type.<br/><br/>Currently the only supported migration type is *SiteLinkAdExtension*.<br/><br/>**Note:** [!INCLUDE[sitelinks_migration_eta](../campaign-api/includes/sitelinks-migration-eta.md)]<br/><br/>**Required**: Yes|*string*|


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
    <Action mustUnderstand="1">GetAccountMigrationStatuses</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAccountMigrationStatusesRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </AccountIds>
      <MigrationType i:nil="false"></MigrationType>
    </GetAccountMigrationStatusesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAccountMigrationStatusesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MigrationStatuses*|An array of account migration statuses.<br /><br />For each account identifier specified in the request, an *AccountMigrationStatusesInfo* object is returned.|[AccountMigrationStatusesInfo](../campaign-api/accountmigrationstatusesinfo-data-object.md) array|


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
    <GetAccountMigrationStatusesResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <MigrationStatuses p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <AccountMigrationStatusesInfo>
          <AccountId></AccountId>
          <MigrationStatusInfo p4:nil="false">
            <MigrationStatusInfo>
              <MigrationType p4:nil="false"></MigrationType>
              <StartTimeInUtc p4:nil="false"></StartTimeInUtc>
              <Status></Status>
            </MigrationStatusInfo>
          </MigrationStatusInfo>
        </AccountMigrationStatusesInfo>
      </MigrationStatuses>
    </GetAccountMigrationStatusesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AccountMigrationStatusesInfo](../campaign-api/accountmigrationstatusesinfo-data-object.md)  
[MigrationStatusInfo](../campaign-api/migrationstatusinfo-data-object.md)  
