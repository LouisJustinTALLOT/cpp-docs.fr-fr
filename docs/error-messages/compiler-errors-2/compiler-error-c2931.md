---
title: Erreur du compilateur C2931
ms.date: 11/04/2016
f1_keywords:
- C2931
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
ms.openlocfilehash: 8fffa6e272da64ca7baa35af635b2b0a7d40c6f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661329"
---
# <a name="compiler-error-c2931"></a>Erreur du compilateur C2931

'class' : type-class-id redéfini en tant que fonction membre d’'identifier'

Vous ne pouvez pas utiliser une classe ou un modèle générique en tant que fonction membre d’une autre classe.

Cette erreur peut être provoquée si des accolades sont incorrectement appariées.

L’exemple suivant génère l’erreur C2931 :

```
// C2931.cpp
// compile with: /c
template<class T>
struct TC { };
struct MyStruct {
   void TC<int>();   // C2931
};

struct TC2 { };
struct MyStruct2 {
   void TC2();
};
```

L’erreur C2931 peut également se produire lors de l’utilisation de génériques.

```
// C2931b.cpp
// compile with: /clr /c
generic<class T> ref struct GC {};
struct MyStruct {
   void GC<int>();   // C2931
   void GC2();   // OK
};
```