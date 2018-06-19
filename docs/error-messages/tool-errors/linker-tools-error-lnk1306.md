---
title: Erreur LNK1306 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1306
dev_langs:
- C++
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb340a4c28f94f18e0c4b65bea8749394e002bd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300496"
---
# <a name="linker-tools-error-lnk1306"></a>Erreur des outils Éditeur de liens LNK1306  
  
> Fonction de point d’entrée DLL ne peut pas être managée ; compilez en natif  
  
`DllMain` ne peut pas être compilé en langage MSIL ; Il doit être compilé en mode natif.  
  
Pour résoudre ce problème,  
  
-   Compilez le fichier qui contient le point d’entrée sans **/CLR**.  
  
-   Placez le point d’entrée dans un `#pragma unmanaged` section.  
  
Pour plus d'informations, voir :  
  
-   [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [managed, unmanaged](../../preprocessor/managed-unmanaged.md)  
  
-   [Initialisation d’assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [DLL et comportement de la bibliothèque runtime Visual C++](../../build/run-time-library-behavior.md)  
  
## <a name="example"></a>Exemple  
  
L’exemple suivant génère l’erreur LNK1306.  
  
```cpp  
// LNK1306.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
// LNK1306 error expected  
#include <windows.h>  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
```  
  
Pour résoudre ce problème, n’utilisez pas l’option/CLR pour compiler ce fichier, ou utilisez un `#pragma` directive à placer la définition de point d’entrée dans une section non managée, comme indiqué dans cet exemple :  
  
```cpp  
// LNK1306fix.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
#include <windows.h>  
#pragma managed(push, off)  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
#pragma managed(pop)  
```  
