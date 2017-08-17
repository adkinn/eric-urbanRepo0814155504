---
title: "Account Data Object"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f02a0a1-9a71-4c37-b765-66d6338d1b4e
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Account Data Object
Defines an account. This is the base object from which the advertising accounts derive.

Do not try to instantiate an *Account*. You can create the [AdvertiserAccount](../customer-api/advertiseraccount-data-object.md) object that derives from it. 

## Syntax

```xml
\<xs:complexType name="Account">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="AccountType" type="tns:AccountType" />
    \<xs:element minOccurs="0" name="BillToCustomerId" nillable="true" type="xsd:long" />
    \<xs:element minOccurs="0" name="CountryCode" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="CurrencyType" nillable="true" type="tns:CurrencyType" />
    \<xs:element minOccurs="0" name="AccountFinancialStatus" nillable="true" type="tns:AccountFinancialStatus" />
    \<xs:element minOccurs="0" name="Id" nillable="true" type="xs:long" />
    \<xs:element minOccurs="0" name="Language" nillable="true" type="tns:LanguageType" />
    \<xs:element minOccurs="0" name="ForwardCompatibilityMap" xmlns:q2="http://schemas.datacontract.org/2004/07/System.Collections.Generic" nillable="true" type="q2:ArrayOfKeyValuePairOfstringstring" />
    \<xs:element minOccurs="0" name="LastModifiedByUserId" nillable="true" type="xsd:long" />
    \<xs:element minOccurs="0" name="LastModifiedTime" nillable="true" type="xsd:dateTime" />
    \<xs:element minOccurs="0" name="Name" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="Number" nillable="true" type="xsd:string" />
    \<xs:element minOccurs="0" name="ParentCustomerId" type="xsd:long" />
    \<xs:element minOccurs="0" name="PauseReason" nillable="true" type="xs:unsignedByte" />
    \<xs:element minOccurs="0" name="PaymentMethodId" nillable="true" type="xsd:long" />
    \<xs:element minOccurs="0" name="PaymentMethodType" nillable="true" type="tns:PaymentMethodType" />
    \<xs:element minOccurs="0" name="PrimaryUserId" nillable="true" type="xsd:long" />
    \<xs:element minOccurs="0" name="AccountLifeCycleStatus" nillable="true" type="tns:AccountLifeCycleStatus" />
    \<xs:element minOccurs="0" name="TimeStamp" nillable="true" type="xsd:base64Binary" />
    \<xs:element minOccurs="0" name="TimeZone" nillable="true" type="tns:TimeZoneType" />
    \<xs:element minOccurs="0" name="PauseReason" nillable="true" type="xs:unsignedByte" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountFinancialStatus*|The financial status of the account. For example, the status can indicate whether the account is in good standing or is past due.|[AccountFinancialStatus](../customer-api/accountfinancialstatus-value-set.md)|
|*AccountLifeCycleStatus*|The status of the account. You cannot set the status of the account.|[AccountLifeCycleStatus](../customer-api/accountlifecyclestatus-value-set.md)|
|*AccountType*|The type of the account. For example, whether the account is an advertiser account.|[AccountType](../customer-api/accounttype-value-set.md)|
|*BillToCustomerId*|The identifier of the customer that is billed for the charges that the account generates. This is either the reseller that manages this account on behalf of the owner or the identifier of the customer that owns the account.<br/><br/>The service sets the identifier based on the owner of the payment instrument identified in the *PaymentMethodId* element.|*long*|
|*CountryCode*|The code that identifies the country/region in which the account operates. The service uses the country/region information for billing purposes.<br/><br/>For a list of country code values, see [Common Market Values](http://go.microsoft.com/fwlink/?LinkId=691345).<br/><br/>**Note:** If you specify a country code value when signing up a customer, the value is ignored. The signup process instead gets the country code value from the *CountryCode* element of the customer’s address. For more information, see the *CustomerAddress* element of the [Customer](../customer-api/customer-data-object.md).|*string*|
|*CurrencyType*|The type of currency that is used to settle the account. The service uses the currency information for billing purposes.|[CurrencyType](../customer-api/currencytype-value-set.md)|
|*ForwardCompatibilityMap*|For a list of valid key and value strings for this element, see [Account ForwardCompatibilityMap](#ForwardCompatibilityMap) in the section below.|*KeyValuePairOfstringstring* array|
|*Id*|The system generated identifier of the account.<br/><br/>This is the identifier that you set the *AccountId* element and *CustomerAccountId* SOAP header to in many of the campaign requests.|*long*|
|*Language*|The language used to render the invoice (if you use an invoice as your payment method).<br/><br/>If you specify a language value when signing up a customer, the value is ignored. The signup process instead gets the language value from the *Lcid* element of the [User](../customer-api/user-data-object.md). If the *Lcid* element is set to a value such as *FrenchCanada*, the *Language* element is set to *French*.|[LanguageType](../customer-api/languagetype-value-set.md)|
|*LastModifiedByUserId*|The identifier of the last user to update the account’s information.|*long*|
|*LastModifiedTime*|The date and time that the account was last updated. The value is in Coordinated Universal Time (UTC).<br/><br/>**Note:** The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](http://msdn.microsoft.com/library/ms256220.aspx).|*dateTime*|
|*Name*|The name of the account. The name can contain a maximum of 100 characters and must be unique within the customer.|*string*|
|*Number*|The system generated account number that is used to identify the account in the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application. The account number has the form *xxxxxxxx*, where *xxxxxxxx* is a series of any eight alphanumeric characters.|*string*|
|*ParentCustomerId*|The identifier of the customer that owns the account.<br/><br/>In the campaign requests that require a customer identifier, this is the identifier that you set the *CustomerId* SOAP header to.|*long*|
|*PauseReason*|A flag value that indicates who paused the account. The following are the possible values:<br/><br/>1 – The user paused the account.<br/><br/>2 – The billing service paused the account.<br/><br/>4 – The user and billing service paused the account.|*unsignedByte*|
|*PaymentMethodId*|The identifier of the payment instrument to use to settle the account.<br/><br/>When signing up a customer, set this element to NULL. The service picks up the payment method identifier associated with the reseller’s invoice automatically.|*long*|
|*PaymentMethodType*|The type of payment instrument to use to settle the account. You do not have to set this value because the type is determined by the payment instrument corresponding to the *PaymentMethodId* element.<br/><br/>When you call the [GetAccount](../customer-api/getaccount-service-operation.md) and [SearchAccounts](../customer-api/searchaccounts-service-operation.md) to get the account data, *PaymentMethodType* is set to NULL, and you cannot determine the payment method that the account uses.<br/><br/>**Note:** Reserved for internal use.|[PaymentMethodType](../customer-api/paymentmethodtype-value-set.md)|
|*PrimaryUserId*|The identifier of the account manager who is primarily responsible for managing this account.<br/><br/>By default, the value is set to the reseller’s user identifier.|*long*|
|*TimeStamp*|The time-stamp value that the system uses internally to reconcile updates when you call the [UpdateAccount](../customer-api/updateaccount-service-operation.md) and [DeleteAccount](../customer-api/deleteaccount-service-operation.md) operations.|*base64Binary*|
|*TimeZone*|The default time-zone value to use for campaigns in this account.<br/><br/>If you do not specify a value when the account is added, the time zone will be set to *PacificTimeUSCanadaTijuana* by default.<br/><br/>**Note:** This time-zone value is used by the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application to display the account time zone preference, and does not provide a default time-zone value for campaigns that are created by using the Campaign Management API.|[TimeZoneType](../customer-api/timezonetype-value-set.md)|

## <a name="ForwardCompatibilityMap"></a>Account ForwardCompatibilityMap
The following is the list of keys that are available for the *ForwardCompatibilityMap* element of an *Account*.

-   [AutoTag](#autotag)

-   [TrackingUrlTemplate](#trackingurltemplate)

### <a name="autotag"></a>AutoTag
[!INCLUDE[brand](../customer-api/includes/brand.md)] can automatically add UTM tags to your destination URL so you can use your website analytics tool, for example Google Analytics, to track how people got to your website. Auto-tags are applied for example to expanded text ads, keywords, Bing Shopping Campaigns, and Sitelink Extensions. For details about auto-tagging, please see the Bing Ads help article [How do I add UTM tags to my landing page URL?](http://help.bingads.microsoft.com/#apex/3/en/56762/-1).

The  *AutoTag* key and value pair is an account level setting that determines whether to append or replace the supported UTM tracking codes. Tracking codes are inserted dynamically when each ad is shown, and the URL that you set up and stored in [!INCLUDE[brand](../customer-api/includes/brand.md)] is not updated. 

The possible values for the *AutoTag* key are as follows. If the *AutoTag* key is not specified, the default value is 0.

* 0 - [!INCLUDE[brand](../customer-api/includes/brand.md)] will not append any UTM tracking codes to your ad or keyword final URL.

* 1 - [!INCLUDE[brand](../customer-api/includes/brand.md)] will automatically append the supported UTM tracking codes, and preserve any existing UTM tracking codes that you added to your ad or keyword's final URL.

* 2 - [!INCLUDE[brand](../customer-api/includes/brand.md)] will automatically append the supported UTM tracking codes, and replace any of the existing and supported UTM tracking codes that you added to your ad or keyword's final URL.

### <a name="trackingurltemplate"></a>TrackingUrlTemplate
The tracking template to use as a default for all URLs in your account. The value of the *TrackingUrlTemplate* key can be set to any valid string as described below.

[!INCLUDE[validationrules_trackingurltemplate](../customer-api/includes/validationrules-trackingurltemplate.md)]

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]

## See Also
[AdvertiserAccount](../customer-api/advertiseraccount-data-object.md)  

