---
title: Erreur du compilateur C3530 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3530
dev_langs:
- C++
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6514d655ab813ae21ecb440415f87bce63f3591
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253516"
---
# <a name="compiler-error-c3530"></a>Erreur du compilateur C3530
'auto' ne peut pas être combiné avec n’importe quel autre spécificateur de type  
  
 Un spécificateur de type est utilisé avec le `auto` (mot clé).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  N’utilisez pas un spécificateur de type dans une déclaration de variable qui utilise le `auto` (mot clé).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant donne C3530 parce que variable `x` est déclaré avec le `auto` (mot clé) et le type `int`, et parce que l’exemple est compilé avec **/Zc : auto**.  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [auto, mot clé](../../cpp/auto-keyword.md)