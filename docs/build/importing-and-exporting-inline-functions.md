---
title: Importation et exportation de fonctions inline
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
ms.openlocfilehash: fb117ce6c6088b9fdca57f7d4fd7d0193e1813c2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425547"
---
# <a name="importing-and-exporting-inline-functions"></a>Importation et exportation de fonctions inline

Les fonctions importées peuvent être définies comme étant inline. L’effet est à peu près identique à la définition d’une fonction inline standard ; les appels à la fonction sont développés en code inline, comme une macro. Il s’agit essentiellement utile comme un moyen de prendre en charge C++ classes dans une DLL qui peuvent être inline à certaines de leurs membres fonctions pour plus d’efficacité.

Une fonctionnalité d’une fonction importée inline est que vous pouvez prendre son adresse en C++. Le compilateur retourne l’adresse de la copie de la fonction inline résidant dans la DLL. Une autre fonctionnalité des fonctions inline importées est que vous pouvez initialiser les données locales statiques de la fonction importée, contrairement aux données importées globales.

> [!CAUTION]
>  Soyez prudent lorsque vous en fournissant des fonctions inline importées, car elles peuvent donner lieu à des conflits de versions. Une fonction inline est développée dans le code d’application ; Par conséquent, si vous réécrivez ultérieurement la fonction, il ne pas mis à jour, sauf si l’application elle-même est recompilée. (Normalement, les fonctions DLL peuvent être mis à jour sans régénération des applications qui les utilisent.)

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL](../build/exporting-from-a-dll.md)

- [Exporter à partir d’une DLL à l’aide. Fichiers DEF](../build/exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Voir aussi

[Importation et exportation](../build/importing-and-exporting.md)
