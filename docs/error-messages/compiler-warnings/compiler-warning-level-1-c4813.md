---
title: Compilateur avertissement (niveau 1) C4813 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4813
dev_langs: C++
helpviewer_keywords: C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f4e888d924c79d18f1b12b1d92cfd0d40f5cc47
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4813"></a>Avertissement du compilateur (niveau 1) C4813
'function' : une fonction friend d’une classe locale doit avoir été précédemment déclarée  
  
 Une fonction friend dans une classe interne n’a pas été déclarée dans la classe externe.  
  
 L’exemple suivant génère l’avertissement C4813 :  
  
```  
// C4813.cpp  
// compile with: /W1 /LD  
void MyClass()  
{  
   // void func();  
   class InnerClass  
   {  
      friend void func();   // C4813 uncomment declaration above  
   };  
}  
```