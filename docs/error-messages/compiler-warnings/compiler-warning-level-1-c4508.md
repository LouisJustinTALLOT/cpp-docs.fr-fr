---
title: Avertissement du compilateur (niveau 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 54baf35eaeb5ef2c8add024f25c059480d60617b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186561"
---
# <a name="compiler-warning-level-1-c4508"></a>Avertissement du compilateur (niveau 1) C4508

'fonction' : la fonction doit retourner une valeur ; type de retour’void’pris par défaut

La fonction n’a aucun type de retour spécifié. Dans ce cas, C4430 doit également se déclencher et le compilateur implémente le correctif signalé par C4430 (la valeur par défaut est int).

Pour résoudre cet avertissement, déclarez explicitement le type de retour des fonctions.

L’exemple suivant génère l’C4508 :

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```
