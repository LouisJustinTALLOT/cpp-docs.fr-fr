---
description: En savoir plus sur les conversions de Function-Call
title: Conversions d'appel de fonction
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: f37cf2ef6c35cb8e7c856e1ab722a1efda2da61d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195955"
---
# <a name="function-call-conversions"></a>Conversions d'appel de fonction

Le type de conversion effectué sur les arguments dans un appel de fonction dépend de la présence d’un prototype de fonction (déclaration anticipée) avec les types d’argument déclarés pour la fonction appelée.

Si un prototype de fonction est présent et inclut des types d’argument déclarés, le compilateur effectue la vérification de type (voir [Fonctions](../c-language/functions-c.md)).

Si aucun prototype de fonction n’est présent, seules les conversions arithmétiques habituelles sont effectuées sur les arguments figurant dans l’appel de fonction. Ces conversions sont effectuées indépendamment sur chaque argument figurant dans l’appel. Cela signifie qu’une **`float`** valeur est convertie en **`double`** ; **`char`** une **`short`** valeur ou est convertie en **`int`** , et **`unsigned char`** ou **`unsigned short`** est converti en **`unsigned int`** .

## <a name="see-also"></a>Voir aussi

[Conversions de type](../c-language/type-conversions-c.md)
