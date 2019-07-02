---
title: Prise en charge de clang/LLVM dans les projets Visual Studio CMake
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++
ms.openlocfilehash: 6773d9cdb076ef305ba635306f3bc9c6575d2203
ms.sourcegitcommit: b233f05adae607f75815111006a771c432df5a9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67517104"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Prise en charge de clang/LLVM dans les projets Visual Studio CMake

::: moniker range="<=vs-2017"

Prise en charge clang est disponible dans Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Vous pouvez utiliser Visual Studio avec Clang pour modifier et déboguer C++ CMake les projets qui cible Windows ou Linux.

**Windows** : Visual Studio 2019 version 16.1 inclut la prise en charge de la modification, la génération et le débogage avec Clang/LLVM dans les projets CMake ciblant Windows. 

**Linux** : Pour les projets Linux CMake, aucune prise en charge spéciale de Visual Studio n’est requis. Vous pouvez installer Clang à l’aide du Gestionnaire de package de votre distribution et ajouter les commandes appropriées dans le fichier CMakeLists.txt.

## <a name="install"></a>Installez

Pour une meilleure IDE prise en charge dans Visual Studio, nous vous recommandons d’utiliser les derniers outils de compilateur Clang pour Windows. Si vous ne disposez pas celles, vous pouvez les installer en ouvrant Visual Studio Installer en choisissant **compilateur Clang pour Windows** sous **développement bureautique avec C++**  composants facultatifs.

![Installation des composants clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Créer une nouvelle configuration

Pour ajouter une nouvelle configuration Clang à un projet CMake :

1. Avec le bouton droit sur le fichier CMakeLists.txt dans **l’Explorateur de solutions** et choisissez **CMake les paramètres de projet**.

1. Sous **Configurations**, appuyez sur la **ajouter une Configuration** bouton :

   ![Ajouter une configuration](media/cmake-add-config-icon.png)

1. Choisissez la configuration souhaitée de Clang (Notez que les configurations Clang distinctes sont fournies pour Windows et Linux), puis appuyez sur **sélectionnez**:

   ![Configuration de CMake Clang](media/cmake-clang-configuration.png)

1. Pour apporter des modifications à cette configuration, utilisez le **éditeur de paramètres CMake**. Pour plus d’informations, consultez [CMake de personnaliser les paramètres dans Visual Studio build](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modifier une configuration existante pour utiliser Clang

Pour modifier une configuration existante pour utiliser Clang, procédez comme suit :

1. Avec le bouton droit sur le fichier CMakeLists.txt dans **l’Explorateur de solutions** et choisissez **CMake les paramètres de projet**.

1. Sous **général** sélectionner le **ensemble d’outils** liste déroulante et choisissez l’ensemble d’outils Clang souhaitée :

   ![Ensemble d’outils Clang de CMake](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Emplacements Clang personnalisés

Par défaut, Visual Studio recherche Clang dans deux emplacements :

- (Windows) La copie installée en interne de Clang/LLVM est fourni avec le programme d’installation de Visual Studio.
- (Windows et Linux) La variable d’environnement PATH.

Vous pouvez spécifier un autre emplacement en définissant le **CMAKE_C_COMPILER** et **CMAKE_CXX_COMPILER** variables CMake dans **paramètres CMake**:

![Ensemble d’outils Clang de CMake](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Modes de compatibilité clang

Pour les configurations de Windows, CMake par défaut appelle Clang dans [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) mode et des liens avec l’implémentation Microsoft de la bibliothèque Standard. Par défaut, **clang-cl.exe** se trouve dans `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

 Vous pouvez modifier ces valeurs dans **paramètres CMake** sous **CMake variables et cache**. Cliquez sur **Show advanced variables**. Faites défiler jusqu'à trouver **CMAKE_CXX_COMPILER**, puis cliquez sur le **Parcourir** bouton pour spécifier un chemin d’accès du compilateur différents.

## <a name="edit-build-and-debug"></a>Modifier, générer et déboguer

Une fois que vous avez défini une configuration Clang, vous pouvez générer et déboguer le projet. Visual Studio détecte que vous utilisez le compilateur Clang et fournit des fonctionnalités IntelliSense, mise en surbrillance, de navigation et autres fonctionnalités d’édition. Erreurs et avertissements sont affichent dans le **fenêtre sortie**.

Lors du débogage, vous pouvez utiliser des points d’arrêt, la mémoire et la visualisation des données et la plupart des autres fonctionnalités de débogage. Certaines fonctionnalités de dépend du compilateur telles que Modifier & Continuer ne sont pas disponibles pour les configurations de Clang.

![CMake Clang débogage](media/clang-debug-visualize.png)

::: moniker-end
