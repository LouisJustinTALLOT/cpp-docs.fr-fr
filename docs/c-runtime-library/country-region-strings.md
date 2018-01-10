---
title: "Chaînes de pays et de région | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords: country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94ad99ebd05fa9e37a56f2e12818f30f1f4b1212
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="countryregion-strings"></a>Chaînes de pays et de région
Les chaînes de pays et de région peuvent être combinés avec une chaîne de langue pour créer une spécification de paramètres régionaux pour les fonctions `setlocale`, `_wsetlocale`, `_create_locale`et `_wcreate_locale` . Pour obtenir la liste des noms de pays/région qui sont pris en charge par les différentes versions du système d’exploitation Windows, consultez les [Informations de référence de l’API NLS (National Language Support)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). Dans les listes, la chaîne de pays/région peut être une des valeurs de la colonne **Locale - Language Country/Region** ou une des abréviations de la colonne **Country or Region name abbreviation**. Pour plus d’informations sur la prise en charge linguistique dans les systèmes d’exploitation Windows par version, consultez [Appendix A: Product Behavior](http://msdn.microsoft.com/goglobal/bb896001.aspx) dans [MS-LCID] : Informations de référence Windows LCID (Language Code Identifier).  
  
 L’implémentation de la bibliothèque Runtime C prend également en charge les chaînes et abréviations de pays/région supplémentaires suivantes :  
  
|Chaîne de pays/région|Abréviation|Nom des paramètres régionaux équivalents|  
|----------------------------|------------------|----------------------------|  
|america|USA|fr-FR|  
|britain|GBR|en-GB|  
|china|CHN|zh-CN|  
|czech|CZE|cs-CZ|  
|england|GBR|en-GB|  
|great britain|GBR|en-GB|  
|holland|NLD|NL-NL|  
|hong-kong|HKG|zh-HK|  
|new-zealand|NZL|en-NZ|  
|nz|NZL|en-NZ|  
|pr china|CHN|zh-CN|  
|pr-china|CHN|zh-CN|  
|puerto-rico|PRI|es-PR|  
|slovak|SVK|sk-SK|  
|south africa|ZAF|af-ZA|  
|south korea|KOR|ko-KR|  
|south-africa|ZAF|af-ZA|  
|south-korea|KOR|ko-KR|  
|trinidad & tobago|TTO|en-TT|  
|uk|GBR|en-GB|  
|united-kingdom|GBR|en-GB|  
|united-states|USA|fr-FR|  
|us|USA|fr-FR|  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes relatives aux noms, aux langues, au pays et à la région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Chaînes de langue](../c-runtime-library/language-strings.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)