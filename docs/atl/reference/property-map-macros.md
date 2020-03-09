---
title: Macros de mappage de propriétés
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
ms.openlocfilehash: 1e2e7235dd924467d9d5e0613a704fedf8340ae4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857182"
---
# <a name="property-map-macros"></a>Macros de mappage de propriétés

Ces macros définissent les mappages et les entrées des propriétés.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Marque le début du mappage de propriétés ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Indique l’étendue, ou dimensions, d’un contrôle ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Entre une description de propriété, un DISPID de propriété et un CLSID de page de propriétés dans le mappage de propriété.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Entre une description de propriété, une propriété DISPID, un CLSID de page de propriétés et un `IDispatch` IID dans le mappage de propriété.|
|[PROP_PAGE](#prop_page)|Entre un CLSID de page de propriétés dans le mappage de propriété.|
|[END_PROP_MAP](#end_prop_map)|Marque la fin du mappage de propriétés ATL.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP

Marque le début de la carte des propriétés de l’objet.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
dans Spécifie la classe qui contient le mappage de propriété.

### <a name="remarks"></a>Notes

Le mappage des propriétés stocke les descriptions des propriétés, les DISPID, les IDENTIFICATEURs des pages de propriétés et les IID `IDispatch`. Les classes [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)et [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) utilisent le mappage des propriétés pour récupérer et définir ces informations.

Lorsque vous créez un objet à l’aide de l’Assistant Projet ATL, l’Assistant crée un mappage de propriétés vide en spécifiant BEGIN_PROP_MAP suivi de [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP n’enregistre pas l’étendue (autrement dit, les dimensions) d’un mappage de propriétés, car un objet qui utilise un mappage de propriété peut ne pas avoir d’interface utilisateur. par conséquent, il n’aurait aucune étendue. Si l’objet est un contrôle ActiveX avec une interface utilisateur, il a une étendue. Dans ce cas, vous devez spécifier [PROP_DATA_ENTRY](#prop_data_entry) dans votre mappage de propriétés pour fournir l’étendue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY

Indique l’étendue, ou dimensions, d’un contrôle ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
dans Description de la propriété.

*member*<br/>
dans Données membres contenant l’étendue ; par exemple, `m_sizeExtent`.

*vt*<br/>
dans Spécifie le type VARIANT de la propriété.

### <a name="remarks"></a>Notes

Cette macro provoque la conservation des données membres spécifiées.

Lorsque vous créez un contrôle ActiveX, l’Assistant insère cette macro après la macro de mappage de propriété [BEGIN_PROP_MAP](#begin_prop_map) et avant la macro de mappage de propriété [END_PROP_MAP](#end_prop_map).

### <a name="example"></a>Exemple

Dans l’exemple suivant, l’étendue de l’objet (`m_sizeExtent`) est persistante.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE

Utilisez cette macro pour entrer une description de propriété, un DISPID de propriété et un CLSID de page de propriétés dans le mappage de propriété de l’objet.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
dans Description de la propriété.

*égal*<br/>
dans DISPID de la propriété.

*identificateur*<br/>
dans CLSID de la page de propriétés associée. Utilisez la valeur spéciale CLSID_NULL pour une propriété qui n’a pas de page de propriétés associée.

*vt*<br/>
dans Type de la propriété.

### <a name="remarks"></a>Notes

La macro PROP_ENTRY n’a pas été sécurisée et dépréciée. Il a été remplacé par PROP_ENTRY_TYPE.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marque le début de la carte des propriétés. la macro [END_PROP_MAP](#end_prop_map) marque la fin.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Semblable à [PROP_ENTRY_TYPE](#prop_entry_type), mais vous permet de spécifier un IID spécifique si votre objet prend en charge plusieurs interfaces doubles.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Paramètres

*szDesc*<br/>
dans Description de la propriété.

*égal*<br/>
dans DISPID de la propriété.

*identificateur*<br/>
dans CLSID de la page de propriétés associée. Utilisez la valeur spéciale CLSID_NULL pour une propriété qui n’a pas de page de propriétés associée.

*iidDispatch*<br/>
dans IID de l’interface double définissant la propriété.

*vt*<br/>
dans Type de la propriété.

### <a name="remarks"></a>Notes

La macro PROP_ENTRY_EX n’a pas été sécurisée et dépréciée. Il a été remplacé par PROP_ENTRY_TYPE_EX.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marque le début de la carte des propriétés. la macro [END_PROP_MAP](#end_prop_map) marque la fin.

### <a name="example"></a>Exemple

L’exemple suivant regroupe des entrées pour `IMyDual1` suivie d’une entrée pour `IMyDual2`. Le regroupement par interface double permet d’améliorer les performances.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>PROP_PAGE

Utilisez cette macro pour entrer un CLSID de page de propriétés dans le mappage de propriété de l’objet.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
dans CLSID d’une page de propriétés.

### <a name="remarks"></a>Notes

PROP_PAGE est semblable à [PROP_ENTRY_TYPE](#prop_entry_type), mais ne nécessite pas de description de propriété ou de DISPID.

> [!NOTE]
>  Si vous avez déjà entré un CLSID avec PROP_ENTRY_TYPE ou [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), vous n’avez pas besoin de créer une entrée supplémentaire avec PROP_PAGE.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marque le début de la carte des propriétés. la macro [END_PROP_MAP](#end_prop_map) marque la fin.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>END_PROP_MAP

Marque la fin du mappage des propriétés de l’objet.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Notes

Lorsque vous créez un objet à l’aide de l’Assistant Projet ATL, l’Assistant crée un mappage de propriétés vide en spécifiant [BEGIN_PROP_MAP](#begin_prop_map) suivi de END_PROP_MAP.

### <a name="example"></a>Exemple

Consultez l’exemple de [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)
