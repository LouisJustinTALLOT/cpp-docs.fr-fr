---
title: 'Contrôles ATL : Classes de prise en charge générale'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
ms.openlocfilehash: c3d6f7588e333a27a8bc766d982660aaa4d984c9
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818607"
---
# <a name="controls-general-support-classes"></a>Contrôles : Classes de prise en charge générale

Les classes suivantes fournissent la prise en charge générale pour les contrôles ATL :

- [CComControl](../atl/reference/ccomcontrol-class.md) se compose de membres de données et des fonctions d’assistance qui sont essentielles à des contrôles ATL.

- [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) fournit les méthodes nécessaires pour les contrôles.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) fournit les méthodes principales par le biais duquel un conteneur communique avec un contrôle. Gère l’activation et la désactivation des contrôles de la place.

- [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) combine l’initialisation dans un seul appel pour éviter les retards lors du chargement des contrôles conteneurs.

- [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) fournit une interaction minimale de la souris pour un contrôle inactif dans le cas contraire.

## <a name="sample-program"></a>Exemple de programme

[ATLFire](../visual-cpp-samples.md)

## <a name="related-articles"></a>Articles connexes

[Didacticiel ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../atl/atl-class-overview.md)
