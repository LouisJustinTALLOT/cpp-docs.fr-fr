---
description: 'En savoir plus sur : erreur du compilateur C2952'
title: Erreur du compilateur C2952
ms.date: 11/04/2016
f1_keywords:
- C2952
helpviewer_keywords:
- C2952
ms.assetid: a40e18a2-d02c-4511-854f-6c6fd6789a1a
ms.openlocfilehash: 00fb882378a4e72f84cc8077df2d3dcdfda1b361
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210604"
---
# <a name="compiler-error-c2952"></a>Erreur du compilateur C2952

'déclaration' : la liste de paramètres est absente de la déclaration de type

Une déclaration de modèle est incorrecte.

L’exemple suivant génère l’erreur C2952 :

```cpp
// C2952.cpp
// compile with: /c
template <class T>
struct S {
   template <class T1>
   struct S1 {
      void f();
   };
};

template <class T> void S<T>::S1<T>::f() {}   // C2952

// OK
template <class T>
template <class T1>
void S<T>::S1<T1>::f() {}
```

L’erreur C2952 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2952b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC {
   generic <class T1>
   ref struct GC1 {
      void f();
   };
};

generic <class T> void GC<T>::GC1<T>::f() {}   // C2952

// OK
generic <class T>
generic <class T1>
void GC<T>::GC1<T1>::f() {}
```
