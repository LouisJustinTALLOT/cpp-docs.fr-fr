---
title: 'Procédure pas à pas : déploiement de votre programme (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1753c63673b9dd083e2b690788801bd467938c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335534"
---
# <a name="walkthrough-deploying-your-program-c"></a>Procédure pas à pas : déploiement de votre programme (C++)
Maintenant que vous avez créé votre application en suivant les procédures pas à pas décrites précédemment, qui sont listées dans [Utilisation de l’IDE Visual Studio pour le développement d’applications de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md), la dernière étape consiste à créer un programme d’installation pour permettre à d’autres utilisateurs d’installer le programme sur leurs ordinateurs. Pour cela, vous allez ajouter un nouveau projet à votre solution existante. La sortie de ce nouveau projet est un fichier setup.exe qui installe votre application sur un autre ordinateur.  
  
 Cette procédure pas à pas indique comment utiliser Windows Installer pour déployer votre application. Vous pouvez également utiliser ClickOnce pour déployer une application. Pour plus d’informations, consultez [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md). Pour plus d’informations sur le déploiement en général, consultez [Déploiement d’applications, de services et de composants](/visualstudio/deployment/deploying-applications-services-and-components).  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Cette procédure pas à pas part du principe que vous comprenez les notions de base du langage C++.  
  
-   Elle suppose également que vous avez effectué les procédures pas à pas connexes précédentes répertoriées dans [Utilisation de l’IDE Visual Studio pour le développement d’applications de bureau C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
-   Cette procédure pas à pas ne peut pas être effectuée dans les éditions Express de Visual Studio.  
  
-   Si ce n'est déjà fait, téléchargez InstallShield Limited Edition (ISLE), comme indiqué dans la procédure plus loin dans cet article. ISLE est une version gratuite d'InstallShield pour les développeurs Visual Studio qui remplace les fonctionnalités des modèles de projet d'installation et de déploiement présents dans les éditions antérieures de Visual Studio.  
  
### <a name="to-install-the-isle-setup-and-deployment-project-template"></a>Pour installer le modèle de projet d'installation et de déploiement ISLE  
  
1.  Quand vous êtes connecté à Internet, dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.  
  
2.  Dans le volet gauche de la boîte de dialogue, développez les nœuds **Installé**, **Modèles** et **Autres types de projets**, puis sélectionnez **Configuration et déploiement**. Dans le volet central, sélectionnez **Activer InstallShield Limited Edition**, puis choisissez le bouton **OK**.  
  
3.  Suivez les instructions pour installer InstallShield Limited Edition pour Visual Studio (ISLE).  
  
4.  Après avoir téléchargé, installé et activé ISLE, fermez Visual Studio et rouvrez-le.  
  
5.  Dans la barre de menus, choisissez **Fichier**, **Projets et solutions récents**, puis choisissez la solution **Game** pour la rouvrir.  
  
### <a name="to-create-a-setup-project-and-install-your-program"></a>Pour créer un projet d'installation et installer votre programme  
  
1.  Modifiez la configuration de solution active en Mise en production. Dans la barre de menus, choisissez **Générer**, puis **Gestionnaire de configurations**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la liste déroulante **Configuration de la solution active**, sélectionnez **Release**. Cliquez sur le bouton **Fermer** pour enregistrer la configuration.  
  
2.  Dans la barre de menus, choisissez **Fichier**, **Nouveau**, **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.  
  
3.  Dans le volet gauche de la boîte de dialogue, développez les nœuds **Installé**, **Modèles** et **Autres types de projets**, puis sélectionnez **Configuration et déploiement**. Dans le volet central, sélectionnez **Projet InstallShield Limited Edition**.  
  
4.  Entrez le nom du projet d’installation dans la zone **Nom**. Pour cet exemple, entrez **Game Installer**. Dans la liste déroulante **Solution**, sélectionnez **Ajouter à la solution**. Choisissez le bouton **OK** pour créer le projet d’installation. Un onglet **Assistant Projet (Game Installer)** s’ouvre dans la fenêtre de l’éditeur.  
  
5.  En bas de l’onglet **Assistant Projet (Game Installer)**, cliquez sur le lien **Informations sur l’application**.  
  
6.  Dans la page **Informations sur l’application**, spécifiez le nom de votre société tel que vous souhaitez qu’il apparaisse dans le programme d’installation. Vous pouvez utiliser le nom de votre propre société ou, pour cet exemple, **Contoso**. Spécifiez le nom de votre application ; dans cet exemple, spécifiez **Game**. Spécifiez l’adresse web de votre société ou, pour cet exemple, utilisez **http://www.contoso.com**.  
  
7.  En bas de l’onglet **Assistant Projet (Game Installer)**, cliquez sur le lien **Installation Interview**.  
  
8.  Dans la page **Installation Interview**, sous **Do you want to display a License Agreement Dialog**, sélectionnez la case d’option **No**. Sous **Do you want to prompt users to enter their Company Name and User Name**, sélectionnez la case d’option **No**.  
  
9. Dans **l’Explorateur de solutions**, développez le projet **Game Installer**, développez le nœud **Planifier votre installation**, puis ouvrez la page **Informations générales**.  
  
10. Sous l’onglet **Informations générales (Game Installer)** dans la fenêtre de l’éditeur, spécifiez un **ID de création de balise**, par exemple **regid.2012-12.com.Contoso**.  
  
11. Dans **l’Explorateur de solutions**, sous le projet **Game Installer**, développez le nœud **Spécifiez les données d’application**, puis ouvrez la page **Fichiers**.  
  
12. Sous l’onglet **Fichiers (Game Installer)** dans la fenêtre de l’éditeur, sous **Fichiers de l’ordinateur source**, ouvrez le menu contextuel de **Sortie principale de Game**, puis choisissez **Copier**.  
  
13. Ouvrez un menu contextuel dans l’espace situé sous la colonne **Nom** dans **Fichiers de l’ordinateur de destination**, puis choisissez **Coller**. Un nouvel élément nommé **Sortie de Game.Primary** apparaît.  
  
14. Dans **l’Explorateur de solutions**, sous le nœud **Spécifiez les données d’application**, ouvrez la page **Composants redistribuables**.  
  
15. Sous l’onglet **Composants redistribuables (Game Installer)** de la fenêtre de l’éditeur, cochez la case **Visual C++ 11.0 CRT (x86)**.  
  
16. Dans la barre de menus, choisissez **Générer**, **Générer la solution** pour générer le projet Game et le projet Game Installer.  
  
17. Dans le dossier de solution, recherchez le programme setup.exe qui a été généré à partir du programme Game Installer, puis lancez-le pour installer l’application Game sur votre ordinateur. Vous pouvez copier ce fichier pour installer l'application et ses fichiers de bibliothèques requis sur un autre ordinateur.  
  
18. Vous pouvez définir de nombreuses options dans le projet d’installation pour répondre à vos besoins. Pour plus d’informations, dans **l’Explorateur de solutions**, sous le projet **Game Installer**, ouvrez la page **Mise en route**, puis utilisez la touche F1 pour ouvrir la bibliothèque d’aide ISLE.  
  
## <a name="next-steps"></a>Étapes suivantes  
 **Précédent :** [Procédure pas à pas : débogage d’un projet (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)   
 [Génération de programmes C/C++](../build/building-c-cpp-programs.md)  
 [Déploiement des applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)