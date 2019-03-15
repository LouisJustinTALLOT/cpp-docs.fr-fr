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
ms.openlocfilehash: 6bdf5b86724ae07aa073a9feb1cc4d5723bc6e6b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819115"
---
# <a name="exporting-from-a-dll"></a>Exportation à partir d'une DLL

Un fichier DLL a une disposition ressemble beaucoup à un fichier .exe, avec une différence importante : un fichier DLL contient une table d’exportations. La table d’exportations contient le nom de chaque fonction de la DLL exporte vers d’autres exécutables. Ces fonctions sont les points d’entrée dans la DLL ; Seules les fonctions dans la table d’exportations sont accessibles par d’autres exécutables. Toutes les autres fonctions dans la DLL sont privées à la DLL. La table d’exportations de DLL peut être affichée à l’aide de la [DUMPBIN](reference/dumpbin-reference.md) outil avec l’option /EXPORTS.

Vous pouvez exporter des fonctions à partir d’une DLL à l’aide de deux méthodes :

- Créer un fichier de définition (.def) de module et utiliser le fichier .def lors de la génération de la DLL. Utilisez cette approche si vous souhaitez [exporter des fonctions à partir de votre DLL par ordinal plutôt que par nom](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

- Utilisez le mot clé **__declspec (dllexport)** dans la définition de la fonction.

Lorsque vous exportez des fonctions soit la méthode, veillez à utiliser le [__stdcall](../cpp/stdcall.md) convention d’appel.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de fichiers .def](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Exporter des fonctions à partir d’une DLL par ordinal plutôt que par nom](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Lier un exécutable à une DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Importation dans une application](importing-into-an-application.md)

- [L’importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Importation et exportation](importing-and-exporting.md)
