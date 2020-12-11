---
description: 'En savoir plus sur : exportation de fonctions C à utiliser dans des exécutables en langage C ou C++'
title: Exportation de fonctions C à utiliser dans des exécutables en langage C ou C++
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: 9a45eb0a6f2a73f89696c03325690bc82ecd3082
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156656"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Exportation de fonctions C à utiliser dans des exécutables en langage C ou C++

Si vous avez des fonctions dans une DLL écrite en C auxquelles vous souhaitez accéder à partir d’un module de langage C ou C++, vous devez utiliser la macro de préprocesseur **__cplusplus** pour déterminer la langue en cours de compilation, puis déclarer ces fonctions avec une liaison C si elles sont utilisées à partir d’un module de langage C++. Si vous utilisez cette technique et fournissez des fichiers d’en-tête pour votre DLL, ces fonctions peuvent être utilisées par les utilisateurs C et C++ sans aucune modification.

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

Si vous avez besoin de lier des fonctions C à votre exécutable C++ et que les fichiers d’en-tête de déclaration de fonction n’ont pas utilisé la technique ci-dessus, dans le fichier source C++, procédez comme suit pour empêcher le compilateur de décorer les noms de fonctions C :

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de fichiers. def](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide d' __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Noms décorés](reference/decorated-names.md)

- [Utilisation d’extern pour spécifier la liaison](../cpp/extern-cpp.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d'une DLL](exporting-from-a-dll.md)
