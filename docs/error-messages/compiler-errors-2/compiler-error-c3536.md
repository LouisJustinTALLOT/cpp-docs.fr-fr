---
title: Erreur du compilateur C3536 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3536
dev_langs:
- C++
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f88e656b0d63b6a7a4d60ace2f4cd5e2347d188
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250285"
---
# <a name="compiler-error-c3536"></a>Erreur du compilateur C3536
'symbole' : ne peut pas être utilisée avant d’être initialisée  
  
 Le symbole indiqué ne peut pas être utilisé avant d’être initialisée. Dans la pratique, cela signifie qu'une variable ne peut pas être utilisée pour s'initialiser.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  N’initialisez pas de variable avec elle-même.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3536, car chaque variable est initialisée avec elle-même.  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [auto, mot clé](../../cpp/auto-keyword.md)