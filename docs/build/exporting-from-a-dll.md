---
title: Exportation à partir d’une DLL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07efe3d73b3f78dfb30e85ffad6434e2907c36c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367951"
---
# <a name="exporting-from-a-dll"></a>Exportation à partir d'une DLL  
  
Un fichier DLL a une structure similaire à un fichier .exe, avec une différence importante : un fichier DLL contient une table d’exportations. La table d’exportations contient le nom de chaque fonction de la DLL exporte vers d’autres exécutables. Ces fonctions sont les points d’entrée dans la DLL ; Seules les fonctions dans la table d’exportation est accessible par d’autres exécutables. D’autres fonctions dans la DLL appartiennent à la DLL. La table d’exportations de DLL peut être affichée à l’aide de la [DUMPBIN](../build/reference/dumpbin-reference.md) outil avec l’option /EXPORTS.  
  
 Vous pouvez exporter des fonctions à partir d’une DLL à l’aide de deux méthodes :  
  
-   Créer un fichier de définition (.def) de module et utiliser le fichier .def lors de la génération de la DLL. Utilisez cette approche si vous souhaitez [exporter des fonctions à partir de votre DLL par ordinal plutôt que par nom](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
-   Utilisez le mot clé **__declspec (dllexport)** dans la définition de la fonction.  
  
 Lorsque vous exportez des fonctions ou l’autre méthode, veillez à utiliser le [__stdcall](../cpp/stdcall.md) convention d’appel.  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Exporter à partir d’une DLL à l’aide de fichiers .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Exporter des fonctions à partir d’une DLL par ordinal plutôt que par nom](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)  
  
-   [Déterminer la méthode de liaison à utiliser](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
-   [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Importation dans une application](../build/importing-into-an-application.md)  
  
-   [Importation et exportation de fonctions inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importations mutuelles](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Importation et exportation](../build/importing-and-exporting.md)