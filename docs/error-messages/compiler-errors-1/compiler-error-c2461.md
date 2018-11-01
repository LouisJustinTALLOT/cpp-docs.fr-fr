---
title: Erreur du compilateur C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: e8f82ed4ce8ad77a22961a42c8e9a256e6f647db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535133"
---
# <a name="compiler-error-c2461"></a>Erreur du compilateur C2461

> «*classe*' : syntaxe du constructeur absence de paramètres formels

Le constructeur de la classe ne spécifie pas de tous les paramètres formels. La déclaration d’un constructeur doit spécifier une liste de paramètres formels. La liste peut être vide.

Pour résoudre ce problème, ajoutez une paire de parenthèses après la déclaration de *classe*:: **classe*.

## <a name="example"></a>Exemple

L’exemple suivant montre comment la corriger C2461 :

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```