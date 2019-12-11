---
title: Avertissement du compilateur (niveau 4) C4339
ms.date: 11/04/2016
f1_keywords:
- C4339
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
ms.openlocfilehash: e7c3f6f3a2cb9da9857d8336d24d57caf8114850
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991208"
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
