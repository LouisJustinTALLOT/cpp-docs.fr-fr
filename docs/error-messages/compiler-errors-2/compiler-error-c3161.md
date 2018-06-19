---
title: Erreur du compilateur C3161 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2d7aff3eb41c03f5be774704922340ac54126fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250701"
---
# <a name="compiler-error-c3161"></a>Erreur du compilateur C3161
'interface' : classe d’imbrication, le struct, union ou interface dans une interface non conforme ; imbrication d’une interface dans une classe, struct ou une union est non conforme  
  
 Un [__interface](../../cpp/interface.md) ne peut apparaître que dans une portée globale ou au sein d’un espace de noms. Une classe, struct ou union ne peut pas apparaître dans une interface.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3161.  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```