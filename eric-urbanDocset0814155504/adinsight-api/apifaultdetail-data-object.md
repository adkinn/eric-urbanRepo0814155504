---
title: "ApiFaultDetail Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d278e37-93ef-4e25-9dbc-355f3e307431
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ApiFaultDetail Data Object
Defines a fault object that operations return when web service-specific errors occur, such as when the request message contains incomplete or invalid data.

## Syntax

```xml
\<xs:complexType name="ApiFaultDetail">
  \<xs:complexContent mixed="false">
    \<xs:extension xmlns:q4="https://adapi.microsoft.com" base="q4:ApplicationFault">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="BatchErrors" nillable="true" type="tns:ArrayOfBatchError" />
        \<xs:element minOccurs="0" name="OperationErrors" nillable="true" type="tns:ArrayOfOperationError" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *ApiFaultDetail* object inherits elements from the [ApplicationFault](../adinsight-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BatchErrors*|An array of batch errors that identifies the items in the batch of items in the request message that caused the operation to fail. Each object contains the details that explain why the item caused the failure.|[BatchError](../adinsight-api/batcherror-data-object.md) array|
|*OperationErrors*|An array of operation errors that contains the reasons that explain why the service operation failed when the error is not related to a specific item in the batch of items.|[OperationError](../adinsight-api/operationerror-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The *ApiFaultDetail* object inherits the following element from the [ApplicationFault](../adinsight-api/applicationfault-data-object.md) object. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)  

