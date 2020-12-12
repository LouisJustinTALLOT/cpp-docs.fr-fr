---
description: 'En savoir plus sur : erreur du compilateur C2653'
title: Erreur du compilateur C2653
ms.date: 11/30/2017
f1_keywords:
- C2653
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
ms.openlocfilehash: f3be7ade8a6dcfc6aa8c5a83cc8a055fc230789d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286148"
---
# <a name="compiler-error-c2653"></a>Erreur du compilateur C2653

> '*identificateur*' : n’est pas un nom de classe ou d’espace de noms

La syntaxe du langage requiert un nom de classe, de structure, d’Union ou d’espace de noms ici.

Cette erreur peut se produire lorsque vous utilisez un nom qui n’a pas été déclaré en tant que classe, structure, Union ou espace de noms devant un opérateur de portée. Pour résoudre ce problème, déclarez le nom ou incluez l’en-tête qui déclare le nom avant de l’utiliser.

C2653 est également possible si vous tentez de définir un espace de noms *composé*, un espace de noms qui contient un ou plusieurs noms d’espaces de noms imbriqués dans l’étendue. Les définitions d’espaces de noms composés ne sont pas autorisées en C++ avant C++ 17. Les espaces de noms composés sont pris en charge à partir de Visual Studio 2015 Update 3 quand vous spécifiez l’option de compilateur [/std : c + + latest](../../build/reference/std-specify-language-standard-version.md) . À compter de Visual Studio 2017 version 15,5, le compilateur prend en charge les définitions d’espaces de noms composés lorsque l’option [/std : c++ 17](../../build/reference/std-specify-language-standard-version.md) est spécifiée.

## <a name="examples"></a>Exemples

Cet exemple génère C2653, car un nom de portée est utilisé, mais n’est pas déclaré. Le compilateur attend un nom de classe, de structure, d’Union ou d’espace de noms avant un opérateur de portée ( ::).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

Dans le code qui n’est pas compilé pour les normes C++ 17 ou versions ultérieures, les espaces de noms imbriqués doivent utiliser une déclaration d’espace de noms explicite à chaque niveau d’imbrication :

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual Studio 2015 Update 3,
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
