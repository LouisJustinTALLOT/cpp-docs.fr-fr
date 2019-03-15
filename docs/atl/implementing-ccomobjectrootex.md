---
title: Implémentation de CComObjectRootEx
ms.date: 11/04/2016
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
ms.openlocfilehash: 80ce9936546b936770d8dedd0ba55f8c05617d37
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809754"
---
# <a name="implementing-ccomobjectrootex"></a>Implémentation de CComObjectRootEx

[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) est essentielle ; tous les objets ATL doivent avoir une instance de `CComObjectRootEx` ou [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) dans leur héritage. `CComObjectRootEx` fournit le mécanisme `QueryInterface` par défaut en fonction des entrées de la mappe COM.

Via sa mappe COM, les interfaces d'un objet sont exposées à un client quand celui-ci émet une requête pour une interface. La requête est effectuée via `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM.

Vous pouvez entrer des interfaces dans la table de mappage COM avec le [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry) macro ou une de ses variantes. Par exemple, le code suivant entre les interfaces `IDispatch`, `IBeeper` et `ISupportErrorInfo` dans le tableau de mappage COM :

[!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]

## <a name="see-also"></a>Voir aussi

[Principes de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Macros de mappage COM](../atl/reference/com-map-macros.md)
