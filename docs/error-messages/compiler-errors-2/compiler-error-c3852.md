---
description: 'En savoir plus sur : erreur du compilateur C3852'
title: Erreur du compilateur C3852
ms.date: 11/04/2016
f1_keywords:
- C3852
helpviewer_keywords:
- C3852
ms.assetid: 194e5c5e-0dfb-414e-86db-791c11eb610c
ms.openlocfilehash: f5bfeb5507943dc4f860b81912bfb6880621f290
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255234"
---
# <a name="compiler-error-c3852"></a>Erreur du compilateur C3852

'membre’ayant le type’type' : l’initialisation d’agrégats n’a pas pu initialiser ce membre

Une tentative a été faite pour assigner une initialisation par défaut dans le cadre d’une initialisation d’agrégat à un membre de données qui ne peut pas recevoir une initialisation par défaut dans une initialisation d’agrégats.

Les exemples suivants génèrent des C3852 :

```cpp
// C3852.cpp
struct S
{
   short s;
};

struct S1
{
   int i;
   const S s;
};

struct S2
{
   int i;
   char & rc;
};

int main()
{
   S1 s1 = { 1 };   // C3852 const member
   // try the following line instead
   // S1 s1 = { 1, 2 };

   S2 s2 = { 2 };   // C3852 reference member
   // try the following line instead
   // char c = 'a';
   S2 s2 = { 2, c };
}
```
