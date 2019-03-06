---
title: Modifications du système de génération
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
ms.openlocfilehash: 742b018ae96ff706336a81b49e1d8e5fb954d9b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425443"
---
# <a name="build-system-changes"></a>Modifications du système de génération

Le système MSBuild est utilisé pour générer des projets Visual C++. Toutefois, dans Visual Studio 2008 et versions antérieures, le système de VCBuild a été utilisé. Certains types de fichiers et les concepts qui dépendaient de VCBuild n’existent pas ou sont représentés différemment dans le système actuel. Ce document présente les différences dans le système de génération en cours.

## <a name="vcproj-is-now-vcxproj"></a>.vcproj est désormais .vcxproj

Fichiers de projet ne plus utilisent l’extension de nom de fichier .vcproj. Visual Studio convertit automatiquement les fichiers projet qui ont été créés par une version antérieure de Visual C++ pour le format utilisé par le système actuel. Pour plus d’informations sur la mise à niveau manuellement un projet, consultez [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).

Dans la version actuelle, l’extension de nom de fichier pour un fichier de projet est .vcxproj.

## <a name="vsprops-is-now-props"></a>.vsprops est désormais .props

Dans les versions antérieures, un *feuille de propriétés de projet* est un fichier basé sur XML qui possède une extension de nom de fichier .vsprops. Une feuille de propriétés de projet vous permet de spécifier des commutateurs pour les outils de génération tels que le compilateur ou l’éditeur de liens et de créer des macros définies par l’utilisateur.

Dans la version actuelle, l’extension de nom de fichier pour une feuille de propriétés de projet est .props.

## <a name="custom-build-rules-and-rules-files"></a>Fichiers .rules et les règles de génération personnalisée

Dans les versions antérieures, un *fichier de règles* est un fichier basé sur XML qui possède une extension de nom de fichier .rules. Un fichier de règles vous permet de définir des règles de génération personnalisée et les incorporer dans le processus de génération d’un projet Visual C++. Une règle de génération personnalisée, qui peut être associée à une ou plusieurs extensions de nom de fichier, vous permet de passer des fichiers d’entrée à un outil qui crée un ou plusieurs fichiers de sortie.

Dans cette version, les règles de génération personnalisée sont représentées par trois types de fichiers .xml, .props et .targets, au lieu d’un fichier .rules. Lorsqu’un fichier .rules créé à l’aide d’une version antérieure de Visual C++ est migré vers la version actuelle, les fichiers .xml, .props et .targets équivalents sont créées et stockées dans votre projet avec le fichier .rules d’origine.

> [!IMPORTANT]
>  Dans la version actuelle, l’IDE ne prend pas en charge la création de nouvelles règles. Pour cette raison, le plus simple d’utiliser un fichier de règles à partir d’un projet qui a été créé à l’aide d’une version antérieure de Visual C++ consiste à migrer le projet vers la version actuelle.

## <a name="inheritance-macros"></a>Macros d’héritage

Dans les versions antérieures, le **$ (Inherit)** macro Spécifie l’ordre dans lequel les propriétés héritées apparaissent sur la ligne de commande qui est composée par le système de génération de projet. Le **$ (NoInherit)** macro toute occurrence de $ (Inherit) doivent être ignorés et toutes les propriétés devant être héritées, pas à être héritée. Par exemple, par défaut la macro $ (Inherit) entraîne des fichiers spécifiés à l’aide de la [/I (autres répertoires Include)](../build/reference/i-additional-include-directories.md) option du compilateur à ajouter à la ligne de commande.

Dans la version actuelle, l’héritage est pris en charge en spécifiant la valeur d’une propriété comme la concaténation d’un ou plusieurs des valeurs littérales et des macros de propriété. Le **$ (Inherit)** et **$ (NoInherit)** macros ne sont pas prises en charge.

Dans l’exemple suivant, une liste délimitée par des points-virgules est affectée à une propriété sur une page de propriétés. La liste se compose de la concaténation de la  *\<valeur >* littéral et la valeur de la `MyProperty` propriété, qui est accessible à l’aide de la notation de macro, **$(**  <em>MyProperty</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>. vcxproj.user fichiers

Un fichier utilisateur (. vcxproj.user) stocke des propriétés spécifiques à l’utilisateur, pour les paramètres de l’exemple, le débogage et déploiement. Le fichier vcxproj.user s’applique à tous les projets pour un utilisateur particulier.

## <a name="vcxprojfilters-file"></a>. vcxproj.filters fichier

Lorsque **l’Explorateur de solutions** est utilisé pour ajouter un fichier à un projet, le fichier de filtres (. vcxproj.filters) définit l’emplacement dans le **l’Explorateur de solutions** arborescence le fichier est ajouté, en fonction de son extension de nom de fichier.

## <a name="vc-directories-settings"></a>Paramètres de répertoires VC ++

Paramètres de répertoires Visual C++ sont spécifiés sur le [VC ++ Directories Property Page](../ide/vcpp-directories-property-page.md). Dans les versions antérieures de Visual Studio, les paramètres de répertoires s’appliquent par utilisateur et la liste des répertoires exclus est spécifiée dans le fichier sysincl.dat.

Vous ne pouvez pas modifier les paramètres de répertoires VC ++ si vous exécutez [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) en ligne de commande. Vous ne pouvez pas également modifier les paramètres si vous ouvrez le **outils** menu, cliquez sur **importation et exportation de paramètres**, puis sélectionnez le **réinitialiser tous les paramètres** option.

Migrer les paramètres de répertoires VC ++ à partir d’un fichier .vssettings créé par une version antérieure de Visual C++. Ouvrez le **outils** menu, cliquez sur **importation et exportation de paramètres**, sélectionnez **importer les paramètres d’environnement sélectionnés**, puis suivez les instructions de l’Assistant. Ou lorsque vous démarrez Visual Studio pour la première fois, sur le **choisissez Paramètres d’environnement par défaut** boîte de dialogue, sélectionnez **migrer mes paramètres éligibles depuis une version précédente et appliquez-les en plus des paramètres par défaut sélectionné ci-dessous**.

## <a name="see-also"></a>Voir aussi

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
