---
description: 'En savoir plus sur : erreur du compilateur C3849'
title: Erreur du compilateur C3849
ms.date: 11/04/2016
f1_keywords:
- C3849
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
ms.openlocfilehash: 6dbe4656eea2691c1c77c1afa389be80ab76af18
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255351"
---
# <a name="compiler-error-c3849"></a>Erreur du compilateur C3849

un appel de style fonction sur une expression de type’type’perdrait les qualificateurs const et/ou volatile pour toutes les surcharges d’opérateur nombre disponibles

Une variable avec un type const-volatile spécifié ne peut appeler que des fonctions membres définies avec des qualifications const-volatile identiques ou supérieures.

Pour corriger cette erreur, fournissez une fonction membre appropriée. Vous ne pouvez pas exécuter une conversion sur un objet qualifié const ou volatile lorsque la conversion provoque une perte de qualification. Vous pouvez obtenir des qualificateurs, mais vous ne pouvez pas perdre de qualificateurs dans une conversion.

Les exemples suivants génèrent des C3849 :

```cpp
// C3849.cpp
void glbFunc3(int i, char c)
{
   i;
}
typedef void (* pFunc3)(int, char);

void glbFunc2(int i)
{
   i;
}

typedef void (* pFunc2)(int);

void glbFunc1()
{
}
typedef void (* pFunc1)();

struct S4
{
   operator ()(int i)
   {
      i;
   }

   operator pFunc1() const
   {
      return &glbFunc1;
   }

   operator pFunc2() volatile
   {
      return &glbFunc2;
   }

   operator pFunc3()
   {
      return &glbFunc3;
   }

   // operator pFunc1() const volatile
   // {
   //    return &glbFunc1;
   // }
};

int main()
{
   // Cannot call any of the 4 overloads of "operator ()(.....)" and
   // "operator pFunc()" because none is declared as "const volatile"
   const volatile S4 s4;  // can only call cv member functions of S4
   s4();   // C3849 to resolve, uncomment member function
}
```
