---
title: "AdApiFaultDetail Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e323910-37c9-4365-9033-b30c6c34af7d
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdApiFaultDetail Data Object
Defines a fault object that operations return when generic errors occur, such as an authentication error.

## Syntax

```xml
\<xs:complexType name="AdApiFaultDetail">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:ApplicationFault">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="Errors" nillable="true" type="tns:ArrayOfAdApiError" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *AdApiFaultDetail* object derives from the [ApplicationFault](../reporting-api/applicationfault-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Errors*|An array of [AdApiError](../reporting-api/adapierror-data-object.md) objects that contains the details that explain why the service operation failed.|[AdApiError](../reporting-api/adapierror-data-object.md) array|

## <a name="InheritedElements"></a>Inherited Elements
The *AdApiFaultDetail* object derives from the [ApplicationFault](../reporting-api/applicationfault-data-object.md) object, and inherits the following element. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*TrackingId*|The identifier of the log entry that contains the details of the API call.|*string*|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[Handling Service Errors and Exceptions](https://msdn.microsoft.com/library/bing-ads-error-handling-guide.aspx)

