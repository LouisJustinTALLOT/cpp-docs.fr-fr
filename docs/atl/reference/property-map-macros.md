---
title: Macros de mappage de propriété | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
dev_langs:
- C++
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: caa298ebbb96b04145bf2beb52f93838708ae50b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50088900"
---
# <a name="property-map-macros"></a>Macros de mappage de propriété

Ces macros définissent les mappages des propriétés et des entrées.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Marque le début de la table de propriétés ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Indique l’étendue ou dimensions, d’un contrôle ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Insère une page de description, propriété DISPID et propriété des propriétés CLSID dans le mappage de propriété.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Insère une description de la propriété propriété DISPID, CLSID, page des propriétés et `IDispatch` IID dans le mappage de propriété.|
|[PROP_PAGE](#prop_page)|Insère une page de propriétés CLSID dans le mappage de propriété.|
|[END_PROP_MAP](#end_prop_map)|Marque la fin de la table de propriétés ATL.|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="begin_prop_map"></a>  BEGIN_PROP_MAP

Marque le début du mappage des propriétés de l’objet.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
[in] Spécifie la classe contenant le mappage de propriété.

### <a name="remarks"></a>Notes

Le mappage de propriété stocke les descriptions de propriété, propriété DISPID, CLSID, page des propriétés et `IDispatch` IID. Classes [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), et [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)utiliser le mappage de propriété pour récupérer et définir ces informations.

Lorsque vous créez un objet avec l’Assistant Projet ATL, l’Assistant va créer un mappage de propriétés vide en spécifiant BEGIN_PROP_MAP suivie [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP n’enregistre pas le niveau (autrement dit, les dimensions) d’un mappage de propriété, car un objet à l’aide d’un mappage de propriété n’est peut-être pas une interface utilisateur, il serait donc aucune mesure. Si l’objet est un contrôle ActiveX avec une interface utilisateur, il a une étendue. Dans ce cas, vous devez spécifier [PROP_DATA_ENTRY](#prop_data_entry) dans votre mappage de propriété pour fournir l’étendue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>  PROP_DATA_ENTRY

Indique l’étendue ou dimensions, d’un contrôle ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
[in] La description de la propriété.

*member*<br/>
[in] Le membre de données contenant l’étendue ; par exemple, `m_sizeExtent`.

*vt*<br/>
[in] Spécifie le type VARIANT de la propriété.

### <a name="remarks"></a>Notes

Cette macro provoque la donnée membre spécifiée à rendre persistant.

Lorsque vous créez un contrôle ActiveX, l’Assistant insère cette macro après la macro de mappage de propriété [BEGIN_PROP_MAP](#begin_prop_map) et avant la macro de mappage de propriété [END_PROP_MAP](#end_prop_map).

### <a name="example"></a>Exemple

Dans l’exemple suivant, l’étendue de l’objet (`m_sizeExtent`) est persistant.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>  PROP_ENTRY_TYPE

Utilisez cette macro à entrer une page de description, propriété DISPID et propriété des propriétés CLSID dans le mappage des propriétés de l’objet.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
[in] La description de la propriété.

*DISPID*<br/>
[in] DISPID de la propriété.

*clsid*<br/>
[in] Le CLSID de la page de propriété associée. Utilisez la valeur spéciale CLSID_NULL pour une propriété qui n’a pas d’une page de propriété associée.

*vt*<br/>
[in] Le type de propriété.

### <a name="remarks"></a>Notes

La macro PROP_ENTRY était non sécurisé et déconseillées. Elle a été remplacée par PROP_ENTRY_TYPE.

Le [BEGIN_PROP_MAP](#begin_prop_map) macro marque le début du mappage de propriété ; le [END_PROP_MAP](#end_prop_map) macro marque la fin.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>  PROP_ENTRY_TYPE_EX

Semblable à [PROP_ENTRY_TYPE](#prop_entry_type), mais vous permet d’indiquer un IID spécifique si votre objet prend en charge les interfaces doubles multiples.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
[in] La description de la propriété.

*DISPID*<br/>
[in] DISPID de la propriété.

*clsid*<br/>
[in] Le CLSID de la page de propriété associée. Utilisez la valeur spéciale CLSID_NULL pour une propriété qui n’a pas d’une page de propriété associée.

*iidDispatch*<br/>
[in] IID de l’interface double définissant la propriété.

*vt*<br/>
[in] Le type de propriété.

### <a name="remarks"></a>Notes

La macro PROP_ENTRY_EX était non sécurisé et déconseillées. Elle a été remplacée par PROP_ENTRY_TYPE_EX.

Le [BEGIN_PROP_MAP](#begin_prop_map) macro marque le début du mappage de propriété ; le [END_PROP_MAP](#end_prop_map) macro marque la fin.

### <a name="example"></a>Exemple

L’exemple suivant regroupe les entrées pour `IMyDual1` suivie d’une entrée pour `IMyDual2`. Le regroupement par interface double améliore les performances.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>  PROP_PAGE

Utilisez cette macro à entrer une page de propriétés CLSID dans le mappage des propriétés de l’objet.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[in] Le CLSID d’une page de propriétés.

### <a name="remarks"></a>Notes

PROP_PAGE est similaire à [PROP_ENTRY_TYPE](#prop_entry_type), mais ne nécessite pas une description de la propriété ou le DISPID.

> [!NOTE]
>  Si vous avez déjà entré un CLSID avec PROP_ENTRY_TYPE ou [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), vous n’avez pas besoin de créer une entrée supplémentaire avec PROP_PAGE.

Le [BEGIN_PROP_MAP](#begin_prop_map) macro marque le début du mappage de propriété ; le [END_PROP_MAP](#end_prop_map) macro marque la fin.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>  END_PROP_MAP

Marque la fin de mappage des propriétés de l’objet.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Notes

Lorsque vous créez un objet avec l’Assistant Projet ATL, l’Assistant va créer un mappage de propriétés vide en spécifiant [BEGIN_PROP_MAP](#begin_prop_map) suivie END_PROP_MAP.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
