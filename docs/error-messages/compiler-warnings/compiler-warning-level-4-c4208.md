---
title: Compilateur avertissement (niveau 4) C4208 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4208
dev_langs:
- C++
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b61f8b0a6a0ac61982bee79abb81f083d40a48f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292361"
---
# <a name="compiler-warning-level-4-c4208"></a>Avertissement du compilateur (niveau 4) C4208
extension non standard utilisée : delete [exp] - exp analysée mais ignorée  
  
 Avec les extensions Microsoft (/Ze), vous pouvez supprimer un tableau à l’aide d’une valeur entre accolades avec le [opérateur delete](../../cpp/delete-operator-cpp.md). La valeur est ignorée.  
  
```  
// C4208.cpp  
// compile with: /W4  
int main()  
{  
   int * MyArray = new int[18];  
   delete [18] MyArray;      // C4208  
   MyArray = new int[18];  
   delete [] MyArray;        // ok  
}  
```  
  
 Ces valeurs sont non valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).