---
title: Expressions constantes C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35041b3a58f53586702db73d3bc5f6103f4f7cd7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054361"
---
# <a name="c-constant-expressions"></a>Expressions constantes C++

Un *constante* valeur fait partie qui ne change pas. C++ fournit deux mots clés qui vous permettent d'exprimer l'intention qu'un objet n'est pas destiné à être modifié, et d'appliquer cette intention.

C++ requiert des expressions constantes (expressions qui ont pour valeur une constante) pour les déclarations des éléments suivants :

- Limites d'index de tableau

- Sélecteurs dans les instructions case

- Spécification de longueur de champ de bits

- Initialiseurs d'énumération

Les seuls opérandes autorisés dans les expressions constantes sont :

- Littéraux

- Constantes d'énumération

- Valeurs déclarées comme const qui sont initialisées avec des expressions constantes

- **sizeof** expressions

Les constantes non intégrales doivent être converties (explicitement ou implicitement) en types intégraux pour être autorisées dans une expression constante. Par conséquent, le code suivant est conforme :

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Les conversions explicites en types intégraux sont autorisées dans les expressions constantes ; tous les autres types et les types dérivés ne sont pas conformes, sauf lorsque utilisé en tant qu’opérandes pour le **sizeof** opérateur.

L'opérateur virgule et les opérateurs d'assignation de virgule ne peuvent pas être utilisés dans les expressions constantes.

## <a name="see-also"></a>Voir aussi

[Types d’expressions](../cpp/types-of-expressions.md)