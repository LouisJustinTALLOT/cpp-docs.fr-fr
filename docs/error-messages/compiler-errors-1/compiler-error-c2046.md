---
title: Erreur du compilateur C2046 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2046
dev_langs:
- C++
helpviewer_keywords:
- C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 717c53b0cddd5b4262f43eaf54bb5d9461a92b82
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2046"></a>Erreur du compilateur C2046
instruction case non conforme  
  
 Le mot clé `case` ne peut être spécifié que dans une instruction `switch` .  
  
 L’exemple suivant génère l’erreur C2046 :  
  
```  
// C2046.cpp  
int main() {  
   case 0:   // C2046  
}  
```  
  
 Solution possible :  
  
```  
// C2046b.cpp  
int main() {  
   int i = 0;  
  
   switch(i) {  
      case 0:  
      break;  
  
      default:  
      break;  
   }  
}  
```
