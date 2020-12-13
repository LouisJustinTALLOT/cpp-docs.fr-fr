---
description: 'En savoir plus sur : implémentation de CComObjectRootEx'
title: Implémentation de CComObjectRootEx
ms.date: 11/04/2016
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
ms.openlocfilehash: 235d10a8c390311230057da5dda11e5a8f093445
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152839"
---
# <a name="implementing-ccomobjectrootex"></a>Implémentation de CComObjectRootEx

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) est essentiel ; tous les objets ATL doivent avoir une instance de `CComObjectRootEx` ou [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) dans leur héritage. `CComObjectRootEx` fournit le mécanisme `QueryInterface` par défaut en fonction des entrées de la mappe COM.

Via sa mappe COM, les interfaces d'un objet sont exposées à un client quand celui-ci émet une requête pour une interface. La requête est effectuée via `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM.

Vous pouvez entrer des interfaces dans la table de mappage COM avec la macro [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry) ou l’une de ses variantes. Par exemple, le code suivant entre les interfaces `IDispatch`, `IBeeper` et `ISupportErrorInfo` dans le tableau de mappage COM :

[!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]

## <a name="see-also"></a>Voir aussi

[Notions de base des objets COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Macros de mappage COM](../atl/reference/com-map-macros.md)
