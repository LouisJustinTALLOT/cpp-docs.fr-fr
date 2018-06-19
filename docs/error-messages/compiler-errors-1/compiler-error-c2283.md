---
title: Erreur du compilateur C2283 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2283
dev_langs:
- C++
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb602d1fa330876820cc7e1fe75fcfe7b736b81e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170854"
---
# <a name="compiler-error-c2283"></a>Erreur du compilateur C2283
'identificateur' : spécificateur pure ou spécificateur de substitution abstrait non autorisé sur un struct sans nom  
  
 Une fonction membre d’une classe ou d’une structure sans nom est déclarée avec un spécificateur pure, ce qui n’est pas autorisé.  
  
 L’exemple suivant génère l’erreur C2283 :  
  
```  
// C2283.cpp  
// compile with: /c  
struct {  
   virtual void func() = 0;   // C2283  
};  
struct T {  
   virtual void func() = 0;   // OK  
};  
```