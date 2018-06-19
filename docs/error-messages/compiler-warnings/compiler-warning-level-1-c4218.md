---
title: Compilateur avertissement (niveau 1) C4218 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88b27af84c390760274bb20665eec4452c8e7072
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279748"
---
# <a name="compiler-warning-level-1-c4218"></a>Avertissement du compilateur (niveau 4) C4218
extension non standard utilisée : doit spécifier au moins une classe de stockage ou un type  
  
 Avec les extensions Microsoft (/Ze), vous pouvez déclarer une variable sans spécification d’une classe de stockage ou de type. Le type par défaut est `int`.  
  
## <a name="example"></a>Exemple  
  
```  
// C4218.c  
// compile with: /W4  
i;  // C4218  
  
int main()  
{  
}  
```  
  
 Ces déclarations sont non valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).