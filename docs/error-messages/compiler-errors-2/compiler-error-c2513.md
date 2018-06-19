---
title: Erreur du compilateur C2513 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2513
dev_langs:
- C++
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 704e5d71301886d46c8a2ce08d7ea34ef1f8275a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228256"
---
# <a name="compiler-error-c2513"></a>Erreur du compilateur C2513
'type' : aucune variable déclarée avant '='  
  
 Le spécificateur de type apparaît dans la déclaration sans identificateur de variable.  
  
 L’exemple suivant génère l’erreur C2513 :  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 Cette erreur peut également être générée à la suite d’un travail de mise en conformité du compilateur pour Visual Studio .NET 2003 : initialisation d’un typedef ne sont plus autorisé. L’initialisation d’un typedef n’est pas autorisée par la norme et génère une erreur du compilateur.  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 Une alternative consisterait à supprimer `typedef` pour définir une variable avec la liste d’initialiseurs d’agrégat, mais cela n’est pas recommandée car elle créer une variable avec le même nom que le type et masquer le nom de type.