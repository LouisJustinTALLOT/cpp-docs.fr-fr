---
title: Créer des projets multiplateformes C++ dans Visual Studio
description: Ce tutoriel montre comment configurer, compiler et déboguer un projet CMake open source C++ dans Visual Studio qui cible Linux et Windows.
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: deb2c91d6d09d8945e5eb57a7ac742c5b1705e83
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825316"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Tutoriel : Créer des projets multiplateformes C++ dans Visual Studio 

Le développement en C et C++ dans Visual Studio ne cible plus seulement les environnements Windows. Ce tutoriel montre comment utiliser Visual Studio pour le développement multiplateforme en C++ basé sur CMake sans avoir à créer ou générer des projets Visual Studio. Quand vous ouvrez un dossier qui contient un fichier CMakeLists.txt, Visual Studio configure automatiquement IntelliSense et les paramètres de build. Vous pouvez alors rapidement modifier, compiler et déboguer votre code localement sur Windows, puis changer de configuration pour faire la même chose sur Linux, tout cela directement depuis Visual Studio.

Dans ce didacticiel, vous apprendrez à :

> [!div class="checklist"]
> * Cloner un projet CMake open source à partir de GitHub
> * Ouvrir le projet dans Visual Studio 
> * Générer et déboguer un exécutable cible sur Windows
> * Ajouter une connexion à une machine Linux
> * Générer et déboguer la même cible sur Linux

## <a name="prerequisites"></a>Prérequis

- Configurer Visual Studio pour le développement multiplateforme en C++
    - Tout d’abord, vous devez [avoir installé Visual Studio](https://visualstudio.microsoft.com/vs/). Ensuite, vérifiez que vous avez installé les **charges de travail de développement Desktop en C++** et de **développement Linux en C++**. Cette installation minimale occupe seulement 3 Go et prend normalement dix minutes au maximum, selon la vitesse de téléchargement.
- Configurer une machine Linux pour le développement multiplateforme en C++
    - Visual Studio ne nécessite pas de distribution particulière de Linux. Le système d’exploitation peut s’exécuter sur une machine physique ou virtuelle, dans le cloud ou sur le sous-système Windows pour Linux (WSL). Toutefois, dans la mesure où ce tutoriel s’utilise dans un environnement graphique, le sous-système Windows pour Linux n’est pas recommandé, car il est conçu principalement pour des opérations de ligne de commande.
    - Sur la machine Linux, Visual Studio a besoin de ces outils : compilateurs C++, GDB, ssh et zip. Sur les systèmes Debian, vous pouvez installer ces dépendances de la manière suivante.
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb zip
    ```
    - Visual Studio nécessite l’installation d’une version récente de CMake avec le mode serveur activé (version 3.8 minimum) sur la machine Linux. Microsoft fournit une build universelle de CMake que vous pouvez installer sur n’importe quelle distribution Linux. Nous vous recommandons d’utiliser cette build pour avoir les fonctionnalités les plus récentes. Vous pouvez obtenir les fichiers binaires de CMake à partir de la [duplication (fork) Microsoft dans le dépôt CMake](https://github.com/Microsoft/CMake/releases) sur GitHub. Accédez à cette page et téléchargez la version correspondant à l’architecture système sur votre machine Linux, puis définissez-la en tant qu’exécutable :
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - Vous pouvez voir les options d’exécution du script en spécifiant `-–help`. Nous vous recommandons d’utiliser l’option `–prefix` pour spécifier le chemin d’installation **/usr/local**, qui est l’emplacement par défaut où Visual Studio recherche CMake. L’exemple suivant montre le script Linux-x86_64. Changez ce code si vous utilisez une plateforme cible différente. 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- Git pour Windows installé sur votre machine Windows.
- Un compte GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Cloner un projet CMake open source à partir de GitHub

Ce tutoriel utilise le SDK Bullet Physics sur GitHub, qui fournit des simulations d’interactions physiques et de détection de collisions pour plusieurs applications différentes. Il inclut des exemples de programmes exécutables que vous pouvez compiler et exécuter sans avoir à écrire du code supplémentaire. Ce tutoriel ne modifie pas le code source ni les scripts de build. Pour commencer, clonez le dépôt bullet3 de GitHub sur la machine où vous avez installé Visual Studio. 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. Dans le menu principal de Visual Studio, choisissez **Fichier > Ouvrir > CMake** et accédez au fichier CMakeLists.txt situé à la racine du dépôt bullet3 que vous venez de télécharger.

    ![Menu Fichier > Ouvrir > CMake dans Visual Studio](media/cmake-open-cmake.png)

    Dès que vous ouvrez le dossier, la structure de ce dossier s’affiche dans l’**Explorateur de solutions**.

    ![Vue des dossiers dans l’Explorateur de solutions Visual Studio](media/cmake-bullet3-solution-explorer.png)

    Cette vue montre le contenu réel du disque ; ce n’est pas une vue logique ou filtrée. Par défaut, elle n’affiche pas les fichiers masqués. 

2. Appuyez sur le bouton **Afficher tous les fichiers** pour voir la totalité des fichiers du dossier.

    ![Bouton Afficher tous les fichiers dans l’Explorateur de solutions Visual Studio](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Basculer vers une vue des cibles

Quand vous ouvrez un dossier qui utilise CMake, Visual Studio génère automatiquement le cache CMake. Cette opération peut prendre plus ou moins de temps selon la taille de votre projet. 

1. Dans la **fenêtre Sortie**, sélectionnez **Afficher la sortie à partir de**, puis choisissez **CMake** pour superviser l’état du processus de génération du cache. À la fin de l’opération, le message « Extraction des informations cibles terminée » s’affiche.

    ![Fenêtre Sortie de Studio Visual montrant la sortie à partir de CMake](media/cmake-bullet3-output-window.png)

    Une fois cette opération terminée, IntelliSense est configuré, le projet peut être généré et vous pouvez déboguer l’application. Visual Studio peut maintenant afficher une vue logique de la solution basée sur les cibles spécifiées dans les fichiers CMakeLists. 

2. Utilisez le bouton **Solutions et dossiers** dans l’**Explorateur de solutions** pour passer à la vue des cibles de CMake.

    ![Bouton Solutions et dossiers dans l’Explorateur de solutions pour afficher la vue des cibles de CMake](media/cmake-bullet3-show-targets.png)

    Voici comment se présente cette vue pour le SDK Bullet :

    ![Vue des cibles de CMake dans l’Explorateur de solutions](media/cmake-bullet3-targets-view.png)

    La vue des cibles offre une vue plus intuitive du contenu de cette base de code source. Vous pouvez voir que certaines cibles sont des bibliothèques alors que d’autres sont des exécutables. 

3. Développez un nœud dans la vue des cibles de CMake pour voir les fichiers de code source associés, quel que soit leur emplacement sur le disque.

## <a name="set-a-breakpoint-build-and-run"></a>Définir un point d’arrêt, compiler et exécuter

Dans cette étape, nous allons déboguer un exemple de programme qui utilise la bibliothèque Bullet Physics.
  
1. Dans l’**Explorateur de solutions**, sélectionnez AppBasicExampleGui et développez-le. 
1. Ouvrez le fichier `BasicExample.cpp`. 
1. Définissez un point d’arrêt à déclencher quand vous cliquez dans l’application exécutée. L’événement de clic est géré dans une méthode au sein d’une classe d’assistance. Pour y accéder rapidement :

    1. Sélectionnez `CommonRigidBodyBase` duquel le struct `BasicExample` est dérivé à la ligne 30 environ.
    1. Cliquez avec le bouton droit et choisissez **Atteindre la définition**. Vous êtes maintenant dans l’en-tête CommonRigidBodyBase.h. 
    1. Dans la vue du navigateur au-dessus de votre source, vous devez voir que vous êtes dans `CommonRigidBodyBase`. À droite, vous pouvez sélectionner les membres à examiner. Cliquez sur la liste déroulante et sélectionnez `mouseButtonCallback` pour accéder à la définition de cette fonction dans l’en-tête.

        ![Barre d’outils de la liste des membres Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Ajoutez un point d’arrêt sur la première ligne dans cette fonction. Ce point d’arrêt est déclenché quand vous cliquez sur un bouton de la souris dans la fenêtre de l’application lancée sous le débogueur Visual Studio.

1. Pour lancer l’application, sélectionnez la liste déroulante de lancement avec l’icône de lecture qui indique « Sélectionner un élément de démarrage » dans la barre d’outils. Dans la liste déroulante, sélectionnez AppBasicExampleGui.exe. Le nom de l’exécutable figure maintenant sur le bouton de lancement :

    ![Liste déroulante de lancement avec « Sélectionner un élément de démarrage » dans la barre d’outils Visual Studio](media/cmake-bullet3-launch-button.png)

5.  Appuyez sur le bouton de lancement pour générer l’application et ses dépendances associées, puis lancez-la avec le débogueur Visual Studio attaché. Après quelques instants, l’application exécutée apparaît :

    ![Débogage d’une application Windows dans Visual Studio](media/cmake-bullet3-launched.png)

6. Déplacez votre souris dans la fenêtre d’application, puis cliquez sur un bouton pour déclencher le point d’arrêt. Cela ramène Visual Studio au premier plan, avec l’éditeur montrant la ligne où l’exécution a été interrompue. Vous pouvez alors inspecter les variables, les objets, les threads et la mémoire de l’application. Vous pouvez exécuter votre code pas à pas de manière interactive. Vous pouvez cliquer sur **Continuer** pour reprendre l’exécution de l’application et la quitter normalement, ou arrêter son exécution dans Visual Studio à l’aide du bouton Arrêter.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Ajouter une configuration x64-Debug explicite pour Windows

Jusqu’ici, vous avez utilisé la configuration par défaut **x64-Debug** pour Windows. Les configurations indiquent à Visual Studio quelle plateforme cible utiliser pour CMake. La configuration par défaut n’est pas représentée sur le disque. Quand vous ajoutez explicitement une configuration, Visual Studio crée un fichier appelé CMakeSettings.json qui est rempli avec les paramètres de toutes les configurations spécifiées. 

1. Ajoutez une nouvelle configuration en cliquant sur la liste déroulante Configuration dans la barre d’outils et en sélectionnant **Gérer les configurations…**

    ![Liste déroulante Gérer les configurations](media/cmake-bullet3-manage-configurations.png)

    La boîte de dialogue **Ajouter la configuration à CMakeSettings** s’affiche.

    ![Boîte de dialogue Ajouter la configuration à CMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

    Cette boîte de dialogue affiche toutes les configurations prédéfinies dans Visual Studio ainsi que l’ensemble des configurations personnalisées que vous avez éventuellement créées. Si vous souhaitez continuer à utiliser la configuration par défaut **x64-Debug**, celle-ci doit être la première ajoutée. En ajoutant cette configuration, vous serez en mesure de basculer entre les configurations Windows et Linux. Sélectionnez **x64-Debug** et cliquez sur **Sélectionner**. Cette opération crée le fichier CMakeSettings.json avec une configuration **x64-Debug** et bascule Visual Studio sur cette configuration au lieu de la configuration par défaut. Vous voyez que le nom de la configuration dans la liste déroulante ne comporte plus la mention « (par défaut) ». Vous pouvez utiliser un nom de votre choix pour vos configurations en changeant le paramètre de nom directement dans CMakeSettings.json.

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Ajouter une configuration Linux et se connecter à la machine distante

1. Ajoutez maintenant une configuration Linux. Cliquez avec le bouton droit sur le fichier CMakeSettings.json dans la vue de l’**Explorateur de solutions**, puis sélectionnez **Ajouter une configuration**. Comme précédemment, la boîte de dialogue Ajouter la configuration à CMakeSettings s’affiche. Sélectionnez **Linux-Debug** cette fois, puis enregistrez le fichier CMakeSettings.json. 
2. Sélectionnez à présent **Linux-Debug** dans la liste déroulante des configurations.

    ![Liste déroulante des configurations de lancement, avec les options X64-Debug et Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

    Si vous vous connectez à un système Linux pour la première fois, la boîte de dialogue **Se connecter au système distant** s’affiche.

    ![Boîte de dialogue Se connecter au système distant dans Visual Studio](media/cmake-bullet3-connection-manager.png)

    Si vous avez déjà ajouté une connexion à distance, vous pouvez ouvrir cette fenêtre en accédant à **Outils > Options > Multiplateforme > Gestionnaire des connexions**.
 
3. Entrez les informations de connexion à votre machine Linux et cliquez sur **Connexion**. Visual Studio ajoute cette machine dans CMakeSettings.json en tant que machine par défaut pour la configuration **Linux-Debug**. Il extrait également les en-têtes de la machine distante afin de vous fournir des données IntelliSense propres à cette machine. Après cela, Visual Studio envoie vos fichiers à la machine distante, puis y crée le cache CMake. Quand ces étapes sont terminées, Visual Studio est configuré pour utiliser la même base de code source avec cette machine Linux distante. Ces étapes peuvent prendre plus ou moins de temps selon la vitesse de votre réseau et la puissance de votre machine distante. La fin de ces étapes vous est indiquée par l’affichage du message « Extraction des informations cibles terminée » dans la fenêtre Sortie de CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Définir un point d’arrêt, compiler et exécuter sur Linux

Comme il s’agit d’une application de bureau, vous devez fournir des informations de configuration supplémentaires pour la configuration debug. 

1. Dans la vue des cibles de CMake, cliquez avec le bouton droit sur AppBasicExampleGui et choisissez **Paramètres de débogage et de lancement** pour ouvrir le fichier launch.vs.json qui se trouve dans le sous-dossier masqué **.vs**. Ce fichier est propre à votre environnement de développement local. Vous pouvez le déplacer à la racine de votre projet si vous souhaitez le vérifier et le partager avec votre équipe. Dans ce fichier, une configuration a été ajoutée pour AppBasicExampleGui. Ces paramètres par défaut conviennent dans la plupart des cas, mais comme il s’agit ici d’une application de bureau, vous devez fournir des informations supplémentaires pour lancer le programme et l’afficher sur la machine Linux. 
2. Vous avez besoin de la valeur de la variable d’environnement `DISPLAY` sur votre machine Linux. Pour l’obtenir, exécutez cette commande.

    ```cmd
    echo $DISPLAY
    ```

    Dans la configuration pour AppBasicExampleGui, il y a un tableau de paramètres « pipeArgs » où figure une ligne « ${debuggerCommand} ». C’est la commande qui lance gdb sur la machine distante. Visual Studio doit exporter la vue dans ce contexte avant que cette commande s’exécute. Par exemple, si la valeur de votre vue est :1, modifiez cette ligne de la façon suivante :

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. Maintenant, pour lancer et déboguer l’application, choisissez la liste déroulante **Sélectionner un élément de démarrage** dans la barre d’outils et choisissez AppBasicExampleGui. Appuyez maintenant sur ce bouton ou sur **F5**. Cette action génère l’application et ses dépendances associées sur la machine Linux distante, puis la lance avec le débogueur Visual Studio attaché. Sur votre machine Linux distante, vous devez voir apparaître une fenêtre d’application.

4. Déplacez votre souris dans la fenêtre d’application et cliquez sur un bouton pour déclencher le point d’arrêt. L’exécution du programme s’interrompt, Visual Studio revient au premier plan, et vous êtes au point d’arrêt défini. Vous devez également voir une fenêtre de console Linux s’ouvrir dans Visual Studio. Cette fenêtre affiche une sortie de la machine Linux distante, et elle peut aussi accepter une entrée pour `stdin`. Comme n’importe quelle fenêtre Visual Studio, elle peut être ancrée à l’emplacement d’affichage de votre choix et conserve sa position dans les sessions ultérieures.

    ![Fenêtre de console Linux dans Visual Studio](media/cmake-bullet3-linux-console.png)

5. Vous pouvez alors inspecter les variables, les objets, les threads et la mémoire de l’application, et exécuter votre code pas à pas de manière interactive à l’aide de Visual Studio. Mais cette fois, vous faites tout cela sur une machine Linux distante au lieu de votre environnement Windows local. Vous pouvez cliquer sur **Continuer** pour reprendre l’exécution de l’application et la quitter normalement, ou appuyer sur le bouton Arrêter pour arrêter son exécution, comme sur une machine locale.

6. Si vous examinez la fenêtre Pile des appels, vous voyez les appels à `x11OpenGLWindow` puisque Visual Studio a lancé l’application sur Linux.

    ![Fenêtre Pile des appels montrant la pile des appels Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Ce que vous avez appris 

Dans ce tutoriel, vous avez cloné une base de code directement à partir de GitHub, puis vous l’avez compilée, exécutée et déboguée sur Windows sans apporter de modifications. Vous avez ensuite compilé, exécuté et débogué cette même base de code sur une machine Linux distante après avoir légèrement modifié la configuration. 

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
