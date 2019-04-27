---
title: Avertissement du compilateur (niveau 1) C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: a3ce4c81a86920baddfc1b277df0236a96254be4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207394"
---
# <a name="compiler-warning-level-1-c4258"></a>Avertissement du compilateur (niveau 1) C4258

'variable' : définition de la boucle for ignorée ; la définition de la portée englobante est utilisée »

Sous [/Ze](../../build/reference/za-ze-disable-language-extensions.md) et [/Zc : forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md), les variables définies dans un [pour](../../cpp/for-statement-cpp.md) boucle sont hors de portée après la **pour** boucle se termine. Cet avertissement se produit si une variable portant le même nom que la variable de boucle, mais définie dans la boucle englobante, est utilisée à nouveau dans la portée contenant le **pour** boucle. Exemple :

```
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