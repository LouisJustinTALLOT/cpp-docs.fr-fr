---
title: Compilateur avertissement (niveau 1) C4508 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5abc1d81c3e94c02a63f73c84f3f5e5c7e9b0b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038937"
---
# <a name="compiler-warning-level-1-c4508"></a>Avertissement du compilateur (niveau 1) C4508

'fonction' : fonction doit retourner une valeur ; supposé de type de retour 'void'

La fonction n’a aucun type de retour spécifié. Dans ce cas, C4430 doit également se déclencher et le compilateur implémente le correctif signalé par l’erreur C4430 (valeur par défaut est de type int).

Pour résoudre cet avertissement, déclarer explicitement le type de retour de fonctions.

L’exemple suivant génère C4508 :

```
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```