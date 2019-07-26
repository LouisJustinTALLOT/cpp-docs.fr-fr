---
title: 'Procédure : Modifier le Framework cible et l’ensemble d’outils de plateforme'
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: 6af7a4eb47c1d3f8b9c52eec39795c9307ca9d8e
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492230"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Procédure : Modifier le Framework cible et l’ensemble d’outils de plateforme

Vous pouvez modifier un fichier projet C++ Visual Studio pour cibler différentes versions de l' C++ ensemble d’outils de plateforme, le SDK Windows etC++le .NET Framework (projets/CLI uniquement). Par défaut, le système de projet utilise la version du. Net Framework et la version de l'ensemble d'outils qui correspondent à la version de Visual Studio que vous utilisez pour créer le projet. Vous pouvez modifier toutes ces valeurs dans le fichier. vcxproj afin de pouvoir utiliser la même base de code pour chaque cible de compilation.

## <a name="platform-toolset"></a>Ensemble d’outils de plateforme

L’ensemble d’outils de plateforme C++ se compose du compilateur (cl. exe) et de l’éditeur de liens (Link. exe)C++ , ainsi que des bibliothèques C/standard. Depuis Visual Studio 2015, la version majeure de l’ensemble d’outils est restée à 14, ce qui signifie que les projets compilés avec Visual Studio 2019 ou Visual Studio 2017 sont compatibles ABI-Backwards avec les projets compilés avec Visual Studio 2015. La version mineure a été mise à jour de 1 pour chaque version depuis Visual Studio 2015:

- Visual Studio 2015: V140
- Visual Studio 2017: V141
- Visual Studio 2019: V142

Ces ensembles d’outils prennent en charge .NET Framework 4,5 et versions ultérieures.

Visual Studio prend également en charge le MULTICIBLAGE pour les C++ projets. Vous pouvez utiliser l’IDE de Visual Studio pour modifier et générer des projets créés avec des versions antérieures de Visual Studio, sans les mettre à niveau pour utiliser une nouvelle version de l’ensemble d’outils. Les ensembles d’outils les plus anciens doivent être installés sur votre ordinateur. Pour plus d’informations, consultez [comment utiliser le multi-ciblage natif dans Visual Studio](../porting/use-native-multi-targeting.md). Par exemple, dans Visual Studio 2015, vous pouvez *cibler* .NET Framework 2,0, mais vous devez utiliser un ensemble d’outils antérieur qui le prend en charge.

## <a name="target-framework-ccli-project-only"></a>Framework cible (C++projet/CLI uniquement)

Lorsque vous changez le Framework cible, remplacez également l'ensemble d'outils de plateforme par une version qui prend en charge ce Framework. Par exemple, pour cibler le .NET Framework 4.5, vous devez utiliser un ensemble d’outils de plateforme compatible, comme Visual Studio 2015 (v140), Visual Studio 2013 (v120) ou Visual Studio 2012 (v110). Vous pouvez utiliser l’ensemble d’outils de plateforme du [Kit de développement logiciel (SDK) Windows 7,1](https://www.microsoft.com/en-us/download/details.aspx?id=8279) pour cibler les plates-formes .NET Framework 2,0, 3,0, 3,5 et 4, ainsi que les plateformes x86/x64.

Vous pouvez étendre davantage la plateforme cible en créant un ensemble d'outils de plateforme personnalisé. Pour plus d’informations, consultez [Multiciblage natif C++](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) sur le blog de Visual C++.

### <a name="to-change-the-target-framework"></a>Pour changer la version cible du .Net Framework

1. Dans Visual Studio, dans l’ **Explorateur de solutions**, sélectionnez votre projet. Sur la barre de menus, ouvrez le menu **Projet** et choisissez **Décharger le projet**. Le fichier de projet (.vcxproj) de votre projet est alors déchargé.

   > [!NOTE]
   >  Le projet C++ ne peut pas être chargé pendant que le fichier projet est en cours de modification dans Visual Studio. Toutefois, vous pouvez utiliser un autre éditeur tel que le Bloc-notes pour modifier le fichier projet lorsque le projet est chargé dans Visual Studio. Visual Studio détecte que le fichier projet a changé et vous invite à recharger le projet.

1. Dans la barre de menus, sélectionnez **Fichier**, **Ouvrir**, **Fichier**. Dans la boîte de dialogue **Ouvrir un fichier** , accédez à votre dossier de projet, puis ouvrez le fichier projet (.vcxproj).

1. Dans le fichier projet, recherchez l'entrée correspondant à la version du Framework cible. Par exemple, si votre projet est destiné à utiliser .NET Framework 4.5, recherchez `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` dans l'élément `<PropertyGroup Label="Globals">` de l'élément `<Project>` . Si l'élément `<TargetFrameworkVersion>` n'est pas présent, votre projet n'utilise pas le .NET Framework et aucune modification n'est requise.

1. Remplacez la valeur par la version du .NET Framework de votre choix, comme v3.5 ou v4.

1. Enregistrez les modifications et fermez l'éditeur.

1. Dans l' **Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Recharger le projet**.

1. Pour vérifier la modification, dans l’ **Explorateur de solutions**, cliquez avec le bouton droit pour ouvrir le menu contextuel pour votre projet (et non pas pour votre solution), puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **Pages de propriétés** de votre projet. Dans le volet gauche de la boîte de dialogue, développez **Propriétés de configuration** , puis sélectionnez **Général**. Vérifiez que **Version du .NET Framework cible** indique la nouvelle version du .NET Framework.

### <a name="to-change-the-platform-toolset"></a>Pour modifier l’ensemble d’outils de plateforme

1. Dans Visual Studio, dans l' **Explorateur de solutions**, ouvrez le menu contextuel pour votre projet (et non pas pour votre solution), puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **Pages de propriétés** de votre projet.

1. Dans la boîte de dialogue **Pages de propriétés** , ouvrez la liste déroulante **Configuration** puis sélectionnez **Toutes les configurations**.

1. Dans le volet gauche de la boîte de dialogue, développez **Propriétés de configuration** , puis sélectionnez **Général**.

1. Dans le volet droit, sélectionnez **Ensemble d'outils de plateforme** , puis sélectionnez l'ensemble d'outils de votre choix dans la liste déroulante. Par exemple, si vous avez installé l’ensemble d’outils Visual Studio 2010, sélectionnez **Visual studio 2010 (V100)** pour l’utiliser pour votre projet.

1. Sélectionnez le bouton **OK** .

## <a name="see-also"></a>Voir aussi

[MSBuild sur la ligne de commande – C++](msbuild-visual-cpp.md)
