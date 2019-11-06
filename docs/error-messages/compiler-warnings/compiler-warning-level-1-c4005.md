---
title: Avertissement du compilateur (niveau 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 71b23ec719198d15a99b4fcfd50db8b151e03226
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627354"
---
# <a name="compiler-warning-level-1-c4005"></a>Avertissement du compilateur (niveau 1) C4005

'identificateur' : redéfinition de macro

L’identificateur de macro est défini deux fois. Le compilateur utilise la deuxième définition de macro.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Définition d’une macro sur la ligne de commande et dans le code à l’aide d’une directive `#define`.

1. Macros importées à partir de fichiers include.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Supprimez l’une des définitions.

1. Utilisez une directive [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) avant la deuxième définition.

L’exemple suivant génère l’C4005 :

```cpp
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```