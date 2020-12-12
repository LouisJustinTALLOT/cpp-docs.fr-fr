---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4339'
title: Avertissement du compilateur (niveau 4) C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: e05a7a73ac0cbbf056e5e30db0989e7fe933d01e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294520"
---
# <a name="compiler-warning-level-4-c4339"></a>Avertissement du compilateur (niveau 4) C4339

'type' : utilisation de ce type non défini dans les métadonnées WinRT ou CLR, ce qui peut provoquer une exception runtime

Un type n'a pas été défini dans le code qui a été compilé pour Windows Runtime ou le Common Language Runtime. Définissez ce type pour éviter une exception d'exécution possible.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L'exemple suivant génère l'erreur C4339 et montre comment la corriger :

```cpp
// C4339.cpp
// compile with: /W4 /clr /c
// C4339 expected
#pragma warning(default : 4339)

// Delete the following line to resolve.
class A;

// Uncomment the following line to resolve.
// class A{};

class X {
public:
   X() {}

   virtual A *mf() {
      return 0;
   }
};

X * f() {
   return new X();
}
```
