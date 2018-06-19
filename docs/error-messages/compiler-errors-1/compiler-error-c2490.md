---
title: Erreur du compilateur C2490 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2490
dev_langs:
- C++
helpviewer_keywords:
- C2490
ms.assetid: 9de6bddd-b2e2-4ce6-b33b-201a8c2c8c54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc366178c31f900b031aacca278e39cc0c2eb493
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198701"
---
# <a name="compiler-error-c2490"></a>Erreur du compilateur C2490
'keyword' est ne pas autorisée dans une fonction avec l’attribut 'naked'  
  
 Une fonction définie comme [naked](../../cpp/naked-cpp.md) ne peut pas utiliser la gestion des exceptions structurées.  
  
 L’exemple suivant génère l’erreur C2490 :  
  
```  
// C2490.cpp  
// processor: x86  
__declspec( naked ) int func() {  
   __try{}   // C2490, structured exception handling  
}  
```