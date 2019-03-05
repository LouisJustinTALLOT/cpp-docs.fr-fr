---
title: Fonctions globales de mappage COM
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: 75d081674fa4b63e66f1296834d3de305665ab9a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271617"
---
# <a name="com-map-global-functions"></a>Fonctions globales de mappage COM

Ces fonctions prennent en charge pour le mappage COM `IUnknown` implémentations.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Délègue à la `IUnknown` d’un objet non regroupées en agrégats.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Génère un code efficace pour la comparaison des interfaces à `IUnknown`.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase.h

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface

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
[in] Un pointeur vers l’objet qui contient le mappage COM des interfaces exposées à `QueryInterface`.

*pEntries*<br/>
[in] Un tableau de `_ATL_INTMAP_ENTRY` structures qui accèdent à une carte des interfaces disponibles.

*iid*<br/>
[in] Le GUID de l’interface demandée.

*ppvObject*<br/>
[out] Un pointeur vers le pointeur d’interface spécifié dans *iid*, ou NULL si l’interface est introuvable.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

`AtlInternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM. Si votre objet est agrégée, `AtlInternalQueryInterface` ne pas déléguer à inconnu externe. Vous pouvez entrer des interfaces dans la table de mappage COM avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou une de ses variantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown

Appelez cette fonction, pour les cas de test pour `IUnknown`.

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Paramètres

*rguid1*<br/>
[in] Le GUID à comparer à `IID_IUnknown`.

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macros de mappage COM](../../atl/reference/com-map-macros.md)
