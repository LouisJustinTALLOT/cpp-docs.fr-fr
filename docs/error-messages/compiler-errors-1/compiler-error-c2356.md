---
title: Erreur du compilateur C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: e306c5a8f9175bc3c7902b20263aa2e451944182
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759930"
---
# <a name="compiler-error-c2356"></a>Erreur du compilateur C2356

le segment d’initialisation ne doit pas changer pendant l’unité de traduction

Causes possibles :

- `#pragma init_seg` précédée du code d’initialisation de segment

- `#pragma init_seg` précédée d’un autre `#pragma init_seg`

Pour résoudre le code, déplacez le code d’initialisation du segment au début du module. Si plusieurs zones doivent être initialisées, déplacez-les vers des modules distincts.

L’exemple suivant génère l’C2356 :

```cpp
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```
