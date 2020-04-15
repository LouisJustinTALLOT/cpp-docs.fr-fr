---
title: 'Procédure pas à pas : déploiement de votre programme (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: eacbcef82f240589e71b59f80d8e19602ceda869
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365010"
---
# <a name="walkthrough-deploying-your-program-c"></a>Procédure pas à pas : déploiement de votre programme (C++)

Maintenant que vous avez créé votre application en suivant les procédures pas à pas décrites précédemment, la dernière étape consiste à créer un programme d'installation pour permettre à d'autres utilisateurs d'installer le programme sur leurs ordinateurs. Pour le programme d’installation, vous allez ajouter un nouveau projet à votre solution existante. La sortie de ce nouveau projet est un fichier setup.exe qui installe votre application sur un autre ordinateur.

La procédure pas à pas indique comment utiliser Windows Installer pour déployer votre application. Vous pouvez également utiliser ClickOnce pour déployer une application. Pour plus d’informations, consultez [ClickOnce Deployment for Visual C++ Applications](../windows/clickonce-deployment-for-visual-cpp-applications.md). Pour plus d’informations sur le déploiement en général, consultez [Déploiement d’applications, de services et de composants](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Prérequis

- La procédure pas à pas part du principe que vous comprenez les notions de base du langage C++.

- Elle suppose également que vous avez effectué les procédures pas à pas connexes précédentes listées dans [Utilisation de l’IDE Visual Studio pour le développement d’applications de bureau C++](using-the-visual-studio-ide-for-cpp-desktop-development.md).

- La procédure pas à pas ne peut pas être effectuée dans les éditions Express de Visual Studio.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Installer le modèle de projet d’installation et de déploiement Visual Studio

Les étapes décrites dans cette section varient en fonction de la version de Visual Studio que vous avez installée. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

<!-- markdownlint-disable MD034 -->

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Pour installer le modèle de projet d’installation et de déploiement Visual Studio 2019

1. Si vous ne l’avez pas déjà fait, téléchargez l’extension Microsoft Visual Studio Installer Projects. L’extension est gratuite pour les développeurs Visual Studio et ajoute les fonctionnalités des modèles de projet d’installation et de déploiement à Visual Studio. Lorsque vous êtes connecté à Internet, dans Visual Studio, choisissez **Extensions** > **Manage Extensions**. Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez sur **Entrée**, sélectionnez **Projets d’installation Microsoft Visual Studio \<version>**, puis cliquez sur **Télécharger**. Choisissez d’exécuter et d’installer l’extension, puis redémarrez Visual Studio.

1. Dans la barre de menus Visual Studio, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez de rouvrir votre projet.

1. Sur la barre de menu, choisissez **File** > **New** > **Project** pour ouvrir la boîte de dialogue Create a **New Project.** Dans la zone de recherche, tapez « installation », puis sélectionnez **Projet d’installation** dans la liste des résultats.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (NomProjet)** s’ouvre dans la fenêtre de l’éditeur.

1. Cliquez avec le bouton droit sur le nœud **Dossier d’application**, puis sélectionnez **Ajouter** > **Sortie de projet** pour ouvrir la boîte de dialogue **Ajouter le groupe de sorties du projet**.

1. Dans la boîte de dialogue, sélectionnez **Sortie principale**, puis cliquez sur **OK**. Un nouvel élément nommé **Sortie principale de Game (active)** s’affiche.

1. Sélectionnez l’élément **Sortie principale de Game (active)**, cliquez avec le bouton droit, puis choisissez **Créer un raccourci vers la sortie principale de Game (active)**. Un nouvel élément nommé **Raccourci vers la sortie principale de Game (active)** s’affiche.

1. Renommez l’élément Raccourci en *Game*, puis faites glisser et déplacez l’élément dans le nœud **Menu Programmes de l’utilisateur** sur le côté gauche de la fenêtre.

1. Dans l’**Explorateur de solutions**, sélectionnez le projet **Game Installer**, puis choisissez **Affichage** > **Fenêtre Propriétés** ou appuyez sur **F4** pour ouvrir la fenêtre **Propriétés**.

1. Spécifiez des détails supplémentaires tels que vous voulez qu’ils s’affichent dans le programme d’installation.  Par exemple, utilisez *Contoso* pour **le fabricant**, *l’installateur de jeu* pour le nom du **produit**, et *https\://www.contoso.com* pour **SupportUrl**.

1. Sur la barre de menu, choisissez **Build** > **Configuration Manager**. Dans la table**Projet**, sous la colonne **Générer**, cochez la case **Game Installer**. Cliquez sur **Fermer**.

1. Dans la barre de menus, choisissez **Générer** > **Générer la solution** pour générer le projet Game et le projet Game Installer.

1. Dans le dossier de solution, recherchez le programme setup.exe qui a été généré à partir du programme Game Installer, puis lancez-le pour installer l’application Game sur votre ordinateur. Vous pouvez copier ce fichier (et GameInstaller.msi) pour installer l’application et ses fichiers de bibliothèques obligatoires sur un autre ordinateur.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Pour installer le modèle de projet d’installation et de déploiement Visual Studio 2017 et antérieur

1. Quand vous êtes connecté à Internet, dans Visual Studio, choisissez **Outils** > **Extensions et mises à jour**.

1. Sous **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez sur **Entrée**, sélectionnez **Projets d’installation Microsoft Visual Studio \<version>**, puis cliquez sur **Télécharger**.

1. Choisissez d’installer l’extension, puis redémarrez Visual Studio.

1. Dans la barre de menus, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez la solution **Game** pour la rouvrir.

### <a name="to-create-a-setup-project-and-install-your-program"></a>Pour créer un projet d'installation et installer votre programme

1. Modifiez la configuration de solution active en Version finale. Sur la barre de menu, choisissez **Build** > **Configuration Manager**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur le bouton **Fermer** pour enregistrer la configuration.

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.

1. Dans le volet gauche de la boîte de dialogue, étendre les nœuds **installés** > **d’autres types de projet,** puis sélectionnez **Visual Studio Installateur**. Dans le volet central, sélectionnez **Projet d’installation**.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Pour cet exemple, entrez *Game Installer*. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (Game Installer)** s’ouvre dans la fenêtre de l’éditeur.

1. Cliquez avec le bouton droit sur le nœud **Dossier d’application**, puis sélectionnez **Ajouter** > **Sortie de projet** pour ouvrir la boîte de dialogue **Ajouter le groupe de sorties du projet**.

1. Dans la boîte de dialogue, sélectionnez **Sortie principale**, puis cliquez sur **OK**. Un nouvel élément nommé **Sortie principale de Game (active)** s’affiche.

1. Sélectionnez l’élément **Sortie principale de Game (active)**, cliquez avec le bouton droit, puis choisissez **Créer un raccourci vers la sortie principale de Game (active)**. Un nouvel élément nommé **Raccourci vers la sortie principale de Game (active)** s’affiche.

1. Renommez l’élément Raccourci en *Game*, puis faites glisser et déplacez l’élément dans le nœud **Menu Programmes de l’utilisateur** sur le côté gauche de la fenêtre.

1. Dans l’**Explorateur de solutions**, sélectionnez le projet **Game Installer**, puis choisissez **Affichage** > **Fenêtre Propriétés** ou appuyez sur **F4** pour ouvrir la fenêtre **Propriétés**.

1. Spécifiez des détails supplémentaires tels que vous voulez qu’ils s’affichent dans le programme d’installation.  Par exemple, utilisez *Contoso* pour **le fabricant**, *l’installateur de jeu* pour le nom du **produit**, et *https\://www.contoso.com* pour **SupportUrl**.

1. Sur la barre de menu, choisissez **Build** > **Configuration Manager**. Dans la table**Projet**, sous la colonne **Générer**, cochez la case **Game Installer**. Cliquez sur **Fermer**.

1. Dans la barre de menus, choisissez **Générer** > **Générer la solution** pour générer le projet Game et le projet Game Installer.

1. Dans le dossier de solution, recherchez le programme setup.exe qui a été généré à partir du programme Game Installer, puis lancez-le pour installer l’application Game sur votre ordinateur. Vous pouvez copier ce fichier (et GameInstaller.msi) pour installer l’application et ses fichiers de bibliothèques obligatoires sur un autre ordinateur.

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

**Précédent :** [Procédure pas à pas : débogage d’un projet (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>Voir aussi

[Référence linguistique de CMD](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)<br/>
[Déploiement des applications de bureau](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
