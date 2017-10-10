---
title: Erreur du compilateur C2890 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2890
dev_langs:
- C++
helpviewer_keywords:
- C2890
ms.assetid: 49147375-182c-42b1-b170-f475cd436d47
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ee25c25fd1c808ece4a6ef7f8538b83216c4b180
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2890"></a>Erreur du compilateur C2890
'classe' : une classe ref peut avoir uniquement une classe de base sans interface  
  
 Une classe de référence peut avoir uniquement une classe de base.  
  
 L’exemple suivant génère l’erreur C2890 :  
  
```  
// C2890.cpp  
// compile with: /clr /c  
ref class A {};  
ref class B {};  
ref class C : public A, public B {};   // C2890  
ref class D : public A {};   // OK  
```  

