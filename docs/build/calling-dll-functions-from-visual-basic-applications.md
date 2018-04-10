---
title: Appeler des fonctions DLL à partir d’Applications Visual Basic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed99b0ebe41a8f1bc9684638fa74e18556dd51f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Appel de fonctions de la DLL à partir d'applications Visual Basic
Pour les applications Visual Basic (ou les applications dans d’autres langages tels que Pascal ou Fortran) appeler des fonctions dans une DLL C/C++, les fonctions doivent être exportées à l’aide de la convention d’appel correcte sans la décoration de noms effectuée par le compilateur.  
  
 `__stdcall`crée la convention d’appel correcte pour la fonction (la fonction appelée nettoie la pile et les paramètres sont passés de droite à gauche) mais décore le nom de la fonction différemment. Ainsi, lorsque **__declspec (dllexport)** est utilisée sur une fonction exportée dans une DLL, le nom décoré est exporté.  
  
 Le `__stdcall` décoration de nom précéder le nom de symbole d’un trait de soulignement (_) et ajoute le symbole avec un arobase (@) suivi par le nombre d’octets dans la liste d’arguments (l’espace de pile requis). Par conséquent, lorsqu’elle est déclarée en tant que :  
  
```  
int __stdcall func (int a, double b)  
```  
  
 est décorée comme :  
  
```  
_func@12  
```  
  
 La convention d’appel C (`__cdecl`) décore le nom en tant que `_func`.  
  
 Pour obtenir le nom décoré, utilisez [mappage](../build/reference/map-generate-mapfile.md). Utilisation de **__declspec (dllexport)** effectue les opérations suivantes :  
  
-   Si la fonction est exportée avec la convention d’appel C (**_cdecl**), elle supprime le trait de soulignement (_) quand le nom est exporté.  
  
-   Si la fonction exportée n’utilise pas la convention d’appel C (par exemple, `__stdcall`), elle exporte le nom décoré.  
  
 Comme il n’existe aucun moyen de remplacement dans laquelle le nettoyage de pile se produit, vous devez utiliser `__stdcall`. Pour la décoration des noms avec `__stdcall`, vous devez les spécifier à l’aide d’alias dans la section EXPORTS du fichier .def. Ceci est illustré comme suit pour la déclaration de fonction suivante :  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 Dans le. Fichier de définition :  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 Pour les DLL puissent être appelées par des programmes écrits en Visual Basic, la technique des alias décrite dans cette rubrique est nécessaire dans le fichier .def. Si l’alias est utilisé dans le programme Visual Basic, utilisez des alias dans le fichier .def n’est pas nécessaire. Il peut être effectuée dans le programme Visual Basic en ajoutant une clause d’alias à la [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) instruction.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Exportation à partir d’une DLL](../build/exporting-from-a-dll.md)  
  
-   [Exportation à partir d’une DLL à l’aide. Fichiers DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportation à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportation de fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)  
  
-   [Noms décorés](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DLL dans Visual C++](../build/dlls-in-visual-cpp.md)