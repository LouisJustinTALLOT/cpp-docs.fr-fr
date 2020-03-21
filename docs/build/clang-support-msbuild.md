---
title: Prise en charge de Clang/LLVM dans les projets Visual Studio Visual Studio
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 5bd90141cdc7646dce206e6b02a605b73d78de95
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078802"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Prise en charge de Clang/LLVM dans les projets Visual Studio

::: moniker range="<=vs-2017"

La prise en charge de Clang pour les projets CMake et MSBuild est disponible dans Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Vous pouvez utiliser Visual Studio 2019 version 16,2 avec Clang pour modifier, générer et déboguer C++ des projets Visual Studio (MSBuild) qui ciblent Windows ou Linux.

## <a name="install"></a>Installer

Pour une meilleure prise en charge de l’IDE dans Visual Studio, nous vous recommandons d’utiliser les outils du compilateur Clang les plus récents pour Windows. Si vous ne les avez pas déjà, vous pouvez les installer en ouvrant la Visual Studio installer et en choisissant  **C++ outils Clang pour Windows** sous **développement C++ bureautique avec des** composants facultatifs. Si vous préférez utiliser une installation Clang existante sur votre ordinateur, choisissez les  **C++ outils de génération Clang-CL pour V142.** composant facultatif. La bibliothèque C++ standard Microsoft requiert au moins Clang 8.0.0 ; la version groupée de Clang sera automatiquement mise à jour pour rester informé des mises à jour de l’implémentation Microsoft de la bibliothèque standard.

![Installation du composant Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Configurer un projet Windows pour utiliser les outils Clang

Pour configurer un projet Visual Studio afin d’utiliser Clang, cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et choisissez **Propriétés**. En règle générale, vous devez d’abord choisir **toutes les configurations** en haut de la boîte de dialogue. Ensuite, sous **général** > **ensemble d’outils de plateforme**, choisissez **LLVM (Clang-CL)** , puis **OK**.

![Installation du composant Clang](media/clang-msbuild-prop-page.png)

Si vous utilisez les outils Clang fournis avec Visual Studio, aucune étape supplémentaire n’est requise. Pour les projets Windows, Visual Studio appelle par défaut Clang en mode [Clang-CL](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) et établit des liens avec l’implémentation Microsoft de la bibliothèque standard. Par défaut, **Clang-CL. exe** se trouve dans `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Si vous utilisez une installation Clang personnalisée, vous pouvez modifier les **Propriétés** du **projet** >  > **répertoires VC + +**  > les **Propriétés de configuration** > les **répertoires exécutables** en ajoutant la racine d’installation Clang personnalisée comme premier répertoire, ou modifier la valeur de la propriété `LLVMInstallDir`. Pour plus d’informations, consultez [définir un emplacement LLVM personnalisé](#custom_llvm_location) .

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Configurer un projet Linux pour utiliser les outils Clang

Pour les projets Linux, Visual Studio utilise le serveur frontal compatible Clang GCC. Les propriétés du projet et presque tous les indicateurs du compilateur sont identiques

Pour configurer un projet Visual Studio Linux pour utiliser Clang :

1. Cliquez avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** , puis choisissez **Propriétés**.
1. En règle générale, vous devez d’abord choisir **toutes les configurations** en haut de la boîte de dialogue.
1. Sous **général** > **ensemble d’outils de plateforme**, choisissez **WSL_Clang_1_0** si vous utilisez le sous-système Windows pour Linux, ou **Remote_Clang_1_0** si vous utilisez un ordinateur distant ou une machine virtuelle.
1. Appuyez sur **OK**.

![Installation du composant Clang](media/clang-msbuild-prop-page.png)

Sur Linux, Visual Studio utilise par défaut le premier emplacement Clang qu’il rencontre dans la propriété d’environnement PATH. Si vous utilisez une installation Clang personnalisée, vous devez modifier la valeur de la propriété `LLVMInstallDir` ou substituer un chemin d’accès sous **Propriétés** du **projet** >  > **répertoires VC + +**  > **Propriétés de configuration** > **répertoires exécutables**. Pour plus d’informations, consultez [définir un emplacement LLVM personnalisé](#custom_llvm_location) .

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>Définir un emplacement LLVM personnalisé

Vous pouvez définir un chemin personnalisé pour LLVM pour un ou plusieurs projets en créant un fichier *Directory. Build. props* et en ajoutant ce fichier au dossier racine de n’importe quel projet. Vous pouvez l’ajouter au dossier de solution racine pour l’appliquer à tous les projets de la solution. Le fichier doit ressembler à ce qui suit (mais remplacez-le par le chemin d’accès réel) :

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Définir des propriétés supplémentaires, modifier, générer et déboguer

Une fois que vous avez configuré une configuration Clang, cliquez à nouveau avec le bouton droit sur le nœud du projet et choisissez **recharger le projet**. Vous pouvez maintenant générer et déboguer le projet à l’aide des outils Clang. Visual Studio détecte que vous utilisez le compilateur Clang et fournit IntelliSense, la mise en surbrillance, la navigation et d’autres fonctionnalités d’édition. Les erreurs et les avertissements s’affichent dans la **fenêtre Sortie**. Les pages de propriétés de projet pour une configuration Clang sont très similaires à celles de MSVC, bien que certaines fonctionnalités dépendantes du compilateur, telles que modifier & continuer, ne soient pas disponibles pour les configurations Clang. Pour définir une option du compilateur Clang ou de l’éditeur de liens qui n’est pas disponible dans les pages de propriétés, vous pouvez l’ajouter manuellement dans les pages de propriétés sous **Propriétés de configuration** > **CC++ /(ou éditeur de liens)**  > ligne de **commande** > **options supplémentaires**.

Lors du débogage, vous pouvez utiliser des points d’arrêt, la visualisation de la mémoire et des données, ainsi que la plupart des autres fonctionnalités de débogage.  

![Débogage Clang](media/clang-debug-msbuild.png)

::: moniker-end
