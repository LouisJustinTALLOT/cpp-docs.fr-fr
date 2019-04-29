---
title: Erreur du compilateur C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: b92d44bcfd04d4de7b39c5bdab5ee146d9b6693b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257632"
---
# <a name="compiler-error-c2632"></a>Erreur du compilateur C2632

'type1' suivi de 'type2' n’est pas conforme

Cette erreur peut être provoquée si le code entre deux spécificateurs de type est manquant.

L’exemple suivant génère C2632 :

```
// C2632.cpp
int float i;   // C2632
```

Cette erreur peut également être due à la mise en conformité du compilateur pour Visual Studio .NET 2003. `bool` est maintenant un type approprié. Dans les versions précédentes, `bool` était un typedef, et vous pouvez créer des identificateurs portant ce nom.

L’exemple suivant génère C2632 :

```
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Pour résoudre cette erreur, afin que le code soit valide dans les versions de Visual Studio .NET 2003 et de Visual Studio .NET de Visual C++, renommez l’identificateur.