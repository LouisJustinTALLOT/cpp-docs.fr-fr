---
title: Erreur du compilateur C2162 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2162
dev_langs:
- C++
helpviewer_keywords:
- C2162
ms.assetid: 34923628-d35e-48ab-9072-b95e3b5f6b45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc7cfebd4563e4d41f6ca50e2cdec667e82fb5f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167968"
---
# <a name="compiler-error-c2162"></a>Erreur du compilateur C2162
paramètre formel de macro attendu  
  
 Le jeton suivant un opérateur d’enchaînement (#) n’est pas un nom de paramètre formel.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2162 :  
  
```  
// C2162.cpp  
// compile with: /c  
#include <stdio.h>  
  
#define print(a) printf_s(b)   // OK  
#define print(a) printf_s(#b)    // C2162  
```