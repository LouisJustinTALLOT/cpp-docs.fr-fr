---
title: Erreur du compilateur C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: 0166cce6011017b8a18821666083f7c47f58b7a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508107"
---
# <a name="compiler-error-c2356"></a>Erreur du compilateur C2356

un segment d’initialisation ne doit pas changer au cours de l’unité de traduction

Causes possibles :

- `#pragma init_seg` précédé par un segment de code d’initialisation

- `#pragma init_seg` précédé par un autre `#pragma init_seg`

Pour résoudre, déplacez le code d’initialisation de segment au début du module. Si plusieurs zones doivent être initialisés, de les déplacer pour séparer les modules.

L’exemple suivant génère l’erreur C2356 :

```
// C2356.cpp
#pragma warning(disable : 4075)

int __cdecl myexit(void (__cdecl *)());
int __cdecl myexit2(void (__cdecl *)());

#pragma init_seg(".mine$m",myexit)
#pragma init_seg(".mine$m",myexit2)   // C2356
```