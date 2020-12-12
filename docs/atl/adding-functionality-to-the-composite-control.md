---
description: 'En savoir plus sur : ajout de fonctionnalités au contrôle composite'
title: Ajout de fonctionnalités au contrôle composite
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 90e1f6b0adfc33817f9fa5a6de6fbdcd276241e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166120"
---
# <a name="adding-functionality-to-the-composite-control"></a>Ajout de fonctionnalités au contrôle composite

Une fois que vous avez inséré les contrôles nécessaires dans le contrôle composite, l’étape suivante consiste à ajouter de nouvelles fonctionnalités. Ces nouvelles fonctionnalités se répartissent généralement en deux catégories :

- Prise en charge d’interfaces supplémentaires et personnalisation du comportement de votre contrôle composite avec des fonctionnalités supplémentaires spécifiques.

- Gestion des événements à partir du contrôle ActiveX contenu (ou contrôles).

Dans le cadre de cet article, le reste de cette section se concentre uniquement sur la gestion des événements à partir des contrôles ActiveX.

> [!NOTE]
> Si vous devez gérer des messages à partir de contrôles Windows, consultez [implémentation d’une fenêtre](../atl/implementing-a-window.md) pour plus d’informations sur la gestion des messages dans ATL.

Après avoir inséré un contrôle ActiveX dans la ressource de boîte de dialogue, cliquez avec le bouton droit sur le contrôle, puis cliquez sur **Ajouter un gestionnaire d’événements**. Sélectionnez l’événement que vous souhaitez gérer, puis cliquez sur **Ajouter et modifier**. Le code du gestionnaire d’événements sera ajouté au fichier. h du contrôle.

Les points de connexion pour les contrôles ActiveX sur le contrôle composite sont automatiquement connectés et déconnectés via des appels à [CComCompositeControl :: AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Voir aussi

[Notions de base des contrôles composites](../atl/atl-composite-control-fundamentals.md)
