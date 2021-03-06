---
description: 'En savoir plus sur : erreur du compilateur C3854'
title: Erreur du compilateur C3854
ms.date: 11/04/2016
f1_keywords:
- C3854
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
ms.openlocfilehash: f6c2399ff4c38cfbb306bd90e5bb5e96b34220eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328159"
---
# <a name="compiler-error-c3854"></a>Erreur du compilateur C3854

l’expression à gauche de' = 'prend la valeur d’une fonction. Impossible d’assigner à une fonction (une fonction n’est pas une l-value)

Une référence ne peut pas être réinitialisée. Le déréférencement d’une référence à une fonction produit une fonction, qui est une rvalue, à laquelle vous ne pouvez pas assigner. Par conséquent, vous ne pouvez pas assigner par le biais d’une référence à une fonction.

L’exemple suivant génère l’C3854 :

```cpp
// C3854.cpp
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);
typedef int (* pFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   pFunc_t pf = &afunc;   // OK initializing a pointer to function

   *pf = &afunc;   // C3854
   // try the following line instead
   // pf = &afunc;
   *rf = &afunc;   // C3854
}
```
