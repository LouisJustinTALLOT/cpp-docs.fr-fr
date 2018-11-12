---
title: _ismbc, routines
ms.date: 11/04/2016
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 707287ea7abe255409911f5388cd1f96d976802b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454633"
---
# <a name="ismbc-routines"></a>_ismbc, routines

Chacune des routines **_ismbc** teste un caractère multioctet `c` pour une condition donnée.

|||
|-|-|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>Notes

Le résultat de chaque routine **_ismbc** dépend de la page de codes multioctet utilisée. Les pages de codes multioctets comportent des caractères alphabétiques sur un octet. Par défaut, la page de codes multioctet est définie sur la page de codes ANSI par défaut du système, obtenue du système d’exploitation au démarrage du programme. Vous pouvez interroger la page de codes multioctet utilisée, ou la remplacer par [_getmbcp](../c-runtime-library/reference/getmbcp.md) ou [_setmbcp](../c-runtime-library/reference/setmbcp.md), respectivement.

La valeur de sortie est affectée par le paramètre de catégorie `LC_CTYPE` des paramètres régionaux. Pour plus d’informations, consultez [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis.

|Routine|Condition de test|Exemple de page de codes 932|
|-------------|--------------------|---------------------------|
|[_ismbcalnum, _ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alphanumérique|Retourne une valeur différente de zéro si et seulement si `c` est une représentation sur un octet d’une lettre de l’alphabet anglais ASCII : consultez les exemples pour `_ismbcdigit` et `_ismbcalpha`.|
|[_ismbcalpha, _ismbcalpha\_](../c-runtime-library/reference/ismbcalnum-functions.md)|Alphabétique|Retourne une valeur différente de zéro si, et seulement si, `c` est une représentation sur un octet d’une lettre de l’alphabet anglais ASCII (voir des exemples pour `_ismbcupper` et `_ismbclower`) ou une lettre katakana : 0xA6<=`c`<=0xDF.|
|[_ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Chiffre|Retourne une valeur différente de zéro si et seulement si `c` est une représentation sur un octet d’un chiffre ASCII : 0x30<=`c`<=0x39.|
|[_ismbcgraph, _ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Graphique|Retourne une valeur différente de zéro si et seulement si `c` est une représentation sur un octet d’un caractère imprimable ASCII ou katakana, à l’exception d’un espace blanc ( ). Afficher des exemples pour `_ismbcdigit`, `_ismbcalpha` et `_ismbcpunct`|
|[_ismbclegal, _ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Caractère multioctet valide|Retourne une valeur différente de zéro si, et seulement si, le premier octet de `c` appartient à la plage 0x81-0x9F ou 0xE0-0xFC et que le deuxième octet appartient à la plage 0x40-0x7E ou 0x80-FC.|
|[_ismbclower, _ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Caractère alphabétique minuscule|Retourne une valeur différente de zéro si et seulement si `c` est une représentation sur un octet d’une lettre de l’alphabet anglais minuscule ASCII : 0x61<=`c`<=0x7A.|
|[_ismbcprint, _ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Imprimable|Retourne une valeur différente de zéro si, et seulement si, `c` est une représentation sur un octet d’un caractère imprimable ASCII ou katakana, y compris un espace blanc ( ). Voir des exemples pour `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha` et `_ismbcpunct`.|
|[_ismbcpunct, _ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Ponctuation|Retourne une valeur différente de zéro si et seulement si `c` est une représentation sur un octet d’un caractère de ponctuation ASCII ou katakana.|
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Espace ou tabulation horizontale|Retourne une valeur différente de zéro si, et seulement si, `c` est une représentation sur un octet d’un espace ou d’un caractère de tabulation horizontale : `c`=0x20 ou `c`=0x09.|
|[_ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Whitespace|Retourne une valeur différente de zéro si, et seulement si, `c` est un espace blanc : `c`=0x20 ou 0x09<=`c`<=0x0D.|
|[_ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Symbole multioctet|Retourne une valeur différente de zéro si et seulement si 0x8141<=`c`<=0x81AC.|
|[_ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Caractère alphabétique majuscule|Retourne une valeur différente de zéro si et seulement si `c` est une représentation sur un octet d’une lettre de l’alphabet anglais majuscule ASCII : 0x41<=`c`<=0x5A.|

**Routines spécifiques à la page de codes 932**

Les routines suivantes sont spécifiques à la page de codes 932.

|Routine|Condition de test (page de codes 932 uniquement)|
|-------------|-------------------------------------------|
|[_ismbchira, _ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana sur deux octets : 0x829F<=`c`<=0x82F1.|
|[_ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana sur deux octets : 0x8340<=`c`<=0x8396.|
|[_ismbcl0, _ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS non-Kanji : 0x8140<=`c`<=0x889E.|
|[_ismbcl1, _ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS niveau 1 : 0x889F<=`c`<=0x9872.|
|[_ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS niveau 2 : 0x989F<=`c`<=0xEA9E.|

`_ismbcl0`, `_ismbcl1` et `_ismbcl2` vérifient que la valeur spécifiée `c` satisfait aux conditions de test décrites ci-dessus, mais ne vérifient pas que `c` est un caractère multioctet valide. Si l’octet de poids faible est compris dans les plages 0x00-0x3F, 0x7F ou 0xFD-0xFF, ces fonctions retournent une valeur différente de zéro, indiquant que le caractère satisfait à la condition de test. Utilisez [_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) pour tester si le caractère multioctet est défini.

**Fin des fonctions spécifiques à la page de codes 932**

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../c-runtime-library/character-classification.md)<br/>
[is, isw, routines](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, routines](../c-runtime-library/ismbb-routines.md)