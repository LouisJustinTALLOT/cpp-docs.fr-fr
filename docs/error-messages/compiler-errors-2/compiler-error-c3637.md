---
title: Erreur du compilateur C3637
ms.date: 11/04/2016
f1_keywords:
- C3637
helpviewer_keywords:
- C3637
ms.assetid: 72391377-8519-43d9-870a-73a6423deb74
ms.openlocfilehash: 84bb6717a563db20b2ce0c66f301d8e38d7722c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742546"
---
# <a name="compiler-error-c3637"></a>Erreur du compilateur C3637

'fonction' : une définition de fonction friend ne peut pas être une spécialisation d’un type de fonction

Une fonction friend a été définie de manière incorrecte pour un modèle ou un générique.

L’exemple suivant génère l’C3637 :

```cpp
// C3637.cpp
template <class T>
void f();

struct S {
   friend void f<int>() {}   // C3637
};
```

Solution possible :

```cpp
// C3637b.cpp
// compile with: /c
template <class T>
void f();

struct S {
   friend void f() {}
};
```

C3637 peut également se produire lors de l’utilisation de génériques :

```cpp
// C3637c.cpp
// compile with: /clr

generic <class T>
void gf();

struct S {
   friend void gf<int>() {}   // C3637
};
```

Solution possible :

```cpp
// C3637d.cpp
// compile with: /clr /c
generic <class T>
void gf();

struct S {
   friend void gf() {}
};
```
