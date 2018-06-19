---
title: Erreur du compilateur C3540 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27bae73d387612be41d8462bf0e5e0d82516ba1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256042"
---
# <a name="compiler-error-c3540"></a>Erreur du compilateur C3540
'type' : Impossible d’appliquer sizeof à un type contenant 'auto'  
  
 Le [sizeof](../../cpp/sizeof-operator.md) opérateur ne peut pas être appliqué au type indiqué car il contient le `auto` spécificateur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant donne C3540.  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [auto, mot clé](../../cpp/auto-keyword.md)   
 [/ Zc : auto (déduire le Type de Variable)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof, opérateur](../../cpp/sizeof-operator.md)