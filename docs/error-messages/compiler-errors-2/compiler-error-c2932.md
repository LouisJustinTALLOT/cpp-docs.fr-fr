---
title: Erreur du compilateur C2932
ms.date: 11/04/2016
f1_keywords:
- C2932
helpviewer_keywords:
- C2932
ms.assetid: c28e88d9-e654-4367-bfb4-13c780bca9bd
ms.openlocfilehash: c1afe47e27cb38b2a3886854ce6efe34273c9132
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750102"
---
# <a name="compiler-error-c2932"></a>Erreur du compilateur C2932

'class' : type-class-id redéfini comme donnée membre de 'identifier'

Vous ne pouvez pas utiliser une classe générique ou de modèle en tant que membre de données.

L’exemple suivant génère l’erreur C2932 :

```cpp
// C2932.cpp
// compile with: /c
template<class T>
struct TC {};

struct MyStruct {
   int TC<int>;   // C2932
   int TC;   // OK
};
```

L’erreur C2932 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2932b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};

struct MyStruct {
   int GC<int>;   // C2932
   int GC;   // OK
};
```
