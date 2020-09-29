---
title: Ajout d’un objet simple ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.atl
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
ms.openlocfilehash: 85c19c483ff27bd34431ec163e3baadac1855236
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499349"
---
# <a name="adding-an-atl-simple-object"></a>Ajout d’un objet simple ATL

Pour ajouter un objet ATL (Active Template Library) à votre projet, votre projet doit avoir été créé en tant qu’application ATL ou en tant qu’application MFC qui contient la prise en charge ATL. Vous pouvez utiliser l' [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL, ou [Ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL pour une application MFC.

Vous pouvez définir des interfaces COM pour votre nouvel objet ATL quand vous le créez pour la première fois, ou les ajouter ultérieurement à l’aide de la commande [implémenter l’interface](../../ide/implementing-an-interface-visual-cpp.md#implement-interface-wizard) du menu contextuel **affichage de classes** .

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Pour ajouter un objet simple ATL à votre projet ATL COM

1. Dans **Explorateur de solutions** ou [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter l’objet ATL simple.

1. Dans le menu contextuel, cliquez sur **Ajouter**, puis sur **Ajouter une classe**.

1. Dans le volet **modèles** de la boîte de dialogue [Ajouter une classe](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) , cliquez sur **objet simple ATL**, puis cliquez sur **ouvrir** pour afficher l ['Assistant objet simple ATL](../../atl/reference/atl-simple-object-wizard.md).

1. Définissez des options supplémentaires pour votre projet dans la page [options](../../atl/reference/options-atl-simple-object-wizard.md) de l’Assistant **objet simple ATL** .

1. Cliquez sur **Terminer** pour ajouter l’objet à votre projet.

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une nouvelle interface à un projet ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Ajout de points de connexion à un objet](../../atl/adding-connection-points-to-an-object.md)<br/>
[Ajout d’une méthode](../../ide/adding-a-method-visual-cpp.md)<br/>
[Classe MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Ajout d’une classe C++ générique](../../ide/adding-a-generic-cpp-class.md)
