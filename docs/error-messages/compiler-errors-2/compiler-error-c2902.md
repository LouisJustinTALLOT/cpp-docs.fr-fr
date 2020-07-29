---
title: Erreur du compilateur C2902
ms.date: 11/04/2016
f1_keywords:
- C2902
helpviewer_keywords:
- C2902
ms.assetid: 89d78d0e-78e5-4c2c-a0f9-a60110e9395e
ms.openlocfilehash: 287ca42be0f1c09a6438af067feb299e7a01df6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230881"
---
# <a name="compiler-error-c2902"></a>Erreur du compilateur C2902

'jeton' : jeton inattendu après 'modèle', identificateur attendu

Le jeton qui suit le mot clé **`template`** n’est pas un identificateur.

L’exemple suivant génère l’erreur C2902 :

```cpp
// C2902.cpp
// compile with: /c
namespace N {
   template<class T> class X {};
   class Y {};
}
void g() {
   N::template + 1;   // C2902
}

void f() {
   N::template X<int> x1;   // OK
}
```

L’erreur C2902 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2902b.cpp
// compile with: /clr /c
namespace N {
   generic<class T> ref class GC {};
}

void f() {
   N::generic + 1;   // C2902
   N::generic GC<int>^ x;
}
```
