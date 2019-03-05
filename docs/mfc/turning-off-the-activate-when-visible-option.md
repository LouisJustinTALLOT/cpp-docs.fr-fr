---
title: Désactivation de l'option Actif quand il est visible
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: a7afe9617aa356916fe184828d7684f228293e39
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304728"
---
# <a name="turning-off-the-activate-when-visible-option"></a>Désactivation de l'option Actif quand il est visible

Un contrôle possède deux états : actives et inactives. En règle générale, ces États ont été différenciés par indique si le contrôle avait une fenêtre. Un contrôle actif avait une fenêtre ; un contrôle inactif n’ont pas. Avec l’introduction de l’activation sans fenêtre, cette distinction n’est plus universelle, mais s’applique toujours à de nombreux contrôles.

Par rapport au reste de l’initialisation généralement effectuée par un contrôle ActiveX, la création d’une fenêtre est une opération très coûteuse. Dans l’idéal, un contrôle doit retarder créer sa fenêtre jusqu'à ce que cela est absolument nécessaire.

De nombreux contrôles n’avez pas besoin d’être actives pendant tout ce temps qu'ils sont visibles dans un conteneur. Souvent, un contrôle peut rester dans l’état inactif jusqu'à ce que l’utilisateur effectue une opération qui requiert qu’elle soit active (par exemple, en cliquant avec la souris ou en appuyant sur la touche TAB). Pour qu’un contrôle reste inactif jusqu'à ce que le conteneur doit l’activer, supprimez le **OLEMISC_ACTIVATEWHENVISIBLE** indicateur à partir d’indicateurs divers du contrôle :

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

Le **OLEMISC_ACTIVATEWHENVISIBLE** indicateur est omis automatiquement si vous désactivez le **activer quand il est Visible** option dans le [paramètres de contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) page du ActiveX MFC Assistant contrôle lorsque vous créez votre contrôle.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : Optimisation](../mfc/mfc-activex-controls-optimization.md)
