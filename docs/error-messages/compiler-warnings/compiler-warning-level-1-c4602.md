---
title: Compilateur avertissement (niveau 1) C4602 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4602
dev_langs: C++
helpviewer_keywords: C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ff97549aed96263814c4d6a52e7634b6fd8ec04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4602"></a>Avertissement du compilateur (niveau 1) C4602
\#pragma pop_macro : 'nom de macro' pas de #pragma push_macro défini au préalable pour cet identificateur  
  
 Si vous utilisez [pop_macro](../../preprocessor/pop-macro.md) pour une macro particulière, vous devez au préalable passer le nom de cette macro à [push_macro](../../preprocessor/push-macro.md). L’exemple suivant génère l’avertissement C4602 :  
  
```  
// C4602.cpp  
// compile with: /W1  
int main()  
{  
   #pragma pop_macro("x")   // C4602 x is not on the stack  
}  
```