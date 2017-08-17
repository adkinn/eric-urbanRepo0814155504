---
title: "TimeZoneType Value Set"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63937253-2636-402d-b868-5232280a38e0
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# TimeZoneType Value Set
Defines the possible time zones for the customer management service.

> [!NOTE]
> The value set defines the full set of time zones. For more information, see [Time Zones](https://msdn.microsoft.com/library/bing-ads-time-zones.aspx).

## Syntax

```xml
\<xs:simpleType name="TimeZoneType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="AbuDhabiMuscat">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">32</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Adelaide">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">11</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Alaska">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">72</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="AlmatyNovosibirsk">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">25</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="AmsterdamBerlinBernRomeStockholmVienna">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">48</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Arizona">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">68</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="AstanaDhaka">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">24</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="AthensBuckarestIstanbul">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">43</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="AtlanticTimeCanada">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">58</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="AucklandWellington">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">3</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Azores">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">51</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Baghdad">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">37</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="BakuTbilisiYerevan">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">31</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="BangkokHanoiJakarta">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">21</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="BeijingChongqingHongKongUrumqi">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">19</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="BelgradeBratislavaBudapestLjubljanaPrague">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">47</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="BogotaLimaQuito">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">61</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Brasilia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">54</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Brisbane">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">9</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="BrusselsCopenhagenMadridParis">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">46</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Bucharest">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">42</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="BuenosAiresGeorgetown">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">55</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Cairo">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">41</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="CanberraMelbourneSydney">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">8</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="CapeVerdeIsland">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">52</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="CaracasLaPaz">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">59</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="CasablancaMonrovia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">49</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="CentralAmerica">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="CentralTimeUSCanada">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">65</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ChennaiKolkataMumbaiNewDelhi">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">27</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="ChihuahuaLaPazMazatlan">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">69</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Darwin">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">10</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="EasternTimeUSCanada">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">62</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Ekaterinburg">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">29</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="FijiKamchatkaMarshallIsland">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">2</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Greenland">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">56</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="GreenwichMeanTimeDublinEdinburghLisbonLondon">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">50</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="GuadalajaraMexicoCityMonterrey">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">66</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="GuamPortMoresby">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">7</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="HararePretoria">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">40</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Hawaii">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">73</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="HelsinkiKyivRigaSofiaTallinnVilnius">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">39</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Hobart">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">6</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="IndianaEast">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">63</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="InternationalDatelineWest">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">75</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="IrkutskUlaanBataar">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">18</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="IslamabadKarachiTashkent">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">28</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Jerusalem">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">38</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Kabul">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">30</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Kathmandu">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">26</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Krasnoyarsk">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">20</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="KualaLumpurSingapore">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">17</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="KuwaitRiyadh">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">36</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="MagadanSolomonIslandNewCaledonia">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">4</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="MidAtlantic">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">53</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="MidwayIslandAndSamoa">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">74</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="MoscowStPetersburgVolgograd">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">35</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="MountainTimeUSCanada">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">70</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Nairobi">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">34</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Newfoundland">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">57</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Nukualofa">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">1</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="OsakaSapporoTokyo">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">14</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="PacificTimeUSCanadaTijuana">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">71</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Perth">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Rangoon">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">22</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Santiago">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">60</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SarajevoSkopjeWarsawZagreb">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">45</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Saskatchewan" />
    \<xs:enumeration value="Seoul">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">13</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="SriJayawardenepura">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">23</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Taipei">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">15</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Tehran">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">33</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Vladivostok">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">5</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="WestCentralAfrica">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">44</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
    \<xs:enumeration value="Yakutsk">
      \<xs:annotation>
        \<xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">12</EnumerationValue>
        \</xs:appinfo>
      \</xs:annotation>
    \</xs:enumeration>
  \</xs:restriction>
\</xs:simpleType>
\<xs:element name="TimeZoneType" type="tns:TimeZoneType" nillable="true" />
```

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]