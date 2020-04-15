---
title: Créer des projets multiplateformes C++ dans Visual Studio
description: Comment configurer, compiler et déboçonner un projet CMake open-source CMD dans Visual Studio qui cible Linux et Windows.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328741"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Tutorial : Créez des projets multiplateformes CMD dans Visual Studio

Le développement en C et C++ dans Visual Studio ne cible plus seulement les environnements Windows. Ce tutoriel montre comment utiliser Visual Studio pour le développement de plateformes croisées C SUR Windows et Linux. Il est basé sur CMake, de sorte que vous n’avez pas à créer ou générer des projets Visual Studio. Lorsque vous ouvrez un dossier contenant un fichier CMakeLists.txt, Visual Studio configure l’IntelliSense et crée automatiquement les paramètres. Vous pouvez rapidement commencer à éditer, construire et débogage votre code localement sur Windows. Ensuite, changez votre configuration pour faire la même chose sur Linux, le tout à partir de Visual Studio.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Cloner un projet CMake open source à partir de GitHub
> * Ouvrir le projet dans Visual Studio
> * Générer et déboguer un exécutable cible sur Windows
> * Ajouter une connexion à une machine Linux
> * Générer et déboguer la même cible sur Linux

## <a name="prerequisites"></a>Prérequis

* Configurer Visual Studio pour le développement multiplateforme en C++
  * Tout d’abord, [installez Visual Studio](https://visualstudio.microsoft.com/vs/) et choisissez le **développement de bureau avec le** développement de C et Linux avec des charges de travail **C .** Cette installation minimale n’est que de 3 Go. Selon votre vitesse de téléchargement, l’installation ne devrait pas prendre plus de 10 minutes.

* Configurer une machine Linux pour le développement multiplateforme en C++
  * Visual Studio ne nécessite pas de distribution particulière de Linux. L’OS peut fonctionner sur une machine physique, dans un VM ou dans le nuage. Vous pouvez également utiliser le sous-système Windows pour Linux (WSL). Cependant, pour ce tutoriel un environnement graphique est nécessaire. WSL n’est pas recommandé ici, car il est destiné principalement à des opérations de ligne de commandement.
  * Visual Studio a besoin de ces outils sur la machine Linux: compilateurs C , gdb, ssh, rsync, ninja, et zip. Sur les systèmes de Debian, vous pouvez utiliser cette commande pour installer ces dépendances :

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio nécessite une version récente de CMake sur la machine Linux qui a le mode serveur activé (au moins 3,8). Microsoft fournit une build universelle de CMake que vous pouvez installer sur n’importe quelle distribution Linux. Nous vous recommandons d’utiliser cette build pour vous assurer que vous avez les dernières fonctionnalités. Vous pouvez obtenir les fichiers binaires de CMake à partir de la [duplication (fork) Microsoft dans le dépôt CMake](https://github.com/Microsoft/CMake/releases) sur GitHub. Allez à cette page et téléchargez la version qui correspond à l’architecture du système sur votre machine Linux, puis marquez-la comme un exécutable:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Vous pouvez voir les options d’exécution du script en spécifiant `-–help`. Nous vous recommandons `–prefix` d’utiliser l’option de spécifier l’installation dans le chemin **/usr,** parce que **/usr/bin** est l’emplacement par défaut où Visual Studio cherche CMake. L’exemple suivant montre le script Linux-x86_64. Changez-le au besoin si vous utilisez une plate-forme cible différente.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Git pour Windows installé sur votre machine Windows.
* Un compte GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Cloner un projet CMake open source à partir de GitHub

Ce tutoriel utilise le Bullet Physics SDK sur GitHub. Il fournit des simulations de détection des collisions et de physique pour de nombreuses applications. Le SDK comprend des exemples de programmes exécutables qui compilent et s’exécutent sans avoir à écrire du code supplémentaire. Ce tutoriel ne modifie aucun code source ou ne crée pas de scripts. Pour commencer, clonez le référentiel *bullet3* de GitHub sur la machine où vous avez Visual Studio installé.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. Sur le menu principal visual Studio, choisissez **File > Open > CMake**. Naviguez vers le fichier CMakeLists.txt dans la racine de la solution de balle3 que vous venez de télécharger.

    ![Menu Fichier > Ouvrir > CMake dans Visual Studio](media/cmake-open-cmake.png)

    Dès que vous ouvrez le dossier, votre structure de dossier devient visible dans la **Solution Explorer**.

    ![Vue des dossiers dans l’Explorateur de solutions Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Cette vue montre le contenu réel du disque ; ce n’est pas une vue logique ou filtrée. Par défaut, elle n’affiche pas les fichiers masqués.

1. Choisissez le bouton **Afficher tous les fichiers** pour voir tous les fichiers dans le dossier.

    ![Bouton Afficher tous les fichiers dans l’Explorateur de solutions Visual Studio](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Basculer vers une vue des cibles

Quand vous ouvrez un dossier qui utilise CMake, Visual Studio génère automatiquement le cache CMake. Cette opération peut prendre plus ou moins de temps selon la taille de votre projet.

1. Dans la **fenêtre Sortie**, sélectionnez **Afficher la sortie à partir de**, puis choisissez **CMake** pour superviser l’état du processus de génération du cache. À la fin de l’opération, le message « Extraction des informations cibles terminée » s’affiche.

   ![Fenêtre Sortie de Studio Visual montrant la sortie à partir de CMake](media/cmake-bullet3-output-window.png)

   Une fois cette opération terminée, IntelliSense est configuré. Vous pouvez construire le projet, et déboiffer l’application. Visual Studio affiche désormais une vue logique de la solution, basée sur les cibles spécifiées dans les fichiers CMakeLists.

1. Utilisez le bouton **Solutions et dossiers** dans l’**Explorateur de solutions** pour passer à la vue des cibles de CMake.

   ![Bouton Solutions et dossiers dans l’Explorateur de solutions pour afficher la vue des cibles de CMake](media/cmake-bullet3-show-targets.png)

   Voici comment se présente cette vue pour le SDK Bullet :

   ![Vue des cibles de CMake dans l’Explorateur de solutions](media/cmake-bullet3-targets-view.png)

   La vue des cibles offre une vue plus intuitive du contenu de cette base de code source. Vous pouvez voir que certaines cibles sont des bibliothèques alors que d’autres sont des exécutables.

1. Développez un nœud dans la vue des cibles de CMake pour voir les fichiers de code source associés, quel que soit leur emplacement sur le disque.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Ajouter une configuration x64-Debug explicite pour Windows

Visual Studio crée une configuration **x64-Debug** par défaut pour Windows. Les configurations indiquent à Visual Studio quelle plateforme cible utiliser pour CMake. La configuration par défaut n’est pas représentée sur le disque. Lorsque vous ajoutez explicitement une configuration, Visual Studio crée un fichier appelé *CMakeSettings.json*. Il est peuplé de paramètres pour toutes les configurations que vous spécifiez.

1. Ajoutez une nouvelle configuration. Ouvrez la **configuration** drop-down dans la barre d’outils et sélectionnez **Gérer les configurations**.

   ![Liste déroulante Gérer les configurations](media/cmake-bullet3-manage-configurations.png)

   [L’éditeur CMake Paramètres](customize-cmake-settings.md) ouvre ses portes. Sélectionnez le panneau vert plus sur le côté gauche de l’éditeur pour ajouter une nouvelle configuration. Le **dialogue Add Configuration to CMakeSettings** apparaît.

   ![Boîte de dialogue Ajouter la configuration à CMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

   Ce dialogue affiche toutes les configurations incluses avec Visual Studio, ainsi que toutes les configurations personnalisées que vous créez. Si vous voulez continuer à utiliser une configuration **x64-Debug,** qui devrait être la première que vous ajoutez. Sélectionnez **x64-Debug,** puis choisissez le bouton **Sélectionnez.** Visual Studio crée le fichier CMakeSettings.json avec une configuration pour **x64-Debug**, et l’enregistre au disque. Vous pouvez utiliser un nom de votre choix pour vos configurations en changeant le paramètre de nom directement dans CMakeSettings.json.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Définissez un point d’arrêt, construisez et exécutez sur Windows

Dans cette étape, nous allons déboguer un exemple de programme qui utilise la bibliothèque Bullet Physics.
  
1. Dans l’**Explorateur de solutions**, sélectionnez AppBasicExampleGui et développez-le.

1. Ouvrez le fichier `BasicExample.cpp`.

1. Définissez un point d’arrêt qui est touché lorsque vous cliquez sur l’application en cours d’exécution. L’événement de clic est géré dans une méthode au sein d’une classe d’assistance. Pour y accéder rapidement :

   1. Sélectionnez `CommonRigidBodyBase` que `BasicExample` la struct est dérivée. C’est autour de la ligne 30.

   1. Cliquez avec le bouton droit et choisissez **Atteindre la définition**. Maintenant, vous êtes dans l’en-tête CommonRigidBodyBase.h.

   1. Dans la vue du navigateur au-dessus de votre `CommonRigidBodyBase`source, vous devez voir que vous êtes dans le . À droite, vous pouvez sélectionner les membres à examiner. Ouvrez le drop-down et sélectionnez `mouseButtonCallback` pour aller à la définition de cette fonction dans l’en-tête.

      ![Barre d’outils de la liste des membres Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Ajoutez un point d’arrêt sur la première ligne dans cette fonction. Il est frappé lorsque vous cliquez sur un bouton de souris dans la fenêtre de l’application, lorsqu’il est exécuté sous le debugger Visual Studio.

1. Pour lancer l’application, sélectionnez le dépôt de lancement dans la barre d’outils. C’est celui avec l’icône de jeu vert qui dit "Select Startup Item". Dans le drop-down, sélectionnez AppBasicExampleGui.exe. Le nom de l’exécutable figure maintenant sur le bouton de lancement :

   ![Liste déroulante de lancement avec « Sélectionner un élément de démarrage » dans la barre d’outils Visual Studio](media/cmake-bullet3-launch-button.png)

1. Choisissez le bouton de lancement pour construire l’application et les dépendances nécessaires, puis lancez-le avec le débbuggeur Visual Studio attaché. Après quelques instants, l’application exécutée apparaît :

   ![Débogage d’une application Windows dans Visual Studio](media/cmake-bullet3-launched.png)

1. Déplacez votre souris dans la fenêtre d’application, puis cliquez sur un bouton pour déclencher le point d’arrêt. Le point d’arrêt ramène Visual Studio au premier plan, et l’éditeur montre la ligne où l’exécution est en pause. Vous pouvez inspecter les variables d’application, les objets, les threads et la mémoire, ou passer à travers votre code de manière interactive. Choisissez **Continuer** à laisser l’application reprendre, puis la sortir normalement. Ou, arrêtez l’exécution dans Visual Studio en utilisant le bouton d’arrêt.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Ajouter une configuration Linux et se connecter à la machine distante

1. Ajoutez une configuration Linux. Cliquez avec le bouton droit sur le fichier CMakeSettings.json dans la vue de l’**Explorateur de solutions**, puis sélectionnez **Ajouter une configuration**. Comme précédemment, la boîte de dialogue Ajouter la configuration à CMakeSettings s’affiche. Sélectionnez **Linux-Debug** cette fois, puis enregistrez le fichier CMakeSettings.json (ctrl et s).

1. Sélectionnez **Linux-Debug** dans la configuration drop-down.

   ![Liste déroulante des configurations de lancement, avec les options X64-Debug et Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

   Si c’est la première fois que vous vous connectez à un système Linux, le dialogue **Connect to Remote System** apparaît.

   ![Boîte de dialogue Se connecter au système distant dans Visual Studio](media/cmake-bullet3-connection-manager.png)

   Si vous avez déjà ajouté une connexion à distance, vous pouvez ouvrir cette fenêtre en naviguant vers **Tools > Options > Cross Platform > Connection Manager**.

1. Fournissez les [informations de connexion à votre machine Linux](/cpp/linux/connect-to-your-remote-linux-computer) et choisissez **Connect**. Visual Studio ajoute cette machine quant à CMakeSettings.json comme votre connexion par défaut pour **Linux-Debug**. Il tire également vers le bas les en-têtes de votre machine à distance, de sorte que vous obtenez [IntelliSense spécifique à cette connexion à distance](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Ensuite, Visual Studio envoie vos fichiers à la machine à distance et génère le cache CMake sur le système distant. Ces étapes peuvent prendre un certain temps, en fonction de la vitesse de votre réseau et de la puissance de votre machine à distance. Vous saurez qu’il est complet lorsque le message "Target info extraction fait" apparaît dans la fenêtre de sortie CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Définissez un point d’arrêt, construisez et exécutez sur Linux

Étant donné qu’il s’agit d’une application de bureau, vous devez fournir des informations de configuration supplémentaires à la configuration de débogé.

1. Dans la vue CMake Targets, cliquez à droite AppBasicExampleGui et choisissez **Debug et Paramètres de lancement** pour ouvrir le fichier launch.vs.json qui est dans le sous-pliage caché **.vs.** Ce fichier est propre à votre environnement de développement local. Vous pouvez le déplacer à la racine de votre projet si vous souhaitez le vérifier et le partager avec votre équipe. Dans ce fichier, une configuration a été ajoutée pour AppBasicExampleGui. Ces paramètres par défaut fonctionnent dans la plupart des cas, mais pas ici. Parce qu’il s’agit d’une application de bureau, vous devez fournir des informations supplémentaires pour lancer le programme afin que vous puissiez le voir sur votre machine Linux.

1. Pour trouver la valeur `DISPLAY` de la variable de l’environnement sur votre machine Linux, exécutez cette commande :

   ```cmd
   echo $DISPLAY
   ```

   Dans la configuration d’AppBasicExampleGui, il existe un tableau de paramètres, "pipeArgs". Il contient une ligne: "$debuggerCommand". C’est la commande qui lance gdb sur la machine à distance. Visual Studio doit exporter l’affichage dans ce contexte avant que cette commande ne s’exécute. Par exemple, si la valeur `:1`de votre écran est, modifiez cette ligne comme suit :

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Lancez et débassez votre application. Ouvrez le **Select Startup Item** drop-down dans la barre d’outils et choisissez **AppBasicExampleGui**. Ensuite, soit choisissez l’icône de jeu vert dans la barre d’outils, ou appuyez sur **F5**. L’application et ses dépendances sont construites sur la machine Linux à distance, puis lancé avec le debugger Visual Studio attaché. Sur votre machine Linux distante, vous devez voir apparaître une fenêtre d’application.

1. Déplacez votre souris dans la fenêtre d’application et cliquez sur un bouton. Le point d’arrêt est touché. Pauses d’exécution du programme, Visual Studio revient au premier plan, et vous voyez votre point d’arrêt. Vous devez également voir une fenêtre de console Linux s’ouvrir dans Visual Studio. La fenêtre fournit la sortie de la machine Linux `stdin`à distance, et il peut également accepter l’entrée pour . Comme n’importe quelle fenêtre Visual Studio, vous pouvez l’amarrer là où vous préférez la voir. Sa position persiste dans les sessions à venir.

   ![Fenêtre de console Linux dans Visual Studio](media/cmake-bullet3-linux-console.png)

1. Vous pouvez alors inspecter les variables, les objets, les threads et la mémoire de l’application, et exécuter votre code pas à pas de manière interactive à l’aide de Visual Studio. Mais cette fois, vous faites tout cela sur une machine Linux à distance au lieu de votre environnement Windows local. Vous pouvez choisir **Continuer** à laisser l’application reprendre et sortir normalement, ou vous pouvez choisir le bouton d’arrêt, tout comme avec l’exécution locale.

1. Si vous examinez la fenêtre Pile des appels, vous voyez les appels à `x11OpenGLWindow` puisque Visual Studio a lancé l’application sur Linux.

   ![Fenêtre Pile des appels montrant la pile des appels Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Ce que vous avez appris

Dans ce tutoriel, vous avez cloné une base de code directement à partir de GitHub. Vous l’avez construit, couru et déboqué sur Windows sans modifications. Ensuite, vous avez utilisé la même base de code, avec des modifications mineures de configuration, pour construire, exécuter et déboguer sur une machine Linux à distance.

## <a name="next-steps"></a>Étapes suivantes

Consultez les rubriques suivantes pour en savoir plus sur la configuration et le débogage des projets CMake dans Visual Studio :

> [!div class="nextstepaction"]
> [Projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Configurer un projet CMake Linux](../linux/cmake-linux-project.md)<br/><br/>
> [Se connecter à votre ordinateur Linux distant](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Personnaliser les paramètres de génération CMake](customize-cmake-settings.md)<br/><br/>
> [Configurer des sessions de débogage CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Déployer, exécuter et déboguer un projet Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [Informations de référence sur la configuration prédéfinie de CMake](cmake-predefined-configuration-reference.md)
>
