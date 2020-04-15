---
title: DHTML, tables d'événements
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: 30c755b2901374cffab3ce91d0683811ef6624b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365807"
---
# <a name="dhtml-event-maps"></a>DHTML, tables d'événements

Les macros suivantes peuvent être utilisées pour gérer les événements DHTML.

## <a name="dhtml-event-map-macros"></a>DHTML Event Map Macros

Les macros suivantes peuvent être utilisées pour gérer les événements DHTML dans les classes [dérivées de CDHtmlDialog.](../../mfc/reference/cdhtmldialog-class.md)

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Marque le début de la carte des événements DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Marque le début de la carte des événements DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Déclare la carte de l’événement DHTML.|
|[DHTML_EVENT](#dhtml_event)|Utilisé pour gérer un événement au niveau du document pour un seul élément HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Utilisé pour gérer un événement tiré par un contrôle ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Utilisé pour gérer un événement au niveau du document pour tous les éléments HTML avec une classe CSS particulière.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Utilisé pour gérer un événement au niveau de l’élément.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Utilisé pour `onafterupdate` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Utilisé pour `onbeforeupdate` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Utilisé pour `onblur` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Utilisé pour `onchange` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Utilisé pour `onclick` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Utilisé pour `ondataavailable` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Utilisé pour `ondatasetchanged` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Utilisé pour `ondatasetcomplete` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Utilisé pour `ondblclick` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Utilisé pour `ondragstart` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Utilisé pour `onerrorupdate` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Utilisé pour `onfilterchange` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Utilisé pour `onfocus` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Utilisé pour `onhelp` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Utilisé pour `onkeydown` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Utilisé pour `onkeypress` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Utilisé pour `onkeyup` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Utilisé pour `onmousedown` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Utilisé pour `onmousemove` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Utilisé pour `onmouseout` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Utilisé pour `onmouseover` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Utilisé pour `onmouseup` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Utilisé pour `onresize` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Utilisé pour `onrowenter` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Utilisé pour `onrowexit` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Utilisé pour `onselectstart` gérer l’événement à partir d’un élément HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Utilisé pour gérer un événement au niveau du document pour tous les éléments avec une balise HTML particulière.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Marque la fin de la carte de l’événement DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Marque la fin de la carte de l’événement DHTML. |

## <a name="url-event-map-macros"></a>URL Event Map Macros

Les macros suivantes peuvent être utilisées pour gérer les événements DHTML dans les classes dérivées [de CMultiPageDHtmlDialog.](../../mfc/reference/cmultipagedhtmldialog-class.md)

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Marque le début de la carte des événements DHTML et URL multipages.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Marque le début d’une carte d’événement DHTML intégrée.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Marque le début d’une carte d’entrée d’événement URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Déclare la carte des événements DHTML et URL multipage.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Marque la fin de la carte des événements DHTML et URL multipages.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Marque la fin d’une carte d’événement DHTML intégrée.|
|[END_URL_ENTRIES](#end_url_entries)|Marque la fin d’une carte d’entrée d’événement URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Cartographiez une URL ou une ressource HTML à une page dans un dialogue à plusieurs pages.|

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP

Marque le début de la carte de l’événement DHTML `className`lorsqu’il est placé dans le fichier source pour la classe identifiée par .

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Le nom de la classe contenant la carte de l’événement DHTML. Cette classe devrait dériver directement ou indirectement de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) et inclure la [macro DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) dans sa définition de classe.

### <a name="remarks"></a>Notes

Ajoutez une carte d’événement DHTML `CDHtmlDialog` à votre classe pour fournir des informations qui peuvent être utilisées pour acheminer les événements déclenchés par des éléments HTML ou les contrôles ActiveX dans une page Web pour les fonctions de gestionnaire dans votre classe.

Placez la macro BEGIN_DHTML_EVENT_MAP dans le fichier de mise en œuvre (.cpp) de la classe suivi d’DHTML_EVENT macros pour les événements que la classe doit gérer (par exemple, DHTML_EVENT_ONMOUSEOVER pour les événements de mouseover). Utilisez la [macro END_DHTML_EVENT_MAP](#end_dhtml_event_map) pour marquer la fin de la carte de l’événement. Ces macros mettent en œuvre la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE

Marque le début de la carte de l’événement DHTML dans la définition de classe pour *className*.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Le nom de la classe contenant la carte de l’événement DHTML. Cette classe devrait dériver directement ou indirectement de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) et inclure la [macro DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) dans sa définition de classe.

### <a name="remarks"></a>Notes

Ajoutez une carte d’événement DHTML `CDHtmlDialog` à votre classe pour fournir des informations qui peuvent être utilisées pour acheminer les événements déclenchés par des éléments HTML ou les contrôles ActiveX dans une page Web pour les fonctions de gestionnaire dans votre classe.

Placez la BEGIN_DHTML_EVENT_MAP macro dans le fichier de définition (.h) de la classe suivi d’DHTML_EVENT macros pour les événements que la classe doit gérer (par exemple, DHTML_EVENT_ONMOUSEOVER pour les événements de mouseover). Utilisez la [macro END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) pour marquer la fin de la carte de l’événement. Ces macros mettent en œuvre la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP

Déclare une carte d’événement DHTML dans une définition de classe.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Cette macro doit être utilisée dans la définition des classes [CDHtmlDialog-dérivées.](../../mfc/reference/cdhtmldialog-class.md)

Utilisez [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) ou [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) pour implémenter la carte.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) déclare la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event"></a><a name="dhtml_event"></a>DHTML_EVENT

Gère (au niveau du document) un événement identifié par *des origines dédipées* par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
Le DISPID de l’événement à gérer.

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement, ou NULL pour gérer les événements documentaires.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL

Gère l’événement identifié par *le désarroié* tiré par le contrôle ActiveX identifié par *controlName*.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’id de répartition de l’événement à gérer.

*controlName (en)*<br/>
Un LPCWSTR tenant l’ID HTML du contrôle de tir de l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS

Gère (au niveau du document) un événement identifié par *des insipides* provenant de n’importe quel élément HTML avec la classe CSS identifiée par *elemName*.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’id de répartition de l’événement à gérer.

*elemName elemName*<br/>
Un LPCWSTR tenant la classe CSS des éléments HTML s’approvisionnant en événements.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT

Poignées (à l’élément identifié par *elemName*) un événement identifié par *dispid*.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’id de répartition de l’événement à gérer.

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

Si cette macro est utilisée pour gérer les événements non-bubbling, la source de l’événement sera l’élément identifié par *elemName*.

Si cette macro est utilisée pour gérer les événements bouillonnants, l’élément identifié par *elemName* peut ne pas être la source de l’événement (la source pourrait être n’importe quel élément contenu par *elemName*).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE

Poignées (au niveau du `onafterupdate` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE

Poignées (au niveau du `onbeforeupdate` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR

Gère (au niveau de `onblur` l’élément) l’événement. Il s’agit d’un événement nonbubbling.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE

Gère (au niveau de `onchange` l’élément) l’événement. Il s’agit d’un événement nonbubbling.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK

Poignées (au niveau du `onclick` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE

Poignées (au niveau du `ondataavailable` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED

Poignées (au niveau du `ondatasetchanged` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE

Poignées (au niveau du `ondatasetcomplete` document) l’événement `elemName`provient de l’élément HTML identifié par .

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK

Poignées (au niveau du `ondblclick` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART

Poignées (au niveau du `ondragstart` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE

Poignées (au niveau du `onerrorupdate` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE

Poignées (au niveau du `onfilterchange` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS

Gère (au niveau de `onfocus` l’élément) l’événement. Il s’agit d’un événement nonbubbling.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP

Poignées (au niveau du `onhelp` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN

Poignées (au niveau du `onkeydown` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS

Poignées (au niveau du `onkeypress` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP

Poignées (au niveau du `onkeyup` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN

Poignées (au niveau du `onmousedown` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE

Poignées (au niveau du `onmousemove` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT

Poignées (au niveau du `onmouseout` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER

Poignées (au niveau du `onmouseover` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP

Poignées (au niveau du `onmouseup` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE

Gère (au niveau de `onresize` l’élément) l’événement. Il s’agit d’un événement nonbubbling.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER

Poignées (au niveau du `onrowenter` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT

Poignées (au niveau du `onrowexit` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART

Poignées (au niveau du `onselectstart` document) l’événement provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName elemName*<br/>
Un LPCWSTR détenant l’ID de l’élément HTML s’approvisionnant en l’événement.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG

Gère (au niveau du document) `dispid` un événement identifié par n’importe quel élément HTML avec l’étiquette HTML identifiée par *elemName*.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’id de répartition de l’événement à gérer.

*elemName elemName*<br/>
L’étiquette HTML des éléments HTML s’approvisionnant en événements.

*membreFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [carte d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP

Marque la fin de la carte de l’événement DHTML.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Doit être utilisé en conjonction avec [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP

Démarre la définition d’une carte d’événement DHTML et URL dans un dialogue à plusieurs pages.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Mettez BEGIN_DHTML_URL_EVENT_MAP dans le fichier d’implémentation de votre classe [dérivée CMultiPageDHtmlDialog.](../../mfc/reference/cmultipagedhtmldialog-class.md) Suivez-le avec [des cartes d’événements DHTML intégrées](#begin_embed_dhtml_event_map) et [des entrées d’URL,](#begin_url_entries)puis fermez-le avec [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Inclure la [macro DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) dans la définition de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP

Commence la définition d’une carte d’événement DHTML intégrée dans un dialogue multipage.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Le nom de la classe contenant la carte de l’événement. Cette classe devrait dériver directement ou indirectement de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). La carte intégrée de l’événement DHTML doit être à l’intérieur d’une [carte d’événement DHTML et URL](#begin_dhtml_url_event_map)).

*mapName (en)*<br/>
Spécifie la page dont il s’agit de la carte de l’événement. Cela correspond *mapName* dans la [macro URL_EVENT_ENTRY](#url_event_entry) définissant réellement l’URL ou la ressource HTML.

### <a name="remarks"></a>Notes

Étant donné qu’un dialogue DHTML à plusieurs pages se compose de plusieurs pages HTML, chacune pouvant soulever des événements DHTML, des cartes d’événements intégrées sont utilisées pour cartographier les événements aux gestionnaires par page.

Les cartes d’événements intégrées dans une carte d’événement DHTML et URL se composent d’une macro BEGIN_EMBED_DHTML_EVENT_MAP suivie [d’DHTML_EVENT](#dhtml_event) macros et d’une macro [END_EMBED_DHTML_EVENT_MAP.](#end_embed_dhtml_event_map)

Chaque carte d’événement intégrée nécessite une [entrée d’événement URL](#url_event_entry) correspondante pour cartographier *mapName* (spécifié dans BEGIN_EMBED_DHTML_EVENT_MAP) à une URL ou une ressource HTML.

### <a name="example"></a>Exemple

Voir l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES

Démarre la définition d’une carte d’entrée d’événement URL dans un dialogue à plusieurs pages.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Le nom de la classe contenant la carte d’entrée de l’événement URL. Cette classe devrait dériver directement ou indirectement de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). La carte d’entrée de l’événement URL doit être à l’intérieur [d’une carte d’événement DHTML et URL](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Notes

Étant donné qu’un dialogue DHTML à plusieurs pages se compose de plusieurs pages HTML, les entrées d’événements URL sont utilisées pour cartographier les URL ou les ressources HTML aux [cartes d’événements DHTML intégrées correspondantes.](#begin_embed_dhtml_event_map) Mettez URL_EVENT_ENTRY macros entre BEGIN_URL_ENTRIES et [END_URL_ENTRIES](#end_url_entries) macros.

### <a name="example"></a>Exemple

Voir l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP

Déclare une carte d’événement DHTML et URL dans une définition de classe.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Cette macro doit être utilisée dans la définition de [CMultiPageDHtmlDialog-classes](../../mfc/reference/cmultipagedhtmldialog-class.md)dérivées.

Une carte DHTML et URL des événements contient [des cartes d’événements DHTML intégrées](#begin_embed_dhtml_event_map) et [des entrées d’événements URL](#begin_url_entries) pour cartographier les événements DHTML aux gestionnaires sur une base par page. Utilisez [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) pour implémenter la carte.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP

Marque la fin d’une carte d’événement DHTML et URL.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Le nom de la classe contenant la carte de l’événement. Cette classe devrait dériver directement ou indirectement de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Cela devrait correspondre *className* dans le [macro BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) correspondant.

### <a name="example"></a>Exemple

Voir l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP

Marque la fin d’une carte d’événement DHTML intégrée.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Exemple

Voir l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="end_url_entries"></a><a name="end_url_entries"></a>END_URL_ENTRIES

Marque la fin d’une carte d’entrée d’événement URL.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>Exemple

Voir l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="url_event_entry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY

Cartographiez une URL ou une ressource HTML à une page dans un dialogue à plusieurs pages.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Le nom de la classe contenant la carte d’entrée de l’événement URL. Cette classe devrait dériver directement ou indirectement de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). La carte d’entrée de l’événement URL doit être à l’intérieur [d’une carte d’événement DHTML et URL](#begin_dhtml_url_event_map)).

*url*<br/>
L’URL ou la ressource HTML pour la page.

*mapName (en)*<br/>
Spécifie la page dont l’URL est *url*. Cela correspond *mapName* dans le [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) macro qui cartographie les événements à partir de cette page.

### <a name="remarks"></a>Notes

Si la page est une ressource HTML, *url* doit être la représentation des chaînes du numéro d’identification de la ressource (c’est-à-dire « 123 », et non 123 ou ID_HTMLRES1).

L’identifiant de page, *mapName*, est un symbole arbitraire utilisé pour lier les cartes d’événements DHTML intégrées aux cartes d’entrée d’événements URL. Sa portée est limitée à la carte des événements DHTML et URL.

### <a name="example"></a>Exemple

Voir l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml.h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Marque la fin de la carte de l’événement DHTML.

### <a name="syntax"></a>Syntaxe

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Notes

Doit être utilisé en conjonction avec [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Spécifications

**En-tête:** afxdhtml.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)
