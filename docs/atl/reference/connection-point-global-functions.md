---
title: Fonctions globales de Point de connexion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a1c972be0b4e14d881812195856465dbc7c9e70
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075786"
---
# <a name="connection-point-global-functions"></a>Fonctions globales de Point de connexion

Ces fonctions prennent en charge des points de connexion et le récepteur maps.

> [!IMPORTANT]
>  Les fonctions répertoriées dans le tableau suivant ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlAdvise](#atladvise)|Crée une connexion entre le point de connexion d'un objet et le récepteur d'un client.|
|[AtlUnadvise](#atlunadvise)|Met fin à la connexion établie via `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Conseille ou avertit des entrées dans une table de récepteur d’événements.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="atladvise"></a>  AtlAdvise

Crée une connexion entre le point de connexion d'un objet et le récepteur d'un client.

> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Paramètres

*pUnkCP*<br/>
[in] Un pointeur vers le `IUnknown` de l’objet, le client souhaite se connecter avec.

*pUnk*<br/>
[in] Un pointeur vers le client `IUnknown`.

*IID*<br/>
[in] Le GUID du point de connexion. En règle générale, cela est identique à l’interface sortante managée par le point de connexion.

*PDW*<br/>
[out] Pointeur vers le cookie qui identifie de façon unique la connexion.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le récepteur implémente l’interface sortante pris en charge par le point de connexion. Le client utilise le *pdw* cookie à supprimer de la connexion en le passant à [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>  AtlUnadvise

Met fin à la connexion établie via [AtlAdvise](#atladvise).

> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Paramètres

*pUnkCP*<br/>
[in] Un pointeur vers le `IUnknown` de l’objet auquel le client est connecté avec.

*IID*<br/>
[in] Le GUID du point de connexion. En règle générale, cela est identique à l’interface sortante managée par le point de connexion.

*entrepôt de données*<br/>
[in] Le cookie qui identifie de façon unique la connexion.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>  AtlAdviseSinkMap

Appelez cette fonction pour conseiller ou déconseiller toutes les entrées de la table d'événements du récepteur de l'objet.

> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Paramètres

*pT*<br/>
[in] Pointeur vers l’objet qui contient la table de récepteur.

*bAdvise*<br/>
[in] TRUE si toutes les entrées de récepteur doivent être avertie ; FALSE si toutes les entrées de récepteur doivent être arrêter.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macros de point de connexion](../../atl/reference/connection-point-macros.md)
