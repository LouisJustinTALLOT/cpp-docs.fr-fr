---
title: Erreur du compilateur C2653 | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8e1df7dd6337b1a3e363a5744181b12d94c879b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234965"
---
# <a name="compiler-error-c2653"></a>Erreur du compilateur C2653

> '*identificateur*' : n’est pas un nom de classe ou espace de noms

La syntaxe du langage requiert un nom de classe, structure, union ou espace de noms ici.

Cette erreur peut se produire lorsque vous utilisez un nom qui n’a pas été déclaré en tant que classe, structure, union ou espace de noms devant un opérateur de portée. Pour résoudre ce problème, déclarez le nom ou inclure l’en-tête qui déclare le nom avant de les utiliser.

C2653 est également possible si vous essayez de définir un *espace de noms composé*, un espace de noms qui contient un ou plusieurs noms d’espace de noms imbriqué à l’étendue. Compound, espace de noms définitions ne sont pas autorisées en C++ avant C ++ 17. Espaces de noms composés sont pris en charge depuis Visual Studio 2015 Update 3 lorsque vous spécifiez la [/std : c ++ dernière](../../build/reference/std-specify-language-standard-version.md) option du compilateur. À partir de Visual C++ 2017 version 15.5, le compilateur prend en charge les définitions de l’espace de noms composé lorsque le [/std : c ++ 17](../../build/reference/std-specify-language-standard-version.md) option est spécifiée.

## <a name="examples"></a>Exemples

Cet exemple génère l’erreur C2653, car un nom de l’étendue est utilisé mais non déclaré. Le compilateur attend un nom de classe, structure, union ou espace de noms avant un opérateur de portée ( :).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

Dans le code qui n’est pas compilé pour C ++ 17 ou normes ultérieures, espaces de noms imbriqués doivent utiliser une déclaration d’espace de noms explicite à chaque niveau d’imbrication :

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
