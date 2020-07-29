---
title: Conversions d'appel de fonction
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: e4e84c9d4e1f25a56c0bcabcec99e5e75fcaa321
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229673"
---
# <a name="function-call-conversions"></a>Conversions d'appel de fonction

Le type de conversion effectué sur les arguments dans un appel de fonction dépend de la présence d’un prototype de fonction (déclaration anticipée) avec les types d’argument déclarés pour la fonction appelée.

Si un prototype de fonction est présent et inclut des types d’argument déclarés, le compilateur effectue la vérification de type (voir [Fonctions](../c-language/functions-c.md)).

Si aucun prototype de fonction n’est présent, seules les conversions arithmétiques habituelles sont effectuées sur les arguments figurant dans l’appel de fonction. Ces conversions sont effectuées indépendamment sur chaque argument figurant dans l’appel. Cela signifie qu’une **`float`** valeur est convertie en **`double`** ; **`char`** une **`short`** valeur ou est convertie en **`int`** , et **`unsigned char`** ou **`unsigned short`** est converti en **`unsigned int`** .

## <a name="see-also"></a>Voir aussi

[Conversions de type](../c-language/type-conversions-c.md)
