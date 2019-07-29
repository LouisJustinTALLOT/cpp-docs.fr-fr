---
title: Création d'une application MFC
ms.date: 07/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 454a994da6db2841317d41ea1cdacfd36b0705e4
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606482"
---
# <a name="creating-an-mfc-application"></a>Création d'une application MFC

Une application MFC est une application exécutable pour Windows qui se base sur la bibliothèque MFC (Microsoft Foundation Class). Le moyen le plus simple de créer une application MFC consiste à utiliser l’Assistant Application MFC (projet d’application**MFC** dans Visual Studio 2019). Pour créer une application console MFC, utilisez l’Assistant Windows Desktop et choisissez l' **application console** et les options des **en-têtes MFC** .

> [!IMPORTANT]
>  Les projets MFC ne sont pas pris en charge dans les éditions Visual Studio Express.

Les exécutables MFC se décomposent généralement en cinq types: les applications Windows standard, les boîtes de dialogue, les applications basées sur les formulaires, les applications de style Explorateur et les applications de style navigateur Web. Pour plus d'informations, voir :

- [Utilisation des classes pour écrire des applications Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Création et affichage de boîtes de dialogue](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Création d’une application MFC basée sur les formulaires](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Création d’une application MFC de style Explorateur de fichiers](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Création d’une application MFC de style navigateur web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

L'Assistant Application MFC génère les classes et fichiers appropriés pour n'importe lequel de ces types d'applications, en fonction des options sélectionnées dans l'Assistant.

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>Pour créer une application MFC à l'aide de l'Assistant Application MFC

1. Suivez les instructions de la rubrique d’aide [créer C++ un projet d’application console](../../get-started/tutorial-console-cpp.md).

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **application MFC** dans le volet modèles pour ouvrir l’Assistant.

1. Définissez les paramètres de votre application à l’aide de l' [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md).

    > [!NOTE]
    >  Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir votre nouveau projet dans l’environnement de développement.

Une fois votre projet créé, vous pouvez visualiser les fichiers créés dans l’**Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)

