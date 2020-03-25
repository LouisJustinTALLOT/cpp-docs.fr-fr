---
title: Avertissement du compilateur (niveau 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 2474645a555748b559b1661a2b5327ca1b83e534
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176376"
---
# <a name="compiler-warning-level-1-c4117"></a>Avertissement du compilateur (niveau 1) C4117

nom de macro 'name' réservé, 'Command' ignoré

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Tentative de définition ou de suppression de la définition d’une macro prédéfinie.

1. Tentative de définition ou de suppression de la définition de l’opérateur de préprocesseur **defined**.

L’exemple suivant génère l’avertissement C4117 :

```cpp
// C4117.cpp
// compile with: /W1
#define __FILE__ test         // C4117. __FILE__ is a predefined macro
#define ValidMacroName test   // ok

int main() {
}
```
