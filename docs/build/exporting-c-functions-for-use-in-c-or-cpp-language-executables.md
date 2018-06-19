---
title: Exportation de fonctions C à utiliser dans des exécutables en langage C++ ou C | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee1d572bbfaa31ac626bfeb2b6ed7f61604628c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367704"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Exportation de fonctions C à utiliser dans des exécutables en langage C ou C++  
  
Si vous avez des fonctions dans une DLL écrite en C que vous souhaitez accéder à partir d’un langage C ou un module en C++, vous devez utiliser le **__cplusplus** macro de préprocesseur pour déterminer le langage compilé, puis de déclarer ces fonctions avec liaison C si utilisé à partir d’un module en C++. Si vous utilisez cette technique et fournissez les fichiers d’en-tête pour votre DLL, ces fonctions peuvent être utilisées par les utilisateurs de C et C++ sans modification.  
  
Le code suivant montre un fichier d’en-tête qui peut être utilisé par les applications clientes C et C++ :  
  
```h  
// MyCFuncs.h  
#ifdef __cplusplus  
extern "C" {  // only need to export C interface if  
              // used by C++ source code  
#endif  
  
__declspec( dllimport ) void MyCFunc();  
__declspec( dllimport ) void AnotherCFunc();  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
Si vous devez lier des fonctions C à votre exécutable C++ et les fichiers d’en-tête de fonction déclaration n’ont pas utilisé la technique ci-dessus, dans le fichier source C++, procédez comme suit pour empêcher le compilateur de décorer les noms de fonctions C :  
  
```cpp  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Exporter à partir d’une DLL à l’aide de fichiers .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importer dans une application à l’aide de __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Noms décorés](../build/reference/decorated-names.md)  
  
-   [Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation à partir d’une DLL](../build/exporting-from-a-dll.md)