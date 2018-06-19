---
title: Implémentation de CComObjectRootEx | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CComObjectRootEx
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class, implementing
- CComObjectRootEx class
ms.assetid: 79630c44-f2df-4e9e-b730-400a0ebfbd2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44c62e7589b9b300ceaa2886760bf2c3d85550ce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356532"
---
# <a name="implementing-ccomobjectrootex"></a>Implémentation de CComObjectRootEx
[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) est essentiel ; tous les objets ATL doivent avoir une instance du `CComObjectRootEx` ou [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) dans leur héritage. `CComObjectRootEx` fournit le mécanisme `QueryInterface` par défaut en fonction des entrées de la mappe COM.  
  
 Via sa mappe COM, les interfaces d'un objet sont exposées à un client quand celui-ci émet une requête pour une interface. La requête est effectuée via `CComObjectRootEx::InternalQueryInterface`. `InternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM.  
  
 Vous pouvez entrer des interfaces dans la table de mappage COM avec le [COM_INTERFACE_ENTRY](reference/com-interface-entry-macros.md#com_interface_entry) (macro) ou une de ses variantes. Par exemple, le code suivant entre les interfaces `IDispatch`, `IBeeper` et `ISupportErrorInfo` dans le tableau de mappage COM :  
  
 [!code-cpp[NVC_ATL_COM#1](../atl/codesnippet/cpp/implementing-ccomobjectrootex_1.h)]  
  
## <a name="see-also"></a>Voir aussi  
 [Notions de base des objets ATL COM](../atl/fundamentals-of-atl-com-objects.md)   
 [Macros de mappage COM](../atl/reference/com-map-macros.md)

