---
title: Avertissement du compilateur (niveau 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a192fb9d8dc046bb3493b90b85371175520ccf95
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230725"
---
# <a name="compiler-warning-level-1-c4258"></a>Avertissement du compilateur (niveau 1) C4258

'variable' : la définition de la boucle for est ignorée ; la définition de la portée englobante est utilisée

Sous [/Ze](../../build/reference/za-ze-disable-language-extensions.md) et [/Zc : forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md), les variables définies dans une boucle [for](../../cpp/for-statement-cpp.md) sont hors de portée à la fin de la **`for`** boucle. Cet avertissement se produit si une variable portant le même nom que la variable de boucle, mais définie dans la boucle englobante, est réutilisée dans l’étendue contenant la **`for`** boucle. Par exemple :

```cpp
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```
