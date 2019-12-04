---
title: Erreur du compilateur C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 1c58c2d5da0049ec670e11c930b397caec3cbbee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751519"
---
# <a name="compiler-error-c2990"></a>Erreur du compilateur C2990

'class' : type sans classe tel qu’il a déjà été déclaré comme type de classe

La classe non générique ou de modèle redéfinit une classe générique ou de modèle. Recherchez les conflits dans les fichiers d’en-tête.

L’exemple suivant génère l’C2990 :

```cpp
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 peut également se produire en raison d’une modification avec rupture C++ dans le compilateur Microsoft pour Visual Studio 2005 ; le compilateur exige désormais que plusieurs déclarations pour le même type soient identiques en ce qui concerne la spécification du modèle.

L’exemple suivant génère l’C2990 :

```cpp
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```
