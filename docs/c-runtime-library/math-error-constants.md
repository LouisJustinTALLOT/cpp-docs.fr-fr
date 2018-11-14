---
title: Constantes d'erreur mathématique
ms.date: 11/04/2016
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
ms.openlocfilehash: f51d9a3a28118d922f81a44e31c9abc610645f13
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524987"
---
# <a name="math-error-constants"></a>Constantes d'erreur mathématique

## <a name="syntax"></a>Syntaxe

```

#include <math.h>
```

## <a name="remarks"></a>Notes

Les routines mathématiques de la bibliothèque Runtime peuvent générer des constantes d’erreur mathématique.

Ces erreurs, comme indiqué ci-dessous, correspondent aux types d’exception définis dans les MATH.H et sont retournées par la fonction `_matherr` en cas d’erreur mathématique.

|Constante|Signification|
|--------------|-------------|
|`_DOMAIN`|L’argument de fonction est en dehors du domaine de la fonction.|
|`_OVERFLOW`|Le résultat est trop grand pour être représenté dans le type de retour de la fonction.|
|`_PLOSS`|Perte partielle de précision survenue.|
|`_SING`|Singularité de l’argument : l’argument de la fonction a une valeur non conforme. (Par exemple, la valeur 0 est passée à une fonction qui requiert une valeur différente de zéro).|
|`_TLOSS`|Perte totale de précision survenue.|
|`_UNDERFLOW`|Le résultat est trop petit pour être représenté.|

## <a name="see-also"></a>Voir aussi

[_matherr](../c-runtime-library/reference/matherr.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)