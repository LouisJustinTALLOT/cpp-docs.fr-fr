---
description: 'En savoir plus sur : fonctions globales de mappage COM'
title: Fonctions globales de mappage COM
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: ee502a68a0a3b21849d2fabdadcc9ecbbcc1602d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141334"
---
# <a name="com-map-global-functions"></a>Fonctions globales de mappage COM

Ces fonctions assurent la prise en charge des implémentations de mappage COM `IUnknown` .

|Fonction|Description|
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Délègue au `IUnknown` d’un objet qui n’est pas agrégé.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Génère du code efficace pour la comparaison des interfaces par rapport à `IUnknown` .|

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a> AtlInternalQueryInterface

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
dans Pointeur vers l’objet qui contient la table COM des interfaces exposées à `QueryInterface` .

*pEntries*<br/>
dans Tableau de `_ATL_INTMAP_ENTRY` structures qui accèdent à une carte des interfaces disponibles.

*vaut*<br/>
dans GUID de l’interface demandée.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface spécifié dans *IID*, ou null si l’interface est introuvable.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`AtlInternalQueryInterface` gère seulement des interfaces dans le tableau de mappage COM. Si votre objet est agrégé, `AtlInternalQueryInterface` ne délègue pas à l’objet externe inconnu. Vous pouvez entrer des interfaces dans le tableau de mappage COM avec la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou l’une de ses variantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a> InlineIsEqualIUnknown

Appelez cette fonction pour le cas particulier de test de `IUnknown` .

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Paramètres

*rguid1*<br/>
dans GUID avec lequel effectuer la comparaison `IID_IUnknown` .

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macros de mappage COM](../../atl/reference/com-map-macros.md)
