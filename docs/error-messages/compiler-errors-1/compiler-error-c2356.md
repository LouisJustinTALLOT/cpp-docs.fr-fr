---
description: 'En savoir plus sur : erreur du compilateur C2356'
title: Erreur du compilateur C2356
ms.date: 11/04/2016
f1_keywords:
- C2356
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
ms.openlocfilehash: c0e2d179bb41e6cbae674d92976674ab90f05c0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328335"
---
# <a name="compiler-error-c2356"></a>Erreur du compilateur C2356

le segment d’initialisation ne doit pas changer pendant l’unité de traduction

Causes possibles :

- `#pragma init_seg` précédé du code d’initialisation de segment

- `#pragma init_seg` précédé d’un autre `#pragma init_seg`

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
