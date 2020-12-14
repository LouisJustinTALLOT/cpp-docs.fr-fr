---
description: 'En savoir plus sur : erreur du compilateur C2764'
title: Erreur du compilateur C2764
ms.date: 11/04/2016
f1_keywords:
- C2764
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
ms.openlocfilehash: c700286a840c518597947f21f0455bc711f68275
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239530"
---
# <a name="compiler-error-c2764"></a>Erreur du compilateur C2764

'param' : paramètre de modèle non utilisé ou pouvant être déduit dans la spécialisation partielle’spécialisation'

Un paramètre de modèle n’est pas utilisé dans une spécialisation partielle. Cela rend la spécialisation partielle inutilisable, car le paramètre de modèle ne peut pas être déduit.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2764 :

```cpp
// C2764.cpp
#include <stdio.h>
template <class T1, class T2>
struct S  {
   int m_i;
};

template <class T1, class T2>
struct S<int, T2*> {   // C2764
// try the following line instead
// struct S<T1(*)(T2), T2*> {
   char m_c;
};

int main() {
   S<int, char> s1;
   S<void (*)(short), short *> s2;
   s2.m_c = 10;
   s1.m_i = s2.m_c;
   printf_s("%d\n", s1.m_i);
}
```
