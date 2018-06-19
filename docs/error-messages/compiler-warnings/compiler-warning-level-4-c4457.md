---
title: Du compilateur (niveau 4) d’avertissement C4457 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4457
dev_langs:
- C++
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80eac0ade54df1626e993bfed12468b2aa34402f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300974"
---
# <a name="compiler-warning-level-4-c4457"></a>Du compilateur (niveau 4) d’avertissement C4457
  
> déclaration de '*identificateur*' paramètre de fonction de masque
  
La déclaration de *identificateur* dans l’étendue locale masque la déclaration du paramètre portant le même nom de fonction. Cet avertissement vous informe que les références à *identificateur* dans l’étendue locale correspondent à la version déclarée localement, pas le paramètre, ce qui peut ou ne peut pas être votre intention. Pour résoudre ce problème, nous vous recommandons de que vous donnez des noms de variables locales qui ne sont pas conflictuels portant des noms de paramètre.  
    
## <a name="example"></a>Exemple
  
L’exemple suivant génère C4457, car le paramètre `x` et la variable locale `x` dans `member_fn` ont le même nom. Pour résoudre ce problème, utilisez des noms différents pour les paramètres et les variables locales.  
  
```cpp  
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        } 
        a += x; // uses parameter x
    }
} s;
```  
