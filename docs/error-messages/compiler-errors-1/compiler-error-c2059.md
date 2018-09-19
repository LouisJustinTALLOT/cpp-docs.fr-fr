---
title: Erreur du compilateur C2059 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2059
dev_langs:
- C++
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88d33ba33483ba8a2c9764f5336218a354d644e6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096949"
---
# <a name="compiler-error-c2059"></a>Erreur du compilateur C2059

Erreur de syntaxe : 'token'

Le jeton a provoqué une erreur de syntaxe.

L’exemple suivant génère un message d’erreur pour la ligne qui déclare `j`.

```
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

Pour déterminer la cause de l’erreur, examinez la ligne qui est répertoriée dans le message d’erreur, mais également les lignes au-dessus de lui. Si l’examen des lignes ne donne aucun indice sur le problème, essayez de le commenter la ligne qui est répertoriée dans le message d’erreur et éventuellement plusieurs lignes au-dessus de lui.

Si le message d’erreur se produit sur un symbole qui suit immédiatement un `typedef` variable, assurez-vous que la variable est définie dans le code source.

Vous pouvez obtenir l’erreur C2059 si un symbole a la valeur nothing, comme peut se produire lorsque **/D** `symbol` **=** sert à compiler.

```
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

Un autre cas dans lequel l’erreur C2059 peut se produire est lorsque vous compilez une application qui spécifie une structure dans les arguments par défaut pour une fonction. La valeur par défaut pour un argument doit être une expression. Une liste d’initialiseurs, par exemple, un utilisée pour initialiser une structure, n’est pas une expression.  Pour résoudre ce problème, définissez un constructeur pour effectuer l’initialisation requise.

L’exemple suivant génère l’erreur C2059 :

```
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

Vous pouvez également obtenir l’erreur C2059 si vous définissez une classe de modèle de membre ou une fonction en dehors de la classe. Pour plus d’informations, consultez [l’article de la Base de connaissances 241949](http://support.microsoft.com/kb/241949).

L’erreur C2059 peut se produire pour une conversion incorrecte.

L’exemple suivant génère l’erreur C2059 :

```
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

L’erreur C2059 peut également se produire si vous essayez de créer un espace de noms qui contient un point.

L’exemple suivant génère l’erreur C2059 :

```
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

L’erreur C2059 peut se produire lorsqu’un opérateur qui permettre qualifier un nom (`::`, `->`, et `.`) doit être suivi par le mot clé `template`, comme illustré dans cet exemple :

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};

```

Par défaut, C++ suppose que `AY::Rebind` n’est pas un modèle ; par conséquent, ce qui suit `<` est interprété comme un inférieur-signe supérieur.  Vous devez indiquer au compilateur explicitement qui `Rebind` est un modèle afin de pouvoir analyser correctement le crochet angulaire. Pour corriger cette erreur, utilisez le `template` mot clé sur le nom du type dépendants, comme illustré ici :

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};

```