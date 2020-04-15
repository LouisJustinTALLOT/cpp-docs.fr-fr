---
title: Ajout de fonctionnalités au contrôle composite
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 5de18f863831973af384d2456adb5b2214f0dd68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317429"
---
# <a name="adding-functionality-to-the-composite-control"></a>Ajout de fonctionnalités au contrôle composite

Une fois que vous avez inséré tous les contrôles nécessaires dans le contrôle composite, l’étape suivante consiste à ajouter de nouvelles fonctionnalités. Cette nouvelle fonctionnalité se divise généralement en deux catégories :

- Soutenir des interfaces supplémentaires et personnaliser le comportement de votre contrôle composite avec des fonctionnalités spécifiques supplémentaires.

- Manipulation des événements à partir du contrôle ActifX contenu (ou des contrôles).

Aux fins et à la portée de cet article, le reste de cette section se concentre uniquement sur la gestion des événements à partir des contrôles ActiveX.

> [!NOTE]
> Si vous avez besoin de gérer les messages à partir des contrôles Windows, voir [La mise en œuvre d’une fenêtre](../atl/implementing-a-window.md) pour plus d’informations sur le traitement des messages dans ATL.

Après avoir inséré un contrôle ActiveX dans la ressource de dialogue, cliquez à droite sur le contrôle et cliquez sur **Ajouter Event Handler**. Sélectionnez l’événement que vous souhaitez gérer et cliquez sur **Ajouter et modifier**. Le code du gestionnaire d’événements sera ajouté au fichier .h du contrôle.

Les points de connexion pour les contrôles ActiveX sur le contrôle composite sont automatiquement connectés et déconnectés via des appels à [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Voir aussi

[Notions de base des contrôles composites](../atl/atl-composite-control-fundamentals.md)
