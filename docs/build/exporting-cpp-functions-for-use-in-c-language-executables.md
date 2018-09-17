---
title: Exportation de fonctions C++ à utiliser dans des exécutables en langage C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abdc8dc0f853faf0649581d535cb631c232e8276
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709941"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Exportation de fonctions C++ à utiliser dans des exécutables en langage C

Si vous disposez de fonctions dans une DLL écrite en C++ que vous souhaitez accéder à partir d’un module en langage C, vous devez déclarer ces fonctions avec liaison C au lieu d’une liaison C++. Sauf indication contraire, le compilateur C++ utilise C++ d’affectation de noms (également connu sous la décoration de nom) de type sécurisé et C++, conventions d’appel, qui peuvent être difficiles à appeler à partir de C.

Pour spécifier une liaison C, spécifiez `extern "C"` déclarations de fonctions. Exemple :

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de fichiers .def](../build/exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Noms décorés](../build/reference/decorated-names.md)

- [Utilisation d’extern pour spécifier la liaison](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](../build/exporting-from-a-dll.md)