---
title: "Chaînes relatives aux noms, aux langues, au pays et à la région | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 22da7776e46171467a37d46c3de3227f060eaf77
ms.openlocfilehash: c03ad862cbba1038cfd651156f987cfbaf5b63f7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="locale-names-languages-and-countryregion-strings"></a>Chaînes relatives aux noms, aux langues, au pays et à la région
L'argument *locale* des fonctions `setlocale` et `_create_locale` peut être défini en utilisant les noms de paramètres régionaux, les langages, les codes de pays ou de région, et les pages de codes prises en charge par l'API de NLS Windows. L'argument *locale* prend la forme suivante :  
  
> *locale* :: "*locale_name*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "*language*\[\_*country-region*]\[.*code_page*]]"  
&nbsp;&nbsp;&nbsp;&nbsp;| ".*code_page*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "C"  
&nbsp;&nbsp;&nbsp;&nbsp;| ""  
&nbsp;&nbsp;&nbsp;&nbsp;| NULL  
  
 La forme de nom des paramètres régionaux est préférée ; par exemple, utilisez `en-US` pour l'anglais (États-Unis) ou `bs-Cyrl-BA` pour le Bosniaque (cyrillique, Bosnie-Herzégovine). Le jeu de noms de paramètres régionaux est décrit dans la rubrique [Locale Names](http://msdn.microsoft.com/library/windows/desktop/dd373814.aspx). Pour obtenir la liste des noms de paramètres régionaux pris en charge par la version du système d’exploitation Windows, consultez la colonne **Culture Name** de la rubrique [National Language Support (NLS) API Reference](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). Cette ressource répertorie le langage, le script, et les parties régionales des noms de paramètres régionaux pris en charge. Pour plus d’informations sur les noms de paramètres régionaux pris en charge dont les ordres de tri ne sont pas définis par défaut, consultez la colonne **Locale name** dans la rubrique [Sort Order Identifiers](http://msdn.microsoft.com/library/windows/desktop/dd374060.aspx). Pour plus d’informations sur la prise en charge linguistique et d’emplacement dans le système d’exploitation Windows par version, consultez [Appendix A: Product Behavior](http://msdn.microsoft.com/goglobal/bb896001.aspx) dans [MS-LCID] : Informations de référence Windows LCID (Language Code Identifier). Sous Windows 10 ou version ultérieure, les noms de paramètres régionaux qui correspondent aux balises de langue BCP-47 valides sont autorisés. Par exemple, `jp-US` est une balise BCP-47 valide, mais elle ne correspond en fait qu’à `US` pour la fonctionnalité des paramètres régionaux.  
  
 La forme *language*[*_country_region*[.*code_page*]] est stockée dans les paramètres régionaux d’une catégorie quand une chaîne de langage, ou une chaîne de langage et une chaîne de pays/région, est utilisée pour créer les paramètres régionaux. L’ensemble de chaînes de langage prises en charge est décrit dans [Language Strings](../c-runtime-library/language-strings.md), et la liste de chaînes de pays/région prises en charge est répertoriée dans [Country/Region Strings](../c-runtime-library/country-region-strings.md). Si le langage spécifié n'est pas associé au pays/région spécifié(e), la langue par défaut pour le pays/la région spécifié(e) est stockée dans les paramètres régionaux. Nous ne recommandons pas cette forme pour les chaînes de paramètres régionaux incorporées dans le code ou sérialisées dans le stockage, car ces chaînes sont plus susceptibles d'être modifiées par une mise à niveau du système d'exploitation que par la forme de nom des paramètres régionaux.  
  
 La page de codes est la page de codes ANSI/OEM qui est associée aux paramètres régionaux. La page de codes est déterminée pour vous lorsque vous spécifiez des paramètres régionaux seulement par langage ou par langage et pays/région. La valeur spéciale `.ACP` spécifie la page de codes ANSI pour le pays/la région. La valeur spéciale `.OCP` spécifie la page de codes OEM pour le pays/la région. Par exemple, si vous spécifiez `"Greek_Greece.ACP"` comme paramètres régionaux, les paramètres régionaux sont stockés comme `Greek_Greece.1253` (page de codes ANSI pour le grec), et si vous spécifiez `"Greek_Greece.OCP"` comme paramètres régionaux, ils sont stockés comme `Greek_Greece.737` (page de codes OEM pour le grec). Pour plus d’informations sur les pages de code, consultez [Code Pages](../c-runtime-library/code-pages.md). Pour obtenir la liste des pages de codes prises en charge sur Windows, consultez la rubrique [Code Page Identifiers](http://msdn.microsoft.com/library/windows/desktop/dd317756.aspx).  
  
 Si vous utilisez uniquement la page de codes pour spécifier les paramètres régionaux, la langue par défaut et le pays/la région du système sont utilisés. Par exemple, si vous spécifiez `".1254"` (turc ANSI) comme paramètres régionaux sur un système configuré pour l’anglais (États-Unis), les paramètres régionaux stockés sont `English_United States.1254`. Nous déconseillons cette forme, car elle peut aboutir à un comportement incohérent.  
  
Une valeur d’argument *locale* de `C` spécifie l'environnement de conformation minimal ANSI pour la conversion en C. Les paramètres régionaux `C` supposent que chaque type de données `char` est 1 octet et que sa valeur est toujours inférieure à 256. Si *locale* pointe vers une chaîne vide, les paramètres régionaux sont donnés par l'environnement défini lors de l'implémentation.  
  
Spécifiez toutes les catégories de paramètres régionaux en même temps pour les fonctions `setlocale` et `_wsetlocale` à l'aide de la catégorie `LC_ALL` . Les catégories peuvent toutes être définies aux mêmes paramètres régionaux, ou vous pouvez définir chaque catégorie individuellement en utilisant un argument de paramètres régionaux qui se présente comme suit :  
  
> LC_ALL_specifier :: locale  
&nbsp;&nbsp;&nbsp;&nbsp;| [LC_COLLATE=locale][;LC_CTYPE=locale][;LC_MONETARY=locale][;LC_NUMERIC=locale][;LC_TIME=locale]  
  
Spécifiez plusieurs types de catégories, séparés par des points-virgules. Les types de catégories non spécifiés utilisent les paramètres régionaux actuels. Par exemple, cet extrait de code attribue à toutes les catégories les paramètres régionaux actuels `de-DE`, puis définit les catégories `LC_MONETARY` sur `en-GB` et `LC_TIME` sur `es-ES` :  
  
```C  
_wsetlocale(LC_ALL, L"de-DE");  
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence sur les bibliothèques Runtime C](../c-runtime-library/c-run-time-library-reference.md)   
 [_get_current_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [Chaînes de langue](../c-runtime-library/language-strings.md)   
 [Chaînes pays/région](../c-runtime-library/country-region-strings.md)
