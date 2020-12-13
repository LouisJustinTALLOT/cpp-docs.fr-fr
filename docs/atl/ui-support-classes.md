---
description: 'En savoir plus sur : classes de prise en charge de l’interface utilisateur'
title: Classes de prise en charge de l’interface utilisateur (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- user interfaces, support classes
- user interfaces, ATL classes
ms.assetid: 313dfc95-308a-4118-b919-5a3c3673b865
ms.openlocfilehash: d8bc345db05ef886c2a054356ae6bd8d299c8045
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138253"
---
# <a name="ui-support-classes"></a>Classes de prise en charge de l’interface utilisateur

Les classes suivantes fournissent une prise en charge générale de l’interface utilisateur :

- [IDocHostUIHandlerDispatch](../atl/reference/idochostuihandlerdispatch-interface.md) Interface au moteur d’analyse et de rendu HTML de Microsoft.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) Fournit les méthodes principales par le biais desquelles un conteneur communique avec un contrôle. Gère l’activation et la désactivation des contrôles sur place.

- [IOleInPlaceObjectWindowlessImpl](../atl/reference/ioleinplaceobjectwindowlessimpl-class.md) Gère la réactivation des contrôles sur place. Permet à un contrôle sans fenêtre de recevoir des messages, ainsi que de participer à des opérations de glisser-déplacer.

- [IOleInPlaceActiveObjectImpl](../atl/reference/ioleinplaceactiveobjectimpl-class.md) Aide à la communication entre un contrôle sur place et son conteneur.

- [IViewObjectExImpl](../atl/reference/iviewobjecteximpl-class.md) Permet à un contrôle de s’afficher directement et d’informer le conteneur des modifications apportées à son affichage. Prend en charge le dessin sans scintillement, les contrôles non rectangulaires et transparents, ainsi que le test de positionnement.

## <a name="related-articles"></a>Articles connexes

[Tutoriel ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../atl/atl-class-overview.md)
