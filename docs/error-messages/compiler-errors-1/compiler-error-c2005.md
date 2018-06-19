---
title: Erreur du compilateur C2005 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2005
dev_langs:
- C++
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 484c6b690b54ea7f847128091500e75192440bc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169288"
---
# <a name="compiler-error-c2005"></a>Erreur du compilateur C2005
\#ligne attendait un numéro de ligne, a trouvé 'jeton'  
  
 Le `#line` la directive doit être suivie d’un numéro de ligne.  
  
 L’exemple suivant génère l’erreur C2005 :  
  
```  
// C2005.cpp  
int main() {  
   int i = 0;  
   #line i   // C2005  
}  
```  
  
 Solution possible :  
  
```  
// C2005b.cpp  
int main() {  
   int i = 0;  
   #line 0  
}  
```