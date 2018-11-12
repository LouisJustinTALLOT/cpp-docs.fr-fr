---
title: Erreur du compilateur C3854
ms.date: 11/04/2016
f1_keywords:
- C3854
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
ms.openlocfilehash: 3b48e2c65003537102864fdafe7db70b06ade029
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437789"
---
# <a name="compiler-error-c3854"></a>Erreur du compilateur C3854

expression à gauche de '=' correspond à une fonction. Impossible d’assigner à une fonction (une fonction n’est pas une l-value)

Une référence ne peut pas être réinitialisée. Annulation d’une référence à une fonction génère une fonction, qui est une rvalue, à laquelle vous ne pouvez pas affecter. Par conséquent, vous ne pouvez pas affecter une référence à une fonction.

L’exemple suivant génère l’erreur C3854 :

```
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