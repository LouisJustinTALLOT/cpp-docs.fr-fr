---
title: Conversions d'appel de fonction
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: d9f205bbbbac353b57743f8e1211b20fa3d32f05
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152480"
---
# <a name="function-call-conversions"></a>Conversions d'appel de fonction

Le type de conversion effectué sur les arguments dans un appel de fonction dépend de la présence d’un prototype de fonction (déclaration anticipée) avec les types d’argument déclarés pour la fonction appelée.

Si un prototype de fonction est présent et inclut des types d’argument déclarés, le compilateur effectue la vérification de type (voir [Fonctions](../c-language/functions-c.md)).

Si aucun prototype de fonction n’est présent, seules les conversions arithmétiques habituelles sont effectuées sur les arguments figurant dans l’appel de fonction. Ces conversions sont effectuées indépendamment sur chaque argument figurant dans l’appel. Cela signifie qu'une valeur **float** est convertie en valeur **double**, qu'une valeur `char` ou **short** est convertie en valeur `int` et qu'une valeur `unsigned char` ou **unsigned short** est convertie en valeur `unsigned int`.

## <a name="see-also"></a>Voir aussi

[Conversions de type](../c-language/type-conversions-c.md)
