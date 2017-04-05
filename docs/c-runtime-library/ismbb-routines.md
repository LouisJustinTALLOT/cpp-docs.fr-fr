---
title: _ismbb, routines | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _ismbb
- ismbb
dev_langs:
- C++
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: fc4d8a98d8ab3c482b19af683c2f1428f5164290
ms.lasthandoff: 03/29/2017

---
# <a name="ismbb-routines"></a>_ismbb, routines
Teste la valeur d’entier donnée `c` pour une condition particulière, en utilisant les paramètres régionaux actuels ou une catégorie d’état de conversion LC_CTYPE spécifiée.  
  
|||  
|-|-|  
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|  
|[_ismbbalpha, _ismbbalpha_l](http://msdn.microsoft.com/en-us/8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|  
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|  
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|  
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|  
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|  
  
## <a name="remarks"></a>Notes  
 Chaque routine dans la famille `_ismbb` teste la valeur d’entier donné `c` pour une condition particulière. Le résultat du test dépend de la page de codes multioctets en vigueur. Par défaut, la page de codes multioctets est définie sur la page de codes ANSI obtenue à partir du système d’exploitation au démarrage du programme. Vous pouvez utiliser [_getmbcp](../c-runtime-library/reference/getmbcp.md) pour interroger la page de codes multioctets en cours d’utilisation, ou [_setmbcp](../c-runtime-library/reference/setmbcp.md) pour la modifier.  
  
 La valeur de sortie est affectée par la valeur du paramètre de catégorie `LC_CTYPE` des paramètres régionaux. Pour plus d’informations, consultez [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Les versions de ces fonctions qui n’ont pas le suffixe **_l** utilisent les paramètres régionaux actuels pour ce comportement dépendant de ces paramètres. Les versions qui ont le suffixe **_l** sont identiques, mais elles utilisent plutôt les paramètres régionaux qui ont été passés.  
  
 Les routines de la famille `_ismbb` testent l’entier donné `c` comme suit.  
  
|Routine|Condition de test d’octet|  
|-------------|-------------------------|  
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbalpha](http://msdn.microsoft.com/en-us/8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0)|`isalpha` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|  
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Identique à `_ismbbprint`, mais `_ismbbgraph` n’inclut pas le caractère espace (0x20).|  
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Symbole de texte non-ASCII autre que les signes de ponctuation. Par exemple, dans la page de codes 932 uniquement, `_ismbbkalnum` teste la présence de katakanas alphanumériques.|  
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 – 0xDF). Propre à la page de codes 932.|  
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Texte non-ASCII ou symbole de ponctuation non-ASCII. Par exemple, dans la page de codes 932 uniquement, `_ismbbkprint` teste s’il s’agit de katakanas alphanumériques ou de ponctuation katakana (plage : 0xA1 – 0xDF).|  
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Ponctuation non-ASCII. Par exemple, dans la page de codes 932 uniquement, `_ismbbkpunct` teste la présence d'une ponctuation katakana.|  
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Premier octet d’un caractère multioctet. Par exemple, dans la page de codes 932 uniquement, les plages valides sont 0x81 – 0x9F, 0xE0 – 0xFC.|  
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** inclut le caractère espace (0x20).|  
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|  
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Deuxième octet de caractère multioctet. Par exemple, dans la page de codes 932 uniquement, les plages valides sont 0x40 – 0x7E, 0x80 – 0xEC.|  
  
 Le tableau suivant indique les valeurs ORed qui composent les conditions de test pour ces routines. Les constantes de manifeste `_BLANK`, `_DIGIT`, `_LOWER`, `_PUNCT`et `_UPPER` sont définies dans Ctype.h.  
  
|Routine|_BLANK|_DIGIT|LOWER|_PUNCT|UPPER|Texte<br /><br /> non<br /><br /> ASCII|Texte<br /><br /> non<br /><br /> ASCII|  
|-------------|-------------|-------------|-----------|-------------|-----------|------------------------------|-------------------------------|  
|`_ismbbalnum`|—|x|x|—|x|x|—|  
|`_ismbbalpha`|—|—|x|—|x|x|—|  
|`_ismbbblank`|x|—|—|—|—|—|—|  
|`_ismbbgraph`|—|x|x|x|x|x|x|  
|`_ismbbkalnum`|—|—|—|—|—|x|—|  
|`_ismbbkprint`|—|—|—|—|—|x|x|  
|`_ismbbkpunct`|—|—|—|—|—|—|x|  
|`_ismbbprint`|x|x|x|x|x|x|x|  
|`_ismbbpunct`|—|—|—|x|—|—|x|  
  
 Les routines `_ismbb` sont implémentées comme fonctions et comme macros. Pour plus d’informations sur le choix de l’implémentation, consultez [Recommandations relatives au choix entre une fonction et une macro](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Classification d’octet](../c-runtime-library/byte-classification.md)   
 [is, isw, routines](../c-runtime-library/is-isw-routines.md)   
 [_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)
