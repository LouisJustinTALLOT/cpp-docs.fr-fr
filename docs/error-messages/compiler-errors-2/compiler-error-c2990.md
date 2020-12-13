---
description: 'En savoir plus sur : erreur du compilateur C2990'
title: Erreur du compilateur C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 80aa15940420e9d3e452f2c3a93eefe94fd1561b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328255"
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

C2990 peut également se produire en raison d’une modification avec rupture dans le compilateur Microsoft C++ pour Visual Studio 2005 ; le compilateur exige désormais que plusieurs déclarations pour le même type soient identiques en ce qui concerne la spécification du modèle.

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
