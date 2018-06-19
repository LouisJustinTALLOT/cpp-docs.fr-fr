---
title: Compilateur avertissement (niveau 1) C4526 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5a38d629d61e16b038701522d4bb27a4de7391d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282897"
---
# <a name="compiler-warning-level-1-c4526"></a>Avertissement du compilateur (niveau 1) C4526
'fonction' : fonction membre statique ne peut pas substituer la fonction virtuelle ' substitution ignorée, fonction virtual sera masquée  
  
 La fonction membre statique correspondant aux critères pour remplacer la fonction virtuelle, ce qui rend la fonction membre virtuelle et statique.  
  
 Le code suivant génère C4526 :  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 Solutions possibles sont les suivantes :  
  
-   Si la fonction était destinée à remplacer la fonction virtuelle de classe de base, supprimez le spécificateur statique.  
  
-   Si la fonction était destinée à être une fonction membre statique, renommez-la afin qu’il n’entre en conflit avec la fonction virtuelle de classe de base.