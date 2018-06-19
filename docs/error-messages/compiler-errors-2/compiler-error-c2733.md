---
title: Erreur du compilateur C2733 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2733
dev_langs:
- C++
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc1857cd800dd2d395754b9ae95094d9f57aad27
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234187"
---
# <a name="compiler-error-c2733"></a>Erreur du compilateur C2733
seconde liaison C d’une fonction surchargée 'fonction' non autorisée  
  
 Plusieurs fonctions surchargées sont déclarées avec liaison C. Lorsque vous utilisez une liaison C, seule la forme d’une fonction spécifiée peut être externe. Les fonctions surchargées ayant le même nom non décoré, ils ne peuvent pas être utilisés avec les programmes C.  
  
 L’exemple suivant génère l’erreur C2733 :  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```