---
title: Création d’une Application MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec61db21b27ef49f660751605b4788599f7f3485
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062494"
---
# <a name="creating-an-mfc-application"></a>Création d'une application MFC

Une application MFC est une application exécutable pour Windows qui se base sur la bibliothèque MFC (Microsoft Foundation Class). L'utilisation de l'Assistant Application MFC constitue le moyen le plus facile pour créer une application MFC.

> [!IMPORTANT]
>  Les projets MFC ne sont pas pris en charge dans les éditions Visual Studio Express.

Les exécutables MFC se décomposent généralement en cinq types : les applications Windows standard, boîtes de dialogue, basée sur les formulaires des applications, applications de style Explorateur et les applications de style navigateur Web. Pour plus d'informations, voir :

- [Utilisation des Classes pour écrire des Applications Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Création et affichage de boîtes de dialogue](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Création d’une application MFC basée sur les formulaires](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Création d’une application MFC de style Explorateur de fichiers](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Création d’une application MFC de style navigateur web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

L'Assistant Application MFC génère les classes et fichiers appropriés pour n'importe lequel de ces types d'applications, en fonction des options sélectionnées dans l'Assistant.

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>Pour créer une application MFC à l'aide de l'Assistant Application MFC

1. Suivez les instructions de la rubrique d’aide [Création d’un projet à l’aide d’un Assistant Application Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

1. Dans le **nouveau projet** boîte de dialogue, sélectionnez **Application MFC** dans le volet Modèles pour ouvrir l’Assistant.

1. Définir les paramètres de votre application à l’aide de la [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md).

    > [!NOTE]
    >  Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir votre nouveau projet dans l’environnement de développement.

Une fois votre projet créé, vous pouvez afficher les fichiers créés dans **l’Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../ide/property-pages-visual-cpp.md)

