---
title: Modifications du système de génération dans Visual Studio 2010
ms.date: 11/04/2016
f1_keywords:
- vc.msbuild.changes
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: 621e62379657da66d6eaec7a3ceff780fd610066
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57828171"
---
# <a name="build-system-changes"></a>Modifications du système de génération

Le système MSBuild est utilisé pour générer des projets Visual C++. Toutefois, dans Visual Studio 2008 et les versions antérieures, c’est le système VCBuild qui était utilisé. Certains types de fichiers et concepts qui dépendaient de VCBuild n’existent pas ou sont représentés différemment dans le système actuel. Ce document présente les différences du système de génération actuel.

## <a name="vcproj-is-now-vcxproj"></a>.vcproj devient maintenant .vcxproj

Les fichiers projet n’utilisent plus l’extension de nom de fichier .vcproj. Visual Studio convertit automatiquement les fichiers projet créés par une version antérieure de Visual C++ au format utilisé par le système actuel. Pour plus d’informations sur la mise à niveau manuelle d’un projet, consultez [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).

Dans la version actuelle, l’extension de nom de fichier d’un fichier projet est .vcxproj.

## <a name="vsprops-is-now-props"></a>.vsprops devient maintenant .props

Dans les versions antérieures, une *feuille de propriétés de projet* est un fichier XML qui porte une extension de nom de fichier .vsprops. Une feuille de propriétés de projet permet de spécifier des commutateurs pour les outils de génération tels que le compilateur ou l’éditeur de liens, ainsi que de créer des macros définies par l’utilisateur.

Dans la version actuelle, l’extension de nom de fichier d’une feuille de propriétés de projet est .props.

## <a name="custom-build-rules-and-rules-files"></a>Règles de génération personnalisées et fichiers .rules

Dans les versions antérieures, un *fichier de règles* est un fichier XML qui porte une extension de nom de fichier .rules. Un fichier de règles permet de définir des règles de génération personnalisées et de les incorporer dans le processus de génération d’un projet Visual C++. Une règle de génération personnalisée, que vous pouvez associer à une ou plusieurs extensions de nom de fichier, vous permet de passer des fichiers d’entrée à un outil qui crée un ou plusieurs fichiers de sortie.

Dans cette version, les règles de génération personnalisées sont représentées par trois types de fichiers, à savoir .xml, .props et .targets, au lieu d’un fichier .rules. Quand un fichier .rules créé à l’aide d’une version antérieure de Visual C++ migre vers la version actuelle, des fichiers .xml, .props et .targets équivalents sont créés et stockés dans votre projet avec le fichier .rules d’origine.

> [!IMPORTANT]
>  Dans la version actuelle, l’IDE ne prend pas en charge la création de nouvelles règles. C’est pourquoi la manière la plus simple d’utiliser un fichier de règles d’un projet créé à l’aide d’une version antérieure de Visual C++ consiste à migrer le projet vers la version actuelle.

## <a name="inheritance-macros"></a>Macros d’héritage

Dans les versions antérieures, la macro **$(Inherit)** spécifie l’ordre dans lequel les propriétés héritées apparaissent sur la ligne de commande composée par le système de génération de projet. La macro **$(NoInherit)** permet d’ignorer toutes les occurrences de $(Inherit) et de rendre non héritées toutes les propriétés qui seraient sinon héritées. Par exemple, la macro $(Inherit) entraîne par défaut l’ajout à la ligne de commande des fichiers spécifiés à l’aide de l’option de compilateur [/I (Additional Include Directories)](../build/reference/i-additional-include-directories.md).

Dans la version actuelle, l’héritage est pris en charge en spécifiant la valeur d’une propriété sous forme de concaténation d’une ou plusieurs valeurs littérales et macros de propriété. Les macros **$(Inherit)** et **$(NoInherit)** ne sont pas prises en charge.

Dans l’exemple suivant, une liste délimitée par des points-virgules est affectée à une propriété dans une page de propriétés. La liste est constituée de la concaténation du littéral de la *\<valeur>* et de la valeur de la propriété `MyProperty`, accessible à l’aide de la notation de macro, **$(**<em>MyProperty</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>Fichiers .vcxproj.user

Un fichier utilisateur (.vcxproj.user) stocke des propriétés propres à l’utilisateur, par exemple, des paramètres de débogage et de déploiement. Le fichier vcxproj.user s’applique à tous les projets d’un utilisateur particulier.

## <a name="vcxprojfilters-file"></a>Fichier .vcxproj.filters

Quand vous ajoutez un fichier à un projet par le biais de l’**Explorateur de solutions**, le fichier de filtres (.vcxproj.filters) détermine à quel emplacement le fichier est ajouté dans l’arborescence de l’**Explorateur de solutions**, en fonction de son extension de nom de fichier.

## <a name="vc-directories-settings"></a>Paramètres des répertoires VC++

Les paramètres des répertoires Visual C++ sont spécifiés dans la [page de propriétés des répertoires VC++](../ide/vcpp-directories-property-page.md). Dans les versions antérieures de Visual Studio, les paramètres des répertoires s’appliquent par utilisateur et la liste des répertoires exclus est spécifiée dans le fichier sysincl.dat.

Vous ne pouvez pas changer les paramètres des répertoires VC++ si vous exécutez [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) sur la ligne de commande. Vous ne pouvez pas non plus changer les paramètres si vous ouvrez le menu **Outils**, cliquez sur **Importation et exportation de paramètres**, puis sélectionnez l’option **Réinitialiser tous les paramètres**.

Migrez les paramètres des répertoires VC++ d’un fichier .vssettings créé par une version antérieure de Visual C++. Ouvrez le menu **Outils**, cliquez sur **Importation et exportation de paramètres**, sélectionnez **Importer les paramètres d’environnement sélectionnés**, puis suivez les instructions de l’Assistant. Ou bien, au premier démarrage de Visual Studio, dans la boîte de dialogue **Choisir les paramètres d’environnement par défaut**, sélectionnez **Migrer mes paramètres éligibles depuis une version précédente et les ajouter aux paramètres par défaut sélectionnés ci-dessous**.

## <a name="see-also"></a>Voir aussi

[MSBuild sur la ligne de commande - C++](../build/msbuild-visual-cpp.md)
