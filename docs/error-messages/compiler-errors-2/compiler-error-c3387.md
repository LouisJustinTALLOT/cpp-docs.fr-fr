---
title: Erreur du compilateur C3387 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3387
dev_langs:
- C++
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 79b38cd1793509c92ec2d2941fbb3eb2e7121ee7
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3387"></a>Erreur du compilateur C3387
'membre' : __declspec (dllexport) /\__declspec (dllimport) ne peut pas être appliqué à un membre d’un objet ou d’un type WinRT  
  
 Le `dllimport` et [dllexport](../../cpp/dllexport-dllimport.md) `__declspec` modificateurs ne sont pas valides sur les membres d’un objet ou de type Windows Runtime.  
  
 L'exemple suivant génère l'erreur C3387 et montre comment la corriger :  
  
```  
// C3387a.cpp  
// compile with: /clr /c  
ref class X2 {  
   void __declspec(dllexport) mf() {   // C3387  
   // try the following line instead  
   // void mf() {  
   }  
};  
```
