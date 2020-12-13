---
description: 'En savoir plus sur : erreur du compilateur C3855'
title: Erreur du compilateur C3855
ms.date: 11/04/2016
f1_keywords:
- C3855
helpviewer_keywords:
- C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
ms.openlocfilehash: eeb0dbda6f67d59470cd021ff37877d3a5201862
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328146"
---
# <a name="compiler-error-c3855"></a>Erreur du compilateur C3855

'classe' : le paramètre de type’param’est incompatible avec la déclaration

Le compilateur a trouvé des paramètres génériques ou de modèle sans type avec des noms différents. Cela peut se produire lorsqu’un paramètre de modèle spécifié dans la définition d’une spécialisation de modèle est incompatible avec sa déclaration.

L’exemple suivant génère l’C3855 :

```cpp
// C3855.cpp
template <int N>
struct C {
   void f();
};

template <char N>
void C<N>::f() {}   // C3855
```

Solution possible :

```cpp
// C3855b.cpp
// compile with: /c
template <int N>
struct C {
   void f();
};

template <int N>
void C<N>::f() {}
```

C3855 peut également se produire lors de l’utilisation de génériques :

```cpp
// C3855c.cpp
// compile with: /clr
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GC1<T>::GC2 { };   // C3855
```

Solution possible :

```cpp
// C3855d.cpp
// compile with: /clr /c
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
ref struct GC1<T>::GC2 { };
```
