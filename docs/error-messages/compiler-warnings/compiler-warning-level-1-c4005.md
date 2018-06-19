---
title: Compilateur avertissement (niveau 1) C4005 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4005
dev_langs:
- C++
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a06ea88dab6ac7e89f7d53351b54593fd7bd232
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275374"
---
# <a name="compiler-warning-level-1-c4005"></a>Compilateur avertissement (niveau 1) C4005
'identificateur' : redéfinition de macro  
  
 Identificateur de la macro est défini à deux reprises. Le compilateur utilise la deuxième définition de macro.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Définition d’une macro sur la ligne de commande et dans le code avec un `#define` la directive.  
  
2.  Macros importées depuis des fichiers include.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Supprimez l’une des définitions.  
  
2.  Utilisez un [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) directive avant la seconde définition.  
  
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