---
title: Avertissement du compilateur (niveau 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 97fd5703a744448db87634e313678cf4e824df7f
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626285"
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