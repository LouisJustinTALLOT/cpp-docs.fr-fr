---
title: Erreur du compilateur C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: a9c6465ef87c12135ad4e6709741f0027d8ea3c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638189"
---
# <a name="compiler-error-c2150"></a>Erreur du compilateur C2150

> «*identificateur*' : champ de bits doit être de type 'int', 'signed int' ou 'unsigned int'

Le type de base pour un champ de bits doit être `int`, `signed int`, ou `unsigned int`.

## <a name="example"></a>Exemple

Cet exemple montre comment vous pouvez rencontrer C2150, et comment vous pouvez y remédier :

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```