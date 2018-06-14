---
title: Déployer une application à l’aide du package redistribuable (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37bba00efdf0368973fa4ffbac1cbc6bb6298ce1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339152"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Procédure pas à pas : déploiement d’une application Visual C++ à l’aide du package redistribuable Visual C++
Cet article détaillé décrit comment utiliser le package redistribuable Visual C++ pour déployer une application Visual C++.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure pas à pas, vous devez avoir les composants suivants :  
  
-   Un ordinateur avec Visual Studio installé.  
  
-   Un ordinateur supplémentaire sans les bibliothèques Visual C++.  
  
### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Pour utiliser le package redistribuable Visual C++ afin de déployer une application  
  
1.  Créez et générez une application MFC en suivant les trois premières étapes dans [Procédure pas à pas : Déploiement d’une application Visual C++ à l’aide d’un projet d’installation](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
2.  Créez un fichier, appelez-le setup.bat et ajoutez-lui les commandes suivantes. Remplacez `MyMFCApplication` par le nom de votre projet.  
  
    ```cmd
    @echo off  
    vcredist_x86.exe  
    mkdir "C:\Program Files\MyMFCApplication"  
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"  
    ```  
  
3.  Créez un fichier d’installation à extraction automatique :  
  
    1.  À l’invite de commandes ou dans la fenêtre **Exécuter**, exécutez iexpress.exe.  
  
    2.  Sélectionnez **Créer un fichier de directive à extraction automatique**, puis choisissez le bouton **Suivant**.  
  
    3.  Sélectionnez **Extraire les fichiers et exécuter une commande d’installation**, puis **Suivant**.  
  
    4.  Dans la zone de texte, entrez le nom de votre application MFC, puis choisissez **Suivant**.  
  
    5.  Dans la page **Invite de confirmation**, sélectionnez **Aucune invite**, puis **Suivant**.  
  
    6.  Dans la page **Contrat de licence**, sélectionnez **Ne pas afficher de licence**, puis **Suivant**.  
  
    7.  Dans la page **Fichiers empaquetés**, ajoutez les fichiers suivants, puis choisissez **Suivant**.  
  
        -   Votre application MFC (fichier .exe).  
  
        -   vcredist_x86.exe. Ce fichier se trouve dans \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\vcredist_x86\\.  
  
        -   Le fichier setup.bat que vous avez créé à l’étape précédente.  
  
    8.  Dans la page **Programme d’installation à lancer**, dans la zone de texte **Programme d’installation**, entrez la ligne de commande suivante, puis choisissez **Suivant**.  
  
         **cmd.exe /c "setup.bat"**  
  
    9. Dans la page **Afficher la fenêtre**, sélectionnez **Par défaut**, puis **Suivant**.  
  
    10. Dans la page **Message de fin**, sélectionnez **Aucun message**, puis **Suivant**.  
  
    11. Dans la page **Nom du package et options**, entrez un nom pour votre fichier d’installation à extraction automatique, sélectionnez l’option **Stocker les fichiers à l’aide du nom de fichier long à l’intérieur du package**, puis **Suivant**. La fin du nom de fichier doit être Setup.exe, par exemple, MyMFCApplicationSetup.exe.  
  
    12. Dans la page **Configurer le redémarrage**, sélectionnez **Aucun redémarrage**, puis **Suivant**.  
  
    13. Dans la page **Enregistrer la directive à extraction automatique**, sélectionnez **Enregistrer le fichier de directive à extraction automatique (SED)**, puis **Suivant**.  
  
    14. Dans la page **Créer un package**, choisissez **Suivant**.  
  
4.  Testez le fichier d’installation à extraction automatique sur l’autre ordinateur, celui qui n’a pas les bibliothèques Visual C++ :  
  
    1.  Sur l’autre ordinateur, téléchargez une copie du fichier d’installation, puis installez-le en l’exécutant et en suivant les étapes qu’il fournit.  
  
    2.  Exécutez l’application MFC.  
  
         Le fichier d’installation à extraction automatique installe l’application MFC qui se trouve dans le dossier que vous avez spécifié à l’étape 2. L’application s’exécute correctement, car le programme d’installation du package redistribuable Visual C++ est inclus dans le fichier d’installation à extraction automatique.  
  
        > [!IMPORTANT]
        >  Pour déterminer la version du runtime qui est installée, le programme d’installation vérifie la clé de Registre \HKLM\SOFTWARE\Microsoft\VisualStudio\11.0\VC\Runtimes\\[plateforme]. Si la version actuellement installée est plus récente que la version que le programme d’installation tente d’installer, le programme d’installation aboutit sans installer la version antérieure et laisse une entrée supplémentaire dans la page des programmes installés dans le Panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de déploiement](../ide/deployment-examples.md)