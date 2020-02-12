---
title: Erreur du compilateur C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: f91eb428fcb49c81187788730128545916955790
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127658"
---
# <a name="compiler-error-c2059"></a>Erreur du compilateur C2059

erreur de syntaxe : 'Token'

Le jeton a provoqué une erreur de syntaxe.

L’exemple suivant génère un message d’erreur pour la ligne qui déclare `j`.

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

Pour déterminer la cause de l’erreur, examinez non seulement la ligne qui est indiquée dans le message d’erreur, mais également les lignes au-dessus. Si l’examen des lignes ne donne aucune indication sur le problème, essayez de commenter la ligne qui est indiquée dans le message d’erreur et peut-être plusieurs lignes au-dessus de celle-ci.

Si le message d’erreur se produit sur un symbole qui suit immédiatement une variable `typedef`, assurez-vous que la variable est définie dans le code source.

L’exception C2059 est levée lorsqu’un nom de symbole de préprocesseur est réutilisé comme identificateur. Dans l’exemple suivant, le compilateur voit `DIGITS.ONE` comme le nombre 1, qui n’est pas valide en tant que nom d’élément enum :

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

Vous pouvez obtenir C2059 si un symbole prend la valeur Nothing, comme cela peut se produire lorsque l' **=** de_symboles_ **/d**est utilisée pour compiler.

```cpp
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

L’apparition d’une application qui spécifie une structure dans les arguments par défaut d’une fonction est un autre cas dans lequel C2059 peut se produire. La valeur par défaut d’un argument doit être une expression. Une liste d’initialiseurs, par exemple, qui est utilisée pour initialiser une structure, n’est pas une expression.  Pour résoudre ce problème, définissez un constructeur pour effectuer l’initialisation requise.

L’exemple suivant génère l’exemple C2059 :

```cpp
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

C2059 peut se produire pour un cast mal formé.

L’exemple suivant génère l’exemple C2059 :

```cpp
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

L’opération C2059 peut également se produire si vous tentez de créer un nom d’espace de noms qui contient un point.

L’exemple suivant génère l’exemple C2059 :

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

C2059 peut se produire lorsqu’un opérateur qui peut qualifier un nom (`::`, `->`et `.`) doit être suivi du mot clé `template`, comme illustré dans cet exemple :

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

Par défaut, C++ suppose que `AY::Rebind` n’est pas un modèle ; par conséquent, la `<` suivante est interprétée comme un signe inférieur à.  Vous devez indiquer au compilateur explicitement que `Rebind` est un modèle afin qu’il puisse analyser correctement le Chevron. Pour corriger cette erreur, utilisez le mot clé `template` sur le nom du type dépendant, comme illustré ici :

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
