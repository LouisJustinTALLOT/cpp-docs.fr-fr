---
title: Création d'un projet DLL MFC
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 6a1718e1f347be46b2f228479d3dbd30027b3160
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077443"
---
# <a name="creating-an-mfc-dll-project"></a>Création d'un projet DLL MFC

Une DLL MFC est un fichier binaire qui agit comme une bibliothèque partagée de fonctions qui peuvent être utilisées simultanément par plusieurs applications. Le moyen le plus simple de créer un projet DLL MFC consiste à utiliser l’Assistant DLL MFC.

> [!NOTE]
>  L’apparence des fonctionnalités dans l’IDE peut dépendre de vos paramètres actifs ou de l’édition et peut différer de ceux décrits dans l’aide de. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Pour créer un projet DLL MFC à l’aide de l’Assistant DLL MFC

1. Suivez les instructions de la rubrique d’aide [création d’une application MFC](creating-an-mfc-application.md) , mais choisissez **bibliothèque de liens dynamiques MFC** ou **DLL MFC** dans la liste des modèles disponibles.

1. Définissez les paramètres de votre application à l’aide de la page Paramètres de l' [application](../../mfc/reference/application-settings-mfc-dll-wizard.md) de l' [Assistant DLL MFC](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir votre nouveau projet dans **Explorateur de solutions**.

Une fois votre projet créé, vous pouvez visualiser les fichiers créés dans l’**Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Voir aussi

[Types de projets C++ dans Visual Studio](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)
