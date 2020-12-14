---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4636'
title: Avertissement du compilateur (niveau 3) C4636
ms.date: 11/04/2016
f1_keywords:
- C4636
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
ms.openlocfilehash: 09ba549c4fcd7f48a1a6ed7e1e16bc293c7ad884
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238113"
---
# <a name="compiler-warning-level-3-c4636"></a>Avertissement du compilateur (niveau 3) C4636

Commentaire de document XML appliqué à 'construct' : la balise requiert un attribut '' non vide.

Une balise, telle que `cref`, ne possédait aucune valeur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4636.

```cpp
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
