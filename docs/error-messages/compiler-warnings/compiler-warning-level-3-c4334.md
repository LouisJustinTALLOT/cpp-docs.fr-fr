---
title: Compilateur avertissement (niveau 3) C4334 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f26749c968c3cac18b509046633ba3d91d15a4be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292683"
---
# <a name="compiler-warning-level-3-c4334"></a>Avertissement du compilateur (niveau 3) C4334
'opérateur' : résultat du décalage 32 bits converti implicitement en 64 bits (était décalage 64 bits destinée ?)  
  
 Le résultat du décalage 32 bits a été implicitement converti en 64 bits et le compilateur soupçonne qu’un décalage 64 bits a été conçu.  Pour résoudre cet avertissement, utilisez le décalage 64 bits, ou explicitement convertir le résultat de la touche MAJ enfoncée en 64 bits.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4334.  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```