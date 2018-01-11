---
title: Erreur du compilateur C2617 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2617
dev_langs: C++
helpviewer_keywords: C2617
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 502893544555ca5ec827efd667779fe87dc2976a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2617"></a>Erreur du compilateur C2617
'fonction' : instruction return incohérente  
  
 La fonction spécifiée n’a pas un type de retour déclaré et une précédente retour instruction n’a pas fourni une valeur.  
  
 L’exemple suivant génère l’erreur C2617 :  
  
```  
// C2617.cpp  
int i;  
func() {   // no return type prototype  
   if( i ) return;   // no return value  
   else return( 1 );   // C2617 detected on this line  
}  
```  
  
 Solution possible :  
  
```  
// C2617b.cpp  
// compile with: /c  
int i;  
int MyF() {  
   if (i)  
      return 0;  
   else   
      return (1);  
}  
```