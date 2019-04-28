---
title: Ajout d’une Page de propriétés ATL
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: c61f666865d3e1db4cdcf2dc6d3e07c2113a79c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249097"
---
# <a name="adding-an-atl-property-page"></a>Ajout d’une Page de propriétés ATL

Pour ajouter une page de propriétés bibliothèque ATL (Active Template) à votre projet, votre projet doit avoir été créé comme une application ATL ou comme une application MFC qui contient la prise en charge ATL. Vous pouvez utiliser la [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL pour une application MFC.

Si vous ajoutez une page de propriétés pour un contrôle, votre contrôle doit prendre en charge la [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) interface. Par défaut, cette interface est dans la liste de dérivation de votre contrôle classe lorsque vous [créer un contrôle ATL](../../atl/reference/adding-an-atl-control.md) à l’aide de la [Assistant contrôle ATL](../../atl/reference/atl-control-wizard.md).

> [!NOTE]
> Si votre classe de contrôle n’a pas [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) dans sa liste de dérivation, vous devez l’ajouter manuellement.

## <a name="to-add-an-atl-property-page-to-your-project"></a>Pour ajouter une page de propriétés ATL à votre projet

1. Dans le **l’Explorateur de solutions** ou [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez sur le nom du projet auquel vous souhaitez ajouter la page de propriétés ATL.

1. Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une classe**.

1. Dans le [ajouter une classe](../../ide/add-class-dialog-box.md) boîte de dialogue le **modèles** volet, cliquez sur **Page de propriétés ATL** puis cliquez sur **Open** pour afficher la [Assistant Page de propriétés ATL](../../atl/reference/atl-property-page-wizard.md).

Une fois que vous créez une page de propriétés pour un contrôle, vous devez fournir le [PROP_PAGE](property-map-macros.md#prop_page) entrée dans le mappage des propriétés pour le contrôle.

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../../atl/atl-com-property-pages.md)<br/>
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Exemple : Implémentation d’une page de propriétés](../../atl/example-implementing-a-property-page.md)
