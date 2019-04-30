---
title: Déployer une application Visual C++ à l'aide d'un projet d'installation
ms.date: 09/17/2018
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: e2d83d45f1369e250b24708edd17f4004e030a17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387810"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Procédure pas à pas : Déploiement d’une application Visual C++ à l’aide d’un projet d’installation

Décrit comment utiliser un projet d’installation pour déployer une application Visual C++.

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Un ordinateur sur lequel Visual Studio est installé.

- Un ordinateur supplémentaire sans les bibliothèques Visual C++.

### <a name="to-deploy-an-application-by-using-a-setup-project"></a>Pour déployer une application à l’aide d’un projet d’installation

1. Créer un nouveau projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Utilisez **l’Assistant Application MFC** pour créer une solution Visual Studio. Pour rechercher l’Assistant, dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C++**, sélectionnez **MFC**, sélectionnez **Application MFC**, entrez un nom pour le projet, puis cliquez sur **OK**. Cliquez sur **Terminer**.

   > [!NOTE]
   > Si le type **Application MFC** est manquant :<br/>
   > **Visual Studio 2017** : Sélectionnez **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Installez l’option située sous **Développement Desktop en C++** dans la section des components **Facultatifs**, nommée **MFC Visual C++ pour x86 et x64**.<br/>
   > **Visual Studio 2015** : Cliquez sur le bouton Démarrer de Windows, puis tapez **Ajout/Suppression de programmes**. Ouvrez le programme à partir de la liste des résultats, puis recherchez votre installation de Microsoft Visual Studio 2015 dans la liste des programmes installés. Double-cliquez dessus, puis choisissez **Modifier** et sélectionnez le composant **Microsoft Foundation Classes** sous **Visual C++**.

1. Remplacez la configuration de la solution active par **Release**. Dans le menu **Générer**, sélectionnez **Gestionnaire de configurations**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la zone de liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur **Fermer**.

1. Appuyez sur **Ctrl**+**Maj**+**G** pour générer l’application. Sinon, dans le menu **Générer**, cliquez sur **Générer la solution**. La génération de l’application permet au projet d’installation d’utiliser la sortie de ce projet d’application MFC.

1. Si vous ne l’avez pas déjà fait, téléchargez l’extension des projets Microsoft Visual Studio Installer. L’extension est gratuite pour les développeurs Visual Studio et ajoute les fonctionnalités des modèles de projet d’installation et de déploiement à Visual Studio. Quand vous êtes connecté à Internet, dans Visual Studio, choisissez **Outils** > **Extensions et mises à jour**. Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez sur **Entrée**, sélectionnez **Projets d’installation Microsoft Visual Studio \<version>**, puis cliquez sur **Télécharger**. Choisissez d’exécuter et d’installer l’extension, puis redémarrez Visual Studio.

1. Dans la barre de menus, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez de rouvrir votre projet.

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**. Ensuite, dans le volet gauche de la boîte de dialogue, développez les nœuds **Installé** > **Autres types de projets**, puis sélectionnez **Visual Studio Installer**. Dans le volet central, sélectionnez **Projet d’installation**.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (NomProjet)** s’ouvre dans la fenêtre de l’éditeur.

1. Cliquez avec le bouton droit sur le nœud **Dossier d’application**, puis sélectionnez **Ajouter** > **Sortie de projet** pour ouvrir la boîte de dialogue **Ajouter le groupe de sorties du projet**. Dans la boîte de dialogue, sélectionnez **Sortie principale**, puis cliquez sur **OK**. Un nouvel élément nommé **Sortie principale de NomProjet (active)** s’affiche.

1. Cliquez avec le bouton droit sur le nœud **Dossier d’application**, puis sélectionnez **Ajouter** > **Assembly** pour ouvrir la boîte de dialogue **Sélectionner un composant**. Sélectionnez et ajoutez toutes les DLL exigées par le programme, comme indiqué par l’article [Détermination des DLL à redistribuer](determining-which-dlls-to-redistribute.md).

1. Sélectionnez l’élément **Sortie principale de NomProjet (active)**, cliquez avec le bouton droit, puis choisissez **Créer un raccourci vers la sortie principale de NomProjet (active)**. Un nouvel élément nommé **Raccourci vers la sortie principale de NomProjet (active)** s’affiche. Vous pouvez renommer l’élément Raccourci, puis faites glisser et déplacez l’élément dans le nœud **Menu Programmes de l’utilisateur** sur le côté gauche de la fenêtre.

1. Dans la barre de menus, choisissez **Build** > **Gestionnaire de configurations**. Dans la table**Projet**, sous la colonne **Générer**, cochez la case correspondant au projet de déploiement. Cliquez sur **Fermer**.

1. Dans la barre de menus, choisissez **Générer** > **Générer la solution** pour générer le projet MFC et le projet de déploiement.

1. Dans le dossier de solution, recherchez le programme setup.exe qui a été généré à partir du projet de déploiement. Vous pouvez copier ce fichier (et le fichier .msi) pour installer l’application et ses fichiers de bibliothèques nécessaires sur un autre ordinateur. Exécutez le programme d’installation sur un deuxième ordinateur qui ne dispose pas des bibliothèques Visual C++.

## <a name="see-also"></a>Voir aussi

[Exemples de déploiement](deployment-examples.md)<br/>
