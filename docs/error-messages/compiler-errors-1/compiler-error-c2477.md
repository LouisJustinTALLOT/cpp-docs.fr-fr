---
title: Erreur du compilateur C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: aa276ea839f11574609b183d78b46e08581a1b51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743651"
---
# <a name="compiler-error-c2477"></a>Erreur du compilateur C2477

'membre' : les données membres static ne peuvent pas être initialisées via une classe dérivée

Une donnée membre statique d’une classe de modèle a été initialisée de manière incorrecte. Il s’agit d’une modification avec rupture avec les C++ versions du compilateur Microsoft antérieures à Visual Studio .NET 2003, afin de se conformer à la norme ISO C++ .

L’exemple suivant génère l’C2477 :

```cpp
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```
