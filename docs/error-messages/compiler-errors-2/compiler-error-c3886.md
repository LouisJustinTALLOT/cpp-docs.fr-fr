---
title: Erreur du compilateur C3886 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3886
dev_langs: C++
helpviewer_keywords: C3886
ms.assetid: 485f6c12-cc1b-4146-9034-409a0a5e615e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f58b5ebdc2aedca35ef1e94855785fbe59fcf10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3886"></a>Erreur du compilateur C3886
'var' : une donnée membre littérale doit être initialisée.  
  
 A [littéral](../../windows/literal-cpp-component-extensions.md) variable doit être initialisée lorsqu’elle est déclarée.  
  
 L’exemple suivant génère l’erreur C3886 :  
  
```  
// C3886.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   literal int staticConst;   // C3886  
   literal int staticConst2 = 0;   // OK  
};  
```