---
title: Fonctions globales de point de connexion
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 6474297f8b9adf04541f7d232fb88d5e52d4e88c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331529"
---
# <a name="connection-point-global-functions"></a>Fonctions globales de point de connexion

Ces fonctions fournissent un support pour les points de connexion et les cartes d’évier.

> [!IMPORTANT]
> Les fonctions énumérées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlAdvise](#atladvise)|Crée une connexion entre le point de connexion d'un objet et le récepteur d'un client.|
|[AtlUnadvise](#atlunadvise)|Termine la connexion `AtlAdvise`établie par .|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Conseille ou déconseille les entrées dans une carte d’évier d’événements.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atladvise"></a><a name="atladvise"></a>AtlAdvise

Crée une connexion entre le point de connexion d'un objet et le récepteur d'un client.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Paramètres

*pUnkCP (en)*<br/>
[dans] Un pointeur `IUnknown` à l’objet avec qui le client veut se connecter.

*Punk*<br/>
[dans] Un pointeur pour `IUnknown`le client .

*Iid*<br/>
[dans] Le GUID du point de connexion. Typiquement, c’est la même chose que l’interface sortante gérée par le point de connexion.

*Pdw*<br/>
[out] Un pointeur vers le cookie qui identifie uniquement la connexion.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’évier implémente l’interface sortante supportée par le point de connexion. Le client utilise le cookie *pdw* pour supprimer la connexion en le passant à [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a>AtlUnadvise (AtlUnadvise)

Termine la connexion établie par [AtlAdvise](#atladvise).

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Paramètres

*pUnkCP (en)*<br/>
[dans] Un pointeur `IUnknown` sur l’objet avec lequel le client est connecté.

*Iid*<br/>
[dans] Le GUID du point de connexion. Typiquement, c’est la même chose que l’interface sortante gérée par le point de connexion.

*dw*<br/>
[dans] Le cookie qui identifie de façon unique la connexion.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a>AtlAdviseSinkMap

Appelez cette fonction pour conseiller ou déconseiller toutes les entrées de la table d'événements du récepteur de l'objet.

> [!IMPORTANT]
> Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
[dans] Un pointeur de l’objet contenant la carte de l’évier.

*bAdvise (en)*<br/>
[dans] VRAI si toutes les entrées d’évier doivent être conseillées ; FALSE si toutes les entrées d’évier doivent être déconseillées.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macros point de connexion](../../atl/reference/connection-point-macros.md)
