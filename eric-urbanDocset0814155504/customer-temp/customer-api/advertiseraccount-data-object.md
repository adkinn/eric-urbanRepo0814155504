---
title: "AdvertiserAccount Data Object"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4305d5e6-675c-4551-bb50-90cf33c4c682
caps.latest.revision: 24
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdvertiserAccount Data Object
Defines an advertiser account.

## Syntax

```xml
\<xs:complexType name="AdvertiserAccount">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:Account">
      \<xs:sequence>
        \<xs:element minOccurs="0" name="LinkedAgencies" nillable="true" type="tns:ArrayOfCustomerInfo" />
        \<xs:element minOccurs="0" name="SalesHouseCustomerId" nillable="true" type="xs:long" />
        \<xs:element minOccurs="0" name="BackUpPaymentInstrumentId" nillable="true" type="xs:long" />
        \<xs:element minOccurs="0" name="BillingThresholdAmount" nillable="true" type="xs:long" />
        \<xs:element minOccurs="0" name="BusinessAddress" nillable="true" type="tns:Address"/>
        \<xs:element minOccurs="0" name="TaxInformation" xmlns:q2="http://schemas.datacontract.org/2004/07/System.Collections.Generic" nillable="true" type="q2:ArrayOfKeyValuePairOfstringstring" />
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements
The *AdvertiserAccount* object derives from the [Account](../customer-api/account-data-object.md) object. For a list of the inherited elements, see [Inherited Elements](#InheritedElements) below.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BackUpPaymentInstrumentId*|The identifier of a backup  payment instrument to use to settle the account. This element is not applicable for invoiced accounts.<br/><br/>**Add:** Read-only<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*long*|
|*BillingThresholdAmount*|A customer specified amount for settling against the selected payment instrument.<br/><br/>**Add:** Read-only<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*decimal*|
|*BusinessAddress*|The location where your business is legally registered. If you are an agency working as an agent for your customer, this is the location where your client is legally registered. If you are an agency working as a reseller, this is the legally registered business address of your company. The business address is used to determine your tax requirements.<br/><br/>**Note:** To update the *BusinessAddress* of an invoice account, contact your account manager or support.<br/><br/>**Add:** Optional. If the *CurrencyType* is set to *INR* or *BRL* and you do not specify the *BusinessAddress*, then the *CountryCode* of the [Address](../customer-api/address-data-object.md) will be set to the corresponding default value as follows: If the currency is set to *INR* the business address country code will be set to *IN*. If the currency is set to *BRL* the business address country code will be set to *BR*. <br/>**Update:** Read-only|[Address](../customer-api/address-data-object.md)|
|*LinkedAgencies*|The list of agencies linked to this account.<br/><br/>Currently only one agency customer is supported. <br/><br/>**Add:** Optional. If the owner manages the account, set to NULL.<br/>**Update:** Read-only|[CustomerInfo](../customer-api/customerinfo-data-object.md) array|
|*SalesHouseCustomerId*|The identifier of the third party that is responsible for a sales lead.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*long*|
|*TaxInformation*|For a list of valid key and value strings for this element, see [AdvertiserAccount TaxInformation](#taxinformation) in the section below.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)] To remove a key and value pair, set the key and then set the value to an empty string (*""*).|*KeyValuePairOfstringstring* array|


## <a name="InheritedElements"></a>Inherited Elements
The *AdvertiserAccount* object derives from the [Account](../customer-api/account-data-object.md) object, and inherits the following elements. 

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountFinancialStatus*|The financial status of the account. For example, the status can indicate whether the account is in good standing or is past due.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AccountFinancialStatus](../customer-api/accountfinancialstatus-value-set.md)|
|*AccountLifeCycleStatus*|The status of the account. You cannot set the status of the account.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AccountLifeCycleStatus](../customer-api/accountlifecyclestatus-value-set.md)|
|*AccountType*|The type of the account. For example, whether the account is an advertiser account.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[AccountType](../customer-api/accounttype-value-set.md)|
|*BillToCustomerId*|The identifier of the customer that is billed for the charges that the account generates. This is either the reseller that manages this account on behalf of the owner or the identifier of the customer that owns the account.<br /><br />The service sets the identifier based on the owner of the payment instrument identified in the *PaymentMethodId* element.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*long*|
|*CountryCode*|The code that identifies the country/region in which the account operates. The service uses the country/region information for billing purposes.<br /><br />For a list of country code values, see [Common Market Values](http://go.microsoft.com/fwlink/?LinkId=691345).<br /><br />**Note:** If you specify a country code value when signing up a customer, the value is ignored. The signup process instead gets the country code value from the *CountryCode* element of the customer’s address. For more information, see the *CustomerAddress* element of the [Customer](../customer-api/customer-data-object.md).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|
|*CurrencyType*|The type of currency that is used to settle the account. The service uses the currency information for billing purposes.<br/><br/>**Add:** Required<br/>**Update:** Read-only|[CurrencyType](../customer-api/currencytype-value-set.md)|
|*ForwardCompatibilityMap*|For a list of valid key and value strings for this element, see [Account ForwardCompatibilityMap](#ForwardCompatibilityMap) in the section below.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)] To remove a key and value pair, set the key and then set the value to an empty string (*""*).|*KeyValuePairOfstringstring* array|
|*Id*|The system generated identifier of the account.<br /><br />This is the identifier that you set the *AccountId* element and *CustomerAccountId* SOAP header to in many of the campaign requests.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*long*|
|*Language*|The language used to render the invoice (if you use an invoice as your payment method).<br /><br />If you specify a language value when signing up a customer, the value is ignored. The signup process instead gets the language value from the *Lcid* element of the [User](../customer-api/user-data-object.md). If the *Lcid* element is set to a value such as *FrenchCanada*, the *Language* element is set to *French*.<br/><br/>**Add:** Read-only<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|[LanguageType](../customer-api/languagetype-value-set.md)|
|*LastModifiedByUserId*|The identifier of the last user to update the account’s information.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*long*|
|*LastModifiedTime*|The date and time that the account was last updated. The value is in Coordinated Universal Time (UTC).<br /><br />**Note:** The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](http://msdn.microsoft.com/library/ms256220.aspx).<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*dateTime*|
|*Name*|The name of the account. The name can contain a maximum of 100 characters and must be unique within the customer.<br/><br/>**Add:** Required<br/>**Update:** Required|*string*|
|*Number*|The system generated account number that is used to identify the account in the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application. The account number has the form *xxxxxxxx*, where *xxxxxxxx* is a series of any eight alphanumeric characters.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*string*|
|*ParentCustomerId*|The identifier of the customer that owns the account.<br /><br />In the campaign requests that require a customer identifier, this is the identifier that you set the *CustomerId* SOAP header to.<br/><br/>**Add:** Required<br/>**Update:** Read-only|*long*|
|*PauseReason*|A flag value that indicates who paused the account. The following are the possible values:<br /><br />1 – The user paused the account.<br /><br />2 – The billing service paused the account.<br /><br />4 – The user and billing service paused the account.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|*unsignedByte*|
|*PaymentMethodId*|The identifier of the payment instrument to use to settle the account.<br /><br />When signing up a customer, set this element to NULL. The service picks up the payment method identifier associated with the reseller’s invoice automatically.<br/><br/>**Add:** Read-only<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*long*|
|*PaymentMethodType*|The type of payment instrument to use to settle the account. You do not have to set this value because the type is determined by the payment instrument corresponding to the *PaymentMethodId* element.<br /><br />When you call the [GetAccount](../customer-api/getaccount-service-operation.md) and [SearchAccounts](../customer-api/searchaccounts-service-operation.md) to get the account data, *PaymentMethodType* is set to NULL, and you cannot determine the payment method that the account uses.<br /><br />**Note:** Reserved for internal use.<br/><br/>**Add:** Read-only<br/>**Update:** Read-only|[PaymentMethodType](../customer-api/paymentmethodtype-value-set.md)|
|*PrimaryUserId*|The identifier of the account manager who is primarily responsible for managing this account.<br /><br />By default, the value is set to the reseller’s user identifier.<br/><br/>**Add:** Read-only<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|*long*|
|*TimeStamp*|The time-stamp value that the system uses internally to reconcile updates when you call the [UpdateAccount](../customer-api/updateaccount-service-operation.md) and [DeleteAccount](../customer-api/deleteaccount-service-operation.md) operations.<br/><br/>**Add:** Read-only<br/>**Update:** Required|*base64Binary*|
|*TimeZone*|The default time-zone value to use for campaigns in this account.<br /><br />If you do not specify a value when the account is added, the time zone will be set to *PacificTimeUSCanadaTijuana* by default.<br /><br />**Note:** This time-zone value is used by the [!INCLUDE[brand](../customer-api/includes/brand.md)] web application to display the account time zone preference, and does not provide a default time-zone value for campaigns that are created by using the Campaign Management API.<br/><br/>**Add:** Optional<br/>**Update:** [!INCLUDE[update_optional_setting_unchanged](../customer-api/includes/update-optional-setting-unchanged.md)]|[TimeZoneType](../customer-api/timezonetype-value-set.md)|

## <a name="ForwardCompatibilityMap"></a>Account ForwardCompatibilityMap
The following is the list of keys that are available for the *ForwardCompatibilityMap* element of an [Account](../customer-api/account-data-object.md).
-   [AutoTag](#autotag)  
-   [TrackingUrlTemplate](#trackingurltemplate)  

**Note:** An Advertiser Campaign Manager user can only update the *TrackingUrlTemplate* and *AutoTag* values in the *ForwardCompatibilityMap* element. The *Id*, *Name* and *TimeStamp* properties are read-only and required for the update; however, all other properties of the Account object are read-only and will be ignored.

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

## <a name="taxinformation"></a>AdvertiserAccount TaxInformation
The following is the list of keys that are available for the *TaxInformation* element of an *AdvertiserAccount*.  

|TaxInformation Key|Description|Countries|
|---------|---------|---------|
|TaxId|The account's tax identifier The tax identifier must be valid in the country that you specified in the BusinessAddress element. Without a tax identifier, taxes might apply based on your business location.<br/><br/>**Add:** Required<br/>**Update:** Read-only|Brazil, Australia, Taiwan|
|GstInNumber|GSTINNumber	This number starts with two numbers representing the state code in which the business is registered followed by a maximum of 13 number and letters.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|India|
|NZGSTNumber|The NZGSTN Number is an 8 or 9 Digit long TaxID. Without a NZGSTN Number taxes might apply based on your business location.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|New Zealand|
|PanNumber|The PAN number.<br/><br/>**Add:** Required<br/>**Update:** Read-only|India|
|TaxType|You can indicate the type of tax. Possible values are Business and Personal.<br/><br/>**Add:** Optional<br/>**Update:** Optional|All|
|VATNumber|The account's Value Added Tax (VAT) registration number (also known as VAT identifier). This number starts with 2 letters that are specific to each country/region, followed by a maximum of 12 numbers or letters. The VAT number must be valid in the country that you specified in the BusinessAddress element. Without a VAT registration number or exemption certificate, taxes might apply based on your business location.<br/><br/>**Add:** Optional<br/>**Update:** Read-only|Austria, Belgium, Bulgaria, Cyprus, Czech Republic, Germany, Denmark, Estonia, Greece, Spain, Finland, France, United Kingdom, Croatia, Hungary, Ireland, Italy, Lithuania, Luxembourg, Latvia, Malta, The Netherlands, Poland, Portugal, Romania, Sweden, Slovenia, Slovakia|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[Account](../customer-api/account-data-object.md)  

