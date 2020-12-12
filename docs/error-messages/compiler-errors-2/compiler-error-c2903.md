---
description: 'En savoir plus sur : erreur du compilateur C2903'
title: Erreur du compilateur C2903
ms.date: 11/04/2016
f1_keywords:
- C2903
helpviewer_keywords:
- C2903
ms.assetid: bf6b223f-4921-48c7-82b9-ff318b42c801
ms.openlocfilehash: 0013be28857ac8e138a78cb7a4e3502cdc04536b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270730"
---
# <a name="compiler-error-c2903"></a>Erreur du compilateur C2903

'identifier' : le symbole n’est ni un modèle de classe, ni un modèle de fonction

Le code tente d’effectuer une instanciation explicite d’un élément autre qu’un modèle.

L’exemple suivant génère l’erreur C2903 :

```cpp
// C2903.cpp
// compile with: /c
namespace N {
   template<class T> class X {};
   class Y {};
}
void g() {
   N::template Y y;   // C2903
   N::X<N::Y> y;   // OK
}
```

L’erreur C2903 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2903b.cpp
// compile with: /clr /c
namespace N {
   class Y {};
   generic<class T> ref class Z {};
}

void f() {
   N::generic Y y;   // C2903
   N:: generic Z<int>^ z;   // OK
}
```
