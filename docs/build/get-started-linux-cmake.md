---
title: Créer des projets multiplateformes C++ dans Visual Studio
description: Comment installer, compiler et déboguer un projet C++ cmake Open source dans Visual Studio qui cible à la fois Linux et Windows.
author: mikeblome
ms.topic: tutorial
ms.date: 11/08/2019
ms.openlocfilehash: 269c9e88133a492f66df7c7f81ab35424aff125d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303254"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Didacticiel : créer C++ des projets multiplateformes dans Visual Studio

Le développement en C et C++ dans Visual Studio ne cible plus seulement les environnements Windows. Ce didacticiel montre comment utiliser Visual Studio pour C++ le développement multiplateforme sur Windows et Linux. Il est basé sur CMake, vous n’avez donc pas à créer ni générer de projets Visual Studio. Lorsque vous ouvrez un dossier qui contient un fichier fichier CMakeLists. txt, Visual Studio configure automatiquement les paramètres IntelliSense et de Build. Vous pouvez rapidement commencer à modifier, générer et déboguer votre code localement sur Windows. Ensuite, basculez votre configuration pour faire de même sur Linux, tout cela à partir de Visual Studio.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
> * Cloner un projet CMake open source à partir de GitHub
> * Ouvrir le projet dans Visual Studio
> * Générer et déboguer un exécutable cible sur Windows
> * Ajouter une connexion à une machine Linux
> * Générer et déboguer la même cible sur Linux

## <a name="prerequisites"></a>Configuration requise

* Configurer Visual Studio pour le développement multiplateforme en C++
  * Tout d’abord, [installez Visual Studio](https://visualstudio.microsoft.com/vs/) et choisissez le développement  **C++ bureautique avec** et le **développement Linux avec charges C++ de travail**. Cette installation minimale est uniquement de 3 Go. Selon la vitesse de téléchargement, l’installation ne doit pas durer plus de 10 minutes.

* Configurer une machine Linux pour le développement multiplateforme en C++
  * Visual Studio ne nécessite pas de distribution particulière de Linux. Le système d’exploitation peut s’exécuter sur un ordinateur physique, sur une machine virtuelle ou dans le Cloud. Vous pouvez également utiliser le sous-système Windows pour Linux (WSL). Toutefois, pour ce didacticiel, un environnement graphique est requis. WSL n’est pas recommandé ici, car il est destiné principalement aux opérations de ligne de commande.
  * Visual Studio requiert ces outils sur l’ordinateur Linux : C++ comcompilers, gdb, SSH, rsync et zip. Sur les systèmes Debian, vous pouvez utiliser cette commande pour installer les dépendances suivantes :

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync zip
    ```

  * Visual Studio requiert une version récente de CMake sur l’ordinateur Linux sur lequel le mode serveur est activé (au moins 3,8). Microsoft fournit une build universelle de CMake que vous pouvez installer sur n’importe quelle distribution Linux. Nous vous recommandons d’utiliser cette build pour vous assurer que vous disposez des dernières fonctionnalités. Vous pouvez obtenir les fichiers binaires de CMake à partir de la [duplication (fork) Microsoft dans le dépôt CMake](https://github.com/Microsoft/CMake/releases) sur GitHub. Accédez à cette page et téléchargez la version qui correspond à l’architecture système sur votre machine Linux, puis marquez-la comme un fichier exécutable :

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Vous pouvez voir les options d’exécution du script en spécifiant `-–help`. Nous vous recommandons d’utiliser l’option `–prefix` pour spécifier l’installation dans le chemin **/usr/local** , car il s’agit de l’emplacement par défaut où Visual Studio recherche cmake. L’exemple suivant montre le script Linux-x86_64. Modifiez-le si nécessaire si vous utilisez une plateforme cible différente.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```

* Git pour Windows installé sur votre machine Windows.
* Un compte GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Cloner un projet CMake open source à partir de GitHub

Ce didacticiel utilise le kit de développement logiciel (SDK) physique des puces sur GitHub. Il assure la détection des collisions et les simulations physiques pour de nombreuses applications. Le SDK comprend des exemples de programmes exécutables qui se compilent et s’exécutent sans qu’il soit nécessaire d’écrire du code supplémentaire. Ce didacticiel ne modifie pas le code source et les scripts de génération. Pour démarrer, clonez le référentiel *bullet3* à partir de GitHub sur l’ordinateur sur lequel Visual Studio est installé.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. Dans le menu principal de Visual Studio, choisissez **fichier > ouvrir > cmake**. Accédez au fichier fichier CMakeLists. txt à la racine du référentiel bullet3 que vous venez de télécharger.

    ![Menu Fichier > Ouvrir > CMake dans Visual Studio](media/cmake-open-cmake.png)

    Dès que vous ouvrez le dossier, votre structure de dossiers devient visible dans le **Explorateur de solutions**.

    ![Vue des dossiers dans l’Explorateur de solutions Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Cette vue montre le contenu réel du disque ; ce n’est pas une vue logique ou filtrée. Par défaut, elle n’affiche pas les fichiers masqués.

1. Choisissez le bouton **Afficher tous les fichiers** pour afficher tous les fichiers dans le dossier.

    ![Bouton Afficher tous les fichiers dans l’Explorateur de solutions Visual Studio](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Basculer vers une vue des cibles

Quand vous ouvrez un dossier qui utilise CMake, Visual Studio génère automatiquement le cache CMake. Cette opération peut prendre plus ou moins de temps selon la taille de votre projet.

1. Dans la **fenêtre Sortie**, sélectionnez **Afficher la sortie à partir de**, puis choisissez **CMake** pour superviser l’état du processus de génération du cache. À la fin de l’opération, le message « Extraction des informations cibles terminée » s’affiche.

   ![Fenêtre Sortie de Studio Visual montrant la sortie à partir de CMake](media/cmake-bullet3-output-window.png)

   Une fois cette opération terminée, IntelliSense est configuré. Vous pouvez générer le projet et déboguer l’application. Visual Studio affiche désormais une vue logique de la solution, en fonction des cibles spécifiées dans les fichiers fichier CMakeLists.

1. Utilisez le bouton **Solutions et dossiers** dans l’**Explorateur de solutions** pour passer à la vue des cibles de CMake.

   ![Bouton Solutions et dossiers dans l’Explorateur de solutions pour afficher la vue des cibles de CMake](media/cmake-bullet3-show-targets.png)

   Voici comment se présente cette vue pour le SDK Bullet :

   ![Vue des cibles de CMake dans l’Explorateur de solutions](media/cmake-bullet3-targets-view.png)

   La vue des cibles offre une vue plus intuitive du contenu de cette base de code source. Vous pouvez voir que certaines cibles sont des bibliothèques alors que d’autres sont des exécutables.

1. Développez un nœud dans la vue des cibles de CMake pour voir les fichiers de code source associés, quel que soit leur emplacement sur le disque.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Ajouter une configuration x64-Debug explicite pour Windows

Visual Studio crée une configuration par défaut de **débogage x64** pour Windows. Les configurations indiquent à Visual Studio quelle plateforme cible utiliser pour CMake. La configuration par défaut n’est pas représentée sur le disque. Quand vous ajoutez explicitement une configuration, Visual Studio crée un fichier appelé *CMakeSettings. JSON*. Elle est remplie avec des paramètres pour toutes les configurations que vous spécifiez.

1. Ajoutez une nouvelle configuration. Ouvrez la liste déroulante **configuration** dans la barre d’outils, puis sélectionnez **gérer les configurations**.

   ![Liste déroulante Gérer les configurations](media/cmake-bullet3-manage-configurations.png)

   L' [éditeur de paramètres cmake](customize-cmake-settings.md) s’ouvre. Sélectionnez le signe plus vert sur le côté gauche de l’éditeur pour ajouter une nouvelle configuration. La boîte **de dialogue Ajouter une configuration à CMakeSettings** s’affiche.

   ![Boîte de dialogue Ajouter la configuration à CMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

   Cette boîte de dialogue affiche toutes les configurations incluses dans Visual Studio, ainsi que toutes les configurations personnalisées que vous créez. Si vous souhaitez continuer à utiliser une configuration de **débogage x64** , celle-ci doit être la première que vous ajoutez. Sélectionnez **x64-Debug**, puis cliquez sur le bouton **Sélectionner** . Visual Studio crée le fichier CMakeSettings. JSON avec une configuration pour **x64-Debug**et l’enregistre sur le disque. Vous pouvez utiliser un nom de votre choix pour vos configurations en changeant le paramètre de nom directement dans CMakeSettings.json.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Définir un point d’arrêt, générer et exécuter sur Windows

Dans cette étape, nous allons déboguer un exemple de programme qui utilise la bibliothèque Bullet Physics.
  
1. Dans l’**Explorateur de solutions**, sélectionnez AppBasicExampleGui et développez-le.

1. Ouvrez le fichier `BasicExample.cpp`.

1. Définissez un point d’arrêt qui atteint le moment où vous cliquez dans l’application en cours d’exécution. L’événement de clic est géré dans une méthode au sein d’une classe d’assistance. Pour y accéder rapidement :

   1. Sélectionnez `CommonRigidBodyBase` duquel la `BasicExample` de struct est dérivée. Il se trouve autour de la ligne 30.

   1. Cliquez avec le bouton droit et choisissez **Atteindre la définition**. Vous êtes maintenant dans l’en-tête CommonRigidBodyBase. h.

   1. Dans la vue du navigateur au-dessus de votre source, vous devez voir que vous êtes dans la `CommonRigidBodyBase`. À droite, vous pouvez sélectionner les membres à examiner. Ouvrez la liste déroulante et sélectionnez `mouseButtonCallback` pour accéder à la définition de cette fonction dans l’en-tête.

      ![Barre d’outils de la liste des membres Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Ajoutez un point d’arrêt sur la première ligne dans cette fonction. Elle est atteinte lorsque vous cliquez sur un bouton de la souris dans la fenêtre de l’application, quand elle est exécutée sous le débogueur Visual Studio.

1. Pour lancer l’application, sélectionnez la liste déroulante lancer dans la barre d’outils. C’est celle avec l’icône de lecture verte qui indique « sélectionner un élément de démarrage ». Dans la liste déroulante, sélectionnez AppBasicExampleGui. exe. Le nom de l’exécutable figure maintenant sur le bouton de lancement :

   ![Liste déroulante de lancement avec « Sélectionner un élément de démarrage » dans la barre d’outils Visual Studio](media/cmake-bullet3-launch-button.png)

1. Choisissez le bouton lancer pour générer l’application et les dépendances nécessaires, puis lancez-la avec le débogueur Visual Studio attaché. Après quelques instants, l’application exécutée apparaît :

   ![Débogage d’une application Windows dans Visual Studio](media/cmake-bullet3-launched.png)

1. Déplacez votre souris dans la fenêtre d’application, puis cliquez sur un bouton pour déclencher le point d’arrêt. Le point d’arrêt rétablit Visual Studio au premier plan et l’éditeur affiche la ligne où l’exécution est suspendue. Vous pouvez inspecter les variables d’application, les objets, les threads et la mémoire, ou parcourir votre code de manière interactive. Choisissez **Continuer** pour laisser l’application reprendre, puis fermez-la normalement. Sinon, arrêtez l’exécution dans Visual Studio à l’aide du bouton arrêter.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Ajouter une configuration Linux et se connecter à la machine distante

1. Ajoutez une configuration Linux. Cliquez avec le bouton droit sur le fichier CMakeSettings.json dans la vue de l’**Explorateur de solutions**, puis sélectionnez **Ajouter une configuration**. Comme précédemment, la boîte de dialogue Ajouter la configuration à CMakeSettings s’affiche. Sélectionnez **Linux-déboguer** cette fois-ci, puis enregistrez le fichier CMakeSettings. JSON (Ctrl + s).

1. Sélectionnez **Linux-Debug** dans la liste déroulante Configuration.

   ![Liste déroulante des configurations de lancement, avec les options X64-Debug et Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

   Si c’est la première fois que vous vous connectez à un système Linux, la boîte de dialogue **se connecter au système distant** s’affiche.

   ![Boîte de dialogue Se connecter au système distant dans Visual Studio](media/cmake-bullet3-connection-manager.png)

   Si vous avez déjà ajouté une connexion à distance, vous pouvez ouvrir cette fenêtre en accédant à **outils > Options > gestionnaire de connexions inter-plateforme >** .

1. Fournissez les [informations de connexion à votre machine Linux](/cpp/linux/connect-to-your-remote-linux-computer) , puis choisissez **se connecter**. Visual Studio ajoute cet ordinateur à CMakeSettings. JSON comme connexion par défaut pour **Linux-Debug**. Il extrait également les en-têtes de votre ordinateur distant, ce [qui vous permet d’utiliser IntelliSense spécifique à cette connexion à distance](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Ensuite, Visual Studio envoie vos fichiers à la machine distante et génère le cache CMake sur le système distant. Ces étapes peuvent prendre un certain temps, en fonction de la vitesse de votre réseau et de la puissance de votre machine distante. Vous savez qu’il est terminé lorsque le message « extraction des informations cibles effectuées » s’affiche dans la fenêtre sortie de CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Définir un point d’arrêt, générer et exécuter sur Linux

Étant donné qu’il s’agit d’une application de bureau, vous devez fournir des informations de configuration supplémentaires à la configuration de débogage.

1. Dans l’affichage CMake targets, cliquez avec le bouton droit sur AppBasicExampleGui et choisissez **paramètres de débogage et de lancement** pour ouvrir le fichier Launch. vs. JSON qui se trouve dans le sous-dossier Hidden **. vs** . Ce fichier est propre à votre environnement de développement local. Vous pouvez le déplacer à la racine de votre projet si vous souhaitez le vérifier et le partager avec votre équipe. Dans ce fichier, une configuration a été ajoutée pour AppBasicExampleGui. Ces paramètres par défaut fonctionnent dans la plupart des cas, mais pas ici. Étant donné qu’il s’agit d’une application de bureau, vous devez fournir des informations supplémentaires pour lancer le programme et le voir sur votre machine Linux.

1. Pour rechercher la valeur de la variable d’environnement `DISPLAY` sur votre machine Linux, exécutez la commande suivante :

   ```cmd
   echo $DISPLAY
   ```

   Dans la configuration de AppBasicExampleGui, il existe un tableau de paramètres, « pipeArgs ». Elle contient une ligne : « $ {debuggerCommand} ». Il s’agit de la commande qui lance gdb sur la machine distante. Visual Studio doit exporter l’affichage dans ce contexte avant l’exécution de cette commande. Par exemple, si la valeur de votre affichage est `:1`, modifiez cette ligne comme suit :

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Lancez et déboguez votre application. Ouvrez la liste déroulante **Sélectionner l’élément de démarrage** dans la barre d’outils, puis choisissez **AppBasicExampleGui**. Ensuite, choisissez l’icône de lecture verte dans la barre d’outils ou appuyez sur **F5**. L’application et ses dépendances sont générées sur l’ordinateur Linux distant, puis lancées avec le débogueur Visual Studio attaché. Sur votre machine Linux distante, vous devez voir apparaître une fenêtre d’application.

1. Déplacez votre souris dans la fenêtre de l’application, puis cliquez sur un bouton. Le point d’arrêt est atteint. L’exécution du programme s’interrompt, Visual Studio revient au premier plan et vous voyez votre point d’arrêt. Vous devez également voir une fenêtre de console Linux s’ouvrir dans Visual Studio. La fenêtre fournit la sortie de la machine Linux distante et peut également accepter une entrée pour `stdin`. Comme n’importe quelle fenêtre Visual Studio, vous pouvez l’ancrer là où vous préférez la voir. Sa position est conservée dans les sessions ultérieures.

   ![Fenêtre de console Linux dans Visual Studio](media/cmake-bullet3-linux-console.png)

1. Vous pouvez alors inspecter les variables, les objets, les threads et la mémoire de l’application, et exécuter votre code pas à pas de manière interactive à l’aide de Visual Studio. Mais cette fois, vous effectuez toutes les opérations sur une machine Linux distante au lieu de votre environnement Windows local. Vous pouvez choisir **Continuer** pour laisser l’application reprendre et se fermer normalement, ou vous pouvez choisir le bouton arrêter, comme avec l’exécution locale.

1. Si vous examinez la fenêtre Pile des appels, vous voyez les appels à `x11OpenGLWindow` puisque Visual Studio a lancé l’application sur Linux.

   ![Fenêtre Pile des appels montrant la pile des appels Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Ce que vous avez appris

Dans ce didacticiel, vous avez cloné une base de code directement à partir de GitHub. Vous l’avez générée, exécutée et déboguée sur Windows sans modification. Ensuite, vous avez utilisé la même base de code, avec des modifications mineures de la configuration, pour générer, exécuter et déboguer sur une machine Linux distante.

## <a name="next-steps"></a>Étapes suivantes :

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
