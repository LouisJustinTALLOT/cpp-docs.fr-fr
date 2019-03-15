---
title: Exportation de fonctions C à utiliser dans des exécutables en langage C ou C++
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: b7ba2ed30615efb3b05e71cecf0ea69898feb8ba
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812432"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Exportation de fonctions C à utiliser dans des exécutables en langage C ou C++

Si vous disposez de fonctions dans une DLL écrite en C et que vous souhaitez accéder à partir d’un langage C ou un module en C++, vous devez utiliser le **__cplusplus** macro de préprocesseur pour déterminer le langage en cours de compilation et ensuite déclarer ces fonctions avec liaison C si utilisé à partir d’un module en C++. Si vous utilisez cette technique et fournissez les fichiers d’en-tête pour votre DLL, ces fonctions peuvent être utilisées par les utilisateurs de C et C++ sans modification.

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

Si vous devez lier des fonctions C à votre exécutable C++ et les fichiers d’en-tête de déclaration (fonction) n’ont pas utilisé la technique ci-dessus, dans le fichier source C++, procédez comme suit pour empêcher le compilateur de décorer les noms de fonction C :

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de fichiers .def](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec (dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Noms décorés](reference/decorated-names.md)

- [Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](exporting-from-a-dll.md)
