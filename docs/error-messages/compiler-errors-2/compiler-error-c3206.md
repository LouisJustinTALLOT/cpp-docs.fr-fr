---
description: 'En savoir plus sur : erreur du compilateur C3206'
title: Erreur du compilateur C3206
ms.date: 11/04/2016
f1_keywords:
- C3206
helpviewer_keywords:
- C3206
ms.assetid: d62995b5-e349-4418-bbe8-8a5e776ca7b0
ms.openlocfilehash: ea4ded5daebe0f002a3d0363fba125c2c02f332b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174011"
---
# <a name="compiler-error-c3206"></a>Erreur du compilateur C3206

'fonction' : argument type non valide pour 'param', liste d’arguments type absente dans le type de classe 'nom_type'

Une fonction avec modèle est définie comme prenant un argument de type de modèle. Toutefois, un argument de type de modèle a été passé.

L’exemple suivant génère l’erreur C3206 :

```cpp
// C3206.cpp
template <class T>
void f() {}

template <class T>
struct S {};

void f1() {
   f<S>();   // C3206
   // try the following line instead
   // f<S<int> >();
}
```

Solution possible :

```cpp
// C3206b.cpp
// compile with: /c
template <class T>
void f() {}

template <class T>
struct S {};

void f1() {
   f<S<int> >();
}
```

L’erreur C3206 peut également se produire lors de l’utilisation de génériques :

```cpp
// C3206c.cpp
// compile with: /clr
generic <class GT1>
void gf() {}

generic <class T>
value struct GS {};

int main() {
   gf<GS>();   // C3206
}
```

Solution possible :

```cpp
// C3206d.cpp
// compile with: /clr
generic <class GT1>
void gf() {}

generic <class T>
value struct GS {};

int main() {
   gf<GS<int> >();
}
```

Un modèle de classe n’est pas autorisé comme argument de type de modèle. L’exemple suivant déclenche l’C3206 :

```cpp
// C3206e.cpp
template <class T>
struct S {};

template <class T>
void func() {   // takes a type
   T<int> t;
}

int main() {
   func<S>();   // C3206 S is not a type.
}
```

Solution possible :

```cpp
// C3206f.cpp
template <class T>
struct S {};

template <class T>
void func() {   // takes a type
   T t;
}

int main() {
   func<S<int> >();
}
```

Si un paramètre de modèle de modèle est nécessaire, vous devez encapsuler la fonction dans une classe de modèle qui prend un paramètre de modèle de modèle :

```cpp
// C3206g.cpp
template <class T>
struct S {};

template<template<class> class TT>
struct X {
   static void func() {
      TT<int> t1;
      TT<char> t2;
   }
};

int main() {
   X<S>::func();
}
```
