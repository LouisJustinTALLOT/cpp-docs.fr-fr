---
title: Création d'un contrôle ActiveX MFC
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.activex.project
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
ms.openlocfilehash: 5e0a81d6a01632bcfadccd241f3a485e6d332627
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077458"
---
# <a name="creating-an-mfc-activex-control"></a>Création d'un contrôle ActiveX MFC

Les programmes de contrôle ActiveX sont des programmes modulaires conçus pour fournir un type de fonctionnalité spécifique à une application parente. Par exemple, vous pouvez créer un contrôle tel qu’un bouton à utiliser dans une boîte de dialogue ou une barre d’outils pour une utilisation dans une page Web.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations, consultez [contrôles ActiveX](../activex-controls.md).

Le moyen le plus simple de créer un contrôle ActiveX MFC consiste à utiliser l' [Assistant contrôle ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md).

### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Pour créer un contrôle ActiveX MFC à l’aide de l’Assistant contrôle ActiveX MFC

1. Suivez les instructions de la rubrique d’aide [création d’une application MFC](creating-an-mfc-application.md) , mais choisissez **contrôle ActiveX MFC** dans la liste des modèles disponibles.

1. Définissez les [paramètres](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)de votre application, les [noms des contrôles](../../mfc/reference/control-names-mfc-activex-control-wizard.md)et les [paramètres de contrôle](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) à l’aide de l’Assistant contrôle ActiveX MFC.

    > [!NOTE]
    >  Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir votre nouveau projet dans l’environnement de développement.

Après avoir créé votre projet, vous pouvez afficher les fichiers créés dans **Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md).

Après avoir créé votre projet, vous pouvez utiliser les assistants code pour ajouter des [fonctions](../../ide/add-member-function-wizard.md), des [variables](../../ide/add-member-variable-wizard.md), des [événements](../../ide/add-event-wizard.md), des [Propriétés](../../ide/names-add-property-wizard.md)et des [méthodes](../../ide/add-method-wizard.md). Pour plus d’informations sur la personnalisation de votre contrôle ActiveX, consultez [contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md).

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Pages de propriétés](../../build/reference/property-pages-visual-cpp.md)
