---
description: 'En savoir plus sur : conversions d’assignation'
title: Conversions d’affectation
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
ms.openlocfilehash: b9889214f160c981c57fc3174b542396d71458bd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97279960"
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

[Conversions de type](../c-language/type-conversions-c.md)
