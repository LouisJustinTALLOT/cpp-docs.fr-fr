---
title: Déployer une application Visual C++ à l'aide d'un projet d'installation
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 8a1242140154c5a0123d71b83983fae20cab5d7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374357"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Procédure pas à pas : déploiement d'une application Visual C++ à l'aide d'un projet d'installation

Décrit comment utiliser un projet d’installation pour déployer une application Visual C++.

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Un ordinateur sur lequel Visual Studio est installé.

- Un ordinateur supplémentaire sans les bibliothèques Visual C++.

## <a name="create-the-setup-project"></a>Créer le projet d’installation

Les instructions pour créer un projet d’installation varient selon la version de Visual Studio que vous avez installée. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Pour créer le projet dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

   ![Projet MFC App](media/vs2019-mfc-app-new-project.png "Nouvelle application MFC")

1. En haut du dialogue, `MFC` tapez dans la boîte de recherche, puis choisissez **L’application MFC** dans la liste des résultats. Si vous ne le voyez pas, vous devrez lancer le programme Visual Studio Install du menu Windows Start et cliquer sur la vignette de **charge de travail de développement de bureau CMD.** En vertu **des composants individuels,** assurez-vous que le composant MFC est vérifié.

1. Dans la page suivante, entrez un nom pour le projet et spécifiez l’emplacement du projet si désiré.

1. Choisissez le bouton **Créer** pour créer le projet client. Lorsque **l’assistant d’application MFC** apparaît, acceptez tous les défauts.

1. Modifier la configuration de la solution active pour **libérer**. Dans le menu **Générer**, sélectionnez **Gestionnaire de configurations**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la zone de liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur **Fermer**.

1. Appuyez **sur Ctrl**+**Shift**+**B** pour construire l’application. Sinon, dans le menu **Générer**, cliquez sur **Générer la solution**. La génération de l’application permet au projet d’installation d’utiliser la sortie de ce projet d’application MFC.

1. Si vous ne l’avez pas déjà fait, téléchargez l’extension Microsoft Visual Studio Installer Projects. L’extension est gratuite pour les développeurs Visual Studio et ajoute les fonctionnalités des modèles de projet d’installation et de déploiement à Visual Studio. Lorsque vous êtes connecté à Internet, dans Visual Studio, choisissez **Extensions** > **Manage Extensions**. Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez **sur Enter**, sélectionnez Microsoft **Visual Studio \<version> Installer Projects**, et cliquez sur **Télécharger**. Choisissez d’exécuter et d’installer l’extension, puis redémarrez Visual Studio.

   ![Projet d’installation de Studio Visuel](media/vs2019-extension-dialog-installer-project.png "Nommez le projet client")

1. Dans la barre de menus Visual Studio, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez de rouvrir votre projet.

1. Sur la barre de menu, choisissez **File** > **New** > **Project** pour ouvrir la boîte de dialogue Create a **New Project.** Dans la zone de recherche, tapez « installation », puis sélectionnez **Projet d’installation** dans la liste des résultats.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (NomProjet)** s’ouvre dans la fenêtre de l’éditeur.

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>Créer le projet en Visual Studio 2017

1. Créez un projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Utilisez le **MFC Application Wizard** pour créer une nouvelle solution Visual Studio. Pour rechercher l’Assistant, dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C++**, sélectionnez **MFC**, sélectionnez **Application MFC**, entrez un nom pour le projet, puis cliquez sur **OK**. Cliquez sur **Terminer**.

   > [!NOTE]
   > Si le type **d’application MFC** est manquant, sélectionnez **Open Visual Studio Installateur** dans le volet gauche de la boîte de dialogue **New Project.** Installez l’option située sous **Développement Desktop en C++** dans la section des components **Facultatifs**, nommée **MFC Visual C++ pour x86 et x64**.

1. Modifier la configuration de la solution active pour **libérer**. Dans le menu **Générer**, sélectionnez **Gestionnaire de configurations**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la zone de liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur **Fermer**.

1. Appuyez **sur Ctrl**+**Shift**+**B** pour construire l’application. Sinon, dans le menu **Générer**, cliquez sur **Générer la solution**. La génération de l’application permet au projet d’installation d’utiliser la sortie de ce projet d’application MFC.

1. Si vous ne l’avez pas déjà fait, téléchargez l’extension Microsoft Visual Studio Installer Projects. L’extension est gratuite pour les développeurs Visual Studio et ajoute les fonctionnalités des modèles de projet d’installation et de déploiement à Visual Studio. Lorsque vous êtes connecté à Internet, dans Visual Studio, choisissez des**extensions et des mises à jour d’outils** **Tools** > . Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez **sur Enter**, sélectionnez Microsoft **Visual Studio \<version> Installer Projects**, et cliquez sur **Télécharger**. Choisissez d’exécuter et d’installer l’extension, puis redémarrez Visual Studio.

1. Dans la barre de menus, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez de rouvrir votre projet.

1. Sur la barre de menu, choisissez **File** > **New** > **Project** pour ouvrir la boîte de dialogue du **nouveau projet.** Puis dans le volet gauche de la boîte de dialogue, étendre les nœuds **installés** > **d’autres types de projet,** et sélectionnez **Visual Studio Installateur**. Dans le volet central, sélectionnez **Projet d’installation**.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (NomProjet)** s’ouvre dans la fenêtre de l’éditeur.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>Pour créer le projet en Visual Studio 2015

1. Créez un projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Utilisez le **MFC Application Wizard** pour créer une nouvelle solution Visual Studio. Pour rechercher l’Assistant, dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C++**, sélectionnez **MFC**, sélectionnez **Application MFC**, entrez un nom pour le projet, puis cliquez sur **OK**. Cliquez sur **Terminer**.

   > [!NOTE]
   > Si le type **d’application MFC** est manquant, cliquez sur le bouton Windows Start et **tapez ajouter des programmes supprimer**. Ouvrez le programme à partir de la liste des résultats, puis recherchez votre installation de Microsoft Visual Studio 2015 dans la liste des programmes installés. Double-cliquez dessus, puis choisissez **Modifier** et sélectionnez le composant **Microsoft Foundation Classes** sous **Visual C++**.

1. Modifier la configuration de la solution active pour **libérer**. Dans le menu **Build,** sélectionnez **Configuration Manager**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la zone de liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur **Fermer**.

1. Appuyez **sur Ctrl**+**Shift**+**B** pour construire l’application. Sinon, dans le menu **Générer**, cliquez sur **Générer la solution**. La génération de l’application permet au projet d’installation d’utiliser la sortie de ce projet d’application MFC.

1. Si vous ne l’avez pas déjà fait, téléchargez l’extension Microsoft Visual Studio Installer Projects. L’extension est gratuite pour les développeurs Visual Studio et ajoute les fonctionnalités des modèles de projet d’installation et de déploiement à Visual Studio. Lorsque vous êtes connecté à Internet, dans Visual Studio, choisissez des**extensions et des mises à jour d’outils** **Tools** > . Dans la boîte de dialogue **Extensions et mises à jour**, sélectionnez l’onglet **En ligne**, puis tapez *Projets Microsoft Visual Studio Installer* dans la zone de recherche. Appuyez **sur Enter**, sélectionnez Microsoft **Visual Studio \<version> Installer Projects**, et cliquez sur **Télécharger**. Choisissez d’exécuter et d’installer l’extension, puis redémarrez Visual Studio.

1. Dans la barre de menus, choisissez **Fichier** > **Projets et solutions récents**, puis choisissez de rouvrir votre projet.

1. Sur la barre de menu, choisissez **File** > **New** > **Project** pour ouvrir la boîte de dialogue du **nouveau projet.** Puis dans le volet gauche de la boîte de dialogue, étendre les nœuds **installés** > **d’autres types de projet,** et sélectionnez **Visual Studio Installateur**. Dans le volet central, sélectionnez **Projet d’installation**.

1. Entrez le nom du projet d’installation dans la zone **Nom**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Fichier (NomProjet)** s’ouvre dans la fenêtre de l’éditeur.

::: moniker-end

## <a name="add-items-to-the-project"></a>Ajouter des éléments au projet

1. Cliquez avec le bouton droit sur le nœud **Dossier d’application**, puis sélectionnez **Ajouter** > **Sortie de projet** pour ouvrir la boîte de dialogue **Ajouter le groupe de sorties du projet**. Dans la boîte de dialogue, sélectionnez **Sortie principale**, puis cliquez sur **OK**. Un nouvel élément nommé **Sortie principale de NomProjet (active)** s’affiche.

1. Cliquez avec le bouton droit sur le nœud **Dossier d’application**, puis sélectionnez **Ajouter** > **Assembly** pour ouvrir la boîte de dialogue **Sélectionner un composant**. Sélectionnez et ajoutez toutes les DLL exigées par le programme, comme indiqué par l’article [Détermination des DLL à redistribuer](determining-which-dlls-to-redistribute.md).

1. Sélectionnez l’élément **Sortie principale de NomProjet (active)**, cliquez avec le bouton droit, puis choisissez **Créer un raccourci vers la sortie principale de NomProjet (active)**. Un nouvel élément nommé **Raccourci vers la sortie principale de NomProjet (active)** s’affiche. Vous pouvez renommer l’élément Raccourci, puis faites glisser et déplacez l’élément dans le nœud **Menu Programmes de l’utilisateur** sur le côté gauche de la fenêtre.

1. Sur la barre de menu, choisissez **Build** > **Configuration Manager**. Dans la table**Projet**, sous la colonne **Générer**, cochez la case correspondant au projet de déploiement. Cliquez sur **Fermer**.

1. Sur la barre de menu, choisissez **Build** > **Build Solution** pour construire le projet MFC et le projet de déploiement.

1. Dans le dossier de solution, recherchez le programme setup.exe qui a été généré à partir du projet de déploiement. Vous pouvez copier ce fichier (et le fichier .msi) pour installer l’application et ses fichiers de bibliothèques nécessaires sur un autre ordinateur. Exécutez le programme d’installation sur un deuxième ordinateur qui ne dispose pas des bibliothèques Visual C++.

## <a name="see-also"></a>Voir aussi

[Exemples de déploiement](deployment-examples.md)<br/>
