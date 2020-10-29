---
title: Configurer un projet C++ MSBuild Linux dans Visual Studio
ms.date: 10/16/2020
description: Configurez un projet Linux basé sur MSBuild dans Visual Studio afin de pouvoir le générer.
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 451f34c257c210463ce11b11f27bc218d41b45c8
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921813"
---
# <a name="configure-a-linux-msbuild-c-project-in-visual-studio"></a>Configurer un projet C++ MSBuild Linux dans Visual Studio

::: moniker range="msvc-140"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

Cette rubrique explique comment configurer un projet Linux basé sur MSBuild comme décrit dans [créer un projet C++ MSBuild Linux dans Visual Studio](create-a-new-linux-project.md). Pour les projets CMake Linux, consultez [configurer un projet cmake Linux](cmake-linux-project.md).

Vous pouvez configurer un projet Linux pour cibler une machine Linux physique, une machine virtuelle ou le [sous-système Windows pour Linux](/windows/wsl/about) (WSL).

::: moniker range="msvc-160"

**Visual Studio 2019 version 16,1** :

- Quand vous ciblez WSL, vous pouvez éviter les opérations de copie nécessaires pour générer et obtenir IntelliSense qui sont nécessaires lorsque vous ciblez un système Linux distant.

- Vous pouvez spécifier des cibles Linux distinctes pour la génération et le débogage.

::: moniker-end

## <a name="general-settings"></a>Paramètres généraux :

Pour afficher les options de configuration, sélectionnez le menu **Propriétés du projet >** , ou cliquez avec le bouton droit sur le projet dans **Explorateur de solutions** et sélectionnez **Propriétés** dans le menu contextuel. Les paramètres généraux s’affichent dans la section **Général** .

![Configuration générale](media/settings_general.png)

Par défaut, un fichier exécutable (.out) est généré. Pour générer une bibliothèque statique ou dynamique, ou utiliser un fichier makefile existant, utilisez le paramètre **Type de configuration** .

Si vous générez pour le sous-système Windows pour Linux (WSL), WSL version 1 est limitée à 64 processus de compilation parallèle. Cela est régi par le paramètre **nombre maximal de travaux de compilation parallèle** dans les **propriétés de configuration > C/C++ > général** .

Quelle que soit la version de WSL que vous utilisez, si vous envisagez d’utiliser plus de 64 processus de compilation parallèle, nous vous recommandons de créer avec Ninja, ce qui est généralement plus rapide et plus fiable. Pour créer avec Ninja, utilisez le paramètre **activer la build incrémentielle** dans les **propriétés de configuration > général** .

Pour plus d’informations sur les paramètres dans les pages de propriétés, consultez [Informations de référence sur les pages de propriétés dans un projet Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Paramètres distants

Pour modifier les paramètres relatifs à l’ordinateur Linux distant, configurez les paramètres distants qui s’affichent sous [général](prop-pages/general-linux.md).

- Pour spécifier un ordinateur Linux cible distant, utilisez l’entrée **Machine de build distante** . Cela vous permet de sélectionner l’une des connexions créées précédemment. Pour créer une entrée, consultez la section [Connexion à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

   ![Machine de build](media/remote-build-machine-vs2019.png)

   ::: moniker range="msvc-160"

   **Visual Studio 2019 version 16,7** : pour cibler le sous-système Windows pour Linux (WSL), définissez la liste déroulante **ensemble d’outils de plateforme** sur **GCC pour le sous-système Windows pour Linux** . Les autres options distantes disparaissent et le chemin de l’interpréteur de commandes WSL par défaut s’affiche à leur place :

   ![Machine de build WSL](media/wsl-remote-vs2019.png)

   Si vous avez des installations de WSL côte à côte, vous pouvez spécifier ici un autre chemin. Pour plus d’informations sur la gestion de plusieurs distributions, consultez [Gérer et configurer le sous-système Windows pour Linux](/windows/wsl/wsl-config#set-a-default-distribution).

   Vous pouvez spécifier une autre cible pour le débogage dans la page **Propriétés de configuration** > **Débogage** .

   ::: moniker-end

- L’entrée **Répertoire racine de build distant** définit l’emplacement racine de l’endroit où le projet est généré sur l’ordinateur Linux distant. Par défaut et en l’absence de modification, il s’agit de **~/projects** .

- L’entrée **Répertoire de projet de build distant** définit l’emplacement où ce projet spécifique est généré sur l’ordinateur Linux distant. Par défaut, il s’agit de **$(RemoteRootDir)/$(ProjectName)** , qui se développe jusqu’à un répertoire nommé d’après le projet actuel, sous le répertoire racine défini ci-dessus.

> [!NOTE]
> Pour changer les compilateurs C et C++ par défaut, ou l’éditeur de liens et le programme d’archivage utilisés pour générer le projet, utilisez les entrées appropriées dans les sections **C/C++ > Général** et **Éditeur de liens > Général** . Vous pouvez spécifier une version spécifique de GCC ou Clang, par exemple. Pour plus d’informations, consultez [Propriétés C/c++ (Linux c++)](prop-pages/c-cpp-linux.md) et propriétés de l' [éditeur de liens (Linux c++)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Copier les sources (uniquement pour les systèmes distants)

::: moniker range="msvc-160"

Cette section ne s’applique pas lorsque vous ciblez WSL.

::: moniker-end

Lors de la génération sur des systèmes distants, les fichiers sources sur votre PC de développement sont copiés sur l’ordinateur Linux où ils sont compilés. Par défaut, toutes les sources dans le projet Visual Studio sont copiées aux emplacements définis dans les paramètres ci-dessus. Toutefois, des sources supplémentaires peuvent également être ajoutées à la liste, ou la copie des sources peut être entièrement désactivée, ce qui est le paramètre par défaut d’un projet Makefile.

- L’option **Sources à copier** détermine quelles sources sont copiées sur l’ordinateur distant. Par défaut, **\@ (SourcesToCopyRemotely)** est défini par défaut sur tous les fichiers de code source du projet, mais n’inclut pas les fichiers de ressources/ressources, tels que les images.

- L’option **Copier les sources** peut être activée et désactivée pour activer et désactiver la copie des fichiers sources sur l’ordinateur distant.

- **Des sources supplémentaires à copier** vous permettent d’ajouter des fichiers sources supplémentaires, qui seront copiés sur le système distant. Vous pouvez spécifier une liste délimitée par des points-virgules ou utiliser la syntaxe **:=** pour spécifier un nom local et distant à utiliser :

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Événements de build

Étant donné que toute la compilation se produit sur un ordinateur distant (ou WSL), plusieurs événements de build supplémentaires ont été ajoutés à la section Événements de build dans les propriétés de projet. Il s’agit des événements suivants : **Événement prébuild distant** , **Événement de préédition des liens distant** et **Événement post-build distant** . Ils se produisent sur l’ordinateur distant avant ou après les différentes étapes du processus.

![Événements de build](media/settings_buildevents.png)

## <a name="intellisense-for-headers-on-remote-systems"></a><a name="remote_intellisense"></a> IntelliSense pour les en-têtes sur les systèmes distants

Quand vous ajoutez une nouvelle connexion dans le **Gestionnaire de connexions** , Visual Studio détecte automatiquement les répertoires include pour le compilateur sur le système distant. Visual Studio compresse ensuite ces fichiers et les copie dans un répertoire sur votre ordinateur Windows local. Après cela, chaque fois que vous utilisez cette connexion dans un projet Visual Studio ou CMake, les en-têtes dans ces répertoires sont utilisés pour fournir IntelliSense.

> [!NOTE]
> Dans Visual Studio 2019 version 16,5 et versions ultérieures, la copie d’en-tête distant a été optimisée. Les en-têtes sont maintenant copiés à la demande lors de l’ouverture d’un projet Linux ou de la configuration de CMake pour une cible Linux. La copie se produit en arrière-plan par projet, en fonction des compilateurs spécifiés du projet. Pour plus d’informations, consultez améliorations de la [précision et des performances de Linux IntelliSense](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/).

Cette fonctionnalité nécessite l’installation de zip sur l’ordinateur Linux. Pour installer zip, utilisez cette commande apt-get :

```cmd
sudo apt install zip
```

Pour gérer votre cache d’en-têtes, accédez à **Outils > Options, Multiplateforme > Gestionnaire de connexions > Gestionnaire IntelliSense des en-têtes distants** . Pour mettre à jour le cache d’en-têtes après avoir effectué des changements sur votre ordinateur Linux, sélectionnez la connexion à distance, puis sélectionnez **Mettre à jour** . Sélectionnez **Supprimer** pour supprimer les en-têtes tout en conservant la connexion. Sélectionnez **Explorer** pour ouvrir le répertoire local dans **l’Explorateur de fichiers** . Traitez ce dossier en lecture seule. Pour télécharger les en-têtes pour une connexion existante qui a été créée avant Visual Studio 2017 version 15,3, sélectionnez la connexion, puis cliquez sur **Télécharger** .

::: moniker range="msvc-150"

![Capture d’écran montrant la boîte de dialogue Options avec Cross Platform > gestionnaire de connexions > en-têtes distants gestionnaire IntelliSense sélectionné.](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="msvc-160"

![Capture d’écran montrant la boîte de dialogue Options avec Cross Platform > gestionnaire de connexions sélectionné.](media/connection-manager-vs2019.png)

Vous pouvez activer la journalisation pour faciliter la résolution des problèmes :

![Journalisation à distance](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="linux-target-locale"></a><a name="locale"></a> Paramètres régionaux cibles Linux

Les paramètres de langue de Visual Studio ne sont pas propagés aux cibles Linux, car Visual Studio ne gère pas ou ne configure pas les packages installés. Les messages affichés dans la fenêtre **sortie** , tels que les erreurs de build, s’affichent à l’aide de la langue et des paramètres régionaux de la cible Linux. Vous devez configurer vos cibles Linux pour les paramètres régionaux souhaités.

## <a name="see-also"></a>Voir aussi

[Définir des propriétés de build et de compilateur](../build/working-with-project-properties.md)<br/>
[Général C++, propriétés (Linux C++)](prop-pages/general-linux.md)<br/>
[Répertoires VC++ (Linux C++)](prop-pages/directories-linux.md)<br/>
[Copier les sources, propriétés de projet (Linux C++)](prop-pages/copy-sources-project.md)<br/>
[Événement de build, propriétés (Linux C++)](prop-pages/build-events-linux.md)
