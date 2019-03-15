---
title: L’importation et exportation de fonctions inline
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
ms.openlocfilehash: ed523d84228124d4a8d99e443c0c744f362f1c56
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822039"
---
# <a name="importing-and-exporting-inline-functions"></a>L’importation et exportation de fonctions inline

Les fonctions importées peuvent être définies comme étant inline. L’effet est à peu près identique à la définition d’une fonction inline standard ; les appels à la fonction sont développés en code inline, comme une macro. Il s’agit essentiellement utile comme un moyen de prendre en charge C++ classes dans une DLL qui peuvent être inline à certaines de leurs membres fonctions pour plus d’efficacité.

Une fonctionnalité d’une fonction importée inline est que vous pouvez prendre son adresse en C++. Le compilateur retourne l’adresse de la copie de la fonction inline résidant dans la DLL. Une autre fonctionnalité des fonctions inline importées est que vous pouvez initialiser les données locales statiques de la fonction importée, contrairement aux données importées globales.

> [!CAUTION]
>  Soyez prudent lorsque vous en fournissant des fonctions inline importées, car elles peuvent donner lieu à des conflits de versions. Une fonction inline est développée dans le code d’application ; Par conséquent, si vous réécrivez ultérieurement la fonction, il ne pas mis à jour, sauf si l’application elle-même est recompilée. (Normalement, les fonctions DLL peuvent être mis à jour sans régénération des applications qui les utilisent.)

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL](exporting-from-a-dll.md)

- [Exporter à partir d’une DLL à l’aide. Fichiers DEF](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec (dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Voir aussi

[Importation et exportation](importing-and-exporting.md)
