---
title: Erreur du compilateur C2104 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2104
dev_langs:
- C++
helpviewer_keywords:
- C2104
ms.assetid: 2ea78896-72a6-4901-a1fa-f33ea88ad61b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28f3a9173f1141c055547149bc18b5f96a3a475b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165907"
---
# <a name="compiler-error-c2104"></a>Erreur du compilateur C2104
' &' sur un champ de bits ignoré  
  
 Vous ne pouvez pas prendre l’adresse d’un champ de bits.  
  
 L’exemple suivant génère l’erreur C2104 :  
  
```  
// C2104.cpp  
struct X {  
   int sb : 1;  
};  
  
int main() {  
   X x;  
   &x.sb;   // C2104   
   x.sb;   // OK  
}  
```