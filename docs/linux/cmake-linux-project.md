---
title: Créer un projet Linux CMake dans Visual Studio
description: Comment créer un projet CMake Linux dans Visual Studio
ms.date: 08/06/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 5753dbb37c11686becb3e141261284b68468a3bc
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507956"
---
# <a name="create-a-cmake-linux-project-in-visual-studio"></a>Créer un projet Linux CMake dans Visual Studio

::: moniker range="vs-2015"
La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur. Pour consulter la documentation de ces versions, définissez la liste déroulante **version** située au-dessus de la table des matières dans **Visual Studio 2017** ou **Visual Studio 2019**.
::: moniker-end

::: moniker range=">=vs-2017"

Nous vous recommandons d’utiliser CMake pour les projets qui sont multiplateformes ou qui seront rendus Open source. Vous pouvez utiliser des projets CMake pour générer et déboguer le même code source sur Windows, le sous-système Windows pour Linux (WSL) et les systèmes distants.

## <a name="before-you-begin"></a>Avant de commencer

Tout d’abord, assurez-vous que la charge de travail Linux de Visual Studio est installée, y compris le composant CMake. Il s’agit du **développement Linux avec** la charge de travail C++ dans le programme d’installation de Visual Studio. Consultez [installer la charge de travail Linux C++ dans Visual Studio](download-install-and-setup-the-linux-development-workload.md) si vous n’êtes pas sûr que ce est installé.

En outre, assurez-vous que les éléments suivants sont installés sur l’ordinateur distant :

- gcc
- gdb
- rsync
- zip
- Ninja-Build (Visual Studio 2019 ou version ultérieure)
::: moniker-end

::: moniker range="vs-2017"
La prise en charge de CMake dans Visual Studio nécessite la prise en charge du mode serveur introduite dans CMake 3,8. Pour une variante CMake fournie par Microsoft, téléchargez les derniers binaires prégénérés à l’adresse [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) .

Les fichiers binaires sont installés dans `~/.vs/cmake` . Une fois les fichiers binaires déployés, votre projet régénère automatiquement. Si le CMake spécifié par le `cmakeExecutable` champ dans *CMakeSettings.json* n’est pas valide (il n’existe pas ou qu’il s’agit d’une version non prise en charge) et que les fichiers binaires prédéfinis sont présents, Visual Studio ignore `cmakeExecutable` et utilise les binaires prédéfinis.

Visual Studio 2017 ne peut pas créer un projet CMake à partir de zéro, mais vous pouvez ouvrir un dossier qui contient un projet CMake existant, comme décrit dans la section suivante.
::: moniker-end

::: moniker range=">=vs-2019"
Vous pouvez utiliser Visual Studio 2019 pour générer et déboguer sur un système Linux distant ou WSL, et CMake sera appelé sur ce système. Cmake version 3,14 ou ultérieure doit être installé sur l’ordinateur cible.

Assurez-vous que l’ordinateur cible dispose d’une version récente de CMake. Souvent, la version offerte par le gestionnaire de package par défaut d’une distribution n’est pas assez récente pour prendre en charge toutes les fonctionnalités requises par Visual Studio. Visual Studio 2019 détecte si une version récente de CMake est installée sur le système Linux. Si aucune valeur n’est trouvée, Visual Studio affiche une barre d’informations en haut du volet de l’éditeur. Il propose d’installer CMake pour vous à partir de [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) .

Avec Visual Studio 2019, vous pouvez créer un projet CMake à partir de zéro, ou ouvrir un projet CMake existant. Pour créer un projet CMake, suivez les instructions ci-dessous. Ou passez directement à l' [ouverture d’un dossier de projet cmake](#open-a-cmake-project-folder) si vous disposez déjà d’un projet cmake.

## <a name="create-a-new-linux-cmake-project"></a>Créer un projet CMake Linux

Pour créer un nouveau projet Linux CMake dans Visual Studio 2019 :

1. Sélectionnez **Fichier > Nouveau projet** dans Visual Studio, ou appuyez sur **Ctrl+Maj+N**.
1. Définissez le **Langage** sur **C++** et recherchez « CMake ». Ensuite, choisissez **Suivant**. Entrez un **Nom** et un **Emplacement**, puis choisissez **Créer**.

Vous pouvez également ouvrir votre propre projet CMake dans Visual Studio 2019. La section suivante explique comment procéder.

Visual Studio crée un fichier *CMakeLists.txt* minimal avec uniquement le nom de l’exécutable et la version minimale de cmake requise. Vous pouvez modifier manuellement ce fichier à votre convenance ; Visual Studio ne remplacera jamais vos changements.

Pour vous aider à mieux comprendre, modifier et créer vos scripts CMake dans Visual Studio 2019, reportez-vous aux ressources suivantes :

- [Documentation in-Editor pour CMake dans Visual Studio](https://devblogs.microsoft.com/cppblog/in-editor-documentation-for-cmake-in-visual-studio/)
- [Navigation dans le code pour les scripts CMake](https://devblogs.microsoft.com/cppblog/code-navigation-for-cmake-scripts/)
- [Ajouter, supprimer et renommer facilement des fichiers et des cibles dans des projets CMake](https://devblogs.microsoft.com/cppblog/easily-add-remove-and-rename-files-and-targets-in-cmake-projects/)
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="open-a-cmake-project-folder"></a>Ouvrir un dossier de projet CMake

Lorsque vous ouvrez un dossier qui contient un projet CMake existant, Visual Studio utilise des variables dans le cache CMake pour configurer automatiquement IntelliSense et les builds. Les paramètres de configuration locale et de débogage sont stockés dans des fichiers JSON. Vous pouvez éventuellement partager ces fichiers avec d’autres personnes qui utilisent Visual Studio.

Visual Studio ne modifie pas les fichiers de *CMakeLists.txt* . Cela permet à d’autres personnes travaillant sur le même projet de continuer à utiliser leurs outils existants. Visual Studio régénère le cache lorsque vous enregistrez les modifications apportées à *CMakeLists.txt*ou, dans certains cas, à *CMakeSettings.jssur*. Si vous utilisez une configuration de **cache existante** , Visual Studio ne modifie pas le cache.

Pour obtenir des informations générales sur la prise en charge de CMake dans Visual Studio, consultez [Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md). Lisez ce qui suit avant de continuer.

Pour commencer, choisissez **fichier**  >  **ouvrir**  >  le**dossier** dans le menu principal ou tapez `devenv.exe <foldername>` dans une fenêtre d’invite de [commandes développeur](../build/building-on-the-command-line.md) . Le dossier que vous ouvrez doit contenir un fichier *CMakeLists.txt* , ainsi que votre code source.

L’exemple suivant montre un fichier *CMakeLists.txt* simple et un fichier. cpp :

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*CMakeLists.txt*:

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="next-steps"></a>Étapes suivantes

[Configurer un projet CMake Linux](cmake-linux-configure.md)

## <a name="see-also"></a>Voir aussi

[Projets CMake dans Visual Studio](../build/cmake-projects-in-visual-studio.md)<br/>
::: moniker-end
