---
title: Compilateur avertissement (niveau 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 76aab2160bd5f7918771dcf63b7297a869da751e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651293"
---
# <a name="compiler-warning-level-1-c4005"></a>Compilateur avertissement (niveau 1) C4005

'identificateur' : redéfinition de macro

La macro est définie à deux reprises. Le compilateur utilise la deuxième définition de macro.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Définition d’une macro dans la ligne de commande et dans le code avec un `#define` directive.

1. Macros importées à partir de fichiers include.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Supprimez l’une des définitions.

1. Utilisez un [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) directive avant la seconde définition.

L’exemple suivant génère l’erreur C4005 :

```
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