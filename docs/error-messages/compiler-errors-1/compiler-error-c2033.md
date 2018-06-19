---
title: Erreur du compilateur C2033 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2033
dev_langs:
- C++
helpviewer_keywords:
- C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: edc9e70ce000fe69876888ec94684d48d2ee9531
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163499"
---
# <a name="compiler-error-c2033"></a>Erreur du compilateur C2033
'identifier' : un champ de bits ne peut pas avoir d’indirection  
  
 Le champ de bits a été déclaré en tant que pointeur, ce qui n’est pas autorisé.  
  
 L’exemple suivant génère l’erreur C2033 :  
  
```  
// C2033.cpp  
struct S {  
   int *b : 1;  // C2033  
};  
```  
  
 Solution possible :  
  
```  
// C2033b.cpp  
// compile with: /c  
struct S {  
   int b : 1;  
};  
```