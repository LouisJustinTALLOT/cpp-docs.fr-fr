---
title: Erreur du compilateur C2652 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2652
dev_langs:
- C++
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 576aef31268c0cdce09162fc367358e0ed044429
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232197"
---
# <a name="compiler-error-c2652"></a>Erreur du compilateur C2652
'identificateur' : constructeur de copie non conforme : premier paramètre ne doit pas être 'identificateur'  
  
 Le premier paramètre dans le constructeur de copie a le même type que la classe, structure ou union pour lequel il est défini. Le premier paramètre peut être une référence au type, mais pas le type lui-même.  
  
 L’exemple suivant génère l’erreur C2651 :  
  
```  
// C2652.cpp  
// compile with: /c  
class A {  
   A( A );   // C2652 takes an A  
};  
class B {  
   B( B& );   // OK, reference to B  
};  
```