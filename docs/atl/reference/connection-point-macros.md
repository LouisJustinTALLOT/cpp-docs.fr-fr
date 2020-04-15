---
title: Macros point de connexion
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 361cf6ab2c7af142c1d57c002681ccf6e4a87bda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331493"
---
# <a name="connection-point-macros"></a>Macros point de connexion

Ces macros définissent les cartes et les entrées des points de connexion.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Marque le début des entrées de carte de point de connexion.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Entre les points de connexion dans la carte.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Studio visuel 2017) Semblable à CONNECTION_POINT_ENTRY mais prend un pointeur à iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Marque la fin des entrées de carte de point de connexion.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

Marque le début des entrées de carte de point de connexion.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Paramètres

*X*<br/>
[dans] Le nom de la classe contenant les points de connexion.

### <a name="remarks"></a>Notes

Démarrez votre carte de point de connexion avec la macro BEGIN_CONNECTION_POINT_MAP, ajoutez des entrées pour chacun de vos points de connexion avec la macro [CONNECTION_POINT_ENTRY,](#connection_point_entry) et complétez la carte avec la macro [END_CONNECTION_POINT_MAP.](#end_connection_point_map)

Pour plus d’informations sur les points de connexion dans ATL, voir l’article [Points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY et CONNECTION_POINT_ENTRY_P

Entre un point de connexion pour l’interface spécifiée dans la carte des points de connexion afin qu’elle puisse être consultée.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Le GUID de l’interface étant ajouté à la carte des points de connexion.

*piid*<br/>
[dans] Pointeur sur le GUID de l’interface en cours adde.

### <a name="remarks"></a>Notes

Les entrées de points de connexion dans la carte sont utilisées par [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). La classe contenant la carte `IConnectionPointContainerImpl`des points de connexion doit hériter de .

Démarrez votre carte de point de connexion avec la macro [BEGIN_CONNECTION_POINT_MAP,](#begin_connection_point_map) ajoutez des entrées pour chacun de vos points de connexion avec la macro CONNECTION_POINT_ENTRY, et complétez la carte avec la macro [END_CONNECTION_POINT_MAP.](#end_connection_point_map)

Pour plus d’informations sur les points de connexion dans ATL, voir l’article [Points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

Marque la fin des entrées de carte de point de connexion.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Notes

Démarrez votre carte de point de connexion avec la macro [BEGIN_CONNECTION_POINT_MAP,](#begin_connection_point_map) ajoutez des entrées pour chacun de vos points de connexion avec la macro [CONNECTION_POINT_ENTRY,](#connection_point_entry) et complétez la carte avec la macro END_CONNECTION_POINT_MAP.

Pour plus d’informations sur les points de connexion dans ATL, voir l’article [Points de connexion](../../atl/atl-connection-points.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions globales de point de connexion](../../atl/reference/connection-point-global-functions.md)
