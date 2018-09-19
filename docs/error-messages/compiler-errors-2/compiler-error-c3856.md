---
title: Erreur du compilateur C3856 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3856
dev_langs:
- C++
helpviewer_keywords:
- C3856
ms.assetid: 242d9322-c325-4f20-be58-b2be6da56d60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfe4a53e9d2f48dab479fa9403ede5c8a8c4a1b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098236"
---
# <a name="compiler-error-c3856"></a>Erreur du compilateur C3856

'type' : classe n’est pas un type de classe

Cette erreur se produit généralement lorsqu’il existe plus générique ou paramètre de modèle répertorie au point de définition qu’il avait au point de déclaration.

L’exemple suivant génère l’erreur C3856 :

```
// C3856.cpp
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>   // C3856
template <class T1>
template <class T2>  // extra template parameter list in definition
struct S<T>::S1{};
```

Solution possible :

```
// C3856b.cpp
// compile with: /c
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1{};
```

C3856 peut également se produire lors de l’utilisation de génériques :

```
// C3856c.cpp
// compile with: /clr
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GS<T>::GS2 {};   // C3856
```

Solution possible :

```
// C3856d.cpp
// compile with: /clr /c
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
ref struct GS<T>::GS2 {};
```