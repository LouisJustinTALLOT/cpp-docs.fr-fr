---
description: 'En savoir plus sur : importation et exportation de fonctions inline'
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
ms.openlocfilehash: 053280685edf8fa88c969399e7905582534c7493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156188"
---
# <a name="importing-and-exporting-inline-functions"></a>Importation et exportation de fonctions inline

Les fonctions importées peuvent être définies en tant que fonctions inline. L’effet est à peu près identique à la définition d’une fonction standard Inline ; les appels à la fonction sont développés en code inline, à l’instar d’une macro. Cela est principalement utile comme un moyen de prendre en charge les classes C++ dans une DLL qui peuvent incorporer certaines de leurs fonctions membres pour plus d’efficacité.

L’une des fonctionnalités d’une fonction inline importée est que vous pouvez prendre son adresse en C++. Le compilateur retourne l’adresse de la copie de la fonction inline résidant dans la DLL. Une autre fonctionnalité des fonctions inline importées est que vous pouvez initialiser des données locales statiques de la fonction importée, contrairement aux données importées globales.

> [!CAUTION]
> Vous devez faire preuve de prudence lorsque vous fournissez des fonctions inline importées, car elles peuvent créer des risques de conflits de versions. Une fonction inline est développée dans le code de l’application ; par conséquent, si vous réécrivez ultérieurement la fonction, elle n’est pas mise à jour, sauf si l’application elle-même est recompilée. (Normalement, les fonctions DLL peuvent être mises à jour sans recréer les applications qui les utilisent.)

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL](exporting-from-a-dll.md)

- [Exportez à partir d’une DLL à l’aide de. Fichiers DEF](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide d' __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

## <a name="see-also"></a>Voir aussi

[Importation et exportation](importing-and-exporting.md)
