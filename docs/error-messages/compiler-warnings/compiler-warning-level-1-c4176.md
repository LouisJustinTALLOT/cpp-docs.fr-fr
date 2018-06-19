---
title: Compilateur avertissement (niveau 1) C4176 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4176
dev_langs:
- C++
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1e00e4bdc18b8adeb95d2425c8b122ffde867cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274860"
---
# <a name="compiler-warning-level-1-c4176"></a>Avertissement du compilateur (niveau 1) C4176
'sous-composant' : sous-composant inconnu pour #pragma component (browser)  
  
 Le pragma **component** contient un sous-composant non valide. Pour exclure les références à un nom en particulier, vous devez utiliser l’option **references** avant ce nom.  
  
## <a name="example"></a>Exemple  
  
```  
// C4176.cpp  
// compile with: /W1 /LD  
#pragma component(browser, off, i)  // C4176  
#pragma component(browser, off, references, i) // ok  
```