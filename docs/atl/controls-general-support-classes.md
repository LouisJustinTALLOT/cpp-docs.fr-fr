---
description: 'En savoir plus sur : contrôles : classes de prise en charge générales'
title: 'Contrôles ATL : classes de prise en charge générales'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- controls [ATL]
- general support classes
ms.assetid: cf73f1d2-7542-48e3-b8c8-9d3abf29f85b
ms.openlocfilehash: a5b147ef2b30f0cc209fdfdabd52b59d7112c475
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148211"
---
# <a name="controls-general-support-classes"></a>Contrôles : classes de prise en charge générales

Les classes suivantes fournissent une prise en charge générale des contrôles ATL :

- [CComControl](../atl/reference/ccomcontrol-class.md) Se compose de fonctions d’assistance et de membres de données essentiels aux contrôles ATL.

- [IOleControlImpl](../atl/reference/iolecontrolimpl-class.md) Fournit les méthodes nécessaires pour les contrôles.

- [IOleObjectImpl](../atl/reference/ioleobjectimpl-class.md) Fournit les méthodes principales par le biais desquelles un conteneur communique avec un contrôle. Gère l’activation et la désactivation des contrôles sur place.

- [IQuickActivateImpl](../atl/reference/iquickactivateimpl-class.md) Combine l’initialisation en un appel unique aux conteneurs d’aide pour éviter les retards lors du chargement des contrôles.

- [IPointerInactiveImpl](../atl/reference/ipointerinactiveimpl-class.md) Fournit une interaction souris minimale pour un contrôle autrement inactif.

## <a name="sample-program"></a>Exemple de programme

[ATLFire](../overview/visual-cpp-samples.md)

## <a name="related-articles"></a>Articles connexes

[Tutoriel ATL](../atl/active-template-library-atl-tutorial.md)

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../atl/atl-class-overview.md)
