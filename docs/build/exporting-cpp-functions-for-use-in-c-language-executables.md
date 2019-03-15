---
title: Exportation de fonctions C++ à utiliser dans des exécutables en langage C
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: a694b77e3730ab82ec1698076cc66729ff115cdc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814018"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Exportation de fonctions C++ à utiliser dans des exécutables en langage C

Si vous disposez de fonctions dans une DLL écrite en C++ que vous souhaitez accéder à partir d’un module en langage C, vous devez déclarer ces fonctions avec liaison C au lieu d’une liaison C++. Sauf indication contraire, le compilateur C++ utilise C++ d’affectation de noms (également connu sous la décoration de nom) de type sécurisé et C++, conventions d’appel, qui peuvent être difficiles à appeler à partir de C.

Pour spécifier une liaison C, spécifiez `extern "C"` déclarations de fonctions. Exemple :

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de fichiers .def](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec (dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Noms décorés](reference/decorated-names.md)

- [Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](exporting-from-a-dll.md)
