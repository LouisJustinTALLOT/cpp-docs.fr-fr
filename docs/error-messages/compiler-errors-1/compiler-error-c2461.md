---
title: Erreur du compilateur C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: 3d290bd2288f76d0ddefa2057e3e01c9edc3cbc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205320"
---
# <a name="compiler-error-c2461"></a>Erreur du compilateur C2461

> '*classe*' : paramètres formels manquants dans la syntaxe du constructeur

Le constructeur de la classe ne spécifie pas de paramètres formels. La déclaration d’un constructeur doit spécifier une liste de paramètres formels. La liste peut être vide.

Pour résoudre ce problème, ajoutez une paire de parenthèses après la *déclaration de classe*::**classe*.

## <a name="example"></a>Exemple

L’exemple suivant montre comment corriger C2461 :

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```
