---
title: Erreur du compilateur C2101 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2101
dev_langs:
- C++
helpviewer_keywords:
- C2101
ms.assetid: 42f0136f-8cc1-4f2b-be1c-721ec9278e66
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65b63962ebdc073ab6ecb68de5251d9e1eae8399
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2101"></a>Erreur du compilateur C2101
'&' sur constante  
  
 L’opérateur d’adresse ( `&` ) doit avoir une l-value comme opérande.  
  
 L’exemple suivant génère l’erreur C2101 :  
  
```  
// C2101.cpp  
int main() {  
   char test;  
   test = &'a';   // C2101  
   test = 'a';   // OK  
}  
```