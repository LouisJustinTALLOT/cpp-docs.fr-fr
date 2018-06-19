---
title: Compilateur avertissement (niveau 4) C4565 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3c4249783686c1fabb44395d3c092eca0d9230a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293357"
---
# <a name="compiler-warning-level-4-c4565"></a>Avertissement du compilateur (niveau 4) C4565
'fonction' : redéfinition ; le symbole était déclaré précédemment avec __declspec (modifier)  
  
 Un symbole a été redéfini ou redéclaré et la deuxième définition ou déclaration, contrairement à la première, n’avait pas une `__declspec` modificateur (***modificateur***). Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, supprimez une des définitions.  
  
 L’exemple suivant génère l’erreur C4565 :  
  
```  
// C4565.cpp  
// compile with: /W4 /LD  
__declspec(noalias) void f();  
void f();   // C4565  
```