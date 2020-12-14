---
description: 'En savoir plus sur : les conversions d’autres types'
title: Conversions depuis les autres types
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: 0b9497c4873e42f9d08463c4ec1396b178b6f362
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293194"
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
