---
title: Compilateur avertissement (niveaux 1 et 4) C4949 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dbf80f85db7334d4bcb46402851cac601d258f2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279644"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Avertissement du compilateur (niveaux 1 et 4) C4949
les pragmas 'managed' et 'unmanaged' sont significatifs uniquement lors de la compilation avec ' / clr [ : option]'  
  
 Le compilateur ignore le [gérés](../../preprocessor/managed-unmanaged.md) et non managé pragmas si le code source n’est pas compilé avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). Cet avertissement possède un caractère informatif.  
  
 L’exemple suivant génère l’erreur C4949 :  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 Lorsque **#pragma unmanaged** est utilisé sans **/CLR**, C4949 est un avertissement de niveau 4.  
  
 L’exemple suivant génère l’erreur C4949 :  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```