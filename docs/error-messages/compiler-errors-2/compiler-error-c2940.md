---
description: 'En savoir plus sur : erreur du compilateur C2940'
title: Erreur du compilateur C2940
ms.date: 11/04/2016
f1_keywords:
- C2940
helpviewer_keywords:
- C2940
ms.assetid: af6bf2bf-8de6-4cfd-bbf0-4c6b32a30edf
ms.openlocfilehash: 2601e32d2e52d332e4f6443dde23b544d955aac1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249683"
---
# <a name="compiler-error-c2940"></a>Erreur du compilateur C2940

'classe' : type-class-id redéfini comme typedef local

Vous ne pouvez pas utiliser une classe générique ou de modèle comme local **`typedef`** .

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
