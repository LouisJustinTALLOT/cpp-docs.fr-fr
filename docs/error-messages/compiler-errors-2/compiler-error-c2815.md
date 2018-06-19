---
title: Erreur du compilateur C2815 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2815
dev_langs:
- C++
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43eadfe636250c0acab9bcb2cd09323292f26a43
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33240816"
---
# <a name="compiler-error-c2815"></a>Erreur du compilateur C2815
'operator delete' : le premier paramètre formel doit être ' void *', mais 'param' a été utilisé.  
  
 Une est définie par l’utilisateur [opérateur delete](../../standard-library/new-operators.md#op_delete) fonction doit prendre un premier paramètre formel de type `void *`.  
  
 L’exemple suivant génère l’erreur C2815 :  
  
```  
// C2815.cpp  
// compile with: /c  
class CMyClass {  
public:  
   void mf1(int *a);  
   void operator delete(CMyClass *);   // C2815  
   void operator delete(void *);   
};  
```