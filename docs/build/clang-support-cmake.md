---
title: Soutien de Clang/LLVM dans les projets Visual Studio CMake
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323183"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Soutien de Clang/LLVM dans les projets Visual Studio CMake

::: moniker range="<=vs-2017"

Le support Clang est disponible dans Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Vous pouvez utiliser Visual Studio avec Clang pour modifier et déboiffer les projets CMake qui ciblent Windows ou Linux.

**Windows**: Visual Studio 2019 version 16.1 comprend la prise en charge de l’édition, la construction et le débogage avec Clang/LLVM dans les projets CMake ciblant Windows.

**Linux**: Pour les projets Linux CMake, aucun support spécial Visual Studio n’est nécessaire. Vous pouvez installer Clang à l’aide du gestionnaire de paquet de votre distro, et ajouter les commandes appropriées dans le fichier CMakeLists.txt.

## <a name="install"></a>Installer

Pour le meilleur support IDE dans Visual Studio, nous vous recommandons d’utiliser les derniers outils de compilation Clang pour Windows. Si vous n’en avez pas déjà, vous pouvez les installer en ouvrant l’installateur visual studio et en choisissant le **compilateur C’Clang pour Windows** sous le développement de bureau avec des composants optionnels **CMD.** Lors de l’utilisation d’une installation Clang personnalisée, vérifiez le composant **d’outils de construction V142.**

![Installation de composants Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Créer une nouvelle configuration

Pour ajouter une nouvelle configuration Clang à un projet CMake :

1. Cliquez à droite sur CMakeLists.txt dans **Solution Explorer** et choisissez **les paramètres CMake pour le projet**.

1. Sous **Configurations**, appuyez sur le bouton **Configuration Ajouter** :

   ![Ajouter une configuration](media/cmake-add-config-icon.png)

1. Choisissez la configuration Clang souhaitée (notez que des configurations Clang séparées sont fournies pour Windows et Linux), puis appuyez sur **Select**:

   ![Configuration CMake Clang](media/cmake-clang-configuration.png)

1. Pour apporter des modifications à cette configuration, utilisez **l’éditeur de paramètres CMake**. Pour plus d’informations, voir [Personnaliser les paramètres de construction CMake dans Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modifier une configuration existante pour utiliser Clang

Pour modifier une configuration existante pour utiliser Clang, suivez ces étapes :

1. Cliquez à droite sur CMakeLists.txt dans **Solution Explorer** et choisissez **les paramètres CMake pour le projet**.

1. Sous **General** sélectionnez le dropdown **Toolset** et choisissez l’outil Clang souhaité :

   ![Outils CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Emplacements personnalisés de Clang

Par défaut, Visual Studio recherche Clang en deux endroits :

- (Windows) La copie installée en interne de Clang/LLVM qui est livré avec l’installateur Visual Studio.
- (Windows et Linux) La variable de l’environnement PATH.

Vous pouvez spécifier un autre emplacement en définissant les variables **CMAKE_C_COMPILER** et **CMAKE_CXX_COMPILER** CMake dans **CMake Paramètres**:

![Outils CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Modes de compatibilité Clang

Pour les configurations Windows, CMake invoque par défaut Clang en mode [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) et des liens avec la mise en œuvre Microsoft de la Standard Library. Par défaut, **clang-cl.exe** `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`est situé dans .

Vous pouvez modifier ces valeurs dans **CMake Paramètres** sous **les variables CMake et le cache**. Cliquez **sur Afficher les variables avancées**. Faites défiler vers le bas pour trouver **CMAKE_CXX_COMPILER,** puis cliquez sur le bouton **Parcourir** pour spécifier un chemin compilateur différent.

## <a name="edit-build-and-debug"></a>Modifier, construire et débouger

Après avoir configuré une configuration Clang, vous pouvez construire et déboiffer le projet. Visual Studio détecte que vous utilisez le compilateur Clang et fournit IntelliSense, mise en évidence, navigation, et d’autres fonctionnalités d’édition. Les erreurs et les avertissements sont affichés dans la **fenêtre de sortie**.

Lors du débogage, vous pouvez utiliser des points d’arrêt, la visualisation de la mémoire et des données, et la plupart des autres fonctionnalités de débogage. Certaines fonctionnalités compilantes telles que Edit et Continue ne sont pas disponibles pour les configurations Clang.

![CMake Clang débogage](media/clang-debug-visualize.png)

::: moniker-end
