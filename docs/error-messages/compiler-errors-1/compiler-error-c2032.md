---
title: Erreur du compilateur C2032 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1db268222f3b9f7ca6f9ce297680866185e6661d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167214"
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
  
 Solution possible :  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```