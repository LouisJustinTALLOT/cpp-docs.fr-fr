---
title: Erreur du compilateur C2562 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2562
dev_langs:
- C++
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab3fd1a5eae008785a688bcbade674425fc8b2ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231604"
---
# <a name="compiler-error-c2562"></a>Erreur du compilateur C2562
'identificateur' : fonction 'void' retournant une valeur  
  
 La fonction est déclarée en tant que `void` mais retourne une valeur.  
  
 Cette erreur peut résulter d’un prototype de fonction incorrect.  
  
 Cette erreur peut être résolue si vous spécifiez le type de retour dans la déclaration de fonction.  
  
 L’exemple suivant génère l’erreur C2562 :  
  
```  
// C2562.cpp  
// compile with: /c  
void testfunc() {  
   int i;  
   return i;   // C2562 delete the return to resolve  
}  
```