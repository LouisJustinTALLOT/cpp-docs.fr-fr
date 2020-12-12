---
description: 'En savoir plus sur : ajout d’un contrôle ATL'
title: Ajout d’un contrôle ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
ms.openlocfilehash: 91fe393a1e93deb2173ac95a42b7ab9cca339535
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165704"
---
# <a name="adding-an-atl-control"></a>Ajout d’un contrôle ATL

Utilisez cet Assistant pour ajouter un objet d’interface utilisateur à un projet qui prend en charge les interfaces pour tous les conteneurs potentiels. Pour prendre en charge ces interfaces, le projet doit avoir été créé en tant qu’application ATL ou en tant qu’application MFC qui contient la prise en charge ATL. Vous pouvez utiliser l' [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL, ou [Ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL pour une application MFC.

## <a name="to-add-an-atl-control-to-your-project"></a>Pour ajouter un contrôle ATL à votre projet

1. Dans **Explorateur de solutions** ou [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom du projet auquel vous souhaitez ajouter l’objet ATL simple.

1. Dans le menu contextuel, cliquez sur **Ajouter** , puis sur **Ajouter une classe**.

1. Dans la boîte de dialogue [Ajouter une classe](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) , dans le volet modèles, cliquez sur **contrôle ATL**, puis sur **Ajouter** pour afficher l ['Assistant contrôle ATL](../../atl/reference/atl-control-wizard.md).

À l’aide de l' **Assistant contrôle ATL**, vous pouvez créer l’un des trois types de contrôles suivants :

- Contrôle standard

- Contrôle composite

- Contrôle DHTML

En outre, vous pouvez réduire la taille du contrôle et supprimer les interfaces qui ne sont pas utilisées par la plupart des conteneurs en sélectionnant **contrôle minimal** dans la page **options** de l’Assistant.

## <a name="see-also"></a>Voir aussi

[Ajout de fonctionnalités au contrôle composite](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md)
