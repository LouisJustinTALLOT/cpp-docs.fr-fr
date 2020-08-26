---
title: Macros de point de connexion
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 6c716ad85ecb458b4be418a7e8554687dd19f3d8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833515"
---
# <a name="connection-point-macros"></a>Macros de point de connexion

Ces macros définissent les mappages et les entrées des points de connexion.

|Macro|Description|
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Marque le début des entrées de mappage de point de connexion.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Entre des points de connexion dans la carte.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Semblable à CONNECTION_POINT_ENTRY, mais prend un pointeur vers iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Marque la fin des entrées de mappage de point de connexion.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom. h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a> BEGIN_CONNECTION_POINT_MAP

Marque le début des entrées de mappage de point de connexion.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Paramètres

*x*<br/>
dans Nom de la classe contenant les points de connexion.

### <a name="remarks"></a>Notes

Démarrez votre carte de point de connexion à l’aide de la macro BEGIN_CONNECTION_POINT_MAP, ajoutez des entrées pour chacun de vos points de connexion avec la macro [CONNECTION_POINT_ENTRY](#connection_point_entry) et complétez la carte avec la macro [END_CONNECTION_POINT_MAP](#end_connection_point_map) .

Pour plus d’informations sur les points de connexion dans ATL, consultez l’article [points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a> CONNECTION_POINT_ENTRY et CONNECTION_POINT_ENTRY_P

Entre un point de connexion pour l’interface spécifiée dans la carte de points de connexion afin de pouvoir y accéder.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans GUID de l’interface ajoutée à la table des points de connexion.

*piid*<br/>
dans Pointeur vers le GUID de l’interface qui est ajoute.

### <a name="remarks"></a>Notes

Les entrées de point de connexion dans le mappage sont utilisées par [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). La classe qui contient la table de points de connexion doit hériter de `IConnectionPointContainerImpl` .

Démarrez votre carte de point de connexion à l’aide de la macro [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) , ajoutez des entrées pour chacun de vos points de connexion avec la macro CONNECTION_POINT_ENTRY et complétez la carte avec la macro [END_CONNECTION_POINT_MAP](#end_connection_point_map) .

Pour plus d’informations sur les points de connexion dans ATL, consultez l’article [points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a> END_CONNECTION_POINT_MAP

Marque la fin des entrées de mappage de point de connexion.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Notes

Démarrez votre carte de point de connexion à l’aide de la macro [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) , ajoutez des entrées pour chacun de vos points de connexion avec la macro [CONNECTION_POINT_ENTRY](#connection_point_entry) et complétez la carte avec la macro END_CONNECTION_POINT_MAP.

Pour plus d’informations sur les points de connexion dans ATL, consultez l’article [points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions globales de point de connexion](../../atl/reference/connection-point-global-functions.md)
