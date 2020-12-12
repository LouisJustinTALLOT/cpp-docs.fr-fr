---
description: 'En savoir plus sur : mappages d’événements DHTML'
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
ms.openlocfilehash: b9df8f1aa59472de033943efd28f5c688c61e706
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220121"
---
# <a name="dhtml-event-maps"></a>DHTML, tables d'événements

Les macros suivantes peuvent être utilisées pour gérer les événements DHTML.

## <a name="dhtml-event-map-macros"></a>Macros de la table des événements DHTML

Les macros suivantes peuvent être utilisées pour gérer les événements DHTML dans les classes dérivées de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md).

|Nom|Description|
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Marque le début de la table des événements DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Marque le début de la table des événements DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Déclare la table des événements DHTML.|
|[DHTML_EVENT](#dhtml_event)|Utilisé pour gérer un événement au niveau du document pour un seul élément HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Utilisé pour gérer un événement déclenché par un contrôle ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Utilisé pour gérer un événement au niveau du document pour tous les éléments HTML avec une classe CSS particulière.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Utilisé pour gérer un événement au niveau de l’élément.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Utilisé pour gérer l' `onafterupdate` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Utilisé pour gérer l' `onbeforeupdate` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Utilisé pour gérer l' `onblur` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Utilisé pour gérer l' `onchange` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Utilisé pour gérer l' `onclick` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Utilisé pour gérer l' `ondataavailable` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Utilisé pour gérer l' `ondatasetchanged` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Utilisé pour gérer l' `ondatasetcomplete` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Utilisé pour gérer l' `ondblclick` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Utilisé pour gérer l' `ondragstart` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Utilisé pour gérer l' `onerrorupdate` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Utilisé pour gérer l' `onfilterchange` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Utilisé pour gérer l' `onfocus` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Utilisé pour gérer l' `onhelp` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Utilisé pour gérer l' `onkeydown` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Utilisé pour gérer l' `onkeypress` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Utilisé pour gérer l' `onkeyup` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Utilisé pour gérer l' `onmousedown` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Utilisé pour gérer l' `onmousemove` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Utilisé pour gérer l' `onmouseout` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Utilisé pour gérer l' `onmouseover` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Utilisé pour gérer l' `onmouseup` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Utilisé pour gérer l' `onresize` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Utilisé pour gérer l' `onrowenter` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Utilisé pour gérer l' `onrowexit` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Utilisé pour gérer l' `onselectstart` événement à partir d’un élément HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Utilisé pour gérer un événement au niveau du document pour tous les éléments ayant une balise HTML particulière.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Marque la fin de la table des événements DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Marque la fin de la table des événements DHTML. |

## <a name="url-event-map-macros"></a>Macros de mappage d’événements d’URL

Les macros suivantes peuvent être utilisées pour gérer les événements DHTML dans les classes dérivées de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md).

|Nom|Description|
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Marque le début de la table d’événements DHTML et URL multipage.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Marque le début d’une table d’événements DHTML incorporée.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Marque le début d’un mappage d’entrée d’événement d’URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Déclare la table d’événements DHTML et URL multipage.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Marque la fin de la table d’événements DHTML et URL multipage.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Marque la fin d’une table d’événements DHTML incorporée.|
|[END_URL_ENTRIES](#end_url_entries)|Marque la fin d’un mappage d’entrée d’événement d’URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Mappe une URL ou une ressource HTML à une page dans une boîte de dialogue multipage.|

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a> BEGIN_DHTML_EVENT_MAP

Marque le début de la table des événements DHTML lorsqu’elle est placée dans le fichier source pour la classe identifiée par `className` .

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe contenant la table des événements DHTML. Cette classe doit dériver directement ou indirectement de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) et inclure la macro [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) dans sa définition de classe.

### <a name="remarks"></a>Notes

Ajoutez un mappage d’événements DHTML à votre classe pour fournir des informations `CDHtmlDialog` qui peuvent être utilisées pour acheminer des événements déclenchés par des éléments HTML ou des contrôles ActiveX dans une page Web à des fonctions de gestionnaire dans votre classe.

Placez la macro BEGIN_DHTML_EVENT_MAP dans le fichier d’implémentation (. cpp) de la classe, suivi de DHTML_EVENT macros pour les événements que la classe doit gérer (par exemple, DHTML_EVENT_ONMOUSEOVER pour les événements MouseOver). Utilisez la macro [END_DHTML_EVENT_MAP](#end_dhtml_event_map) pour marquer la fin de la table des événements. Ces macros implémentent la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a> BEGIN_DHTML_EVENT_MAP_INLINE

Marque le début de la table des événements DHTML au sein de la définition de classe pour *className*.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe contenant la table des événements DHTML. Cette classe doit dériver directement ou indirectement de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) et inclure la macro [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) dans sa définition de classe.

### <a name="remarks"></a>Notes

Ajoutez un mappage d’événements DHTML à votre classe pour fournir des informations `CDHtmlDialog` qui peuvent être utilisées pour acheminer des événements déclenchés par des éléments HTML ou des contrôles ActiveX dans une page Web à des fonctions de gestionnaire dans votre classe.

Placez la macro BEGIN_DHTML_EVENT_MAP dans le fichier de définition de la classe (. h) suivi de DHTML_EVENT macros pour les événements que la classe doit gérer (par exemple, DHTML_EVENT_ONMOUSEOVER pour les événements MouseOver). Utilisez la macro [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) pour marquer la fin de la table des événements. Ces macros implémentent la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a> DECLARE_DHTML_EVENT_MAP

Déclare une table des événements DHTML dans une définition de classe.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Cette macro doit être utilisée dans la définition de classes dérivées de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md).

Utilisez [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) ou [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) pour implémenter le mappage.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) déclare la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event"></a><a name="dhtml_event"></a> DHTML_EVENT

Handles (au niveau du document) un événement identifié par *DISPID* provient de l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*égal*<br/>
DISPID de l’événement à gérer.

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement, ou NULL pour gérer les événements de document.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a> DHTML_EVENT_AXCONTROL

Gère l’événement identifié par *DISPID* déclenché par le contrôle ActiveX identifié par *nomcontrôle*.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*égal*<br/>
ID de dispatch de l’événement à gérer.

*NomContrôle*<br/>
LPCWSTR contenant l’ID HTML du contrôle déclenchant l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a> DHTML_EVENT_CLASS

Handles (au niveau du document) un événement identifié par *DISPID* provient d’un élément HTML avec la classe CSS identifiée par *elemName*.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*égal*<br/>
ID de dispatch de l’événement à gérer.

*elemName*<br/>
LPCWSTR contenant la classe CSS des éléments HTML qui approvisionnent l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a> DHTML_EVENT_ELEMENT

Handles (au niveau de l’élément identifié par *elemName*) un événement identifié par *DISPID*.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*égal*<br/>
ID de dispatch de l’événement à gérer.

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

Si cette macro est utilisée pour gérer des événements de non-propagation, la source de l’événement sera l’élément identifié par *elemName*.

Si cette macro est utilisée pour gérer les événements de propagation, l’élément identifié par *elemName* peut ne pas être la source de l’événement (la source peut être n’importe quel élément contenu par *elemName*).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a> DHTML_EVENT_ONAFTERUPDATE

Gère (au niveau du document) l' `onafterupdate` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a> DHTML_EVENT_ONBEFOREUPDATE

Gère (au niveau du document) l' `onbeforeupdate` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a> DHTML_EVENT_ONBLUR

Gère (au niveau de l’élément) l' `onblur` événement. Il s’agit d’un événement de non-propagation.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a> DHTML_EVENT_ONCHANGE

Gère (au niveau de l’élément) l' `onchange` événement. Il s’agit d’un événement de non-propagation.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a> DHTML_EVENT_ONCLICK

Gère (au niveau du document) l' `onclick` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a> DHTML_EVENT_ONDATAAVAILABLE

Gère (au niveau du document) l' `ondataavailable` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a> DHTML_EVENT_ONDATASETCHANGED

Gère (au niveau du document) l' `ondatasetchanged` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a> DHTML_EVENT_ONDATASETCOMPLETE

Gère (au niveau du document) l' `ondatasetcomplete` événement généré par l’élément HTML identifié par `elemName` .

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a> DHTML_EVENT_ONDBLCLICK

Gère (au niveau du document) l' `ondblclick` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a> DHTML_EVENT_ONDRAGSTART

Gère (au niveau du document) l' `ondragstart` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a> DHTML_EVENT_ONERRORUPDATE

Gère (au niveau du document) l' `onerrorupdate` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a> DHTML_EVENT_ONFILTERCHANGE

Gère (au niveau du document) l' `onfilterchange` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a> DHTML_EVENT_ONFOCUS

Gère (au niveau de l’élément) l' `onfocus` événement. Il s’agit d’un événement de non-propagation.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a> DHTML_EVENT_ONHELP

Gère (au niveau du document) l' `onhelp` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a> DHTML_EVENT_ONKEYDOWN

Gère (au niveau du document) l' `onkeydown` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a> DHTML_EVENT_ONKEYPRESS

Gère (au niveau du document) l' `onkeypress` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a> DHTML_EVENT_ONKEYUP

Gère (au niveau du document) l' `onkeyup` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a> DHTML_EVENT_ONMOUSEDOWN

Gère (au niveau du document) l' `onmousedown` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a> DHTML_EVENT_ONMOUSEMOVE

Gère (au niveau du document) l' `onmousemove` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a> DHTML_EVENT_ONMOUSEOUT

Gère (au niveau du document) l' `onmouseout` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a> DHTML_EVENT_ONMOUSEOVER

Gère (au niveau du document) l' `onmouseover` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a> DHTML_EVENT_ONMOUSEUP

Gère (au niveau du document) l' `onmouseup` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a> DHTML_EVENT_ONRESIZE

Gère (au niveau de l’élément) l' `onresize` événement. Il s’agit d’un événement de non-propagation.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a> DHTML_EVENT_ONROWENTER

Gère (au niveau du document) l' `onrowenter` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a> DHTML_EVENT_ONROWEXIT

Gère (au niveau du document) l' `onrowexit` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a> DHTML_EVENT_ONSELECTSTART

Gère (au niveau du document) l' `onselectstart` événement généré par l’élément HTML identifié par *elemName*.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
LPCWSTR contenant l’ID de l’élément HTML source de l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a> DHTML_EVENT_TAG

Handles (au niveau du document) un événement identifié par `dispid` provient d’un élément HTML avec la balise HTML identifiée par *elemName*.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*égal*<br/>
ID de dispatch de l’événement à gérer.

*elemName*<br/>
Balise HTML des éléments HTML approvisionnant l’événement.

*memberFxn*<br/>
Fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée à la [table des événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a> END_DHTML_EVENT_MAP

Marque la fin de la table des événements DHTML.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Doit être utilisé conjointement avec [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a> BEGIN_DHTML_URL_EVENT_MAP

Démarre la définition d’une table d’événements DHTML et URL dans une boîte de dialogue multipage.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Placez BEGIN_DHTML_URL_EVENT_MAP dans le fichier d’implémentation de votre classe dérivée de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Suivez-le avec les [entrées d’URL](#begin_url_entries)et les [tables d’événements DHTML incorporées](#begin_embed_dhtml_event_map) , puis fermez-le avec [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Incluez la macro [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) dans la définition de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a> BEGIN_EMBED_DHTML_EVENT_MAP

Démarre la définition d’une table d’événements DHTML incorporée dans une boîte de dialogue multipage.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe contenant la table des événements. Cette classe doit dériver directement ou indirectement de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). La table des événements DHTML incorporée doit se trouver à l’intérieur d’une [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).

*mapName*<br/>
Spécifie la page dont le mappage d’événements est. Cela correspond à *mapname* dans la macro [URL_EVENT_ENTRY](#url_event_entry) définissant en fait l’URL ou la ressource HTML.

### <a name="remarks"></a>Notes

Étant donné qu’une boîte de dialogue DHTML multipage est composée de plusieurs pages HTML, chacune pouvant déclencher des événements DHTML, les tables d’événements incorporées sont utilisées pour mapper des événements aux gestionnaires par page.

Les tables d’événements incorporées dans une table d’événements DHTML et URL consistent en une macro BEGIN_EMBED_DHTML_EVENT_MAP, suivie de [DHTML_EVENT](#dhtml_event) macros et d’une macro [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) .

Chaque table des événements incorporée requiert une [entrée d’événement URL](#url_event_entry) correspondante pour mapper *mapname* (spécifié dans BEGIN_EMBED_DHTML_EVENT_MAP) à une URL ou une ressource HTML.

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a> BEGIN_URL_ENTRIES

Démarre la définition d’un mappage d’entrée d’événement d’URL dans une boîte de dialogue multipage.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe contenant le mappage d’entrée d’événement d’URL. Cette classe doit dériver directement ou indirectement de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Le mappage d’entrée d’événement d’URL doit être à l’intérieur d’une [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Notes

Comme une boîte de dialogue DHTML multipage est composée de plusieurs pages HTML, les entrées d’événement d’URL sont utilisées pour mapper des URL ou des ressources HTML aux [tables d’événements DHTML incorporées](#begin_embed_dhtml_event_map)correspondantes. Placez URL_EVENT_ENTRY macros entre les macros de BEGIN_URL_ENTRIES et de [END_URL_ENTRIES](#end_url_entries) .

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a> DECLARE_DHTML_URL_EVENT_MAP

Déclare une table d’événements DHTML et URL dans une définition de classe.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Cette macro doit être utilisée dans la définition de classes dérivées de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md).

Une carte d’événements DHTML et URL contient des tables d’événements et des [entrées d’URL](#begin_url_entries) [DHTML incorporées](#begin_embed_dhtml_event_map) pour mapper des événements DHTML aux gestionnaires par page. Utilisez [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) pour implémenter le mappage.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a> END_DHTML_URL_EVENT_MAP

Marque la fin d’une table d’événements DHTML et URL.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe contenant la table des événements. Cette classe doit dériver directement ou indirectement de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Cela doit correspondre à *className* dans la macro [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) correspondante.

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a> END_EMBED_DHTML_EVENT_MAP

Marque la fin d’une table d’événements DHTML incorporée.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="end_url_entries"></a><a name="end_url_entries"></a> END_URL_ENTRIES

Marque la fin d’un mappage d’entrée d’événement d’URL.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="url_event_entry"></a><a name="url_event_entry"></a> URL_EVENT_ENTRY

Mappe une URL ou une ressource HTML à une page dans une boîte de dialogue multipage.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Paramètres

*ClassName*<br/>
Nom de la classe contenant le mappage d’entrée d’événement d’URL. Cette classe doit dériver directement ou indirectement de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Le mappage d’entrée d’événement d’URL doit être à l’intérieur d’une [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).

*url*<br/>
URL ou ressource HTML pour la page.

*mapName*<br/>
Spécifie la page dont l’URL est *URL*. Cela correspond à *mapname* dans la macro [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) qui mappe les événements à partir de cette page.

### <a name="remarks"></a>Notes

Si la page est une ressource HTML, *URL* doit être la représentation sous forme de chaîne du numéro d’identification de la ressource (autrement dit, « 123 », et non 123 ou ID_HTMLRES1).

L’identificateur de page, *mapname*, est un symbole arbitraire utilisé pour lier les mappages d’événements DHTML incorporés aux mappages d’entrée d’événement d’URL. La portée est limitée à la table d’événements DHTML et URL.

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdhtml. h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a> END_DHTML_EVENT_MAP_INLINE

Marque la fin de la table des événements DHTML.

### <a name="syntax"></a>Syntaxe

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Notes

Doit être utilisé conjointement avec [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Spécifications

**En-tête :** afxdhtml. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)
