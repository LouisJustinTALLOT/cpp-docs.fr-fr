---
title: Ajout d’une page de propriétés ATL
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: 81f793fbdc6d9dda567051b8c35a96f3d3f2f470
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524629"
---
# <a name="adding-an-atl-property-page"></a>Ajout d’une page de propriétés ATL

> [!NOTE] 
> L’Assistant Page de propriétés ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

Pour ajouter une page de propriétés Active Template Library (ATL) à votre projet, celui-ci doit avoir été créé en tant qu’application ATL ou application MFC qui contient une prise en charge ATL. Vous pouvez utiliser [l’Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL dans une application MFC.

Si vous ajoutez une page de propriétés pour un contrôle, celui-ci doit prendre en charge l’interface [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md). Par défaut, cette interface est dans la liste de dérivation de votre classe de contrôle lorsque vous [créez un contrôle ATL](../../atl/reference/adding-an-atl-control.md) à l’aide de [l’Assistant Contrôle ATL](../../atl/reference/atl-control-wizard.md).

> [!NOTE]
> Si votre classe de contrôle n’a pas [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) dans sa liste de dérivation, vous devez l’ajouter manuellement.

## <a name="to-add-an-atl-property-page-to-your-project"></a>Pour ajouter une page de propriétés ATL à votre projet

1. Dans **l’Explorateur de solutions** ou dans [l’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter la page de propriétés ATL.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.

1. Dans la boîte de dialogue [Ajouter une classe](../../ide/add-class-dialog-box.md), dans le volet **Modèles**, cliquez sur **Page de propriétés ATL**, puis sur **Ouvrir** pour afficher [l’Assistant Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md).

Une fois la page de propriétés d’un contrôle créée, vous devez renseigner l’entrée [PROP_PAGE](property-map-macros.md#prop_page) dans le mappage de propriétés pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../../atl/atl-com-property-pages.md)<br/>
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Exemple : Implémentation d’une page de propriétés](../../atl/example-implementing-a-property-page.md)
