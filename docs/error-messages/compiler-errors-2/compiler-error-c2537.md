---
title: Erreur du compilateur C2537 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2537
dev_langs:
- C++
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6100f77d3a1487bfa1eb12a78ac8187cec43fe64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199955"
---
# <a name="compiler-error-c2537"></a>Erreur du compilateur C2537
'spécificateur' : spécification de liaison non conforme  
  
 Causes possibles :  
  
1.  Le spécificateur de liaison n’est pas pris en charge. Seul le spécificateur de liaison « C » est pris en charge.  
  
2.  Une liaison de « C » est spécifiée pour plusieurs fonctions dans un ensemble de fonctions surchargées. Cette opération n’est pas autorisée.  
  
 L’exemple suivant génère l’erreur C2537 :  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```