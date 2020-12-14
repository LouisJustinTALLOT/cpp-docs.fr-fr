---
description: 'En savoir plus sur : Rubber-Banding et les traceurs'
title: Bande élastique et dispositifs de suivi
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
ms.openlocfilehash: 5d641e7553a2891e0319484558f025c6998f9693
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217833"
---
# <a name="rubber-banding-and-trackers"></a>Bande élastique et dispositifs de suivi

Une autre fonctionnalité fournie avec les dispositifs de suivi est la sélection « bande en caoutchouc », qui permet à un utilisateur de sélectionner plusieurs éléments OLE en faisant glisser un rectangle de dimensionnement autour des éléments à sélectionner. Quand l’utilisateur relâche le bouton gauche de la souris, les éléments de la région sélectionnée par l’utilisateur sont sélectionnés et peuvent être manipulés par l’utilisateur. Par exemple, l’utilisateur peut faire glisser la sélection dans une autre application de conteneur.

L’implémentation de cette fonctionnalité nécessite du code supplémentaire dans la fonction du gestionnaire de WM_LBUTTONDOWN de votre application.

L’exemple de code suivant implémente une sélection de bandes en caoutchouc et des fonctionnalités supplémentaires.

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

Si vous souhaitez autoriser l’orientation réversible du dispositif de suivi lors de la bande de caoutchouc, vous devez appeler [CRectTracker :: TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) avec le troisième paramètre défini sur **true**. N’oubliez pas que l’autorisation de l’orientation réversible entraîne parfois l’inversion de [CRectTracker :: m_rect](../mfc/reference/crecttracker-class.md#m_rect) . Cela peut être corrigé par un appel à [CRect :: NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).

Pour plus d’informations, consultez [éléments clients du conteneur](../mfc/containers-client-items.md) et [glisser-déplacer OLE : personnaliser le glisser-déplacer](../mfc/drag-and-drop-ole.md#customize-drag-and-drop).

## <a name="see-also"></a>Voir aussi

[Dispositifs de suivi : implémentation de dispositifs de suivi dans votre application OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker (classe)](../mfc/reference/crecttracker-class.md)
