---
title: Ajout d'une classe MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.mfc
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
ms.openlocfilehash: 1cc3dc734917da46af99e67da40fe243941102e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296772"
---
# <a name="adding-an-mfc-class"></a>Ajout d'une classe MFC

Pour ajouter des classes dérivées de classes de la bibliothèque Microsoft Foundation classes (MFC) à votre projet, utilisez le **ajouter une classe** disponible à partir de la commande [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code). Spécifiez le nom de la nouvelle classe, sélectionnez la classe de base, puis l’ID de la boîte de dialogue avec laquelle il est associé (le cas échéant). L’Assistant code crée un fichier d’en-tête et un fichier d’implémentation et les ajoute à votre projet.

> [!NOTE]
>  Vous pouvez ajouter des classes MFC à une application COM ATL si vous initialement [créé l’application avec prise en charge MFC](../../atl/reference/mfc-support-in-atl-projects.md). Vous pouvez également ajouter des classes MFC à des projets Win32 qui prend en charge MFC.

### <a name="to-add-an-mfc-class-to-your-project"></a>Pour ajouter une classe MFC à votre projet

1. À partir de l’affichage de classes, cliquez sur le nom du projet. Cliquez sur **ajouter** puis cliquez sur **ajouter une classe** pour ouvrir le [ajouter une classe](../../ide/add-class-dialog-box.md) boîte de dialogue.

1. Dans le volet Modèles, sélectionnez **classe MFC** et appuyez sur la **ajouter** bouton.

1. Définir les paramètres pour la nouvelle classe dans le [Assistant classe MFC](../../mfc/reference/mfc-add-class-wizard.md) boîte de dialogue.

1. Cliquez sur **Terminer** pour fermer l’Assistant et afficher la nouvelle classe dans l’affichage de classes. Vous pouvez également afficher les fichiers créés par l’Assistant dans **l’Explorateur de solutions**.

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Vue d’ensemble de la classe](../../mfc/class-library-overview.md)
