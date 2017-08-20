---
title: "ClientLinkStatus Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdd8a509-9bc2-4628-85a8-dd7255fafeea
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ClientLinkStatus Value Set
Defines the possible status values of a [ClientLink](../customer-api/clientlink-data-object.md).

For more information about the client link lifecycle, see [Link to Client Accounts](https://msdn.microsoft.com/library/bing-ads-agency-management-model-guide.aspx#clientlink).

## Syntax

```xml
<xs:simpleType name="ClientLinkStatus">
      <xs:restriction base="xs:string">
      <xs:enumeration value="LinkPending" />
      <xs:enumeration value="LinkCanceled" />
      <xs:enumeration value="LinkExpired" />
      <xs:enumeration value="LinkAccepted" />
      <xs:enumeration value="LinkDeclined" />
      <xs:enumeration value="LinkInProgress" />
      <xs:enumeration value="Active" />
      <xs:enumeration value="LinkFailed" />
      <xs:enumeration value="UnlinkRequested" />
      <xs:enumeration value="UnlinkPending" />
      <xs:enumeration value="UnlinkCanceled" />
      <xs:enumeration value="UnlinkInProgress" />
      <xs:enumeration value="Inactive" />
      <xs:enumeration value="UnlinkFailed" />
      </xs:restriction>
      </xs:simpleType>
```

## Values

|Value|Description|Read or Write Permissions|
|---------|---------------|-----------------------------|
|Active|The link is established and the managing customer can access the client account.<br /><br />The previous status was LinkInProgress.|Read-only|
|Inactive|The unlink process has completed and the managing customer can no longer access the client account.<br /><br />The previous status was UnlinkInProgress.|Read-only|
|LinkAccepted|The invited client should use this value to accept the link invitation.<br /><br />The previous status was LinkPending.|Read and write are both supported.<br /><br />Only the invited client may set this status, and then on the client link start date the service sets the effective status to LinkInProgress.|
|LinkCanceled|The link request has been canceled by the agency.<br /><br />The previous status was LinkPending.|Read and write are both supported.<br /><br />Only the agency may set this status.|
|LinkDeclined|The link request has been declined by the invited client.<br /><br />The previous status was LinkPending.|Read and write are both supported.<br /><br />Only the invited client may set this status.|
|LinkExpired|The link is inactive due to expiry. The client did not accept or decline the request within 30 days.<br /><br />The previous status was LinkPending.|Read-only|
|LinkFailed|The link process failed to complete successfully.<br /><br />The previous status was LinkInProgress.|Read-only|
|LinkInProgress|The link process is in progress and either waiting for the billing transition to complete or the specified client link start date has not yet arrived.<br /><br />The previous readable status was LinkPending, and the previous write-only status set by the client was LinkAccepted.|Read-only|
|LinkPending|The [ClientLink](../customer-api/clientlink-data-object.md) has been added via the [AddClientLinks](../customer-api/addclientlinks-service-operation.md) operation. The link request has been sent and is pending approval from the client.|Read-only|
|UnlinkCanceled|Reserved for future use.|Not applicable.|
|UnlinkFailed|The unlink process failed to complete successfully, for example because the billing transition could not be completed.<br /><br />The previous status was UnlinkInProgress.|Write-only<br /><br />Only the system can set this status value if the unlink process fails, which resumes the Active status.|
|UnlinkInProgress|The unlink process is in progress and waiting for the billing transition to complete.<br /><br />The previous status was UnlinkPending.|Read-only|
|UnlinkPending|A request to terminate the link has been sent. The request is waiting for the system to begin the unlink progress.<br /><br />The previous status was Active, and the next status will be UnlinkInProgress.|Read-only|
|UnlinkRequested|The agency should use this value to request an unlink.<br /><br />The previous status was Active.|Write-only<br /><br />Only an agency can set this status, and then the service sets the effective status to UnlinkPending.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[ClientLink](../customer-api/clientlink-data-object.md)  
[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)  
[UpdateClientLinks](../customer-api/updateclientlinks-service-operation.md)  

