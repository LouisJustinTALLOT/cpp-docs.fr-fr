---
title: Erreur du compilateur C2764 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2764
dev_langs:
- C++
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3456a9bcca6df1a658600ecf6085bb060f988b3f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043792"
---
# <a name="compiler-error-c2764"></a>Erreur du compilateur C2764

'param' : paramètre de modèle non utilisé ou pouvant être déduit dans la spécialisation partielle 'specialization'

Un paramètre de modèle n’est pas utilisé dans une spécialisation partielle. Cela rend la spécialisation partielle inutilisable, car le paramètre de modèle ne peut pas être déduit.

## <a name="example"></a>Exemple

L’exemple suivant génère C2764 :

```
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