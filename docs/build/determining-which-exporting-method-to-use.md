---
description: 'En savoir plus sur : déterminer la méthode d’exportation à utiliser'
title: Déterminer la méthode d’exportation à utiliser
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 5d9e973d331ebd6190cd8e2a46601dfe2b057d09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162974"
---
# <a name="determine-which-exporting-method-to-use"></a>Déterminer la méthode d’exportation à utiliser

Vous pouvez exporter des fonctions dans les deux fichiers à la fois : un fichier .def ou le mot clé `__declspec(dllexport)`. Pour vous aider à déterminer quelles méthodes sont les plus appropriées pour la DLL, tenez compte de ces questions :

- Prévoyez-vous d'exporter des fonctions ultérieurement ?

- Est-ce-que votre DLL est uniquement utilisée par les applications que vous pouvez régénérer, ou est-elle utilisée par les applications que vous ne pouvez pas régénérer, par exemple, les applications créées par des concepteurs tiers ?

## <a name="pros-and-cons-of-using-def-files"></a>Avantages et inconvénients de l'utilisation des fichiers .def

L'exportation de fonctions dans un fichier .def permet de déterminer les ordinaux d'exportation. Lorsque vous ajoutez une fonction exportée supplémentaire à la DLL, vous pouvez leur assigner une valeur ordinale supérieure (supérieure à toute autre fonction exportée). Dans ce cas, les applications qui utilisent la liaison implicite n'ont pas besoin d'une réédition de leurs liens avec la bibliothèque d'importation contenant la nouvelle fonction. Il est très pratique si vous concevez une DLL destinée à de nombreuses applications car vous pouvez ajouter de nouvelles fonctionnalités et également vérifier qu'elles continuent à fonctionner correctement avec les applications qui reposent dessus. Par exemple, les DLL MFC sont générées à l'aide des fichiers .def.

Un autre avantage de l'utilisation d'un fichier .def est que vous pouvez utiliser l'attribut `NONAME` pour exporter une fonction. Cela met uniquement l'ordinal dans la table d'exportation de la DLL. Pour les DLL comportant un grand nombre de fonctions exportées, l'utilisation de l'attribut `NONAME` peut réduire la taille du fichier DLL. Pour plus d’informations sur l’écriture d’une instruction de définition de module, consultez [règles pour les instructions Module-Definition](reference/rules-for-module-definition-statements.md). Pour plus d’informations sur l’exportation ordinale, consultez [exportation de fonctions à partir d’une dll par ordinal plutôt que par nom](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

L’un des inconvénients de l’utilisation d’un fichier. def est que si vous exportez des fonctions dans un fichier C++, vous devez soit placer les noms décorés dans le fichier. def, soit définir les fonctions exportées en utilisant extern "C" pour éviter la décoration de noms effectuée par le compilateur MSVC.

Si vous placez les noms décorés dans le fichier. def, vous pouvez les obtenir à l’aide de l’outil [DUMPBIN](reference/dumpbin-reference.md) ou à l’aide de l’option [/Map](reference/map-generate-mapfile.md) de l’éditeur de liens. Les noms décorés qui sont produits par le compilateur lui sont spécifiques ; par conséquent, si vous mettez des noms décorés produits par le compilateur dans un fichier .def, les applications liées à la DLL doivent également être créées en utilisant la même version du compilateur afin que les noms décorés dans l'application appelante correspondent aux noms exportés dans le fichier .def de la DLL.

## <a name="pros-and-cons-of-using-__declspecdllexport"></a>Avantages et inconvénients de l’utilisation de __declspec (dllexport)

L'utilisation de `__declspec(dllexport)` est pratique dans la mesure où vous n'avez pas à vous préoccuper de la gestion d'un fichier .def ni de l'obtention des noms décorés des fonctions exportées. Toutefois, l'utilité de ce mode d'exportation est limité par le nombre d'applications liées que vous êtes prêt à reconstruire. Si vous régénérez la DLL avec de nouvelles exportations, vous devrez également régénérer l'application, car les noms décorés des fonctions C++ exportées peuvent changer si vous effectuez une recompilation avec une version différente du compilateur.

### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exportez à partir d’une DLL à l’aide de. Fichiers DEF](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide d' __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Importer dans une application à l’aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

- [Noms décorés](reference/decorated-names.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d'une DLL](exporting-from-a-dll.md)
