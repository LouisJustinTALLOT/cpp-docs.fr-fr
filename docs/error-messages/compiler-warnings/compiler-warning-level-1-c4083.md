---
title: Compilateur avertissement (niveau 1) C4083 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4083
dev_langs:
- C++
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0d0d7baa0e521484841c638cef4332001a65e78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277678"
---
# <a name="compiler-warning-level-1-c4083"></a>Compilateur avertissement (niveau 1) C4083
'jeton' attendu trouver l’identificateur 'identificateur'  
  
 Un identificateur apparaît dans un emplacement erroné dans une **#pragma** instruction.  
  
## <a name="example"></a>Exemple  
  
```  
// C4083.cpp  
// compile with: /W1 /LD  
#pragma warning disable:4083    // C4083  
#pragma warning(disable:4083)   //correct  
```  
  
 Vérifiez la syntaxe de la [#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) directives.