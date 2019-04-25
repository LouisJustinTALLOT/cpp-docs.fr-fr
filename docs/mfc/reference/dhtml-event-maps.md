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
ms.openlocfilehash: 5ae37acd3e0b0c2636e6a3e985490a2feab8fa34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322811"
---
# <a name="dhtml-event-maps"></a>DHTML, tables d'événements

Les macros suivantes peuvent être utilisés pour gérer des événements DHTML.

## <a name="dhtml-event-map-macros"></a>Macros de mappage des événements DHTML

Les macros suivantes peuvent être utilisés pour gérer des événements DHTML dans [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-classes dérivées.

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Marque le début de la table d’événements DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Marque le début de la table d’événements DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Déclare la table d’événements DHTML.|
|[DHTML_EVENT](#dhtml_event)|Utilisé pour gérer un événement au niveau du document pour un élément HTML unique.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Utilisé pour gérer un événement déclenché par un contrôle ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Utilisé pour gérer un événement au niveau du document pour tous les éléments HTML avec une classe CSS particulière.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Utilisé pour gérer un événement au niveau de l’élément.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Permet de gérer le `onafterupdate` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Permet de gérer le `onbeforeupdate` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Permet de gérer le `onblur` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Permet de gérer le `onchange` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Permet de gérer le `onclick` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Permet de gérer le `ondataavailable` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Permet de gérer le `ondatasetchanged` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Permet de gérer le `ondatasetcomplete` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Permet de gérer le `ondblclick` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Permet de gérer le `ondragstart` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Permet de gérer le `onerrorupdate` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Permet de gérer le `onfilterchange` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Permet de gérer le `onfocus` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Permet de gérer le `onhelp` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Permet de gérer le `onkeydown` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Permet de gérer le `onkeypress` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Permet de gérer le `onkeyup` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Permet de gérer le `onmousedown` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Permet de gérer le `onmousemove` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Permet de gérer le `onmouseout` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Permet de gérer le `onmouseover` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Permet de gérer le `onmouseup` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Permet de gérer le `onresize` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Permet de gérer le `onrowenter` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Permet de gérer le `onrowexit` événement à partir d’un élément HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Permet de gérer le `onselectstart` événement à partir d’un élément HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Utilisé pour gérer un événement au niveau du document pour tous les éléments avec une balise HTML particulière.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Marque la fin de la table d’événements DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Marque la fin de la table d’événements DHTML. |

## <a name="url-event-map-macros"></a>Macros de mappage d’événement URL

Les macros suivantes peuvent être utilisés pour gérer des événements DHTML dans [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-classes dérivées.

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Marque le début de la table d’événements DHTML et URL plusieurs pages.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Marque le début d’une table d’événements DHTML incorporé.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Marque le début d’une table d’entrée d’événement URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Déclare la table d’événements DHTML et URL plusieurs pages.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Marque la fin de la table d’événements DHTML et URL plusieurs pages.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Marque la fin d’une table d’événements DHTML incorporée.|
|[END_URL_ENTRIES](#end_url_entries)|Marque la fin d’une table d’entrée d’événement URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Mappe une ressource URL ou HTML à une page dans une boîte de dialogue multipage.|

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP

Marque le début de la table d’événements DHTML lorsqu’elle est placée dans le fichier source pour la classe identifiée par `className`.

```
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Paramètres

*className*<br/>
Le nom de la classe contenant la table d’événements DHTML. Cette classe doit dériver directement ou indirectement [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) et incluent la [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) macro dans sa définition de classe.

### <a name="remarks"></a>Notes

Ajouter une table d’événements DHTML à votre classe pour fournir des informations à `CDHtmlDialog` qui peut être utilisé pour acheminer les événements déclenchés par les éléments HTML ou des contrôles ActiveX dans une page web aux fonctions de gestionnaire dans votre classe.

Placez le begin_dhtml_event_map (macro) dans le fichier implémentation (.cpp) de la classe suivi par des macros DHTML_EVENT pour les événements de que la classe consiste à gérer (par exemple, DHTML_EVENT_ONMOUSEOVER pour les événements mouseover). Utilisez le [END_DHTML_EVENT_MAP](#end_dhtml_event_map) macro pour marquer la fin de la table d’événements. Ces macros implémentent la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE

Marque le début de la table d’événements DHTML dans la définition de classe pour *className*.

```
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Paramètres

*className*<br/>
Le nom de la classe contenant la table d’événements DHTML. Cette classe doit dériver directement ou indirectement [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) et incluent la [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) macro dans sa définition de classe.

### <a name="remarks"></a>Notes

Ajouter une table d’événements DHTML à votre classe pour fournir des informations à `CDHtmlDialog` qui peut être utilisé pour acheminer les événements déclenchés par les éléments HTML ou des contrôles ActiveX dans une page web aux fonctions de gestionnaire dans votre classe.

Placer le begin_dhtml_event_map (macro) dans la définition (.h) fichier de la classe suivi par des macros DHTML_EVENT pour les événements de que la classe consiste à gérer (par exemple, DHTML_EVENT_ONMOUSEOVER pour les événements mouseover). Utilisez le [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) macro pour marquer la fin de la table d’événements. Ces macros implémentent la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP

Déclare une table d’événements DHTML dans une définition de classe.

```
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Cette macro doit être utilisée dans la définition de [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-classes dérivées.

Utilisez [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) ou [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) pour implémenter la carte.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) déclare la fonction suivante :

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event"></a>  DHTML_EVENT

Gère (au niveau du document), un événement identifié par *dispid* provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
Le DISPID de l’événement à gérer.

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML approvisionnement de l’événement, ou NULL pour gérer les événements de document.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL

Gère l’événement identifié par *dispid* déclenché par le contrôle ActiveX identifié par *controlName*.

```
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’ID de dispatch de l’événement à gérer.

*controlName*<br/>
Un LPCWSTR contenant l’ID HTML du contrôle déclenchant l’événement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS

Gère (au niveau du document), un événement identifié par *dispid* provenant de n’importe quel élément HTML avec la classe CSS identifiée par *elemName*.

```
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’ID de dispatch de l’événement à gérer.

*elemName*<br/>
Un LPCWSTR contenant la classe CSS des éléments HTML approvisionnement de l’événement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT

Handles (à l’élément identifié par *elemName*) un événement identifié par *dispid*.

```
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’ID de dispatch de l’événement à gérer.

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

Si cette macro est utilisée pour gérer les événements nonbubbling, la source de l’événement sera l’élément identifié par *elemName*.

Si cette macro est utilisée pour gérer les événements de propagation, l’élément identifié par *elemName* peut ne pas être la source de l’événement (la source peut être n’importe quel élément contenu dans *elemName*).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE

Gère (au niveau du document) le `onafterupdate` événement provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE

Gère (au niveau du document) le `onbeforeupdate` événement provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR

Gère (au niveau de l’élément) le `onblur` événement. Il s’agit d’un événement nonbubbling.

```
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE

Gère (au niveau de l’élément) le `onchange` événement. Il s’agit d’un événement nonbubbling.

```
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK

Gère (au niveau du document) le `onclick` événement provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE

Gère (au niveau du document) le `ondataavailable` événement provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED

Gère (au niveau du document) le `ondatasetchanged` événement provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE

Gère (au niveau du document) le `ondatasetcomplete` événement provenant de l’élément HTML identifié par `elemName`.

```
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK

Gère (au niveau du document) le `ondblclick` événement provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART

Gère (au niveau du document) le `ondragstart` événement provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE

Gère (au niveau du document) le `onerrorupdate` événement provenant de l’élément HTML identifié par *elemName*.

```
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE

Gère (au niveau du document) le `onfilterchange` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS

Gère (au niveau de l’élément) le `onfocus` événement. Il s’agit d’un événement nonbubbling.

```

DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP

Gère (au niveau du document) le `onhelp` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN

Gère (au niveau du document) le `onkeydown` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS

Gère (au niveau du document) le `onkeypress` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP

Gère (au niveau du document) le `onkeyup` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN

Gère (au niveau du document) le `onmousedown` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE

Gère (au niveau du document) le `onmousemove` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT

Gère (au niveau du document) le `onmouseout` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER

Gère (au niveau du document) le `onmouseover` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP

Gère (au niveau du document) le `onmouseup` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE

Gère (au niveau de l’élément) le `onresize` événement. Il s’agit d’un événement nonbubbling.

```

DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER

Gère (au niveau du document) le `onrowenter` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT

Gère (au niveau du document) le `onrowexit` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART

Gère (au niveau du document) le `onselectstart` événement provenant de l’élément HTML identifié par *elemName*.

```

DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Paramètres

*elemName*<br/>
Un LPCWSTR contenant l’ID de l’élément HTML que l’événement d’approvisionnement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG

Gère (au niveau du document), un événement identifié par `dispid` provenant de n’importe quel élément HTML avec la balise HTML identifiée par *elemName*.

```
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Paramètres

*dispid*<br/>
L’ID de dispatch de l’événement à gérer.

*elemName*<br/>
La balise HTML des éléments HTML approvisionnement de l’événement.

*memberFxn*<br/>
La fonction de gestionnaire pour l’événement.

### <a name="remarks"></a>Notes

Utilisez cette macro pour ajouter une entrée pour le [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP

Marque la fin de la table d’événements DHTML.

```
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Doit être utilisée conjointement avec [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP

Démarre la définition d’une table d’événements DHTML et l’URL dans une boîte de dialogue multipage.

```
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Placez BEGIN_DHTML_URL_EVENT_MAP dans le fichier d’implémentation de votre [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-classe dérivée. Suivez avec [incorporé DHTML, tables d’événements](#begin_embed_dhtml_event_map) et [entrées d’URL](#begin_url_entries), puis le fermer avec [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Inclure le [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) macro au sein de la définition de classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP

Démarre la définition d’une table d’événements DHTML incorporée dans une boîte de dialogue multipage.

```
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Paramètres

*className*<br/>
Le nom de la classe contenant la table d’événements. Cette classe doit dériver directement ou indirectement [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). La table d’événements DHTML incorporée doit être à l’intérieur d’un [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).

*mapName*<br/>
Spécifie la page Mapper dont l’événement. Cela correspond à *mapName* dans le [URL_EVENT_ENTRY](#url_event_entry) macro réellement définir la ressource d’URL ou HTML.

### <a name="remarks"></a>Notes

Parce qu’une boîte de dialogue multipage DHTML comprend plusieurs pages HTML, chacun d’eux peut déclencher des événements DHTML, tables d’événements incorporés sont utilisés pour mapper des événements aux gestionnaires sur une base par page.

Tables d’événements incorporé au sein d’une table d’événements DHTML et l’URL se composent d’un begin_embed_dhtml_event_map (macro) suivie [DHTML_EVENT](#dhtml_event) macros et un [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) (macro).

Chaque table d’événements embedded nécessite un correspondant [entrée d’événement URL](#url_event_entry) pour mapper *mapName* (spécifié dans BEGIN_EMBED_DHTML_EVENT_MAP) à une ressource URL ou HTML.

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES

Démarre la définition d’une table d’entrée d’événement URL dans une boîte de dialogue multipage.

```
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Paramètres

*className*<br/>
Le nom de la classe contenant la table d’entrée événements URL. Cette classe doit dériver directement ou indirectement [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Table d’entrée d’événement l’URL doit être à l’intérieur d’un [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Notes

Parce qu’une boîte de dialogue multipage DHTML comprend plusieurs pages HTML, les entrées d’événement URL sont utilisées pour mapper des URL ou HTML ressources correspondant [incorporé DHTML, tables d’événements](#begin_embed_dhtml_event_map). Placer des macros URL_EVENT_ENTRY entre BEGIN_URL_ENTRIES et [END_URL_ENTRIES](#end_url_entries) macros.

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP

Déclare une table d’événements DHTML et l’URL dans une définition de classe.

```
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Notes

Cette macro doit être utilisée dans la définition de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-classes dérivées.

Contient une table d’événements DHTML et URL [incorporé DHTML, tables d’événements](#begin_embed_dhtml_event_map) et [entrées d’événement URL](#begin_url_entries) pour mapper des événements DHTML aux gestionnaires sur une base par page. Utilisez [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) pour implémenter la carte.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP

Marque la fin d’une table d’événements DHTML et l’URL.

```
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Paramètres

*className*<br/>
Le nom de la classe contenant la table d’événements. Cette classe doit dériver directement ou indirectement [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Cela doit correspondre à *className* dans le correspondantes [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) (macro).

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP

Marque la fin d’une table d’événements DHTML incorporée.

```
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="end_url_entries"></a>  END_URL_ENTRIES

Marque la fin d’une table d’entrée d’événement URL.

```
END_URL_ENTRIES()
```

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY

Mappe une ressource URL ou HTML à une page dans une boîte de dialogue multipage.

```
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Paramètres

*className*<br/>
Le nom de la classe contenant la table d’entrée événements URL. Cette classe doit dériver directement ou indirectement [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Table d’entrée d’événement l’URL doit être à l’intérieur d’un [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).

*url*<br/>
La ressource d’URL ou HTML pour la page.

*mapName*<br/>
Spécifie la page dont l’URL est *url*. Cela correspond à *mapName* dans le [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) macro qui mappe les événements à partir de cette page.

### <a name="remarks"></a>Notes

Si la page est une ressource HTML, *url* doit être la représentation sous forme de chaîne de numéro d’identification de la ressource (autrement dit, « 123 », 123 pas ou ID_HTMLRES1).

L’identificateur de la page, *mapName*, est un symbole arbitraire utilisé pour lier incorporé DHTML, tables d’événements pour les tables d’entrée événements URL. Il est limité à la table d’événements DHTML et l’URL.

### <a name="example"></a>Exemple

Consultez l’exemple dans [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdhtml.h

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Marque la fin de la table d’événements DHTML.

### <a name="syntax"></a>Syntaxe

```
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Notes

Doit être utilisée conjointement avec [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdhtml.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)
