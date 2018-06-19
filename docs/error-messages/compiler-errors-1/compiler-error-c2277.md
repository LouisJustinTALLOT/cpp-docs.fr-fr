---
title: Erreur du compilateur C2277 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2277
dev_langs:
- C++
helpviewer_keywords:
- C2277
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7338efab684e9812704673ece8585cd58c850b23
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171729"
---
# <a name="compiler-error-c2277"></a>Erreur du compilateur C2277
'identificateur' : ne peut pas prendre l’adresse de cette fonction membre  
  
 Vous ne pouvez pas prendre l’adresse d’une fonction membre.  
  
 L’exemple suivant génère l’erreur C2277 :  
  
```  
// C2277.cpp  
class A {  
public:  
   A();  
};  
(*pctor)() = &A::A;   // C2277   
```