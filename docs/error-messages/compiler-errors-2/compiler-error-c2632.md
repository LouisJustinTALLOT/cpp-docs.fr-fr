---
title: Erreur du compilateur C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: f69d43bf50f5f13957e49d1e9ffa798a3db5a7b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754691"
---
# <a name="compiler-error-c2632"></a>Erreur du compilateur C2632

'type1 'suivi de’type2 'n’est pas conforme

Cette erreur peut être provoquée s’il manque du code entre deux spécificateurs de type.

L’exemple suivant génère l’C2632 :

```cpp
// C2632.cpp
int float i;   // C2632
```

Cette erreur peut également être générée en raison du travail de conformité du compilateur pour Visual Studio .NET 2003. `bool` est désormais un type approprié. Dans les versions précédentes, `bool` était un typedef, et vous pouviez créer des identificateurs portant ce nom.

L’exemple suivant génère l’C2632 :

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Pour résoudre cette erreur afin que le code soit valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, renommez l’identificateur.
