---
title: Conversions d’affectation
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: cc75bdd8227c09247f6d4270f1fc21235de2eb05
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211838"
---
# <a name="assignment-conversions"></a>Conversions d’affectation

Dans les opérations d'assignation, le type de la valeur assignée est converti en type de la variable qui reçoit l'assignation. C permet des conversions par assignation entre les types intégraux et les types flottants, même si les informations sont perdues lors de la conversion. La méthode de conversion utilisée dépend des types impliqués dans l'assignation, comme décrit dans [Conversions arithmétiques courantes](../c-language/usual-arithmetic-conversions.md) et dans les sections suivantes :

- [Conversions depuis des types intégraux signés](../c-language/conversions-from-signed-integral-types.md)

- [Conversions depuis les types intégraux non signés](../c-language/conversions-from-unsigned-integral-types.md)

- [Conversions depuis les types à virgule flottante](../c-language/conversions-from-floating-point-types.md)

- [Conversions vers et depuis les types pointeur](../c-language/conversions-to-and-from-pointer-types.md)

- [Conversions depuis les autres types](../c-language/conversions-from-other-types.md)

Les qualificateurs de type n’affectent pas la possibilité de la conversion, même si une **`const`** l-value ne peut pas être utilisée sur le côté gauche de l’assignation.

## <a name="see-also"></a>Voir aussi

[Conversions des types](../c-language/type-conversions-c.md)
