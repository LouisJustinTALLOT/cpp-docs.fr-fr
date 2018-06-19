---
title: Erreur du compilateur C3887 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3887
dev_langs:
- C++
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24e407f99da3a2e525eff96ba00137baa5ed5869
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270147"
---
# <a name="compiler-error-c3887"></a>Erreur du compilateur C3887
'var' : l’initialiseur d’une donnée membre littérale doit être une expression constante  
  
 A [littéral](../../windows/literal-cpp-component-extensions.md) membre de données peut uniquement être initialisé avec une expression constante.  
  
 L’exemple suivant génère l’erreur C3887 :  
  
```  
// C3887.cpp  
// compile with: /clr  
ref struct Y1 {  
   static int i = 9;  
   literal  
   int staticConst = i;   // C3887  
};  
```  
  
 Solution possible :  
  
```  
// C3887b.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   literal  
   int staticConst = 9;  
};  
```