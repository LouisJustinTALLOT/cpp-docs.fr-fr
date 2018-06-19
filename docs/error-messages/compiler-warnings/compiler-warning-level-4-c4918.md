---
title: Compilateur avertissement (niveau 4) C4918 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4918
dev_langs:
- C++
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4ca1d8a33ac811a23fbb0ac3e438eeeb9c1acf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296794"
---
# <a name="compiler-warning-level-4-c4918"></a>Avertissement du compilateur (niveau 4) C4918
'character' : caractère non valide dans la liste d’optimisation pragma  
  
 Un caractère inconnu a été trouvé dans la liste d’optimisation d’une instruction pragma [optimize](../../preprocessor/optimize.md) .  
  
 Par exemple, l’instruction suivante génère l’avertissement C4918 :  
  
```  
// C4918.cpp  
// compile with: /W4  
#pragma optimize("X", on) // C4918 expected  
int main()  
{  
}  
```