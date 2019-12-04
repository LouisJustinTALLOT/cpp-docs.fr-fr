---
title: Erreur du compilateur C2940
ms.date: 11/04/2016
f1_keywords:
- C2940
helpviewer_keywords:
- C2940
ms.assetid: af6bf2bf-8de6-4cfd-bbf0-4c6b32a30edf
ms.openlocfilehash: 9477a2da32040db67a143a59d940c5f1cbe94904
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740440"
---
# <a name="compiler-error-c2940"></a>Erreur du compilateur C2940

'classe' : type-class-id redéfini comme typedef local

Vous ne pouvez pas utiliser une classe générique ou de modèle comme `typedef`local.

L’exemple suivant génère l’erreur C2940 :

```cpp
// C2940.cpp
template<class T>
struct TC {};
int main() {
   typedef int TC<int>;   // C2940
   typedef int TC;   // OK
}
```

L’erreur C2940 peut aussi se produire lors de l’utilisation de génériques :

```cpp
// C2940b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };

int main() {
   typedef int GC<int>;   // C2940
   typedef int GC;
}
```
