---
title: Ajout de fonctionnalités au contrôle Composite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59ee8047e17efdebbae6ee58ec243057a477caff
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751131"
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

