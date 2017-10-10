---
title: Erreur du compilateur C3008 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3008
dev_langs:
- C++
helpviewer_keywords:
- C3008
ms.assetid: 04d93201-28e5-4be0-945c-aad616376f4b
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 392725c883621490b6f9d748cf394e01af329606
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3008"></a>Erreur du compilateur C3008
'arg' : une parenthèse fermante ')' est manquante dans une directive 'directive' OpenMP  
  
 Une directive OpenMP qui prend un argument n’avait pas de parenthèse fermante.  
  
 L’exemple suivant génère l’erreur C3008 :  
  
```  
// C3008.c  
// compile with: /openmp  
int main()  
{  
   int x, y, z;  
   #pragma omp parallel shared(x   // C3008  
   // Try the following line instead:  
   #pragma omp parallel shared(x)  
   {  
   }  
}  
```
