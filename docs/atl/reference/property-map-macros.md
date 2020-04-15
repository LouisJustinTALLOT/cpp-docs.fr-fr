---
title: Macros carte de propriété
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
ms.openlocfilehash: 56fdb02939a99e396b9000705753e2475b80f6dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326089"
---
# <a name="property-map-macros"></a>Macros carte de propriété

Ces macros définissent les cartes et les entrées de propriété.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Marque le début de la carte de propriété ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Indique l’étendue, ou les dimensions, d’un contrôle ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Entre une description de propriété, une disIP de propriété et une page de propriété CLSID dans la carte de propriété.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Entre une description de propriété, la propriété DISPID, la page de propriété CLSID, et `IDispatch` IID dans la carte de propriété.|
|[PROP_PAGE](#prop_page)|Entre une page de propriété CLSID dans la carte de propriété.|
|[END_PROP_MAP](#end_prop_map)|Marque la fin de la carte de propriété ATL.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP

Marque le début de la carte des biens de l’objet.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
[dans] Spécifie la classe contenant la carte de propriété.

### <a name="remarks"></a>Notes

La carte de propriété stocke les descriptions de propriété, les `IDispatch` DISPID de propriété, les CLSID de page de propriété, et les CLI. Classes [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), et [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) utiliser la carte de la propriété pour récupérer et définir ces informations.

Lorsque vous créez un objet avec le assistant de projet ATL, l’assistant créera une carte de propriété vide en spécifiant BEGIN_PROP_MAP suivie [de END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP n’enregistre pas l’étendue (c’est-à-dire les dimensions) d’une carte de propriété, parce qu’un objet utilisant une carte de propriété peut ne pas avoir une interface utilisateur, de sorte qu’il n’aurait aucune mesure. Si l’objet est un contrôle ActiveX avec une interface utilisateur, il a une étendue. Dans ce cas, vous devez spécifier [PROP_DATA_ENTRY](#prop_data_entry) dans votre carte de propriété pour fournir la mesure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY

Indique l’étendue, ou les dimensions, d’un contrôle ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
[dans] La description de la propriété.

*Membre*<br/>
[dans] Le membre des données contenant l’étendue; par exemple, `m_sizeExtent`.

*vt*<br/>
[dans] Spécifie le type VARIANT de la propriété.

### <a name="remarks"></a>Notes

Cette macro provoque la persistance du membre des données spécifiés.

Lorsque vous créez un contrôle ActiveX, l’assistant insère cette macro après la carte de propriété macro [BEGIN_PROP_MAP](#begin_prop_map) et avant la carte de propriété macro [END_PROP_MAP](#end_prop_map).

### <a name="example"></a>Exemple

Dans l’exemple suivant, l’étendue de l’objet (`m_sizeExtent`) est en cours de persistance.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE

Utilisez cette macro pour entrer une description de propriété, disPID de propriété, et la page de propriété CLSID dans la carte de propriété de l’objet.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
[dans] La description de la propriété.

*dispid*<br/>
[dans] La disIP de la propriété.

*clsid*<br/>
[dans] Le CLSID de la page de propriété associée. Utilisez la valeur spéciale CLSID_NULL pour une propriété qui n’a pas de page de propriété associée.

*vt*<br/>
[dans] Le type de propriété.

### <a name="remarks"></a>Notes

La macro PROP_ENTRY était précaire et dépréciée. Il a été remplacé par PROP_ENTRY_TYPE.

La [macro BEGIN_PROP_MAP](#begin_prop_map) marque le début de la carte de la propriété; [l’END_PROP_MAP](#end_prop_map) macro marque la fin.

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Semblable à [PROP_ENTRY_TYPE](#prop_entry_type), mais vous permet de spécifier un IID particulier si votre objet prend en charge plusieurs interfaces doubles.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
[dans] La description de la propriété.

*dispid*<br/>
[dans] La disIP de la propriété.

*clsid*<br/>
[dans] Le CLSID de la page de propriété associée. Utilisez la valeur spéciale CLSID_NULL pour une propriété qui n’a pas de page de propriété associée.

*iidDispatch*<br/>
[dans] L’IID de la double interface définissant la propriété.

*vt*<br/>
[dans] Le type de propriété.

### <a name="remarks"></a>Notes

La macro PROP_ENTRY_EX était précaire et dépréciée. Il a été remplacé par PROP_ENTRY_TYPE_EX.

La [macro BEGIN_PROP_MAP](#begin_prop_map) marque le début de la carte de la propriété; [l’END_PROP_MAP](#end_prop_map) macro marque la fin.

### <a name="example"></a>Exemple

L’exemple suivant `IMyDual1` regroupe les entrées `IMyDual2`pour suivie d’une entrée pour . Le regroupement par double interface améliorera les performances.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a>PROP_PAGE

Utilisez cette macro pour entrer une page de propriété CLSID dans la carte de propriété de l’objet.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[dans] Le CLSID d’une page de propriété.

### <a name="remarks"></a>Notes

PROP_PAGE est similaire à [PROP_ENTRY_TYPE,](#prop_entry_type)mais ne nécessite pas de description de propriété ou DISPID.

> [!NOTE]
> Si vous avez déjà entré un CLSID avec PROP_ENTRY_TYPE ou [PROP_ENTRY_TYPE_EX,](#prop_entry_type_ex)vous n’avez pas besoin de faire une entrée supplémentaire avec PROP_PAGE.

La [macro BEGIN_PROP_MAP](#begin_prop_map) marque le début de la carte de la propriété; [l’END_PROP_MAP](#end_prop_map) macro marque la fin.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a>END_PROP_MAP

Marque la fin de la carte des biens de l’objet.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Notes

Lorsque vous créez un objet avec l’assistant de projet ATL, l’assistant créera une carte de propriété vide en spécifiant [BEGIN_PROP_MAP](#begin_prop_map) suivie d’END_PROP_MAP.

### <a name="example"></a>Exemple

Voir l’exemple pour [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
