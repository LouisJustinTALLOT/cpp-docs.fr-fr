---
title: C2178 d’erreur du compilateur | Documents Microsoft
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3727a66554b2e128061820df160c02a1370ebb74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171293"
---
# <a name="compiler-error-c2178"></a>C2178 d’erreur du compilateur  
  
'*identificateur*'ne peut pas être déclarée avec'*spécificateur*' spécificateur  
  
A `mutable` spécificateur a été utilisé dans une déclaration, mais le spécificateur n’est pas autorisé dans ce contexte.  
  
Le `mutable` spécificateur peut être appliqué uniquement à des noms de membres de données de classe et ne peut pas être appliqué à des noms déclarés `const` ou `static`et ne peut pas être appliqué aux membres de référence.  
  
## <a name="example"></a>Exemple  
  
L’exemple suivant montre comment C2178 peut se produire et comment la corriger.  
  
```  
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```  
