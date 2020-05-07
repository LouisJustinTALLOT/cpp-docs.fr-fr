---
title: Exportation à partir d'une DLL à l'aide de fichiers DEF
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 6f7d58bcb42edd89527fff41b08a15321722a6cf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078519"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Exportation à partir d'une DLL à l'aide de fichiers DEF

Un fichier de définition de module ou de fichier DEF (*. def) est un fichier texte contenant une ou plusieurs instructions de module qui décrivent différents attributs d’une DLL. Si vous n’utilisez pas le mot clé **__declspec (dllexport)** pour exporter les fonctions de la dll, la dll requiert un fichier def.

Un fichier DEF minimal doit contenir les instructions de définition de module suivantes :

- La première instruction dans le fichier doit être l’instruction LIBRARY. Cette instruction identifie le fichier DEF comme appartenant à une DLL. L’instruction LIBRARY est suivie du nom de la DLL. L’éditeur de liens place ce nom dans la bibliothèque d’importation de la DLL.

- L’instruction EXPORTS répertorie les noms et, éventuellement, les valeurs ordinales des fonctions exportées par la DLL. Vous assignez la fonction à une valeur ordinale en suivant le nom de la fonction avec un arobase (@) et un nombre. Lorsque vous spécifiez des valeurs ordinales, elles doivent être comprises dans la plage 1 à N, où N est le nombre de fonctions exportées par la DLL. Si vous souhaitez exporter des fonctions par ordinal, consultez [exportation de fonctions à partir d’une dll par ordinal plutôt que par nom](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) , ainsi que cette rubrique.

Par exemple, une DLL qui contient le code permettant d’implémenter un arbre de recherche binaire peut se présenter comme suit :

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Si vous utilisez l' [Assistant DLL MFC](../mfc/reference/mfc-dll-wizard.md) pour créer une DLL MFC, l’Assistant crée un fichier de définition squelette pour vous et l’ajoute automatiquement à votre projet. Ajoutez les noms des fonctions à exporter dans ce fichier. Pour les dll non-MFC, créez vous-même le fichier DEF et ajoutez-le à votre projet. Accédez ensuite à **Project** > **Propriétés** > du projet**fichier de définition du module** **d’entrée** > de l'**éditeur de liens** > et entrez le nom du fichier def. Répétez cette étape pour chaque configuration et plateforme, ou faites-la tout à la fois en sélectionnant **configuration = toutes les configurations**et **plateforme = toutes les plateformes**.

Si vous exportez des fonctions dans un fichier C++, vous devez placer les noms décorés dans le fichier DEF ou définir vos fonctions exportées avec une liaison C standard à l’aide de extern "C". Si vous devez placer les noms décorés dans le fichier DEF, vous pouvez les obtenir à l’aide de l’outil [DUMPBIN](../build/reference/dumpbin-reference.md) ou à l’aide de l’option [/Map](../build/reference/map-generate-mapfile.md) de l’éditeur de liens. Notez que les noms décorés produits par le compilateur sont spécifiques au compilateur. Si vous placez les noms décorés produits par le compilateur Microsoft C++ (MSVC) dans un fichier DEF, les applications qui lient à votre DLL doivent également être générées à l’aide de la même version de MSVC afin que les noms décorés dans l’application appelante correspondent aux noms exportés dans le fichier DEF de la DLL.

> [!NOTE]
> Une DLL générée avec Visual Studio 2015 peut être consommée par les applications générées avec Visual Studio 2017 ou Visual Studio 2019.

Si vous générez une [dll d’extension](../build/extension-dlls-overview.md)et que vous exportez à l’aide d’un fichier def, placez le code suivant au début et à la fin de vos fichiers d’en-tête qui contiennent les classes exportées :

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Ces lignes garantissent que les variables MFC utilisées en interne ou ajoutées à vos classes sont exportées (ou importées) à partir de votre DLL d’extension MFC. Par exemple, quand vous dérivez une `DECLARE_DYNAMIC`classe à l’aide de, la macro `CRuntimeClass` se développe pour ajouter une variable membre à votre classe. Le fait de laisser ces quatre lignes peut entraîner la compilation ou le lien de votre DLL de manière incorrecte, ou provoquer une erreur lorsque l’application cliente est liée à la DLL.

Lors de la génération de la DLL, l’éditeur de liens utilise le fichier DEF pour créer un fichier d’exportation (. exp) et un fichier de bibliothèque d’importation (. lib). L’éditeur de liens utilise ensuite le fichier d’exportation pour générer le fichier DLL. Les exécutables qui sont implicitement liés à la DLL sont liés à la bibliothèque d’importation lorsqu’ils sont générés.

Notez que MFC lui-même utilise des fichiers DEF pour exporter des fonctions et des classes à partir de MFCx0. dll.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide d' __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l'aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [fichiers. def](reference/module-definition-dot-def-files.md)

- [Règles pour les instructions de définition de module](reference/rules-for-module-definition-statements.md)

- [Noms décorés](reference/decorated-names.md)

- [Importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](exporting-from-a-dll.md)
