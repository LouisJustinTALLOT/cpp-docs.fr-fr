---
title: VCBuild et MSBuild
description: Le système de génération VIsual Studio C++ a changé de VCBuild en MSBuild dans Visual Studio 2010.
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: b1b963aca3de75cf9852c55f59a99422568ab4b4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505913"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild et MSBuild : générer des modifications du système dans Visual Studio 2010

Le système MSBuild pour les projets C++ a été introduit dans Visual Studio 2010. Dans Visual Studio 2008 et les versions antérieures, le système VCBuild était utilisé. Certains types de fichiers et concepts qui dépendent de VCBuild n’existent pas ou sont représentés différemment dans MSBuild. Ce document présente les différences du système de génération actuel. Pour convertir un projet Visual Studio 2008 en MSBuild, vous devez utiliser Visual Studio 2010. Une fois le projet converti, vous devez utiliser la version la plus récente de Visual Studio pour effectuer une mise à niveau vers l’ensemble d’outils de compilateur et l’IDE actuel. Pour plus d’informations, notamment sur la façon d’obtenir Visual Studio 2010, consultez [instructions pour Visual studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

Les sections suivantes résument les modifications de VCBuild à MSBuild. Si votre projet VCBuild contient des macros ou des règles de génération personnalisées qui ne sont pas reconnues par MSBuild, consultez [Visual Studio Projects-C++](../build/creating-and-managing-visual-cpp-projects.md) pour savoir comment traduire ces instructions dans le système MSBuild. La conversion initiale de VCBuild en MSBuild n’est qu’une étape intermédiaire. Il n’est pas nécessaire d’avoir un fichier projet entièrement correct ou d’effectuer la compilation du programme sans erreurs. Vous utilisez uniquement Visual Studio 2010 pour convertir le projet au format MSBuild pour que le projet fonctionne dans la dernière version de Visual Studio.

## <a name="vcproj-is-now-vcxproj"></a>.vcproj devient maintenant .vcxproj

Les fichiers projet n’utilisent plus l’extension de nom de fichier .vcproj. Visual Studio 2010 convertit automatiquement les fichiers projet créés par une version antérieure de Visual C++ au format MSBuild, qui utilise l’extension. vcxproj pour les fichiers projet.

## <a name="vsprops-is-now-props"></a>.vsprops devient maintenant .props

Dans Visual Studio 2008 et versions antérieures, une *feuille de propriétés de projet* est un fichier XML qui a une extension de nom de fichier. vsprops. Une feuille de propriétés de projet permet de spécifier des commutateurs pour les outils de génération tels que le compilateur ou l’éditeur de liens, ainsi que de créer des macros définies par l’utilisateur. Dans MSBuild, l’extension de nom de fichier d’une feuille de propriétés de projet est. props.

## <a name="custom-build-rules-and-rules-files"></a>Règles de génération personnalisée et fichiers. Rules

Dans Visual Studio 2008 et versions antérieures, un *fichier de règles* est un fichier XML dont l’extension de nom de fichier est. Rules. Un fichier de règles permet de définir des règles de génération personnalisées et de les incorporer dans le processus de génération d’un projet Visual Studio C++. Une règle de génération personnalisée, que vous pouvez associer à une ou plusieurs extensions de nom de fichier, vous permet de passer des fichiers d’entrée à un outil qui crée un ou plusieurs fichiers de sortie.

Dans le système MSBuild, les règles de génération personnalisées sont représentées par trois types de fichiers,. xml,. props et. targets, au lieu d’un fichier. Rules. Lorsqu’un fichier. Rules qui a été créé à l’aide d’une version antérieure de Visual C++ est migré vers Visual Studio 2010, les fichiers. xml,. props et. targets équivalents sont créés et stockés dans votre projet avec le fichier. Rules d’origine.

> [!IMPORTANT]
> Dans Visual Studio 2010, l’IDE ne prend pas en charge la création de nouvelles règles. Pour cette raison, le moyen le plus simple d’utiliser un fichier de règles à partir d’un projet créé à l’aide d’une version antérieure de Visual C++ consiste à migrer le projet vers Visual Studio 2010.

## <a name="inheritance-macros"></a>Macros d’héritage

Dans Visual Studio 2008 et les versions antérieures, la macro **$ (Inherit)** spécifie l’ordre dans lequel les propriétés héritées apparaissent sur la ligne de commande qui est composée par le système de génération de projet. La macro **$(NoInherit)** permet d’ignorer toutes les occurrences de $(Inherit) et de rendre non héritées toutes les propriétés qui seraient sinon héritées. Par exemple, la macro $(Inherit) entraîne par défaut l’ajout à la ligne de commande des fichiers spécifiés à l’aide de l’option de compilateur [/I (Additional Include Directories)](../build/reference/i-additional-include-directories.md).

Dans Visual Studio 2010, l’héritage est pris en charge en spécifiant la valeur d’une propriété en tant que concaténation d’une ou plusieurs valeurs littérales et macros de propriété. Les macros **$(Inherit)** et **$(NoInherit)** ne sont pas prises en charge.

Dans l’exemple suivant, une liste délimitée par des points-virgules est affectée à une propriété dans une page de propriétés. La liste se compose de la concaténation du *\<value>* littéral et de la valeur de la `MyProperty` propriété, accessible à l’aide de la notation de macro **$ (**<em>MyProperty</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>fichiers. vcxproj. User

Un fichier utilisateur (.vcxproj.user) stocke des propriétés propres à l’utilisateur, par exemple, des paramètres de débogage et de déploiement. Le fichier *vcxproj. User* s’applique à tous les projets pour un utilisateur particulier.

## <a name="vcxprojfilters-file"></a>fichier. vcxproj. filters

Lorsque **Explorateur de solutions** est utilisé pour ajouter un fichier à un projet, le fichier de filtres (*. vcxproj. filters*) définit l’emplacement où le fichier est ajouté dans l’arborescence de **Explorateur de solutions** , en fonction de son extension de nom de fichier.

## <a name="vc-directories-settings"></a>Paramètres des répertoires VC + +

Les paramètres des répertoires Visual C++ sont spécifiés dans la [page de propriétés des répertoires VC++](../build/reference/vcpp-directories-property-page.md). Dans Visual Studio 2008 et versions antérieures, les paramètres des répertoires s’appliquent par utilisateur et la liste des répertoires exclus est spécifiée dans le fichier *SYSINCL. dat* .

Vous ne pouvez pas changer les paramètres des répertoires VC++ si vous exécutez [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) sur la ligne de commande. Vous ne pouvez pas non plus changer les paramètres si vous ouvrez le menu **Outils**, cliquez sur **Importation et exportation de paramètres**, puis sélectionnez l’option **Réinitialiser tous les paramètres**.

Pour migrer les paramètres des répertoires VC + + à partir d’un fichier *. vssettings* créé par une version antérieure de Visual Studio :

1. Ouvrez le menu **Outils** , cliquez sur **importation et exportation de paramètres** .
2. Sélectionnez **Importer les paramètres d’environnement sélectionnés**
3. Suivez les indications fournies par l'Assistant.

## <a name="see-also"></a>Voir aussi

[MSBuild sur la ligne de commande - C++](../build/msbuild-visual-cpp.md)
