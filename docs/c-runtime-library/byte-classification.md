---
description: En savoir plus sur la classification d’octets
title: Classification d’octets
ms.date: 04/04/2018
f1_keywords:
- c.types.bytes
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
ms.openlocfilehash: 00691ca85366c5cbbe28b023f2a269838128fe9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221694"
---
# <a name="byte-classification"></a>Classification d’octets

Chacune de ces routines teste un octet spécifié d’un caractère multioctet pour remplir une condition. Sauf indication contraire, la valeur de sortie est affectée par la valeur du paramètre de catégorie **LC_CTYPE** des paramètres régionaux. Pour plus d’informations, consultez [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis.

> [!NOTE]
> Par définition, les caractères ASCII compris entre 0 et 127 sont une partie de tous les jeux de caractères multioctets. Par exemple, le jeu de caractères japonais katakana inclut aussi bien des caractères ASCII que non-ASCII.

Les constantes prédéfinies dans le tableau suivant sont définies dans \<ctype.h> .

## <a name="multibyte-character-byte-classification-routines"></a>Routines de classification d’octets en caractères multioctets

|Routine|Condition de test de l’octet|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Octet de tête. Le résultat du test dépend du paramètre de catégorie **LC_CTYPE** des paramètres régionaux actuels|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum** &#124;&#124; **_ismbbkalnum**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha** &#124;&#124; **_ismbbkalnum**|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Identique à **_ismbbprint**, mais **_ismbbgraph** n’inclut pas le caractère espace (0x20)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Symbole de texte non-ASCII autre que les signes de ponctuation. Par exemple, dans la page de codes 932 uniquement, **_ismbbkalnum** teste la présence de katakanas alphanumériques|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF), page de codes 932 uniquement|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Texte non-ASCII ou symbole de ponctuation non-ASCII. Par exemple, dans la page de codes 932 uniquement, **_ismbbkprint** teste s’il s’agit de katakanas alphanumériques ou de ponctuation katakana (plage : 0xA1 - 0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Ponctuation non-ASCII. Par exemple, dans la page de codes 932 uniquement, **_ismbbkpunct** teste la présence d’une ponctuation katakana.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Premier octet d’un caractère multioctet. Par exemple, dans la page de codes 932 uniquement, les plages valides sont 0x81 - 0x9F, 0xE0 - 0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint** &#124;&#124; **_ismbbkprint**. **ismbbprint** comprend le caractère espace (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct** &#124;&#124; **_ismbbkpunct**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Deuxième octet de caractère multioctet. Par exemple, dans la page de codes 932 uniquement, les plages valides sont 0x40 - 0x7E, 0x80 - 0xEC.|
|[_ismbslead, _ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Octet de tête (dans le contexte de chaîne)|
|[ismbstrail, _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Octet de fin (dans le contexte de chaîne)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Type d’octet de retour selon l’octet précédent|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Type de retour d’octet dans la chaîne|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Suit l'état d'une conversion en caractères multioctets.|

La macro **MB_LEN_MAX** , définie dans \<limits.h> , est plus longue que la longueur maximale, en octets, d’un caractère multioctet. **MB_CUR_MAX**, défini dans \<stdlib.h> , augmente la longueur maximale en octets d’un caractère multioctet dans les paramètres régionaux actuels.

## <a name="see-also"></a>Voir aussi

[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)
