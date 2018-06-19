---
title: Erreur du compilateur C3363 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3363
dev_langs:
- C++
helpviewer_keywords:
- C3363
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aec09769f4db4f501f62ebaa2a996dfdefb5fcd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254093"
---
# <a name="compiler-error-c3363"></a>Erreur du compilateur C3363
'type' : 'typeid' applicable seulement à un type  
  
 L’opérateur [typeid](../../windows/typeid-cpp-component-extensions.md) a été utilisé incorrectement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3363.  
  
```  
// C3363.cpp  
// compile with: /clr  
int main() {  
   System::typeid;   // C3363  
}  
```