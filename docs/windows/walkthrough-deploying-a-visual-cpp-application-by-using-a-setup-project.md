---
description: 'En savoir plus sur : procédure pas à pas : déploiement d’une application Visual C++ à l’aide d’un projet d’installation'
title: Déployer une application Visual C++ à l'aide d'un projet d'installation
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 3815ce7a489440d6ae7db6bc73a1c17d02d46ae3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135991"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Procédure pas à pas : déploiement d'une application Visual C++ à l'aide d'un projet d'installation

Décrit comment utiliser un projet d’installation pour déployer une application Visual C++.

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Un ordinateur sur lequel Visual Studio est installé.

- Un ordinateur supplémentaire sans les bibliothèques Visual C++.

## <a name="create-the-setup-project"></a>Créer le projet d’installation

Les instructions de création d’un projet d’installation varient en fonction de la version de Visual Studio que vous avez installée. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="=msvc-160"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Pour créer le projet dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

   ![Projet d’application MFC](media/vs2019-mfc-app-new-project.png "Nouvelle application MFC")

1. En haut de la boîte de dialogue, tapez `MFC` dans la zone de recherche, puis choisissez **application MFC** dans la liste des résultats. Si vous ne le voyez pas, vous devez lancer le programme Visual Studio Installer à partir du menu Démarrer de Windows, puis cliquer sur la vignette **charge de travail développement Desktop C++** . Sous **chaque** composant, assurez-vous que le composant MFC est activé.

1. Dans la page suivante, entrez un nom pour le projet, puis spécifiez l’emplacement du projet si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet client. Lorsque l' **Assistant Application MFC** s’affiche, acceptez toutes les valeurs par défaut.

1. Remplacez la configuration de la solution active par **Release**. Dans le menu **Générer**, sélectionnez **Gestionnaire de configurations**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la zone de liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur **Fermer**.

1. Appuyez sur **CTRL** + **MAJ** + **B** pour générer l’application. Sinon, dans le menu **Générer**, cliquez sur **Générer la solution**. La génération de l’application permet au projet d’installation d’utiliser la sortie de ce projet d’application MFC.

1. Si vous ne l’avez pas déjà fait, téléchargez l’extension des projets du programme d’installation Microsoft Visual Studio. L’extension est gratuite pour les développeurs Visual Studio et ajoute les fonctionnalités des modèles de projet d’installation et de déploiement à Visual Studio. Lorsque vous êtes connecté à Internet, dans Visual Studio, choisissez **Extensions**  >  **gérer les extensions**. Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez sur **entrée**, sélectionnez **Microsoft Visual Studio projets de programme d' \<version> installation**, puis cliquez sur **Télécharger**. Choisissez d’exécuter et d’installer l’extension, puis redémarrez Visual Studio.

   ![Projet d’installation Visual Studio](media/vs2019-extension-dialog-installer-project.png "Nommer le projet client")

1. Dans la barre de menus Visual Studio, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez de rouvrir votre projet.

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour ouvrir la boîte de dialogue **créer un nouveau projet** . Dans la zone de recherche, tapez « installation », puis sélectionnez **Projet d’installation** dans la liste des résultats.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (NomProjet)** s’ouvre dans la fenêtre de l’éditeur.

::: moniker-end

::: moniker range="=msvc-150"

### <a name="to-create-the-project-in-visual-studio-2017"></a>Pour créer le projet dans Visual Studio 2017

1. Créez un projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Utilisez l' **Assistant Application MFC** pour créer une nouvelle solution Visual Studio. Pour rechercher l’Assistant, dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C++**, sélectionnez **MFC**, sélectionnez **Application MFC**, entrez un nom pour le projet, puis cliquez sur **OK**. Cliquez sur **Terminer**.

   > [!NOTE]
   > Si le type d' **application MFC** est manquant, sélectionnez **ouvrir Visual Studio installer** dans le volet gauche de la boîte de dialogue **nouveau projet** . Installez l’option située sous **Développement Desktop en C++** dans la section des components **Facultatifs**, nommée **MFC Visual C++ pour x86 et x64**.

1. Remplacez la configuration de la solution active par **Release**. Dans le menu **Générer**, sélectionnez **Gestionnaire de configurations**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la zone de liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur **Fermer**.

1. Appuyez sur **CTRL** + **MAJ** + **B** pour générer l’application. Sinon, dans le menu **Générer**, cliquez sur **Générer la solution**. La génération de l’application permet au projet d’installation d’utiliser la sortie de ce projet d’application MFC.

1. Si vous ne l’avez pas déjà fait, téléchargez l’extension des projets du programme d’installation Microsoft Visual Studio. L’extension est gratuite pour les développeurs Visual Studio et ajoute les fonctionnalités des modèles de projet d’installation et de déploiement à Visual Studio. Lorsque vous êtes connecté à Internet, dans Visual Studio, choisissez **Outils**  >  **extensions et mises à jour**. Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez sur **entrée**, sélectionnez **Microsoft Visual Studio projets de programme d' \<version> installation**, puis cliquez sur **Télécharger**. Choisissez d’exécuter et d’installer l’extension, puis redémarrez Visual Studio.

1. Dans la barre de menus, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez de rouvrir votre projet.

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour ouvrir la boîte de dialogue **nouveau projet** . Ensuite, dans le volet gauche de la boîte de dialogue, développez le  >  nœud **autres types de projets** installés, puis sélectionnez **Visual Studio installer**. Dans le volet central, sélectionnez **Projet d’installation**.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (NomProjet)** s’ouvre dans la fenêtre de l’éditeur.

::: moniker-end

::: moniker range="=msvc-140"

### <a name="to-create-the-project-in-visual-studio-2015"></a>Pour créer le projet dans Visual Studio 2015

1. Créez un projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Utilisez l' **Assistant Application MFC** pour créer une nouvelle solution Visual Studio. Pour rechercher l’Assistant, dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C++**, sélectionnez **MFC**, sélectionnez **Application MFC**, entrez un nom pour le projet, puis cliquez sur **OK**. Cliquez sur **Terminer**.

   > [!NOTE]
   > Si le type d' **application MFC** est manquant, cliquez sur le bouton Démarrer de Windows et tapez **Ajouter supprimer des programmes**. Ouvrez le programme à partir de la liste des résultats, puis recherchez votre installation de Microsoft Visual Studio 2015 dans la liste des programmes installés. Double-cliquez dessus, puis choisissez **Modifier** et sélectionnez le composant **Microsoft Foundation Classes** sous **Visual C++**.

1. Remplacez la configuration de la solution active par **Release**. Dans le menu **générer** , sélectionnez **Configuration Manager**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la zone de liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur **Fermer**.

1. Appuyez sur **CTRL** + **MAJ** + **B** pour générer l’application. Sinon, dans le menu **Générer**, cliquez sur **Générer la solution**. La génération de l’application permet au projet d’installation d’utiliser la sortie de ce projet d’application MFC.

1. Si vous ne l’avez pas déjà fait, téléchargez l’extension des projets du programme d’installation Microsoft Visual Studio. L’extension est gratuite pour les développeurs Visual Studio et ajoute les fonctionnalités des modèles de projet d’installation et de déploiement à Visual Studio. Lorsque vous êtes connecté à Internet, dans Visual Studio, choisissez **Outils**  >  **extensions et mises à jour**. Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez sur **entrée**, sélectionnez **Microsoft Visual Studio projets de programme d' \<version> installation**, puis cliquez sur **Télécharger**. Choisissez d’exécuter et d’installer l’extension, puis redémarrez Visual Studio.

1. Dans la barre de menus, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez de rouvrir votre projet.

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet** pour ouvrir la boîte de dialogue **nouveau projet** . Ensuite, dans le volet gauche de la boîte de dialogue, développez le  >  nœud **autres types de projets** installés, puis sélectionnez **Visual Studio installer**. Dans le volet central, sélectionnez **Projet d’installation**.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (NomProjet)** s’ouvre dans la fenêtre de l’éditeur.

::: moniker-end

## <a name="add-items-to-the-project"></a>Ajouter des éléments au projet

1. Cliquez avec le bouton droit sur le nœud **Dossier d’application**, puis sélectionnez **Ajouter** > **Sortie de projet** pour ouvrir la boîte de dialogue **Ajouter le groupe de sorties du projet**. Dans la boîte de dialogue, sélectionnez **Sortie principale**, puis cliquez sur **OK**. Un nouvel élément nommé **Sortie principale de NomProjet (active)** s’affiche.

1. Cliquez avec le bouton droit sur le nœud **Dossier d’application**, puis sélectionnez **Ajouter** > **Assembly** pour ouvrir la boîte de dialogue **Sélectionner un composant**. Sélectionnez et ajoutez toutes les DLL exigées par le programme, comme indiqué par l’article [Détermination des DLL à redistribuer](determining-which-dlls-to-redistribute.md).

1. Sélectionnez l’élément **Sortie principale de NomProjet (active)**, cliquez avec le bouton droit, puis choisissez **Créer un raccourci vers la sortie principale de NomProjet (active)**. Un nouvel élément nommé **Raccourci vers la sortie principale de NomProjet (active)** s’affiche. Vous pouvez renommer l’élément Raccourci, puis faites glisser et déplacez l’élément dans le nœud **Menu Programmes de l’utilisateur** sur le côté gauche de la fenêtre.

1. Dans la barre de menus, choisissez **générer**  >  **Configuration Manager**. Dans la table **Projet**, sous la colonne **Générer**, cochez la case correspondant au projet de déploiement. Cliquez sur **Fermer**.

1. Dans la barre de menus, choisissez **générer**  >  **générer la solution** pour générer le projet MFC et le projet de déploiement.

1. Dans le dossier de solution, recherchez le programme setup.exe qui a été généré à partir du projet de déploiement. Vous pouvez copier ce fichier (et le fichier .msi) pour installer l’application et ses fichiers de bibliothèques nécessaires sur un autre ordinateur. Exécutez le programme d’installation sur un deuxième ordinateur qui ne dispose pas des bibliothèques Visual C++.

## <a name="see-also"></a>Voir aussi

[Exemples de déploiement](deployment-examples.md)<br/>
