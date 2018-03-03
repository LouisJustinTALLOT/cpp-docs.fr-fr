---
title: Erreur du compilateur C2430 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2430
dev_langs:
- C++
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc33ec719413d481c8994d3cab7def55e5fed658
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2430"></a>Erreur du compilateur C2430
plus d’un registre d’index dans 'identificateur'  
  
 Plus d’un Registre est mis à l’échelle. Le compilateur prend en charge l’indexation de mise à l’échelle, mais vous pouvez uniquement mettre à l’échelle un Registre.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2430.  
  
```  
// C2430.cpp  
// processor: x86  
int main() {  
   _asm mov eax, [ebx*2+ecx*4] // C2430  
}  
```