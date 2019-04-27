---
title: Limites des valeurs à virgule flottante
ms.date: 08/03/2018
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
ms.openlocfilehash: cead21c9a66dbc54b46b1c9f8083022a59e80295
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154399"
---
# <a name="floating-limits"></a>Limites des valeurs à virgule flottante

**Section spécifique à Microsoft**

Le tableau suivant répertorie les limites applicables aux valeurs des constantes à virgule flottante. Ces limites sont également définies dans le fichier d’en-tête standard \<float.h >.

## <a name="limits-on-floating-point-constants"></a>Limites des constantes à virgule flottante

|Constante|Signification|Value|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|Nombre de chiffres, q, tel qu'un nombre à virgule flottante avec q chiffres décimaux peut être arrondi en une représentation à virgule flottante puis restauré à sa valeur initiale sans perte de précision.|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|Plus petit nombre positif x tel que x + 1,0 n'est pas égal à 1,0.|1,192092896e-07F<br/>2,2204460492503131e-016<br/>2,2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|Nombre de chiffres dans la base spécifiée par `FLT_RADIX` dans la mantisse à virgule flottante. La base est 2 ; Par conséquent, ces valeurs spécifient des bits.|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|Nombre à virgule flottante représentable maximal.|3,402823466e+38F<br/>1,7976931348623158e+308<br/>1,7976931348623158e+308|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|Entier maximal tel que 10 élevé à ce nombre est un nombre à virgule flottante qui peut être représenté.|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|Entier maximal tel que `FLT_RADIX` déclenché pour que le nombre est un nombre à virgule flottante qui peut être représenté.|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|Valeur positive minimale.|1,175494351e-38F<br/>2,2250738585072014E-308<br/>2,2250738585072014E-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|Entier négatif minimal tel que 10 élevé à ce nombre est un nombre à virgule flottante qui peut être représenté.|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|Entier négatif minimal tel que `FLT_RADIX` élevé à ce nombre est un nombre à virgule flottante qui peut être représenté.|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|Base de représentation d'exposant|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|Mode d’arrondi d’addition à virgule flottante.|1 (arrondi)<br/>1 (arrondi)<br/>1 (arrondi)|

> [!NOTE]
>  Les informations contenues dans le tableau peuvent différer dans les versions ultérieures du produit.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Limites d’entier](../cpp/integer-limits.md)
