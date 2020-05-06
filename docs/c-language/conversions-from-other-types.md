---
title: Conversions depuis les autres types
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: f9f2d73e57c576dcf8afed008a74e5e7dd9b9d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312464"
---
# <a name="conversions-from-other-types"></a>Conversions depuis les autres types

Comme une valeur **enum** est une valeur **int** par définition, les conversions vers et depuis une valeur **enum** sont les mêmes que celles du type **int**. Pour le compilateur Microsoft C, un entier est identique à une valeur **long**.

**Spécifique à Microsoft**

Aucune conversion entre les types structure ou union n’est autorisée.

Toute valeur peut être convertie en type **void**, mais le résultat d’une telle conversion peut être utilisé uniquement dans un contexte où une valeur d’expression est ignorée, comme dans une instruction d’expression.

Le type **void** n’a aucune valeur, par définition. Donc, il ne peut pas être converti en un autre type et les autres types ne peuvent pas être convertis en **void** par assignation. Toutefois, vous pouvez effectuer un cast explicite d’une valeur en type **void**, comme cela est expliqué dans [Conversions de cast de type](../c-language/type-cast-conversions.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conversions d’assignation](../c-language/assignment-conversions.md)
