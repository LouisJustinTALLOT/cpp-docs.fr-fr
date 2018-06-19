---
title: Avertissement du compilateur C4430 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4430
dev_langs:
- C++
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 311c75ed1fcacdf8b40f096a759d669c9331c2ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272111"
---
# <a name="compiler-warning-c4430"></a>Avertissement du compilateur C4430
spécificateur de type manquant - int est pris en compte par défaut. Remarque : C++ ne prend pas en charge int par défaut  
  
 Cette erreur peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : toutes les déclarations doivent spécifier explicitement le type ; int est supposé ne sont plus.  
  
 C4430 est toujours émis en tant qu’erreur.  Vous pouvez désactiver cet avertissement avec le `#pragma warning` ou **/wd**; consultez [avertissement](../../preprocessor/warning.md) ou [Wn, / W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, Wall, /wd, / nous, /wo, /WV., /Won (niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md)pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4430.  
  
```  
// C4430.cpp  
// compile with: /c  
struct CMyClass {  
   CUndeclared m_myClass;  // C4430  
   int m_myClass;  // OK  
};  
  
typedef struct {  
   POINT();   // C4430  
   // try the following line instead  
   // int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```