---
title: Déployer une application à l’aide du package redistribuable (C++)
ms.date: 04/23/2019
helpviewer_keywords:
- walkthrough, deploying a Visual C++ application by using the redistributable package
ms.assetid: e59becbf-b8c6-4c8e-bab3-b69cc1ed3e5e
ms.openlocfilehash: d2bd0794a67cf70b9da0499e3d2cafa553531fe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370254"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-the-visual-c-redistributable-package"></a>Procédure pas à pas : déploiement d'une application Visual C++ à l'aide de Visual C++ Redistributable Package

Cet article détaillé décrit comment utiliser le package redistribuable Visual C++ pour déployer une application Visual C++.

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez avoir les composants suivants :

- Un ordinateur avec Visual Studio installé.

- Un ordinateur supplémentaire sans les bibliothèques Visual C++.

### <a name="to-use-the-visual-c-redistributable-package-to-deploy-an-application"></a>Pour utiliser le package redistribuable Visual C++ afin de déployer une application

1. Créez et générez une application MFC en suivant les étapes dans [Procédure pas à pas : Déploiement d’une application Visual C++ à l’aide d’un projet d’installation](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

1. Créez un fichier, appelez-le setup.bat et ajoutez-lui les commandes suivantes. Remplacez `MyMFCApplication` par le nom de votre projet.

    ```cmd
    @echo off
    vcredist_x86.exe
    mkdir "C:\Program Files\MyMFCApplication"
    copy MyMFCApplication.exe "C:\Program Files\MyMFCApplication"
    ```

1. Créez un fichier d’installation à extraction automatique :

   1. À l’invite de commandes ou dans la fenêtre **Exécuter**, exécutez iexpress.exe.

   1. Sélectionnez **Créer un fichier de directive à extraction automatique**, puis choisissez le bouton **Suivant**.

   1. Sélectionnez **Extraire les fichiers et exécuter une commande d’installation**, puis **Suivant**.

   1. Dans la zone de texte, entrez le nom de votre application MFC, puis choisissez **Suivant**.

   1. Dans la page **Invite de confirmation**, sélectionnez **Aucune invite**, puis **Suivant**.

   1. Dans la page **Contrat de licence**, sélectionnez **Ne pas afficher de licence**, puis **Suivant**.

   1. Dans la page **Fichiers empaquetés**, ajoutez les fichiers suivants, puis choisissez **Suivant**.

      - Votre application MFC (fichier .exe).

      - vcredist_x86.exe. Dans Visual Studio 2015, ce fichier est situé en *%VCINSTALLDIR%redist\\1033\\*. Dans Visual Studio 2017 et Visual Studio 2019, ce fichier est situé en *%VCToolsRedistDir%*. Vous pouvez également [télécharger le dernier fichier rediste pris en charge de Microsoft](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads).

      - Le fichier setup.bat que vous avez créé à l’étape précédente.

   1. Dans la page **Programme d’installation à lancer**, dans la zone de texte **Programme d’installation**, entrez la ligne de commande suivante, puis choisissez **Suivant**.

      **cmd.exe /c "setup.bat"**

   1. Dans la page **Afficher la fenêtre**, sélectionnez **Par défaut**, puis **Suivant**.

   1. Dans la page **Message de fin**, sélectionnez **Aucun message**, puis **Suivant**.

   1. Dans la page **Nom du package et options**, entrez un nom pour votre fichier d’installation à extraction automatique, sélectionnez l’option **Stocker les fichiers à l’aide du nom de fichier long à l’intérieur du package**, puis **Suivant**. La fin du nom de fichier doit être Setup.exe ; par exemple, *MyMFCApplicationSetup.exe*.

   1. Dans la page **Configurer le redémarrage**, sélectionnez **Aucun redémarrage**, puis **Suivant**.

   1. Dans la page **Enregistrer la directive à extraction automatique**, sélectionnez **Enregistrer le fichier de directive à extraction automatique (SED)**, puis **Suivant**.

   1. Dans la page **Créer un package**, choisissez **Suivant**. Cliquez sur **Terminer**.

1. Testez le fichier d’installation à extraction automatique sur l’autre ordinateur, celui qui n’a pas les bibliothèques Visual C++ :

   1. Sur l’autre ordinateur, téléchargez une copie du fichier d’installation, puis installez-le en l’exécutant et en suivant les étapes qu’il fournit. Selon les options sélectionnées, l’installation peut nécessiter la commande **Exécuter en tant qu’administrateur**.

   1. Exécutez l’application MFC.

      Le fichier d’installation à extraction automatique installe l’application MFC qui se trouve dans le dossier que vous avez spécifié à l’étape 2. L’application s’exécute correctement, car le programme d’installation du package redistribuable Visual C++ est inclus dans le fichier d’installation à extraction automatique.

      > [!IMPORTANT]
      > Pour déterminer quelle version du temps d’exécution est \\installée,\\\\l’installateur vérifie la clé du registre HKLM\\SOFTWARE Microsoft\\VisualStudio_version_\\VC Runtimes version version Version VC Runtimes version Version Version VC Runtimes version Version Version VC Runtimes version Version Version VC\\Runtimes\\_version_\\Version Version. Si la version actuellement installée est plus récente que la version que le programme d’installation tente d’installer, le programme d’installation aboutit sans installer la version antérieure et laisse une entrée supplémentaire dans la page des programmes installés dans le Panneau de configuration.

## <a name="see-also"></a>Voir aussi

[Exemples de déploiement](deployment-examples.md)<br/>
