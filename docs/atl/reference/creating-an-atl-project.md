---
title: Création d’un projet ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.project
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- ATL70.DLL
- _ATL_MIN_CRT macro
- distributing files with ATL components
ms.assetid: 061d5f98-f669-440e-9380-42f017a0f9e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b22e903b86ba3de8bcd98aa47f1b6756288f2f78
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070972"
---
# <a name="creating-an-atl-project"></a>Création d’un projet ATL

Le moyen le plus simple de créer un projet ATL consiste à utiliser l’Assistant Projet ATL, situé dans le **projets Win32** dossier de la **nouveau projet** boîte de dialogue.

## <a name="to-create-an-atl-project-using-the-atl-project-wizard"></a>Pour créer un projet ATL à l’aide de l’Assistant Projet ATL

1. Suivez les instructions de la rubrique [création d’un projet avec un Assistant d’Application Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

1. Sélectionnez le **projet ATL** icône dans le **modèles** volet pour ouvrir le **Assistant Projet ATL**.

1. Définir les paramètres de votre application à l’aide de la [paramètres d’Application](../../atl/reference/application-settings-atl-project-wizard.md) page de la **Assistant Projet ATL**.

   > [!NOTE]
   > Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir votre nouveau projet dans l’environnement de développement.

Une fois votre projet créé, vous pouvez afficher les fichiers créés dans **l’Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md). Pour plus d’informations sur les configurations pour le nouveau projet ATL et comment les modifier, consultez [par défaut des Configurations de projet ATL](../../atl/reference/default-atl-project-configurations.md).

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../ide/property-pages-visual-cpp.md)
