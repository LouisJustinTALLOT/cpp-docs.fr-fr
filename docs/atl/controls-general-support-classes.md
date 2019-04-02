---
title: 'Contrôles ATL : Classes de prise en charge générale'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
ms.openlocfilehash: 3f00348ab0c9f25bdd4f6b7a2b05cd4b82ea48e9
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775268"
---
# <a name="controls-general-support-classes"></a>Contrôles : Classes de prise en charge générale

Les classes suivantes fournissent la prise en charge générale pour les contrôles ATL :

- [CComControl](../atl/reference/ccomcontrol-class.md) se compose de membres de données et des fonctions d’assistance qui sont essentielles à des contrôles ATL.

- [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) fournit les méthodes nécessaires pour les contrôles.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) fournit les méthodes principales par le biais duquel un conteneur communique avec un contrôle. Gère l’activation et la désactivation des contrôles de la place.

- [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) combine l’initialisation dans un seul appel pour éviter les retards lors du chargement des contrôles conteneurs.

- [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) fournit une interaction minimale de la souris pour un contrôle inactif dans le cas contraire.

## <a name="sample-program"></a>Exemple de programme

[ATLFire](../overview/visual-cpp-samples.md)

## <a name="related-articles"></a>Articles connexes

[Didacticiel ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)
