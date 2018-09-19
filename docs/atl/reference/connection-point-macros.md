---
title: Macros de Point de connexion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5b025e29c93cffe9c600646a2475f7e3230fd03
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039541"
---
# <a name="connection-point-macros"></a>Macros de Point de connexion

Ces macros définissent les mappages de point de connexion et les entrées.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Marque le début des entrées de mappage de point de connexion.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Entre les points de connexion dans la classe map.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Mais, comme dans CONNECTION_POINT_ENTRY prend un pointeur vers l’iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Marque la fin des entrées de mappage de point de connexion.|  

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP

Marque le début des entrées de mappage de point de connexion.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Paramètres

*x*<br/>
[in] Le nom de la classe contenant les points de connexion.

### <a name="remarks"></a>Notes

Démarrez votre mappage de point de connexion avec la macro BEGIN_CONNECTION_POINT_MAP, ajoutez des entrées pour chacun de vos points de connexion avec le [CONNECTION_POINT_ENTRY](#connection_point_entry) (macro) et effectuer un mappage avec le [END_CONNECTION_ POINT_MAP](#end_connection_point_map) (macro).

Pour plus d’informations sur les points de connexion ATL, consultez l’article [Points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY et CONNECTION_POINT_ENTRY_P

Affiche un point de connexion de l’interface spécifiée dans le mappage de point de connexion afin qu’il soit accessible.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*IID*<br/>
[in] Le GUID de l’interface qui est ajoutée à la carte de point de connexion. 

*piid*<br/>
[in] Pointeur vers le GUID de l’interface en cours adde.

### <a name="remarks"></a>Notes

Entrées de point de connexion dans le mappage sont utilisées par [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). La classe contenant le mappage de point de connexion doit hériter `IConnectionPointContainerImpl`.

Démarrez votre mappage de point de connexion avec le [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) (macro), ajouter des entrées pour chacun de vos points de connexion avec la macro CONNECTION_POINT_ENTRY et effectuer un mappage avec le [END_CONNECTION_ POINT_MAP](#end_connection_point_map) (macro).

Pour plus d’informations sur les points de connexion ATL, consultez l’article [Points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP

Marque la fin des entrées de mappage de point de connexion.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Notes

Démarrer votre mappage de point de connexion avec le [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) (macro), ajouter des entrées pour chacun de vos points de connexion avec le [CONNECTION_POINT_ENTRY](#connection_point_entry) (macro) et effectuer un mappage avec le END_ Macro CONNECTION_POINT_MAP.

Pour plus d’informations sur les points de connexion ATL, consultez l’article [Points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions globales de point de connexion](../../atl/reference/connection-point-global-functions.md)
