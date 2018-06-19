---
title: Erreur du compilateur C2459 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2459
dev_langs:
- C++
helpviewer_keywords:
- C2459
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6013720b55892ffd34e1faf132a69842e4bceb50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198506"
---
# <a name="compiler-error-c2459"></a>Erreur du compilateur C2459
'identificateur' : est défini ; Impossible d’ajouter comme membre anonyme  
  
 Une classe, structure ou union est redéfinie dans sa propre portée par un membre d’une union anonyme.  
  
 L’exemple suivant génère l’erreur C2459 :  
  
```  
// C2459.cpp  
// compile with: /c  
class C {  
   union { int C; };   // C2459  
   union { int D; };  
};  
```