---
title: Erreur du compilateur C2944
ms.date: 11/04/2016
f1_keywords:
- C2944
helpviewer_keywords:
- C2944
ms.assetid: f209e668-e72f-442a-a438-8c4ff43a404a
ms.openlocfilehash: bed23b7d9117d1d1acad80f4f3d81e8b0b9d0252
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652203"
---
# <a name="compiler-error-c2944"></a>Erreur du compilateur C2944

'classe' : type-class-id redéfini comme argument de valeur d’un modèle

Vous ne pouvez pas utiliser une classe générique ou de modèle à la place d’un symbole comme argument de valeur de modèle.

L’exemple suivant génère l’erreur C2944 :

```
// C2944.cpp
// compile with: /c
template<class T>
class TC { };

template <int TC<int> > struct X1 { };   // C2944

template <class T > struct X2 {};
```

L’erreur C2944 peut également se produire lors de l’utilisation de génériques :

```
// C2944b.cpp
// compile with: /clr /c
generic<class T>
ref class GC {};

template <int GC<int> > struct X2 { };   // C2944
template <class T> struct X3 {};   // OK
```