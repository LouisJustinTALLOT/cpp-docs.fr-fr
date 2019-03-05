---
title: Création d'un contrôle ActiveX MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: 031c8596e568f01cdecd7139d959a77923c341eb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294952"
---
# <a name="creating-an-mfc-activex-control"></a>Création d'un contrôle ActiveX MFC

Programmes de contrôle ActiveX sont modulaire conçu pour donner un type spécifique de fonctionnalités à une application parente. Par exemple, vous pouvez créer un contrôle tel qu’un bouton pour une utilisation dans une boîte de dialogue ou une barre d’outils pour une utilisation dans une page Web.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations, consultez [contrôles ActiveX](../activex-controls.md).

Le moyen le plus simple de créer un contrôle ActiveX MFC consiste à utiliser le [Assistant contrôle ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md).

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Pour créer un contrôle ActiveX de MFC à l’aide de l’Assistant de contrôle ActiveX MFC

1. Suivez les instructions de la rubrique d’aide [Création d’un projet à l’aide d’un Assistant Application Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).

1. Dans le **nouveau projet** boîte de dialogue, sélectionnez le **contrôle ActiveX MFC** icône dans le volet Modèles pour ouvrir l’Assistant contrôle ActiveX MFC.

1. Définir votre [paramètres d’application](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), [des noms de contrôle](../../mfc/reference/control-names-mfc-activex-control-wizard.md), et [contrôler les paramètres](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) à l’aide de l’Assistant de contrôle ActiveX MFC.

    > [!NOTE]
    >  Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir votre nouveau projet dans l’environnement de développement.

Une fois que vous avez créé votre projet, vous pouvez afficher les fichiers créés dans **l’Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).

Une fois que vous avez créé votre projet, vous pouvez utiliser les Assistants de code pour ajouter [fonctions](../../ide/add-member-function-wizard.md), [variables](../../ide/add-member-variable-wizard.md), [événements](../../ide/add-event-wizard.md), [propriétés](../../ide/names-add-property-wizard.md), et [méthodes](../../ide/add-method-wizard.md). Pour plus d’informations sur la personnalisation de votre contrôle ActiveX, consultez [contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md).

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../ide/property-pages-visual-cpp.md)
