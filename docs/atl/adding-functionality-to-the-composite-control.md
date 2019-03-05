---
title: Ajout de fonctionnalités au contrôle Composite
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 9ad7ef3d80579804ac614fbefac1a042a9cf2fba
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299762"
---
# <a name="adding-functionality-to-the-composite-control"></a>Ajout de fonctionnalités au contrôle Composite

Une fois que vous avez inséré les contrôles nécessaires dans le contrôle composite, l’étape suivante implique l’ajout de nouvelles fonctionnalités. Cette nouvelle fonctionnalité se divise généralement en deux catégories :

- Prise en charge des interfaces supplémentaires et personnaliser le comportement de votre contrôle composite avec des fonctionnalités supplémentaires spécifiques.

- Gestion des événements à partir de la relation contenant-contenu contrôle ActiveX (ou contrôles).

Pour l’objectif et la portée de cet article, le reste de cette section se concentre uniquement sur la gestion des événements à partir de contrôles ActiveX.

> [!NOTE]
>  Si vous avez besoin gérer les messages à partir de contrôles de Windows, consultez [implémentation d’une fenêtre](../atl/implementing-a-window.md) pour plus d’informations sur la gestion des messages dans ATL.

Après avoir inséré un contrôle ActiveX dans la ressource de boîte de dialogue, cliquez sur le contrôle, puis sur **ajouter un gestionnaire d’événements**. Sélectionnez l’événement que vous souhaitez gérer, puis cliquez sur **ajouter et modifier des**. Le code de gestionnaire d’événements sera ajouté au fichier .h du contrôle.

Points de connexion pour les contrôles ActiveX sur le contrôle composite sont automatiquement connectés et déconnectés via des appels à [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

## <a name="see-also"></a>Voir aussi

[Notions fondamentales du contrôle composite](../atl/atl-composite-control-fundamentals.md)
