---
title: Avertissement du compilateur (niveau 3) C4636
ms.date: 11/04/2016
f1_keywords:
- C4636
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
ms.openlocfilehash: 7327189a61e2545bb6003cd95e1ddb116f9f7c94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401707"
---
# <a name="compiler-warning-level-3-c4636"></a>Avertissement du compilateur (niveau 3) C4636

Commentaire de document XML appliqué à 'construct' : la balise requiert un attribut '' non vide.

Une balise, telle que `cref`, ne possédait aucune valeur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4636.

```
// C4636.cpp
// compile with: /clr /doc /W3 /c
/// <see cref=''/>
// /// <see cref='System::Exception'/>
ref struct A {   // C4636
   void f(int);
};

// OK
/// <see cref='System::Exception'/>
ref struct B {
   void f(int);
};
```