---
title: Erreur du compilateur C2801 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f68b3f575fcb8b909f58ac2ffbcaca26580279da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237088"
---
# <a name="compiler-error-c2801"></a>Erreur du compilateur C2801
'operator opérateur' doit être un membre non statique  
  
 Les opérateurs suivants peuvent être surchargées uniquement en tant que membres non statiques :  
  
-   Affectation `=`  
  
-   Accès aux membres de classe `->`  
  
-   Mettre en indice `[]`  
  
-   Appel de fonction `()`  
  
 Causes possibles de l’erreur C2801 :  
  
-   Opérateur surchargé n’est pas une classe, une structure ou un membre d’union.  
  
-   Opérateur surchargé est déclaré comme `static`.  
  
-   L’exemple suivant génère l’erreur C2801 :  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```