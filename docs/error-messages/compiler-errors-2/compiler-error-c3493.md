---
title: Erreur du compilateur C3493 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3493
dev_langs:
- C++
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3aec62bfff59396ec73141746193e4e3f16d84fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257314"
---
# <a name="compiler-error-c3493"></a>Erreur du compilateur C3493
Impossible de capturer implicitement 'var', car aucun mode de capture par défaut n’a été spécifié  
  
 La capture de l’expression lambda vide, `[]`, spécifie que l’expression lambda ne capture pas de variables explicitement ou implicitement.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Spécifiez un mode de capture par défaut, ou  
  
-   Capturez explicitement une ou plusieurs variables.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3493 parce qu’il modifie une variable externe, alors qu’il spécifie la clause de capture vide :  
  
```  
// C3493a.cpp  
  
int main()  
{  
   int m = 55;  
   [](int n) { m = n; }(99); // C3493  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant corrige C3493 en spécifiant la capture par référence comme mode de capture par défaut.  
  
```  
// C3493b.cpp  
  
int main()  
{  
   int m = 55;  
   [&](int n) { m = n; }(99);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions lambda](../../cpp/lambda-expressions-in-cpp.md)