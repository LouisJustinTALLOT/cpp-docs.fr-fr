---
title: Du compilateur (niveau 4) d’avertissement C4456 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4456
dev_langs:
- C++
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ca4af4e7353595dc687b77fa87acf70861bcb6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295910"
---
# <a name="compiler-warning-level-4-c4456"></a>Du compilateur (niveau 4) d’avertissement C4456
  
> déclaration de '*identificateur*' masque la déclaration locale précédente
  
La déclaration de *identificateur* dans l’étendue locale masque la déclaration de la déclaration locale précédente du même nom. Cet avertissement vous informe que les références à *identificateur* dans l’étendue locale correspondent à la version déclarée localement, pas précédente local, ce qui peut ou ne peut pas être votre intention. Pour résoudre ce problème, nous vous recommandons de que vous donner des noms de variables locales qui éviter les conflits avec d’autres noms locaux.  
    
## <a name="example"></a>Exemple
  
L’exemple suivant génère C4456, car la variable de contrôle de la boucle `int x` et la variable locale `double x` dans `member_fn` ont le même nom. Pour résoudre ce problème, utilisez des noms différents pour les variables locales.  
  
```cpp  
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        } 
        x += u; // uses local double x
    }
} s;
```  
