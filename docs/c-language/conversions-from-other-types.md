---
title: Conversions depuis les autres types | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e919782022ee64f657611a14d6eae6173a67b8c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382677"
---
# <a name="conversions-from-other-types"></a>Conversions depuis les autres types

Comme une valeur **enum** est une valeur **int** par définition, les conversions vers et depuis une valeur **enum** sont les mêmes que celles du type **int**. Pour le compilateur Microsoft C, un entier est identique à une valeur **long**.

**Section spécifique à Microsoft**

Aucune conversion entre les types structure ou union n’est autorisée.

Toute valeur peut être convertie en type **void**, mais le résultat d’une telle conversion peut être utilisé uniquement dans un contexte où une valeur d’expression est ignorée, comme dans une instruction d’expression.

Le type **void** n’a aucune valeur, par définition. Donc, il ne peut pas être converti en un autre type et les autres types ne peuvent pas être convertis en **void** par assignation. Toutefois, vous pouvez effectuer un cast explicite d’une valeur en type **void**, comme cela est expliqué dans [Conversions de cast de type](../c-language/type-cast-conversions.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conversions d’assignation](../c-language/assignment-conversions.md)  
