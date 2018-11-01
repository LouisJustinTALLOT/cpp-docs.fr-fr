---
title: Avertissement du compilateur (niveau 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: c96db3d4bd1124c96b22363531b7739d0757b613
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624014"
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