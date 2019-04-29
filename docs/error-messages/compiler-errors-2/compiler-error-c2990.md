---
title: Erreur du compilateur C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: f7327b7d2b0cc9fa4b617a9a6033116c43db6258
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366327"
---
# <a name="compiler-error-c2990"></a>Erreur du compilateur C2990

'classe' : type sans classe déjà été déclaré comme un type de classe

Non générique ou la classe de modèle redéfinit une classe générique ou de modèle. Vérifiez les fichiers d’en-tête pour les conflits.

L’exemple suivant génère l’erreur C2990 :

```
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

L’erreur C2990 peut également se produire lors de l’utilisation de génériques :

```
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

L’erreur C2990 peut également se produire en raison d’une modification avec rupture dans le compilateur Visual C++ pour Visual C++ 2005 ; le compilateur exige désormais que plusieurs déclarations pour le même type soient identiques en ce qui concerne la spécification du modèle.

L’exemple suivant génère l’erreur C2990 :

```
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