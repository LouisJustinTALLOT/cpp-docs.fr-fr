---
title: Conversions d'assignation
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: fb3da57af62171ef9670267f94f01ccc097e5942
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649109"
---
# <a name="assignment-conversions"></a>Conversions d'assignation

Dans les opérations d'assignation, le type de la valeur assignée est converti en type de la variable qui reçoit l'assignation. C permet des conversions par assignation entre les types intégraux et les types flottants, même si les informations sont perdues lors de la conversion. La méthode de conversion utilisée dépend des types impliqués dans l'assignation, comme décrit dans [Conversions arithmétiques courantes](../c-language/usual-arithmetic-conversions.md) et dans les sections suivantes :

- [Conversions depuis les types intégraux signés](../c-language/conversions-from-signed-integral-types.md)

- [Conversions depuis les types intégraux non signés](../c-language/conversions-from-unsigned-integral-types.md)

- [Conversions depuis les types à virgule flottante](../c-language/conversions-from-floating-point-types.md)

- [Conversions vers et depuis les types pointeur](../c-language/conversions-to-and-from-pointer-types.md)

- [Conversions depuis les autres types](../c-language/conversions-from-other-types.md)

Les qualificateurs de type n'affectent pas l'admissibilité de la conversion bien qu'il ne soit pas possible d'utiliser une l-value **const** à gauche de l'assignation.

## <a name="see-also"></a>Voir aussi

[Conversions de type](../c-language/type-conversions-c.md)