---
title: Conversions depuis les autres types
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: bd00bbb8944a0273163fa0c5952be510c9dd697c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200333"
---
# <a name="conversions-from-other-types"></a>Conversions depuis les autres types

Comme une **`enum`** valeur est une **`int`** valeur par définition, les conversions vers et à partir d’une **`enum`** valeur sont les mêmes que celles du **`int`** type. Pour le compilateur Microsoft C, un entier est identique à un **`long`** .

**Spécifique à Microsoft**

Aucune conversion entre les types structure ou union n’est autorisée.

Toute valeur peut être convertie en type **`void`** , mais le résultat d’une telle conversion peut être utilisé uniquement dans un contexte où une valeur d’expression est ignorée, comme dans une instruction d’expression.

Le **`void`** type n’a aucune valeur, par définition. Par conséquent, il ne peut pas être converti en un autre type et les autres types ne peuvent pas être convertis en **`void`** assignation par. Toutefois, vous pouvez effectuer un cast explicite d’une valeur en type **`void`** , comme indiqué dans [conversions de cast de type](../c-language/type-cast-conversions.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conversions d’assignation](../c-language/assignment-conversions.md)
