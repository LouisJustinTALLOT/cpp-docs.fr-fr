---
title: Classes de prise en charge de l’interface utilisateur (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.ui
dev_langs:
- C++
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa28c172b4eb22366d2af55d040cb52c9e84a31
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755233"
---
# <a name="ui-support-classes"></a>Classes de prise en charge de l’interface utilisateur

Les classes suivantes fournissent la prise en charge générale de l’interface utilisateur :

- [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) une interface pour le moteur de rendu et de l’analyse HTML de Microsoft.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) fournit les méthodes principales par le biais duquel un conteneur communique avec un contrôle. Gère l’activation et la désactivation des contrôles de la place.

- [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) gère la réactivation des contrôles de la place. Permet à un contrôle sans fenêtre pour recevoir des messages, ainsi que pour participer aux opérations de glisser-déplacer.

- [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) facilite la communication entre un contrôle sur place et de son conteneur.

- [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) permet à un contrôle pour afficher lui-même directement et pour notifier au conteneur des modifications de son affichage. Prend en charge sans scintillement dessin, les contrôles non rectangulaires et transparentes et le test de positionnement.

## <a name="related-articles"></a>Articles connexes

[Didacticiel ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)

