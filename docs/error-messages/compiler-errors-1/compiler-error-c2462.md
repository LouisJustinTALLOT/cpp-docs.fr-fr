---
title: Erreur du compilateur C2462 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2462
dev_langs:
- C++
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4ce82ed15bdb8844f69abc260446c1af2fd4a0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198558"
---
# <a name="compiler-error-c2462"></a>Erreur du compilateur C2462
'identificateur' : Impossible de définir un type dans une 'new-expression'  
  
 Vous ne pouvez pas définir un type dans le champ de l’opérande de le `new` opérateur. Placez la définition du type dans une instruction séparée.  
  
 L’exemple suivant génère l’erreur C2462 :  
  
```  
// C2462.cpp  
int main() {  
   new struct S { int i; };   // C2462  
}  
```