---
title: "Error Codes and Messages"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a599474b-6a17-43dc-abe9-695a9d834744
caps.latest.revision: 5
author: "eric-urban"
ms.author: "scottwhi"
---
# Error Codes and Messages
When you send Bing your transaction message to process, Bing may return one of the following HTTP status codes:

|Status Code|Description
|-|-
|200|Success. Bing successfully queued the message to be processed.
|401|Unauthorized. The message was sent from an IP address that is unknown to Bing or that is not associated with you. The IP address that you send the message from must be an IP address of a server that you provided to Bing prior to sending the message. Contact your TAM to ensure that your list is up to date.
|413|Request entity too large. The transaction message must not exceed 100 MB or 10 MB compressed.
|429|Too many requests. You may have a maximum of five requests queued or being processed at the same time. If you send a sixth request at this time, Bing returns this error. 
|500|Internal server error. This is typically a transient error. Retry the request at 1, 5, and 20 minute intervals. If the request fails after the third attempt, contact your TAM with the following information:<br /><br /><ul><li>CustomerID</li><li>Date and time that the errors occurred.</li><li>The ID in the WebRequestActivityId response header.</li></ul>

## Response body
  
If an HTTP error occurs, the body of the response contains an XML document that contains a description of the error.

```xml
<ArrayOfApiError xmlns="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.BHAC.HotelAdsAPIs.Models" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <ApiError>
    <Code>IPAddressNotAllowed</Code>
    <Message>Customer 4 is not authorized to use IP address 167.220.24.77.</Message>
    \<Property i:nil="true"/>
  </ApiError>
</ArrayOfApiError>
```

The following tables describe the elements found in the error response.

### Error Response
Defines the top-level element of an error response.

|Element|Description|Children
|-|-|-
|ArrayOfApiError|The top-level element of an error response. This element contains a list of errors that occurred.|Array of [ApiError](#apierror)

<a name="apierror" />
### ApiError
Defines an error that occurred.

|Element|Description|Children
|-|-|-
|Code|A code that identifies the error that occurred. For example, IPAddressNotAllowed.|None
|Message|A message that describes the error that occurred.|None
|Property|The name of the property that caused the error. If the error is not related to a property, the element's `nil` attribute is set to **true**.|None

## Codes and messages

The following lists the error codes and messages that the API returns.

|Code|Message
|-|-
|AuthenticationFailure|Authentication failed for unknown reasons.
|InternalError|Internal server error.<br /><br />This is typically a transient error. Retry the request at 1, 5, and 20 minute intervals. If the request fails after the third attempt, contact your TAM with the following information:<br /><br /><ul><li>CustomerID</li><li>Date and time that the errors occurred.</li><li>The ID in the WebRequestActivityId response header.</li></ul>
|IPAddressNotAllowed|Customer {custId} is not authorized to use IP address {clientIp}.<br /><br />The customer is not authorized to send transaction messages from the IP address. You must send the request from an authorized server IP address. Contact your TAM to update your list of authorized server IP addresses.
|RequestThrottled|Customer {customerId} exceeded the number of requests allowed.<br /><br />Customers may have a maximum of five requests queued or being processed. Sending a sixth request in this case will fail. 
|RequestTooLarge|The request size ({requestSizeBytes} bytes) exceeds the maximum allowed ({maxAllowed} bytes).<br /><br /> The transaction message cannot exceed 100 MB or 10 MB compressed. Reduce the size of your transaction message to fit within the limits.
