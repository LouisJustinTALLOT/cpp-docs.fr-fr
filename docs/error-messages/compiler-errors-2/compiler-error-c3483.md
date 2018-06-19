---
title: Erreur du compilateur C3483 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3483
dev_langs:
- C++
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e2605674ff701f70f7be6ea1b4158c9f8f0c6ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258735"
---
# <a name="compiler-error-c3483"></a>Erreur du compilateur C3483
'var' figure déjà dans la liste de capture lambda  
  
 Vous avez passé plusieurs fois la même variable à la liste de capture d’une expression lambda.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimez toutes les instances supplémentaires de la variable de la liste de capture.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3483, car la variable `n` apparaît plusieurs fois dans la liste de capture de l’expression lambda :  
  
```  
// C3483.cpp  
  
int main()  
{  
   int m = 6, n = 5;  
   [m,n,n] { return n + m; }(); // C3483  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)