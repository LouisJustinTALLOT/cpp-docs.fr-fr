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
ms.openlocfilehash: 0313e93ee82bb96f3bfe08e45f70ccfee30dbee6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417760"
---
# <a name="connection-point-global-functions"></a>Fonctions globales de point de connexion

Ces fonctions assurent la prise en charge des points de connexion et des mappages de récepteur.

> [!IMPORTANT]
>  Les fonctions listées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlAdvise](#atladvise)|Crée une connexion entre le point de connexion d'un objet et le récepteur d'un client.|
|[AtlUnadvise](#atlunadvise)|Met fin à la connexion établie par le biais de `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Conseille ou déconseilne des entrées dans une table de récepteurs d’événements.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

##  <a name="atladvise"></a>AtlAdvise

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
dans Pointeur vers l' `IUnknown` de l’objet avec lequel le client souhaite se connecter.

*pUnk*<br/>
dans Pointeur vers le `IUnknown`du client.

*vaut*<br/>
dans GUID du point de connexion. En règle générale, il s’agit de l’interface sortante gérée par le point de connexion.

*PDW*<br/>
à Pointeur vers le cookie qui identifie de façon unique la connexion.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le récepteur implémente l’interface sortante prise en charge par le point de connexion. Le client utilise le cookie *PDW* pour supprimer la connexion en le passant à [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>AtlUnadvise

Met fin à la connexion établie par le biais de [AtlAdvise](#atladvise).

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
dans Pointeur vers l' `IUnknown` de l’objet avec lequel le client est connecté.

*vaut*<br/>
dans GUID du point de connexion. En règle générale, il s’agit de l’interface sortante gérée par le point de connexion.

*dw*<br/>
dans Cookie qui identifie de façon unique la connexion.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap

Appelez cette fonction pour conseiller ou déconseiller toutes les entrées de la table d'événements du récepteur de l'objet.

> [!IMPORTANT]
>  Cette fonction ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Paramètres

*Unis*<br/>
dans Pointeur vers l’objet contenant la table réceptrice.

*bAdvise*<br/>
dans TRUE si toutes les entrées de récepteur doivent être notifiées ; FALSe si toutes les entrées de récepteur ne doivent pas être avisées.

### <a name="return-value"></a>Valeur de retour

Valeur HRESULT standard.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macros de point de connexion](../../atl/reference/connection-point-macros.md)
