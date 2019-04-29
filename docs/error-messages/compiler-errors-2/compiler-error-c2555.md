---
title: Erreur du compilateur C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: cc6c3a3a29665ccf65b77a3d9866986cb0a46b9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353207"
---
# <a name="compiler-error-c2555"></a>Erreur du compilateur C2555

'classe1::fonction1' : fonction virtuelle de substitution type de retour est différent et n’est pas covariant 'classe2::fonction2'

Une fonction virtuelle et une fonction de substitution dérivée ont des listes de paramètres sont identiques, mais différents types de retournés. Une fonction de substitution dans une classe dérivée ne peuvent pas différer d’une fonction virtuelle dans une classe de base uniquement par son type de retour.

Pour résoudre cette erreur, effectuez un cast de la valeur de retour après la fonction virtuelle a été appelée.

Vous pouvez également voir cette erreur si vous compilez avec/CLR.   Par exemple, Visual C++ équivalent à la déclaration c# suivante :

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

est

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

L’exemple suivant génère l’erreur C2555 :

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```