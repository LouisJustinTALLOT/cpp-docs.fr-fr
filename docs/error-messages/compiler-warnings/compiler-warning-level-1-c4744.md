---
title: Compilateur avertissement (niveau 1) C4744 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a45207f85575c8047f673b415ce802dbac24318
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282826"
---
# <a name="compiler-warning-level-1-c4744"></a>Avertissement du compilateur (niveau 1) C4744
'var' a un type différent dans 'fichier1' et 'fichier2' : 'type1' et 'type2'  
  
 Une variable externe référencée ou définie dans deux fichiers possède des types différents dans ces fichiers.  Pour résoudre, rendez les définitions de type, ou modifier le nom de variable dans un des fichiers.  
  
 C4744 est émise uniquement lorsque les fichiers sont compilés avec /GL.  Pour plus d’informations, consultez l’article [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md).  
  
> [!NOTE]
>  L’erreur C4744 se produit généralement dans les fichiers C (pas C++), car en C++, un nom de variable est décoré avec les informations de type.  Lors de l’échantillon (ci-dessous) est compile en C++, vous obtenez l’erreur de l’éditeur de liens LNK2019.  
  
## <a name="example"></a>Exemple  
 Cet exemple contient la première définition.  
  
```  
// C4744.c  
// compile with: /c /GL  
int global;  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4744.  
  
```  
// C4744b.c  
// compile with: C4744.c /GL /W1  
// C4744 expected  
#include <stdio.h>  
  
extern unsigned global;  
  
main()   
{  
    printf_s("%d\n", global);  
}  
```