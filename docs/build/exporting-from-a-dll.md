---
title: Exportation à partir d'une DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: ac00df5a1bf1bcfaa300e12bb47cf1e6291aa0f1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416227"
---
# <a name="exporting-from-a-dll"></a>Exportation à partir d'une DLL

Un fichier DLL a une disposition ressemble beaucoup à un fichier .exe, avec une différence importante : un fichier DLL contient une table d’exportations. La table d’exportations contient le nom de chaque fonction de la DLL exporte vers d’autres exécutables. Ces fonctions sont les points d’entrée dans la DLL ; Seules les fonctions dans la table d’exportations sont accessibles par d’autres exécutables. Toutes les autres fonctions dans la DLL sont privées à la DLL. La table d’exportations de DLL peut être affichée à l’aide de la [DUMPBIN](../build/reference/dumpbin-reference.md) outil avec l’option /EXPORTS.

Vous pouvez exporter des fonctions à partir d’une DLL à l’aide de deux méthodes :

- Créer un fichier de définition (.def) de module et utiliser le fichier .def lors de la génération de la DLL. Utilisez cette approche si vous souhaitez [exporter des fonctions à partir de votre DLL par ordinal plutôt que par nom](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

- Utilisez le mot clé **__declspec (dllexport)** dans la définition de la fonction.

Lorsque vous exportez des fonctions soit la méthode, veillez à utiliser le [__stdcall](../cpp/stdcall.md) convention d’appel.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de fichiers .def](../build/exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Exporter des fonctions à partir d’une DLL par ordinal plutôt que par nom](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)

- [Déterminer la méthode de liaison à utiliser](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Importation dans une application](../build/importing-into-an-application.md)

- [L’importation et exportation de fonctions inline](../build/importing-and-exporting-inline-functions.md)

- [Importations mutuelles](../build/mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Importation et exportation](../build/importing-and-exporting.md)
