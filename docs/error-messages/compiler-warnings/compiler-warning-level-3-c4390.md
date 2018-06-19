---
title: Compilateur avertissement (niveau 3) C4390 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4390
dev_langs:
- C++
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d052a1fa6124aa1518cddec00566e14668fe111d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290086"
---
# <a name="compiler-warning-level-3-c4390"></a>Avertissement du compilateur (niveau 3) C4390
' ;' : vide instruction contrôlée a été trouvée. Cela est son but ?  
  
 Un point-virgule a été trouvé après une instruction de contrôle qui ne contient aucune instruction.  
  
 Si vous obtenez C4390 à cause d’une macro, vous devez utiliser le [avertissement](../../preprocessor/warning.md) pragma pour désactiver C4390 dans le module contenant la macro.  
  
 L’exemple suivant génère l’erreur C4390 :  
  
```  
// C4390.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
   if (i);   // C4390  
      i++;  
}  
```