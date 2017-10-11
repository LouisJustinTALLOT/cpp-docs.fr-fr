---
title: Erreur du compilateur C3737 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3737
dev_langs:
- C++
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: af179d622ffe8354352cc6b87ab009b825e55b36
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3737"></a>Erreur du compilateur C3737
'délégué' : un délégué ne peut pas avoir une convention d’appel explicite  
  
 Vous ne pouvez pas spécifier le [convention d’appel](../../cpp/calling-conventions.md) pour un `delegate`.  
  
## <a name="example"></a>Exemple  
L’exemple suivant génère l’erreur C3737 :  
  
```  
// C3737a.cpp  
// compile with: /clr  
delegate void __stdcall MyFunc();   // C3737  
// Try the following line instead.  
// delegate void MyFunc();  
  
int main() {  
}  
```  

