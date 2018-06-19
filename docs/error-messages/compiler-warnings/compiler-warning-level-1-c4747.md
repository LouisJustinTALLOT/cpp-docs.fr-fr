---
title: Compilateur avertissement (niveau 1) C4747 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 203943f3741d07e278652a7032a6dcdcb305a384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285822"
---
# <a name="compiler-warning-level-1-c4747"></a>Avertissement du compilateur (niveau 1) C4747
Appel managé 'point d’entrée' : Impossible d’exécuter du code managé le verrouillage du chargeur, y compris le point d’entrée de DLL et les appels accessibles à partir du point d’entrée DLL  
  
 Le compilateur a détecté un point d’entrée DLL (probable) compilé en langage MSIL.  En raison de problèmes potentiels de chargement d’une DLL dont le point d’entrée a été compilé en langage MSIL, il est vivement déconseillé à partir de la compilation d’une fonction de point d’entrée DLL en langage MSIL.  
  
 Pour plus d’informations, consultez [l’initialisation d’assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md) et [erreur des outils Éditeur de liens LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Ne compilez pas le module avec **/CLR**.  
  
2.  Marquez la fonction de point d’entrée avec `#pragma unmanaged`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4747.  
  
```  
// C4747.cpp  
// compile with: /clr /c /W1  
// C4747 expected  
#include <windows.h>  
  
// Uncomment the following line to resolve.  
// #pragma unmanaged  
  
BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {  
   return TRUE;  
};  
```