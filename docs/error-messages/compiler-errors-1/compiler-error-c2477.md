---
description: 'En savoir plus sur : erreur du compilateur C2477'
title: Erreur du compilateur C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 50cbb3523e6dc30dc465876435db40a80e2768fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164391"
---
# <a name="compiler-error-c2477"></a>Erreur du compilateur C2477

'membre' : les données membres static ne peuvent pas être initialisées via une classe dérivée

Une donnée membre statique d’une classe de modèle a été initialisée de manière incorrecte. Il s’agit d’une modification avec rupture avec les versions du compilateur Microsoft C++ antérieures à Visual Studio .NET 2003, afin de se conformer à la norme ISO C++.

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
