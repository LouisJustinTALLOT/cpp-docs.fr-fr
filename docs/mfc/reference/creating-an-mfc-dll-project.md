---
title: Création d'un projet DLL MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 21173582f68b1d50fefbe22250546fcce63730b4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278832"
---
# <a name="creating-an-mfc-dll-project"></a>Création d'un projet DLL MFC

Une DLL MFC est un fichier binaire qui agit comme une bibliothèque partagée de fonctions pouvant être utilisé simultanément par plusieurs applications. Pour créer un projet DLL MFC, le plus simple consiste à utiliser l’Assistant DLL MFC.

> [!NOTE]
>  L’apparence des fonctionnalités dans l’IDE peut dépendre de vos paramètres actifs ou votre édition et peut-être différer de celles décrites dans l’aide. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Pour créer un projet de DLL MFC à l’aide de l’Assistant DLL MFC

1. Suivez les instructions de la rubrique d’aide [Création d’un projet à l’aide d’un Assistant Application Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

**Remarque** dans le **nouveau projet** boîte de dialogue, sélectionnez le `MFC DLL` icône dans le volet Modèles pour ouvrir l’Assistant DLL MFC.

1. Définir les paramètres de votre application à l’aide de la [paramètres d’application](../../mfc/reference/application-settings-mfc-dll-wizard.md) page de la [Assistant DLL MFC](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir votre nouveau projet dans **l’Explorateur de solutions**.

Une fois votre projet créé, vous pouvez afficher les fichiers créés dans **l’Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Voir aussi

[Types de projets Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../ide/property-pages-visual-cpp.md)
