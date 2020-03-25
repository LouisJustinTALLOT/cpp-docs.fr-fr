---
title: Avertissement du compilateur (niveau 1) C4075
ms.date: 11/04/2016
f1_keywords:
- C4075
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
ms.openlocfilehash: f69d91ee9335201029d6b566b7987df8c267f82b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200224"
---
# <a name="compiler-warning-level-1-c4075"></a>Avertissement du compilateur (niveau 1) C4075

initialiseurs placés dans une zone d'initialisation non reconnue

Un [#pragma init_seg](../../preprocessor/init-seg.md) utilise un nom de section non reconnu. Le compilateur ignore la commande **pragma** .

L’exemple suivant génère l’avertissement C4075 :

```cpp
// C4075.cpp
// compile with: /W1
#pragma init_seg("mysegg")   // C4075

// try..
// #pragma init_seg(user)

int main() {
}
```
