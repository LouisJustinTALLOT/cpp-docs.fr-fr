---
title: Soutien de Clang/LLVM dans les projets Visual Studio Visual Studio
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 8d7d7fec979d3e7b8f665e56094ee1c309e3b686
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323120"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Soutien de Clang/LLVM dans les projets Visual Studio

::: moniker range="<=vs-2017"

Le support Clang pour les projets CMake et MSBuild est disponible dans Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Vous pouvez utiliser visual Studio 2019 version 16.2 avec Clang pour éditer, construire et déboiser les projets C -Studio visuel (MSBuild) qui ciblent Windows ou Linux.

## <a name="install"></a>Installer

Pour le meilleur support IDE dans Visual Studio, nous vous recommandons d’utiliser les derniers outils de compilation Clang pour Windows. Si vous n’en avez pas déjà, vous pouvez les installer en ouvrant l’installateur Visual Studio et en choisissant des **outils Clang pour Windows** sous le développement de bureau avec des composants optionnels **CMD.** Si vous préférez utiliser une installation Clang existante sur votre machine, choisissez les outils de **construction V 142 de Cmd pour v142.** composant optionnel. La bibliothèque standard Microsoft CMD nécessite actuellement au moins Clang 8.0.0; la version groupée de Clang sera automatiquement mise à jour pour rester à jour avec les mises à jour dans la mise en œuvre Microsoft de la Bibliothèque Standard.

![Installation de composants Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Configurer un projet Windows pour utiliser les outils Clang

Pour configurer un projet Visual Studio pour utiliser Clang, cliquez à droite sur le nœud de projet dans **Solution Explorer** et choisissez **Propriétés**. En règle générale, vous devez d’abord choisir **toutes les configurations** en haut du dialogue. Puis, sous **General** > **Platform Toolset**, choisissez **LLVM (clang-cl)** et puis **OK**.

![Installation de composants Clang](media/clang-msbuild-prop-page.png)

Si vous utilisez les outils Clang qui sont livrés avec Visual Studio, aucune étape supplémentaire n’est nécessaire. Pour les projets Windows, Visual Studio invoque par défaut Clang en mode [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) et des liens avec la mise en œuvre Microsoft de la Standard Library. Par défaut, **clang-cl.exe** `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`est situé dans .

Si vous utilisez une installation Clang personnalisée, vous pouvez soit modifier **Project** > **Properties** > **VCMD DIrectories** > **Configuration Properties** > **Executable Directories** en ajoutant `LLVMInstallDir` la racine d’installation personnalisée Clang comme premier répertoire là-bas, ou changer la valeur de la propriété. Voir [Définir un emplacement LLVM personnalisé](#custom_llvm_location) pour plus d’informations.

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Configurer un projet Linux pour utiliser les outils Clang

Pour les projets Linux, Visual Studio utilise le frontend compatible Clang GCC. Les propriétés du projet et presque tous les drapeaux compilateur sont identiques

Pour configurer un projet Visual Studio Linux pour utiliser Clang :

1. Cliquez à droite sur le nœud de projet dans **Solution Explorer** et choisissez **propriétés**.
1. En règle générale, vous devez d’abord choisir **toutes les configurations** en haut du dialogue.
1. Sous **General** > **Platform Toolset**, choisissez **WSL_Clang_1_0** si vous utilisez Windows Subsystem pour Linux, ou **Remote_Clang_1_0** si vous utilisez une machine à distance ou VM.
1. Appuyez sur **OK**.

![Installation de composants Clang](media/clang-msbuild-prop-page.png)

Sur Linux, Visual Studio utilise par défaut le premier emplacement Clang qu’il rencontre dans la propriété de l’environnement PATH. Si vous utilisez une installation Clang personnalisée, alors `LLVMInstallDir` vous devez changer la valeur de la propriété ou bien remplacer un chemin dans le cadre **de Project** > **Properties** > **VCMD DIrectories** > **Configuration Properties** > **Répertoires Exécutables**. Voir [Définir un emplacement LLVM personnalisé](#custom_llvm_location) pour plus d’informations.

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>Définir un emplacement LLVM personnalisé

Vous pouvez définir un chemin personnalisé pour LLVM pour un ou plusieurs projets en créant un fichier *Directory.build.props* et en ajoutant ce fichier au dossier racine de n’importe quel projet. Vous pouvez l’ajouter au dossier de solution racine pour l’appliquer à tous les projets de la solution. Le fichier devrait ressembler à ceci (mais remplacer votre chemin réel):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Définissez d’autres propriétés, modifiez, construisez et débaillez

Après avoir configuré une configuration Clang, cliquez à nouveau sur le nœud du projet et choisissez le **projet Reload**. Vous pouvez maintenant construire et déboiffer le projet à l’aide des outils Clang. Visual Studio détecte que vous utilisez le compilateur Clang et fournit IntelliSense, mise en évidence, navigation, et d’autres fonctionnalités d’édition. Les erreurs et les avertissements sont affichés dans la **fenêtre de sortie**. Les pages de propriété du projet pour une configuration Clang sont très similaires à celles de MSVC, bien que certaines fonctionnalités compilateur-dépendantes telles que Edit et Continuer ne sont pas disponibles pour les configurations Clang. Pour définir une option de compilateur ou de liaison Clang qui n’est pas disponible dans les pages de propriété, vous pouvez l’ajouter manuellement dans les pages de propriété sous **Configuration Properties** > **C/CMD (ou Linker)** > Option supplémentaire**de la ligne** > **de**commande .

Lors du débogage, vous pouvez utiliser des points d’arrêt, la visualisation de la mémoire et des données, et la plupart des autres fonctionnalités de débogage.  

![Débogage Clang](media/clang-debug-msbuild.png)

::: moniker-end
