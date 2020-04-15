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
ms.openlocfilehash: 6367b2a4b85b2c586c5a4420a8be1f80d334b2e4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363962"
---
# <a name="creating-an-mfc-dll-project"></a>Création d'un projet DLL MFC

Un MFC DLL est un fichier binaire qui agit comme une bibliothèque partagée de fonctions qui peuvent être utilisées simultanément par plusieurs applications. La façon la plus simple de créer un projet MFC DLL est d’utiliser le MFC DLL Wizard.

> [!NOTE]
> L’apparence des fonctionnalités dans l’IDE peut dépendre de vos paramètres actifs ou de votre édition, et peut différer de celles décrites dans Help. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Créer un projet MFC DLL à l’aide du MFC DLL Wizard

1. Suivez les instructions dans le sujet [d’aide Création d’une application MFC,](creating-an-mfc-application.md) mais choisissez **MFC Dynamic Link Library** ou **MFC DLL** dans la liste des modèles disponibles.

1. Définissez les paramètres de votre application à l’aide de la page [paramètres d’application](../../mfc/reference/application-settings-mfc-dll-wizard.md) de la [MFC DLL Wizard](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.

1. Cliquez sur **Finition** pour fermer l’assistant et ouvrir votre nouveau projet dans **Solution Explorer**.

Une fois votre projet créé, vous pouvez visualiser les fichiers créés dans l’**Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Voir aussi

[Types de projets C++ dans Visual Studio](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)
