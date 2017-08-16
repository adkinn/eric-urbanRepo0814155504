---
title: "Ad Languages"
ms.custom: na
ms.date: "08/15/2017"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: ac68ee2d-1cbc-4ea7-b648-68c21f8ffa3a
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Ad Languages
Language options in Bing Ads give you control over your advertising campaign and experience. 

* [Ad Language](#adlanguage)  
* [Product Language](#productlanguage)  
* [Countdown Language](#countdownlanguage)  
* [Structured Snippet Headers](#structuredsnippetheaders)
 
## <a name="adlanguage"></a>Ad Language
Your ad language setting determines the language you will use when you write your ads and should be the language of your customers. The campaign level languages setting applies to all ad groups in the campaign; However, If languages are set at both the ad group and campaign level, the ad group-level language will override the campaign-level language. The ad group level language setting applies to all ads in an ad group. 

> [!NOTE] 
> Not everyone has the Campaign languages feature yet. If you don’t, don’t worry. It’s coming soon.

Your ad language in combination with your location targeting determines who will see your ads. To learn more, see the Bing Ads help article [How does ad language and location targeting affect who can see my ads?](https://help.bingads.microsoft.com/#apex/3/en/51100/0)

The following are the possible languages that you may use to write your ads and keywords.

|Language|Language Code|
|------------|-----------------|
|Danish|DA|
|Dutch|NL|
|English|EN|
|Finnish|FI|
|French|FR|
|German|DE|
|Italian|IT|
|Norwegian|NO|
|Portuguese|PT<br /><br />**Note:** This code differs from the ISO standard for Brazilian Portuguese, PTB.|
|Spanish|ES|
|Swedish|SV|
|TraditionalChinese<br /><br />**Note:** You must use *TraditionalChinese* (without space) when setting the language of a campaign or ad group.<br /><br />**Note:** You must use *Traditional Chinese* (with space) when setting request elements using the Ad Insight Service.|ZH|
		
## <a name="productlanguage"></a>Product Language
Your [customer](https://msdn.microsoft.com/library/bing-ads-customer-management-customer.aspx) language determines the language of the Bing Ads interface. 

The following country codes are supported per customer language e.g. you can use these languages and countries in the [Customer](https://msdn.microsoft.com/library/bing-ads-customer-management-customer.aspx) object when calling the [SignupCustomer](https://msdn.microsoft.com/library/dn451287.aspx) operation.

> [!NOTE]
> In New Zealand, Bing Ads is available only on the Bing network. For other countries listed below, Bing Ads is available on the Yahoo Bing Network.

|Language|Country Code|
|------------|------------------|
|English|AD, AG, AI, AL, AM, AQ, AS, AU, AW, AZ, BA, BB, BD, BE, BG, BI, BM, BN, BS, BT, BW, BY, BZ, CC, CK, CV, CX, CY, CZ, DJ, DM, EE, ER, ET, FJ, FM, FO, GA, GB, GD, GE, GF, GH, GI, GL, GM, GN, GP, GQ, GR, GU, GW, GY, HR, HU, ID, IE, IL, IN, IS, JM, JP, KE, KG, KH, KI, KM, KN, KR, KY, KZ, LA, LC, LI, LK, LR, LS, LT, LV, MC, MD, ME, MG, MH, MK, MM, MN, MO, MP, MQ, MR, MS, MT, MU, MV, MW, MY, NA, NC, NF, NG, NP, NR, NU, NZ, PF, PG, PH, PK, PL, PM, PN, PR, PS, PW, RE, RO, RS, RU, RW, SB, SC, SG, SH, SI, SK, SL, SM, SO, SR, ST, SZ, TC, TH, TJ, TK, TM, TO, TR, TT, TV, TZ, UA, UG, US, UZ, VA, VG, VI, VN, VU, WF, WS, YT, ZA, ZM, ZW|
|French|BF, BJ, CD, CF, CG, CI, CM, FR, HT, LU, ML, NE, SN, TD, TG|
|German|AT, CH, DE|
|Italian|IT|
|Portuguese|AO, BR, MZ, PT, TL|
|Spanish|AR, BO, CL, CO, CR, DO, EC, ES, GT, HN, MX, NI, PA, PE, PY, SV, UY, VE|
|TraditionalChinese|HK, TW|

		
## <a name="countdownlanguage"></a>Countdown Language
Countdown customizers let you easily add a countdown — by day, hour, and then minute — to an event in your Expanded Text Ad. The following language codes are supported for [countdown functions](../concepts/expanded-text-ads.md#countdown).

|Language Code|Language|Countdown Length|
|------------|------------|------------------|
|DA|Danish|11|
|NL|Dutch|10|
|en-AU|English|10|
|en-GB|English|10|
|en-US|English|10|
|FI|Finnish|12|
|FR|French|10|
|DE|German|10|
|IT|Italian|10|
|NO|Norwegian|11|
|pt-BR|Portuguese|10|
|pt-PT|Portuguese|10|
|ES|Spanish|10|
|ES-419|Spanish|10|
|SV|Swedish|10|
|zh-HK|Traditional Chinese|7|
|zh-TW|Traditional Chinese|7|


## <a name="structuredsnippetheaders"></a>Structured Snippet Headers
Structured Snippet headers must be specified in the same language that you intend it to be shown. For example, if you want header *Amenities* in English you must specify the header as *Amenities*.  If you want header *Ausstattung* in German you must specify the header as *Ausstattung* (*Amenities* in German). The following headers are supported per language.

```csv
Language,Amenities,Brands,Courses,Degree programs,Destinations,Featured hotels,Goods,Insurance coverage,Items,Models,Neighborhoods,Services,Service catalog,Shows,Styles,Types
Chinese (Traditional),設施,品牌,課程,學位課程,目的地,精選旅館,商品,保險涵蓋範圍,項目,型號,鄰近地點,服務,服務目錄,節目,風格,類型
English,Amenities,Brands,Courses,Degree programs,Destinations,Featured hotels,Goods,Insurance coverage,Items,Models,Neighborhoods,Services,Service catalog,Shows,Styles,Types
French,Équipements,Marques,Cours,Programmes d’études,Destinations,Sélection d’hôtels,Biens,Couverture d’assurance,Éléments,Modèles,Quartiers,Services,Catalogue de services,Émissions,Styles,Types
German,Ausstattung,Marken,Kurse,Studiengänge,Ziele,Vorgestellte Hotels,Waren,Versicherungsleistung,Artikel,Modelle,Viertel,Services,Dienstleistungen,Sendungen,Stile,Typen
Italian,Attrattive,Marchi,Corsi,Corsi di studio,Destinazioni,Hotel consigliati,Beni,Copertura assicurativa,Articoli,Modelli,Quartieri,Servizi,Catalogo servizi,Programmi,Stili,Tipi
Dutch,Voorzieningen,Merken,Cursussen,Studieprogramma's,Bestemmingen,Aanbevolen hotels,Producten,Dekking,Items,Modellen,Buurten,Services,Servicecatalogus,Shows,Stijlen,Typen
Portuguese (Brazil),Comodidades,Marcas,Cursos,Programas de graduação,Destinos,Hotéis em destaque,Bens,Cobertura do seguro,Itens,Modelos,Arredores,Serviços,Catálogo de serviços,Programas,Estilos,Tipos
Spanish,Servicios adicionales,Marcas,Cursos,Carreras universitarias,Destinos,Hoteles destacados,Artículos,Cobertura de seguros,Elementos,Modelos,Vecindarios,Servicios,Catálogo de servicios,Espectáculos,Estilos,Tipos
Swedish,Bekvämligheter,Varumärken,Kurser,Utbildningar,Resmål,Hotellval,Varor,Försäkring,Objekt,Modeller,Områden,Tjänster,Servicekatalog,Föreställningar,Stilar,Typer
```