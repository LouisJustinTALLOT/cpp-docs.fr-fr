---
title: Erreur du compilateur C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ebf3e4a3aff48311edd5fb95b01a7b2d23990231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202422"
---
# <a name="compiler-error-c2555"></a>Erreur du compilateur C2555

'classe1 :: function1 ' : le type de retour de la fonction virtuelle de substitution diffère et n’est pas covariant de’Class2 :: fonction2 '

Une fonction virtuelle et une fonction de substitution dérivée ont des listes de paramètres identiques, mais des types de retour différents. Une fonction de substitution dans une classe dérivée ne peut pas différer d’une fonction virtuelle dans une classe de base uniquement par son type de retour.

Pour résoudre cette erreur, effectuez un cast de la valeur de retour après l’appel de la fonction virtuelle.

Vous pouvez également voir cette erreur si vous compilez avec/CLR.   Par exemple, l’équivalent C++ visuel de la Déclaration C# suivante :

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

L’exemple suivant génère l’C2555 :

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
