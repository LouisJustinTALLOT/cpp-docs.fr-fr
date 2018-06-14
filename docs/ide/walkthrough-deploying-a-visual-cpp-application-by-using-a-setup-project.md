---
title: Déployer une application Visual C++ à l’aide d’un projet d’installation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 454507a3a3f33b43af0e50c25dab6703aa75a56b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332778"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Procédure pas à pas : déploiement d'une application Visual C++ à l'aide d'un projet d'installation
Décrit comment utiliser un projet d’installation pour déployer une application Visual C++.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   Un ordinateur avec [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] installé.  
  
-   Un ordinateur supplémentaire sans les bibliothèques Visual C++.  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>Pour déployer une application à l’aide d’un projet d’installation  
  
1.  Utilisez **l’Assistant Application MFC** pour créer une solution Visual Studio. Pour rechercher l’Assistant, dans la boîte de dialogue **Nouveau projet**, développez le nœud **Visual C++**, sélectionnez **MFC**, sélectionnez **Application MFC**, entrez un nom pour le projet, puis cliquez sur **OK**.  
  
2.  Remplacez la configuration de la solution active par **Release**. Dans le menu **Générer**, sélectionnez **Gestionnaire de configurations**. Dans la boîte de dialogue **Gestionnaire de configurations**, dans la zone de liste déroulante **Configuration de la solution active**, sélectionnez **Release**.  
  
3.  Appuyez sur F7 pour générer l’application. Sinon, dans le menu **Générer**, cliquez sur **Générer la solution**. Le projet d’installation peut ainsi utiliser la sortie de ce projet d’application MFC.  
  
4.  Si vous ne l’avez pas déjà fait, téléchargez ISLE (InstallShield Limited Edition), qui est gratuit pour les développeurs Visual Studio et remplace les fonctionnalités des modèles de projet dans Visual Studio pour la configuration et le déploiement. Quand vous êtes connecté à Internet, ouvrez la boîte de dialogue **Nouveau projet** en choisissant **Fichier**, **Nouveau**, **Projet** dans la barre de menus, ou en cliquant avec le bouton droit sur votre solution dans **l’Explorateur de solutions** et en choisissant **Ajouter**, **Nouveau projet**. Développez le nœud **Autres types de projets**, choisissez **Activer InstallShield Limited Edition** dans le nœud **Configuration et déploiement**, puis suivez les instructions qui s’affichent. Après avoir téléchargé, installé et activé InstallShield Limited Edition, fermez Visual Studio et rouvrez-le.  
  
5.  Ouvrez de nouveau la boîte de dialogue **Nouveau projet**, développez le nœud **Autres types de projets**, puis choisissez **Projet InstallShield Limited Edition** dans le nœud **InstallShield Limited Edition**.  
  
6.  Suivez les instructions dans le nœud **Mise en route** du projet d’installation créé par le modèle InstallShield Limited Edition pour ajouter une référence de sortie à votre projet MFC Visual Studio.  
  
7.  Générez le projet d’installation pour créer le fichier du programme d’installation (setup.exe). Pour ce faire, cliquez avec le bouton droit sur le nœud du projet d’installation dans **l’Explorateur de solutions** et sélectionnez **Générer**.  
  
     InstallShield Limited Edition crée le fichier de configuration dans l’arborescence du projet d’installation (par défaut, il peut se trouver dans le sous-dossier Express\SingleImage\DiskImages\DISK1 du projet d’installation).  
  
8.  Exécutez le programme d’installation sur un deuxième ordinateur qui ne dispose pas des bibliothèques Visual C++.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de déploiement](../ide/deployment-examples.md)