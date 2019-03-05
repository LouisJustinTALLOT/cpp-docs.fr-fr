---
title: Utilisation d'un contrôle Tab
ms.date: 11/04/2016
helpviewer_keywords:
- CTabCtrl class [MFC], using
- tab controls [MFC], working with
- tab controls [MFC], using
ms.assetid: 819488e3-4944-44b7-9483-195edb8e0aed
ms.openlocfilehash: 1ff4d57f9968f79a964a57b26fc79d68245c1a3e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262959"
---
# <a name="working-with-a-tab-control"></a>Utilisation d'un contrôle Tab

Le moyen le plus simple d’utiliser un contrôle onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) est en l’ajoutant à une ressource de modèle de boîte de dialogue avec l’éditeur de boîtes de dialogue. Vous pouvez également utiliser un contrôle onglet par lui-même. MFC appelle `InitCommonControls` pour vous. Les tâches principales sont les suivantes :

- [Création du contrôle tab](../mfc/creating-the-tab-control.md)

- [Ajout d’onglets à un contrôle tab](../mfc/adding-tabs-to-a-tab-control.md)

- [Traitement des messages de notification de contrôle tab](../mfc/processing-tab-control-notification-messages.md)

Si l’objet de contrôle d’onglet est incorporé dans une classe de vue ou de la boîte de dialogue parente, le contrôle est détruit lorsque le parent est détruit.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
