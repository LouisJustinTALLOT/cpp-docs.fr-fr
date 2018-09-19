---
title: Compilateur avertissement (niveau 1) C4258 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4258
dev_langs:
- C++
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4d9aacd6e3681a1eb42073df8a13d7ce72c5634
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083533"
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