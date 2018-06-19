---
title: Erreur du compilateur C3012 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3012
dev_langs:
- C++
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d30a7fbb50a984c8cec6b45a0ab4759a0578de7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245451"
---
# <a name="compiler-error-c3012"></a>Erreur du compilateur C3012
  
> '*intrinsèque*' : fonction intrinsèque non autorisée directement dans une région parallèle  
  
 Une fonction [intrinsèque du compilateur](../../intrinsics/compiler-intrinsics.md) n’est pas autorisée dans une région `omp parallel` . Pour résoudre ce problème, déplacez intrinsèques hors de la région, ou remplacez-les par leurs équivalents non intrinsèque.   
  
## <a name="example"></a>Exemple  
  
 L’exemple suivant génère l’erreur C3012 et illustre une façon de pour résoudre ce problème :  
  
```cpp  
// C3012.cpp  
// compile with: /openmp  
#ifdef __cplusplus  
extern "C" {  
#endif  
void* _ReturnAddress();  
#ifdef __cplusplus  
}  
#endif  
  
int main()  
{  
   #pragma omp parallel  
   {  
      _ReturnAddress();   // C3012  
   }  
   _ReturnAddress();      // OK  
}  
```