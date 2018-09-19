---
title: Conversions d’appel de fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3a1a245511f0ab849c28ab9a03ba76903609643
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065658"
---
# <a name="function-call-conversions"></a>Conversions d'appel de fonction

Le type de conversion effectué sur les arguments dans un appel de fonction dépend de la présence d’un prototype de fonction (déclaration anticipée) avec les types d’argument déclarés pour la fonction appelée.

Si un prototype de fonction est présent et inclut des types d’argument déclarés, le compilateur effectue la vérification de type (voir [Fonctions](../c-language/functions-c.md)).

Si aucun prototype de fonction n’est présent, seules les conversions arithmétiques habituelles sont effectuées sur les arguments figurant dans l’appel de fonction. Ces conversions sont effectuées indépendamment sur chaque argument figurant dans l’appel. Cela signifie qu'une valeur **float** est convertie en valeur **double**, qu'une valeur `char` ou **short** est convertie en valeur `int` et qu'une valeur `unsigned char` ou **unsigned short** est convertie en valeur `unsigned int`.

## <a name="see-also"></a>Voir aussi

[Conversions de type](../c-language/type-conversions-c.md)