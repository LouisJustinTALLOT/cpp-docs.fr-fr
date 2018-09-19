---
title: Erreur du compilateur C2356 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2356
dev_langs:
- C++
helpviewer_keywords:
- C2356
ms.assetid: 84d5a816-9a61-4d45-9978-38e485bbf767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dfad1703b36e1cd995207d35b99b323c883f828
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065411"
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