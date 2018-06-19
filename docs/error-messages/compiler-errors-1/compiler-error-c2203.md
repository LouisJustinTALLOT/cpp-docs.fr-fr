---
title: Erreur du compilateur C2203 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2203
dev_langs:
- C++
helpviewer_keywords:
- C2203
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0cbf64e673c84a60c37bce3ffd51bc7016eb7a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169931"
---
# <a name="compiler-error-c2203"></a>Erreur du compilateur C2203
Delete (opérateur) ne peut pas spécifier de limites pour un tableau  
  
 Avec la **/Za** l’option (ANSI), le `delete` opérateur peut supprimer la totalité d’un tableau, mais pas les parties ou des membres spécifiques du tableau.  
  
 L’exemple suivant génère l’erreur C2203 :  
  
```  
// C2203.cpp  
// compile with: /Za  
int main() {  
   int *ar = new int[10];  
   delete [4] ar;   // C2203  
   // try the following line instead  
   // delete [] ar;  
}  
```