---
title: Limites des constantes à virgule flottante │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b42fb03aca7334414a43b46be1134941389e4277
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095313"
---
# <a name="limits-on-floating-point-constants"></a>Limites des constantes à virgule flottante

**Section spécifique à Microsoft**

Le tableau suivant répertorie les limites applicables aux valeurs des constantes à virgule flottante. Le fichier d'en-tête FLOAT.H contient ces informations.

### <a name="limits-on-floating-point-constants"></a>Limites sur les constantes à virgule flottante

|Constante|Signification|Value|
|--------------|-------------|-----------|
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|Nombre de chiffres, *q*, de sorte qu’un nombre à virgule flottante avec *q* chiffres décimaux peut être arrondi en représentation à virgule flottante puis restauré à sa valeur initiale sans perte de précision.|6<br />15<br />15|
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|Plus petit nombre positif *x* de sorte que *x* + 1,0 n’est pas égal à 1,0|1,192092896e-07F<br />2,2204460492503131e-016<br />2,2204460492503131e-016|
|**FLT_GUARD**||0|
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|Nombre de chiffres dans la base spécifiée par **FLT_RADIX** dans la mantisse à virgule flottante. La base est 2 ; par conséquent, ces valeurs spécifient des bits.|24<br />53<br />53|
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|Nombre à virgule flottante maximal pouvant être représenté|3,402823466e+38F<br />1,7976931348623158e+308<br />1,7976931348623158e+308|
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|Entier maximal tel que 10 élevé à la puissance de ce nombre est un nombre à virgule flottante pouvant être représenté.|38<br />308<br />308|
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|Entier maximal de sorte que **FLT_RADIX** élevé à la puissance de ce nombre est un nombre à virgule flottante qui peut être représenté.|128<br />1024<br />1024|
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|Valeur positive minimale.|1,175494351e-38F<br />2,2250738585072014E-308<br />2,2250738585072014E-308|
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|Entier négatif minimal tel que 10 élevé à la puissance de ce nombre est un nombre à virgule flottante pouvant être représenté.|-37<br />-307<br />-307|
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|Entier négatif minimal de sorte que **FLT_RADIX** élevé à la puissance de ce nombre est un nombre à virgule flottante qui peut être représenté.|-125<br />-1021<br />-1021|
|**FLT_NORMALIZE**||0|
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|Base de représentation d'exposant|2<br />2<br />2|
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|Mode d'arrondi pour l'addition à virgule flottante|1 (arrondi)<br />1 (arrondi)<br />1 (arrondi)|

Notez que les informations fournies dans le tableau ci-dessus peuvent différer dans des implémentations futures.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Constantes à virgule flottante C](../c-language/c-floating-point-constants.md)