---
title: Ajout d’un contrôle ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: 836b19cef38549bcdf6cddeeda5bbb7fee08a1c1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298436"
---
# <a name="adding-an-atl-control"></a>Ajout d’un contrôle ATL

Utilisez cet Assistant pour ajouter un objet d’interface utilisateur à un projet qui prend en charge des interfaces pour tous les conteneurs potentiels. Pour prendre en charge ces interfaces, le projet doit avoir été créé comme une application ATL ou comme une application MFC qui contient la prise en charge ATL. Vous pouvez utiliser [l’Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL dans une application MFC.

## <a name="to-add-an-atl-control-to-your-project"></a>Pour ajouter un contrôle ATL à votre projet

1. Dans le **l’Explorateur de solutions** ou [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez sur le nom du projet auquel vous souhaitez ajouter l’objet simple ATL.

1. Cliquez sur **ajouter** dans le menu contextuel, puis cliquez sur **ajouter une classe**.

1. Dans le [ajouter une classe](../../ide/add-class-dialog-box.md) boîte de dialogue, dans le volet Modèles, cliquez sur **contrôle ATL**, puis cliquez sur **ajouter** pour afficher le [Assistant contrôle ATL](../../atl/reference/atl-control-wizard.md).

À l’aide de la **Assistant contrôle ATL**, vous pouvez créer un des trois types de contrôles :

- Un contrôle standard

- Un contrôle composite

- Un contrôle DHTML

En outre, vous pouvez réduire la taille du contrôle et supprimer des interfaces qui ne sont pas utilisés par la plupart des conteneurs en sélectionnant **contrôle Minimal** sur le **Options** page de l’Assistant.

## <a name="see-also"></a>Voir aussi

[Ajout d’une fonctionnalité au contrôle composite](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)
