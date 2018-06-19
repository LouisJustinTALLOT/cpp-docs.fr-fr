---
title: Compilateur avertissement (niveau 4) C4571 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4571
dev_langs:
- C++
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ecd2223baec2d2ff7e743442d0b44e54c8cb05d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301344"
---
# <a name="compiler-warning-level-4-c4571"></a>Avertissement du compilateur (niveau 4) C4571
Information : la sémantique changée depuis Visual C++ 7.1 ; les exceptions structurées (SEH) ne sont plus interceptées  
  
 L’erreur C4571 est générée pour chaque bloc catch (...) lors de la compilation avec **/EHs**.  
  
 Lors de la compilation avec **/EHs**, un bloc catch (...) n’intercepte pas d’exception structurée (division par zéro ou un pointeur null, par exemple) ; un catch (...) n’intercepte que levée explicitement, les exceptions C++.  Pour plus d’informations, consultez l’article [Gestion des exceptions](../../cpp/exception-handling-in-visual-cpp.md).  
  
 Cet avertissement est désactivé par défaut.  Activez cet avertissement pour garantir que lorsque vous compilez avec **/EHs** vos blocs catch (...) ne vont pas intercepter des exceptions structurées.  Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
 Vous pouvez résoudre l’erreur C4571 dans une des manières suivantes,  
  
-   Compilez avec **/EHa** si vous souhaitez toujours vos blocs catch (...) pour intercepter les exceptions structurées.  
  
-   N’activez pas l’erreur C4571 si vous ne souhaitez pas que vos blocs catch (...) pour intercepter les exceptions structurées, mais que vous souhaitez toujours utiliser des blocs catch (...).  Vous pouvez toujours intercepter les exceptions structurées à l’aide de la gestion des mots clés structurée des exceptions (**__try**, **__except**, et **__finally**).  Mais n’oubliez pas, lors de la compilation **/EHs** destructeurs sera appelées lors de la levée d’une exception C++, pas lorsqu’une exception SEH se produit.  
  
-   Remplacez les blocs catch (...) avec des blocs catch pour des exceptions C++ spécifiques et ajoutez éventuellement des exceptions structurées autour de la gestion d’exceptions C++ (**__try**, **__except**, et **_ _finally**).  Consultez [gestion structurée des exceptions (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) pour plus d’informations.  
  
 Consultez [/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md) pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4571.  
  
```  
// C4571.cpp  
// compile with: /EHs /W4 /c  
#pragma warning(default : 4571)  
int main() {  
   try {  
      int i = 0, j = 1;  
      j /= i;   // this will throw a SE (divide by zero)  
   }  
   catch(...) {}   // C4571 warning  
}  
```