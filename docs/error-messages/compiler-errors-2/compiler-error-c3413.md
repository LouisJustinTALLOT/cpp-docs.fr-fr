---
title: Erreur du compilateur C3413
ms.date: 11/04/2016
f1_keywords:
- C3413
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
ms.openlocfilehash: 3065478cfff51f2463d4efba7f5a7dafc482fa65
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743014"
---
# <a name="compiler-error-c3413"></a>Erreur du compilateur C3413

'nom' : instanciation explicite non valide

Le compilateur a détecté une instanciation explicite incorrecte.

L’exemple suivant génère l’erreur C3413 :

```cpp
// C3413.cpp
template
class MyClass {};   // C3413
```

Solution possible :

```cpp
// C3413b.cpp
// compile with: /c
template <class T>
class MyClass {};

template <>
class MyClass<int> {};
```
