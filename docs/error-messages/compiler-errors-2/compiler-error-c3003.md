---
title: Erreur du compilateur C3003 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3003
dev_langs:
- C++
helpviewer_keywords:
- C3003
ms.assetid: 22e74f99-bb7f-4518-ab0d-934d5d49bcc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48e3cdcb4df846414cc231999f85da05e3bb9995
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241306"
---
# <a name="compiler-error-c3003"></a>Erreur du compilateur C3003
'directive' : nom de directive OpenMP non autorisé après des clauses de directive  
  
 Un nom de directive OpenMP ne peut pas suivre une clause de directive OpenMP.  
  
 L’exemple suivant génère l’erreur C3003 :  
  
```  
// C3003.c  
// compile with: /openmp  
int main()  
{  
   int x, y, z;  
   #pragma omp parallel shared(x, y, z) for   // C3003  
}  
```