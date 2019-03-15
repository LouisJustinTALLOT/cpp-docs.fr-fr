---
title: Exportation à partir d'une DLL à l'aide de fichiers DEF
ms.date: 01/09/2018
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 35f55ea525bd03c5b0b1b1750d25c1223bc608fc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816995"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Exportation à partir d'une DLL à l'aide de fichiers DEF

Une définition de module ou d’un fichier DEF (*.def) est un fichier texte contenant une ou plusieurs instructions du module décrivant divers attributs d’une DLL. Si vous n’utilisez pas le **__declspec (dllexport)** mot clé pour exporter des fonctions de la DLL, la DLL exige un fichier DEF.

Un fichier DEF minimal doit contenir les instructions de définition de module suivantes :

- La première instruction dans le fichier doit être l’instruction LIBRARY. Cette instruction identifie le fichier DEF comme appartenant à une DLL. L’instruction LIBRARY est suivie du nom de la DLL. L’éditeur de liens place ce nom dans la bibliothèque d’importation de la DLL.

- L’instruction EXPORTS répertorie les noms et, éventuellement, des valeurs ordinales des fonctions exportées par la DLL. Vous affectez à la fonction une valeur ordinale en suivant le nom de la fonction avec un arobase (@) et un nombre. Lorsque vous spécifiez des valeurs ordinales, ils doivent être dans la plage 1 à N, où N est le nombre de fonctions exportées par la DLL. Si vous souhaitez exporter des fonctions par ordinal, consultez [exportation de fonctions à partir d’une DLL par Ordinal plutôt que par nom](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) , ainsi que de cette rubrique.

Par exemple, une DLL qui contient le code pour implémenter un arbre de recherche binaire peut se présenter comme suit :

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Si vous utilisez le [Assistant DLL MFC](../mfc/reference/mfc-dll-wizard.md) pour créer une DLL MFC, l’Assistant crée un squelette de fichier DEF et l’ajoute automatiquement à votre projet. Ajoutez les noms des fonctions à exporter dans ce fichier. Pour les DLL non - MFC, créer le fichier DEF vous-même et ajoutez-le à votre projet. Accédez ensuite à **projet** > **propriétés** > **l’éditeur de liens** > **entrée**  >  **Fichier de définition de module** et entrez le nom du fichier DEF. Répétez cette étape pour chaque plateforme et de configuration, ou procédez à la fois en sélectionnant **Configuration = toutes les Configurations**, et **Platform = toutes les plateformes**.

Si vous exportez des fonctions dans un fichier C++, vous devez placer les noms décorés dans le fichier DEF soit définir les fonctions exportées avec une liaison C standard en utilisant extern « C ». Si vous devez placer les noms décorés dans le fichier DEF, vous pouvez les obtenir à l’aide de la [DUMPBIN](../build/reference/dumpbin-reference.md) d’outils ou en utilisant l’éditeur de liens [/mapper](../build/reference/map-generate-mapfile.md) option. Notez que les noms décorés produits par le compilateur sont spécifiques du compilateur. Si vous placez les noms décorés produits par le compilateur Visual C++ dans un fichier DEF, les applications qui sont liées à votre DLL doivent également être créées à l’aide de la même version de Visual C++ afin que les noms décorés dans l’application appelante correspondent aux noms exportés dans f DEF de la DLL Ile.

Si vous générez un [DLL d’extension](../build/extension-dlls-overview.md), et l’exportation à l’aide d’un fichier DEF, placez le code suivant au début et fin des fichiers d’en-tête contenant les classes exportées :

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Ces lignes garantissent que les variables MFC utilisées en interne ou qui sont ajoutés à vos classes sont exportées (ou importées) à partir de votre DLL d’extension MFC. Par exemple, lorsque vous dérivez une classe à l’aide `DECLARE_DYNAMIC`, la macro se développe pour ajouter un `CRuntimeClass` variable membre à votre classe. Si vous omettez ces quatre lignes risque d’être compilée ou liée de manière incorrecte ou provoquer une erreur lors de l’application cliente établit un lien vers la DLL.

Lorsque vous générez la DLL, l’éditeur de liens utilise le fichier DEF pour créer un fichier d’exportation (.exp) et un fichier de bibliothèque (.lib) d’importation. L’éditeur de liens utilise ensuite le fichier d’exportation pour générer le fichier DLL. Exécutables liés de manière implicite à la liaison DLL à la bibliothèque d’importation lorsqu’elles sont générées.

Notez que MFC elle-même utilise des fichiers DEF pour exporter des fonctions et des classes à partir de MFCx0.dll.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter et importer à l’aide de AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec (dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [fichiers .def](reference/module-definition-dot-def-files.md)

- [Règles pour les instructions de définition de module](reference/rules-for-module-definition-statements.md)

- [Noms décorés](reference/decorated-names.md)

- [L’importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](exporting-from-a-dll.md)
