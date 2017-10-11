---
title: Erreur du compilateur C3698 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3698
dev_langs:
- C++
helpviewer_keywords:
- C3698
ms.assetid: 3c02fb08-7ba4-4637-a06f-19926cb2b5f1
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d49234a7fa0f607877482709c6629ba77cd31806
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3698"></a>Erreur du compilateur C3698
'type' : Impossible d’utiliser ce type comme argument de 'opérateur'  
  
 Un objet managé a été déclaré de manière incorrecte.  
  
 L’exemple suivant génère l’erreur C3698 :  
  
```  
// C3698.cpp  
// compile with: /clr  
  
int main() {  
   array<int>^a = new array<int>^(20);   // C3698  
   array<int>^a2 = gcnew array<int>(20);   // OK  
}  
```
