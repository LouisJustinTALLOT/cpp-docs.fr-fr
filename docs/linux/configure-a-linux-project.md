---
title: Configurer un projet Linux C++ dans Visual Studio
ms.date: 09/18/2018
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: fd87b3d60e6625fb86ad1b494fd878b9b5ca031b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622493"
---
# <a name="configure-a-linux-project"></a>Configurer un projet Linux

Cette rubrique décrit comment configurer un projet Linux C++ dans Visual Studio. Pour plus d’informations sur les projets CMake Linux dans Visual Studio, consultez [Configurer un projet CMake Linux](cmake-linux-project.md).

## <a name="general-settings"></a>Paramètres généraux

Différentes options peuvent être configurées pour un projet Linux avec Visual Studio.  Pour afficher ces options, sélectionnez le menu **Projet > Propriétés** ou cliquez avec le bouton droit sur le projet dans l’**Explorateur de solutions** et sélectionnez **Propriétés** dans le menu contextuel. Les paramètres généraux s’affichent dans la section **Général**.

![Configuration générale](media/settings_general.png)

Par défaut, un fichier exécutable (.out) est créé avec l’outil.  Pour générer une bibliothèque statique ou dynamique, ou utiliser un fichier makefile existant, utilisez la sélection **Type de configuration**.

Pour plus d’informations sur les options dans les pages de propriétés, consultez [Informations de référence sur les pages de propriétés dans un projet Linux](prop-pages-linux.md).

## <a name="remote-settings"></a>Paramètres distants

Pour changer les paramètres relatifs à l’ordinateur Linux distant, configurez les options distantes affichées dans la section de paramètres [Général](prop-pages/general-linux.md) :

- Pour changer l’ordinateur Linux cible, utilisez l’entrée **Machine de build distante**.  Cela vous permet de sélectionner l’une des connexions créées précédemment.  Pour créer une entrée, consultez la section [Connexion à votre ordinateur Linux distant](connect-to-your-remote-linux-computer.md).

- L’entrée **Répertoire racine de build distant** définit l’emplacement racine de l’endroit où le projet est généré sur l’ordinateur Linux distant.  Par défaut et en l’absence de modification, il s’agit de **~/projects**.

- L’entrée **Répertoire de projet de build distant** définit l’emplacement où ce projet spécifique est généré sur l’ordinateur Linux distant.  Par défaut, il s’agit de **$(RemoteRootDir)/$(ProjectName)**, qui se développe jusqu’à un répertoire nommé d’après le projet actuel, sous le répertoire racine défini ci-dessus.

> [!NOTE]
> Pour changer les compilateurs C et C++ par défaut, ou l’éditeur de liens et le programme d’archivage utilisés pour générer le projet, utilisez les entrées appropriées dans les sections **C/C++ > Général** et **Éditeur de liens > Général**.  Vous pouvez les définir pour utiliser une version spécifique de GCC ou même le compilateur Clang, par exemple. Pour plus d’informations, consultez [C/C++, propriétés (Linux C++)](prop-pages/c-cpp-linux.md) et [Éditeur de liens, propriétés (Linux C++)](prop-pages/linker-linux.md).

## <a name="include-directories-and-intellisense-support"></a>Répertoires include et prise en charge d’IntelliSense

**Visual Studio 2017 version 15.6 et antérieures :**<br/>
Par défaut, Visual Studio n’inclut aucun fichier Include au niveau système de l’ordinateur Linux.  Par exemple, les éléments dans le répertoire **/usr/include** ne sont pas présents dans Visual Studio.
Pour une prise en charge [IntelliSense](/visualstudio/ide/using-intellisense) complète, vous devez copier ces fichiers au même emplacement sur votre ordinateur de développement et faire pointer Visual Studio vers celui-ci.  Une option consiste à utiliser SCP (Secure Copy) pour copier les fichiers.  Sur Windows 10, vous pouvez utiliser [Bash sur Windows](https://msdn.microsoft.com/commandline/wsl/about) pour exécuter SCP.  Pour les versions précédentes de Windows, vous pouvez employer un outil tel que [PSCP (PuTTY Secure Copy)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

Vous pouvez copier les fichiers en utilisant une commande semblable à la suivante :

`scp -r linux_username@remote_host:/usr/include .`

Remplacez évidemment les valeurs **linux_username** et **remote_host** ci-dessus par des valeurs appropriées à votre propre environnement.

Une fois que les fichiers sont copiés, utilisez l’élément **Répertoires VC++** dans les propriétés de projet pour indiquer à Visual Studio où se trouvent les fichiers Include supplémentaires récemment copiés.

![Répertoires VC++](media/settings_directories.png)

**Visual Studio 2017 15.7 et versions ultérieures :**<br/>
Voir [Gérer les en-têtes distants pour IntelliSense](#remote_intellisense).

## <a name="copy-sources"></a>Copier les sources

Lors de la génération, les fichiers sources sur votre PC de développement sont copiés sur l’ordinateur Linux où ils sont compilés.  Par défaut, toutes les sources dans le projet Visual Studio sont copiées aux emplacements définis dans les paramètres ci-dessus.  Toutefois, des sources supplémentaires peuvent également être ajoutées à la liste, ou la copie des sources peut être entièrement désactivée, ce qui est le paramètre par défaut d’un projet Makefile.

- L’option **Sources à copier** détermine quelles sources sont copiées sur l’ordinateur distant.  Par défaut, **\@ (SourcesToCopyRemotely)** est défini par défaut sur tous les fichiers de code source dans le projet, mais n’inclut pas les fichiers d’actifs/de ressources, comme les images.

- L’option **Copier les sources** peut être activée et désactivée pour activer et désactiver la copie des fichiers sources sur l’ordinateur distant.

- L’option **Sources supplémentaires à copier** vous permet d’ajouter des fichiers sources supplémentaires qui seront copiés sur le système distant.  Vous pouvez spécifier une liste délimitée par des points-virgules ou utiliser la syntaxe **:=** pour spécifier un nom local et distant à utiliser :

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Événements de build

Étant donné que toute la compilation se produit sur un ordinateur distant, plusieurs événements de build supplémentaires ont été ajoutés à la section Événements de build dans les propriétés de projet.  Il s’agit des événements suivants : **Événement prébuild distant**, **Événement de préédition des liens distant** et **Événement post-build distant**. Ils se produisent sur l’ordinateur distant avant ou après les différentes étapes du processus.

![Événements de build](media/settings_buildevents.png)

## <a name="remote_intellisense"></a> IntelliSense pour les en-têtes distants (Visual Studio 2017 15.7 et ultérieur)

Quand vous ajoutez une nouvelle connexion dans le **Gestionnaire de connexions**, Visual Studio détecte automatiquement les répertoires include pour le compilateur sur le système distant. Visual Studio compresse ensuite ces fichiers et les copie dans un répertoire sur votre ordinateur Windows local. Après cela, chaque fois que vous utilisez cette connexion dans un projet Visual Studio ou CMake, les en-têtes dans ces répertoires sont utilisés pour fournir IntelliSense.

Cette fonctionnalité nécessite l’installation de zip sur l’ordinateur Linux. Pour installer zip, utilisez cette commande apt-get :

```cmd
apt install zip
```

Pour gérer votre cache d’en-têtes, accédez à **Outils > Options, Multiplateforme > Gestionnaire de connexions > Gestionnaire IntelliSense des en-têtes distants**. Pour mettre à jour le cache d’en-têtes après avoir effectué des changements sur votre ordinateur Linux, sélectionnez la connexion à distance, puis sélectionnez **Mettre à jour**. Sélectionnez **Supprimer** pour supprimer les en-têtes tout en conservant la connexion. Sélectionnez **Explorer** pour ouvrir le répertoire local dans **l’Explorateur de fichiers**. Traitez ce dossier en lecture seule. Pour télécharger les en-têtes d’une connexion existante créée avant la version 15.3, sélectionnez la connexion, puis **Télécharger**.

![IntelliSense pour les en-têtes distants](media/remote-header-intellisense.png)

## <a name="see-also"></a>Voir aussi

[Utilisation des propriétés de projet](../ide/working-with-project-properties.md)<br/>
[Général C++, propriétés (Linux C++)](../linux/prop-pages/general-linux.md)<br/>
[Répertoires VC++ (Linux C++)](../linux/prop-pages/directories-linux.md)<br/>
[Copier les sources, propriétés de projet (Linux C++)](../linux/prop-pages/copy-sources-project.md)<br/>
[Événement de build, propriétés (Linux C++)](../linux/prop-pages/build-events-linux.md)