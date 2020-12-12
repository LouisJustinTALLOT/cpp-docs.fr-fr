---
description: 'En savoir plus sur : erreur du compilateur C3203'
title: Erreur du compilateur C3203
ms.date: 11/04/2016
f1_keywords:
- C3203
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
ms.openlocfilehash: ea0c54fc54cfa19d4d41a712fba0fa24fe03abb5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291855"
---
# <a name="compiler-error-c3203"></a>Erreur du compilateur C3203

'type' : la classe non spécialisée modèle ou générique ne peut pas être utilisée comme argument modèle ou générique pour le paramètre modèle ou générique 'param' ; type réel attendu

Vous avez passé un argument non valide à une classe modèle ou générique. La classe modèle ou générique attend un type en tant que paramètre.

Cette erreur peut être générée en raison du travail de conformité du compilateur pour Visual Studio 2005 : un modèle de classe non spécialisé ne peut pas être utilisé en tant qu’argument de modèle dans une liste de classes de base. Pour résoudre l'erreur C3203, ajoutez explicitement le ou les paramètres de type de modèle au nom de la classe de modèle quand vous l'utilisez en tant que paramètre de modèle dans une liste de classes de base.

```cpp
// C3203.cpp
template< typename T >
struct X {
   void f(X) {}
};

template< typename T >
struct Y : public X<Y> {   // C3203
// try the following line instead
// struct Y : public X<Y<T> > {
   void f(Y) {}
};

int main() {
   Y<int> y;
}
```

L'exemple suivant génère l'erreur C3203 et montre comment la corriger :

```cpp
// C3203_b.cpp
// compile with: /c
template <class T>
struct S1 {};

template <class T>
class C1 {};

typedef C1<S1> MyC1;   // C3203

// OK
template <template <class> class T>
class C2 {};

typedef C2<S1> MyC1;

template <class T>
class C3 {};

typedef C3<S1<int> > MyC12;
```

L'erreur C3203 peut également se produire lors de l'utilisation de génériques :

```cpp
// C3203_c.cpp
// compile with: /clr /c
generic <class T>
value struct GS1 {};

generic <class T>
value struct GC1 {};

typedef GC1<GS1> MyGC1;   // C3203
typedef GC1<GS1<int> > MyGC2;   // OK
```
