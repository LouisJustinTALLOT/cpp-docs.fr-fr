---
title: Compilateur avertissement (niveau 1) C4441 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4441
dev_langs:
- C++
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33337741819d908ce9445d82d905ecfc5738acda
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4441"></a>Avertissement du compilateur (niveau 1) C4441
convention d’appel de 'cc1' ignorée ; 'cc2' utilisé à la place  
  
 Les fonctions membres dans des types managés définis par l’utilisateur et des génériques de fonction globale doivent utiliser le [__clrcall](../../cpp/clrcall.md) convention d’appel.  Le compilateur utilisé `__clrcall`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4441.  
  
```  
// C4441.cpp  
// compile with: /clr /W1 /c  
generic <class ItemType>  
void __cdecl Test(ItemType item) {}   // C4441  
// try the following line instead  
// void Test(ItemType item) {}  
  
ref struct MyStruct {  
   void __cdecl Test(){}   // C4441  
   void Test2(){}   // OK  
};  
```