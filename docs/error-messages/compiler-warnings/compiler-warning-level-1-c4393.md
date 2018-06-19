---
title: Compilateur avertissement (niveau 1) C4393 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4393
dev_langs:
- C++
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59a1022f54d22e97a11c0970cad6bcd8918c7190
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277938"
---
# <a name="compiler-warning-level-1-c4393"></a>Avertissement du compilateur (niveau 1) C4393
'var' : const n’a aucun effet sur une donnée membre littérale ; ignoré  
  
 A [littéral](../../windows/literal-cpp-component-extensions.md) membre de données a également été spécifié comme const.  Dans la mesure où une donnée membre littérale implique const, il est inutile ajouter const à la déclaration.  
  
 L’exemple suivant génère l’erreur C4393 :  
  
```  
// C4393.cpp  
// compile with: /clr /W1 /c  
ref struct Y1 {  
   literal const int staticConst = 10;   // C4393  
   literal int staticConst2 = 10;   // OK  
};  
```