---
title: Erreur du compilateur C2952 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2952
dev_langs:
- C++
helpviewer_keywords:
- C2952
ms.assetid: a40e18a2-d02c-4511-854f-6c6fd6789a1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a9dd87eb13b475cd40da78211d0851928ceafec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089266"
---
# <a name="compiler-error-c2952"></a>Erreur du compilateur C2952

'déclaration' : la liste de paramètres est absente de la déclaration de type

Une déclaration de modèle est incorrecte.

L’exemple suivant génère l’erreur C2952 :

```
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

```
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