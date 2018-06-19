---
title: Erreur du compilateur C2571 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96dea582cf5d1211d57eac94a7f70458a51542ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230765"
---
# <a name="compiler-error-c2571"></a>Erreur du compilateur C2571
'fonction' : fonction virtuelle ne peut pas figurer dans l’union 'union'  
  
 Une union est déclarée avec une fonction virtuelle. Vous pouvez déclarer une fonction virtuelle uniquement dans une classe ou structure.  Solutions possibles :  
  
1.  Modifiez l’union d’une classe ou une structure.  
  
2.  Rendez la fonction non virtuelle.  
  
 L’exemple suivant génère l’erreur C2571 :  
  
```  
// C2571.cpp  
// compile with: /c  
union A {  
   virtual void func1();   // C2571  
   void func2();   // OK  
};  
```