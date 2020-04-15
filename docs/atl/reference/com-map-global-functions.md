---
title: COM Map Fonctions globales
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: c4ce7c7a68c0744ad65ef4914088fa12d3340628
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326698"
---
# <a name="com-map-global-functions"></a>COM Map Fonctions globales

Ces fonctions fournissent un `IUnknown` soutien aux implémentations de COM Map.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Délégués à `IUnknown` l’objet non-agrégaté.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Génère un code efficace pour `IUnknown`comparer les interfaces par rapport à .|

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a>AtlInternalQueryInterface

Récupère un pointeur vers l'interface demandée.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*pThis*<br/>
[dans] Un pointeur à l’objet qui contient `QueryInterface`la carte COM des interfaces exposées à .

*pEntries (en)*<br/>
[dans] Un éventail `_ATL_INTMAP_ENTRY` de structures qui accèdent à une carte des interfaces disponibles.

*Iid*<br/>
[dans] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface spécifié en *iid*, ou NULL si l’interface n’est pas trouvée.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`AtlInternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM. Si votre objet est `AtlInternalQueryInterface` agrégé, ne délégue pas à l’inconnu extérieur. Vous pouvez entrer des interfaces dans la table de carte COM avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou l’une de ses variantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a>InlineIsEqualIUnknown

Appelez cette fonction, pour le `IUnknown`cas spécial de test pour .

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Paramètres

*rguid1 (en)*<br/>
[dans] Le GUID à `IID_IUnknown`comparer à .

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Com Carte Macros](../../atl/reference/com-map-macros.md)
