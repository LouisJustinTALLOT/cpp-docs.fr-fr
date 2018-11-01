---
title: Erreur du compilateur C3855
ms.date: 11/04/2016
f1_keywords:
- C3855
helpviewer_keywords:
- C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
ms.openlocfilehash: 12ee1c6aa5f414a9cf3084831c956514593102c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478128"
---
# <a name="compiler-error-c3855"></a>Erreur du compilateur C3855

'classe' : paramètre de type 'param' est incompatible avec la déclaration

Le compilateur a trouvé les modèle sans type ou paramètres génériques avec des noms différents. Cela peut se produire lorsqu’un paramètre de modèle spécifié dans la définition d’une spécialisation de modèle est incompatible avec sa déclaration.

L’exemple suivant génère l’erreur C3855 :

```
// C3855.cpp
template <int N>
struct C {
   void f();
};

template <char N>
void C<N>::f() {}   // C3855
```

Solution possible :

```
// C3855b.cpp
// compile with: /c
template <int N>
struct C {
   void f();
};

template <int N>
void C<N>::f() {}
```

C3855 peut également se produire lors de l’utilisation de génériques :

```
// C3855c.cpp
// compile with: /clr
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GC1<T>::GC2 { };   // C3855
```

Solution possible :

```
// C3855d.cpp
// compile with: /clr /c
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
ref struct GC1<T>::GC2 { };
```