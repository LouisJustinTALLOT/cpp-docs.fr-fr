---
title: Prise en charge de Clang/LLVM dans les projets CMake Visual Studio
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: a23526cf5216e4cc37c3131a0d1ba94a6e923f56
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686429"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Prise en charge de Clang/LLVM dans les projets CMake Visual Studio

::: moniker range="<=vs-2017"

La prise en charge de Clang est disponible dans Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Vous pouvez utiliser Visual Studio avec Clang pour modifier et déboguer des projets C++ CMake qui ciblent Windows ou Linux.

**Windows**: Visual Studio 2019 version 16,1 prend en charge la modification, la génération et le débogage avec CLANG/LLVM dans des projets cmake ciblant Windows.

**Linux**: pour les projets cmake Linux, aucune prise en charge spéciale de Visual Studio n’est requise. Vous pouvez installer Clang à l’aide du gestionnaire de package de votre distribution et ajouter les commandes appropriées dans le fichier CMakeLists.txt.

## <a name="install"></a>Installer

Pour une meilleure prise en charge de l’IDE dans Visual Studio, nous vous recommandons d’utiliser les outils du compilateur Clang les plus récents pour Windows. Si vous ne les avez pas déjà, vous pouvez les installer en ouvrant la Visual Studio Installer et en choisissant **C++ Clang compiler pour Windows** sous **développement bureautique avec les** composants facultatifs c++. Lorsque vous utilisez une installation Clang personnalisée, vérifiez le composant **C++ Clang-CL pour V142 Build Tools** .

![Installation du composant Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Créer une nouvelle configuration

Pour ajouter une nouvelle configuration Clang à un projet CMake :

1. Cliquez avec le bouton droit sur CMakeLists.txt dans **Explorateur de solutions** et choisissez **paramètres cmake pour le projet**.

1. Sous **configurations**, cliquez sur le bouton **Ajouter une configuration** :

   ![Ajouter une configuration](media/cmake-add-config-icon.png)

1. Choisissez la configuration Clang souhaitée (Notez que des configurations Clang distinctes sont fournies pour Windows et Linux), puis appuyez sur **Sélectionner**:

   ![Configuration de CMake Clang](media/cmake-clang-configuration.png)

1. Pour apporter des modifications à cette configuration, utilisez l' **éditeur de paramètres cmake**. Pour plus d’informations, consultez [personnaliser les paramètres de génération cmake dans Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modifier une configuration existante pour utiliser Clang

Pour modifier une configuration existante afin d’utiliser Clang, procédez comme suit :

1. Cliquez avec le bouton droit sur CMakeLists.txt dans **Explorateur de solutions** et choisissez **paramètres cmake pour le projet**.

1. Sous **général** , sélectionnez la liste déroulante **ensemble d’outils** et choisissez l’ensemble d’outils Clang de votre choix :

   ![Capture d’écran de la boîte de dialogue général indiquant que l’ensemble d’outils est sélectionné et que Clang CL x 86 est mis en surbrillance.](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Emplacements Clang personnalisés

Par défaut, Visual Studio recherche Clang à deux emplacements :

- Windows Copie installée en interne de Clang/LLVM qui est fournie avec le programme d’installation de Visual Studio.
- (Windows et Linux) Variable d’environnement PATH.

Vous pouvez spécifier un autre emplacement en définissant les variables **CMAKE_C_COMPILER** et **CMAKE_CXX_COMPILER** CMAKE dans les **paramètres CMAKE**:

![Capture d’écran de la boîte de dialogue C make Settings avec le compilateur c X X en surbrillance.](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Modes de compatibilité Clang

Pour les configurations Windows, CMake appelle par défaut Clang en mode [Clang-CL](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) et établit des liens avec l’implémentation Microsoft de la bibliothèque standard. Par défaut, **clang-cl.exe** se trouve dans `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin` .

Vous pouvez modifier ces valeurs dans les **paramètres cmake** sous **variables et cache cmake**. Cliquez sur **afficher les variables avancées**. Faites défiler la liste pour rechercher **CMAKE_CXX_COMPILER**, puis cliquez sur le bouton **Parcourir**  pour spécifier un autre chemin d’accès du compilateur.

## <a name="edit-build-and-debug"></a>Modifier, générer et déboguer

Une fois que vous avez configuré une configuration Clang, vous pouvez générer et déboguer le projet. Visual Studio détecte que vous utilisez le compilateur Clang et fournit IntelliSense, la mise en surbrillance, la navigation et d’autres fonctionnalités d’édition. Les erreurs et les avertissements s’affichent dans la **fenêtre Sortie**.

Lors du débogage, vous pouvez utiliser des points d’arrêt, la visualisation de la mémoire et des données, ainsi que la plupart des autres fonctionnalités de débogage. Certaines fonctionnalités dépendantes du compilateur, telles que modifier & continuer, ne sont pas disponibles pour les configurations Clang.

![Débogage CMake Clang](media/clang-debug-visualize.png)

::: moniker-end
