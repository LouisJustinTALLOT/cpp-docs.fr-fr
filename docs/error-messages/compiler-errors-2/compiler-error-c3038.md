---
title: Erreur du compilateur C3038 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3038
dev_langs:
- C++
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f65f2c1f2d872353ee60b805618c539355602c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245576"
---
# <a name="compiler-error-c3038"></a>Erreur du compilateur C3038
'var' : la variable de la clause 'private' ne peut pas être une variable de réduction dans un contexte englobant  
  
 Les variables qui apparaissent dans la clause [reduction](../../parallel/openmp/reference/reduction.md) d’une directive parallèle ne peuvent pas être spécifiées dans une clause [private](../../parallel/openmp/reference/private-openmp.md) d’une directive de partage de travail qui est liée à la construction parallèle.  
  
 L’exemple suivant génère l’erreur C3038 :  
  
```  
// C3038.cpp  
// compile with: /openmp /c  
int g_i, g_i2;  
  
int main() {  
   int i;  
  
   #pragma omp parallel reduction(+: g_i)  
   {  
      #pragma omp for private(g_i)   // C3038  
      // try the following line instead  
      // #pragma omp for private(g_i2)  
      for (i = 0; i < 10; ++i)  
         g_i += i;  
   }  
}  
```