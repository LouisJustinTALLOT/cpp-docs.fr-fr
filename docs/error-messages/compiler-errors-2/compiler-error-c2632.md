---
description: 'En savoir plus sur : erreur du compilateur C2632'
title: Erreur du compilateur C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: b6f1091b512d3a01efa933c998bde3d0885bbff1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123511"
---
# <a name="compiler-error-c2632"></a>Erreur du compilateur C2632

'type1 'suivi de’type2 'n’est pas conforme

Cette erreur peut être provoquée s’il manque du code entre deux spécificateurs de type.

L’exemple suivant génère l’C2632 :

```cpp
// C2632.cpp
int float i;   // C2632
```

Cette erreur peut également être générée en raison du travail de conformité du compilateur pour Visual Studio .NET 2003. **`bool`** est désormais un type approprié. Dans les versions précédentes, **`bool`** était un typedef, et vous pouviez créer des identificateurs portant ce nom.

L’exemple suivant génère l’C2632 :

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Pour résoudre cette erreur afin que le code soit valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, renommez l’identificateur.
