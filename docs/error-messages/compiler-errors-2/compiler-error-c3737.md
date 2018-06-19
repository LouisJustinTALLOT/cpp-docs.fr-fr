---
title: Erreur du compilateur C3737 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3737
dev_langs:
- C++
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29d31597e9581d03f97c2b07856ce81c5de50bd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264608"
---
# <a name="compiler-error-c3737"></a>Erreur du compilateur C3737
'délégué' : un délégué ne peut pas avoir une convention d’appel explicite  
  
 Vous ne pouvez pas spécifier le [convention d’appel](../../cpp/calling-conventions.md) pour un `delegate`.  
  
## <a name="example"></a>Exemple  
L’exemple suivant génère l’erreur C3737 :  
  
```  
// C3737a.cpp  
// compile with: /clr  
delegate void __stdcall MyFunc();   // C3737  
// Try the following line instead.  
// delegate void MyFunc();  
  
int main() {  
}  
```  
