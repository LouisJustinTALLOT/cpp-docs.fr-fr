---
title: Erreur du compilateur C2032 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 81bbe4c9e5242f68a5e0e304858c13c9274c1743
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2032"></a>Erreur du compilateur C2032
'identificateur' : fonction ne peut pas être membre struct/union 'StructOuUnion'  
  
 La structure ou union a une fonction membre, ce qui est autorisée en C++, mais pas dans C. Pour résoudre l’erreur, compilez comme un programme C++ ou supprimez la fonction membre.  
  
 L’exemple suivant génère l’erreur C2032 :  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 Résolution possible :  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```
