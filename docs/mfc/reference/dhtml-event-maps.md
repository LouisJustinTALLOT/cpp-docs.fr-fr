---
title: DHTML, tables d’événements | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.macros.shared
dev_langs:
- C++
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8a888cfdf8d83f3628bf4ad80b26db6ac51ad72
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123095"
---
# <a name="dhtml-event-maps"></a>DHTML, tables d'événements
Les macros suivantes peuvent être utilisés pour gérer les événements DHTML.  
  
## <a name="dhtml-event-map-macros"></a>Macros de table d’événements DHTML  
 Les macros suivantes peuvent être utilisés pour gérer les événements DHTML dans [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-classes dérivées.  
  
|||  
|-|-|  
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Marque le début de la table d’événements DHTML.|  
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Marque le début de la table d’événements DHTML.|  
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Déclare la table d’événements DHTML.|  
|[DHTML_EVENT](#dhtml_event)|Utilisé pour gérer un événement au niveau du document pour un élément HTML unique.|  
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Utilisé pour gérer un événement déclenché par un contrôle ActiveX.|  
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Utilisé pour gérer un événement au niveau du document pour tous les éléments HTML avec une classe CSS.|  
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Utilisé pour gérer un événement au niveau de l’élément.|  
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Permet de gérer la `onafterupdate` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Permet de gérer la `onbeforeupdate` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Permet de gérer la `onblur` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Permet de gérer la `onchange` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Permet de gérer la `onclick` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Permet de gérer la `ondataavailable` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Permet de gérer la `ondatasetchanged` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Permet de gérer la `ondatasetcomplete` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Permet de gérer la `ondblclick` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Permet de gérer la `ondragstart` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Permet de gérer la `onerrorupdate` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Permet de gérer la `onfilterchange` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Permet de gérer la `onfocus` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Permet de gérer la `onhelp` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Permet de gérer la `onkeydown` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Permet de gérer la `onkeypress` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Permet de gérer la `onkeyup` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Permet de gérer la `onmousedown` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Permet de gérer la `onmousemove` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Permet de gérer la `onmouseout` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Permet de gérer la `onmouseover` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Permet de gérer la `onmouseup` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Permet de gérer la `onresize` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Permet de gérer la `onrowenter` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Permet de gérer la `onrowexit` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Permet de gérer la `onselectstart` événement à partir d’un élément HTML.|  
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Utilisé pour gérer un événement au niveau du document pour tous les éléments avec une balise HTML particulière.|  
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Marque la fin de la table d’événements DHTML.|  
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Marque la fin de la table d’événements DHTML. |
  
## <a name="url-event-map-macros"></a>Macros de table d’événement URL  
 Les macros suivantes peuvent être utilisés pour gérer les événements DHTML dans [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-classes dérivées.  
  
|||  
|-|-|  
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Marque le début de la table d’événements multipage DHTML et l’URL.|  
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Marque le début d’une table d’événements DHTML incorporé.|  
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Marque le début d’une table d’entrée d’événement URL.|  
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Déclare la table d’événements multipage DHTML et l’URL.|  
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Marque la fin de la table d’événements multipage DHTML et l’URL.|  
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
 *nom de classe*  
 Le nom de la classe contenant la table d’événements DHTML. Cette classe doit dériver directement ou indirectement [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) et inclure le [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) macro dans sa définition de classe.  
  
### <a name="remarks"></a>Notes  
 Ajouter une table d’événements DHTML à votre classe pour fournir des informations à `CDHtmlDialog` qui peut être utilisé pour acheminer les événements déclenchés par les éléments HTML ou des contrôles ActiveX dans une page web aux fonctions de gestionnaire dans votre classe.  
  
 Placez le BEGIN_DHTML_EVENT_MAP (macro) dans le fichier implémentation (.cpp) de la classe suivi par des macros DHTML_EVENT pour les événements de que la classe est de gérer (par exemple, DHTML_EVENT_ONMOUSEOVER pour les événements de souris). Utilisez le [END_DHTML_EVENT_MAP](#end_dhtml_event_map) macro pour marquer la fin de la table d’événements. Ces macros implémentent la fonction suivante :  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE  
 Marque le début de la table d’événements DHTML au sein de la définition de classe pour *className*.  
  
```   
BEGIN_DHTML_EVENT_MAP_INLINE(className)   
```  
  
### <a name="parameters"></a>Paramètres  
 *nom de classe*  
 Le nom de la classe contenant la table d’événements DHTML. Cette classe doit dériver directement ou indirectement [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) et inclure le [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) macro dans sa définition de classe.  
  
### <a name="remarks"></a>Notes  
 Ajouter une table d’événements DHTML à votre classe pour fournir des informations à `CDHtmlDialog` qui peut être utilisé pour acheminer les événements déclenchés par les éléments HTML ou des contrôles ActiveX dans une page web aux fonctions de gestionnaire dans votre classe.  
  
 Placez le BEGIN_DHTML_EVENT_MAP (macro) dans (.h) fichier de définition la classe de suivis par des macros DHTML_EVENT pour les événements de que la classe est de gérer (par exemple, DHTML_EVENT_ONMOUSEOVER pour les événements de souris). Utilisez le [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) macro pour marquer la fin de la table d’événements. Ces macros implémentent la fonction suivante :  
  
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
  
 Utilisez [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) ou [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) pour implémenter le mappage.  
  
 [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) déclare la fonction suivante :  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event"></a>  DHTML_EVENT  
 Gère (au niveau du document), un événement identifié par *dispid* émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *DISPID*  
 Le DISPID de l’événement à gérer.  
  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement, ou NULL pour gérer les événements de document.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL  
 Gère l’événement identifié par *dispid* déclenchés par le contrôle ActiveX identifié par *nom contrôle*.  
  
```   
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)  
```  
  
### <a name="parameters"></a>Paramètres  
 *DISPID*  
 L’ID de dispatch de l’événement à gérer.  
  
 *Nom contrôle*  
 Un LPCWSTR contenant l’ID HTML du contrôle déclenche l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS  
 Gère (au niveau du document), un événement identifié par *dispid* émane par n’importe quel élément HTML de la classe CSS identifiée par *elemName*.  
  
```   
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *DISPID*  
 L’ID de dispatch de l’événement à gérer.  
  
 *elemName*  
 Un LPCWSTR contenant la classe CSS des éléments HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT  
 Handles (à l’élément identifié par *elemName*) un événement identifié par *dispid*.  
  
```   
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn) 
```  
  
### <a name="parameters"></a>Paramètres  
 *DISPID*  
 L’ID de dispatch de l’événement à gérer.  
  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
 Si cette macro est utilisée pour gérer les événements nonbubbling, la source de l’événement sera l’élément identifié par *elemName*.  
  
 Si cette macro est utilisée pour gérer les événements de propagation, l’élément identifié par *elemName* ne peut pas être la source de l’événement (la source peut être n’importe quel élément contenu dans *elemName*).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE  
 Gère (au niveau du document) le `onafterupdate` événement émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE  
 Gère (au niveau du document) le `onbeforeupdate` événement émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR  
 Gère (au niveau de l’élément) le `onblur` événement. Il s’agit d’un événement nonbubbling.  
  
```   
DHTML_EVENT_ONBLUR(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE  
 Gère (au niveau de l’élément) le `onchange` événement. Il s’agit d’un événement nonbubbling.  
  
```   
DHTML_EVENT_ONCHANGE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK  
 Gère (au niveau du document) le `onclick` événement émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT_ONCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE  
 Gère (au niveau du document) le `ondataavailable` événement émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED  
 Gère (au niveau du document) le `ondatasetchanged` événement émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE  
 Gère (au niveau du document) le `ondatasetcomplete` événement émis par l’élément HTML identifié par `elemName`.  
  
```   
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn) 
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK  
 Gère (au niveau du document) le `ondblclick` événement émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART  
 Gère (au niveau du document) le `ondragstart` événement émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE  
 Gère (au niveau du document) le `onerrorupdate` événement émis par l’élément HTML identifié par *elemName*.  
  
```   
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE  
 Gère (au niveau du document) le `onfilterchange` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS  
 Gère (au niveau de l’élément) le `onfocus` événement. Il s’agit d’un événement nonbubbling.  
  
```  
 
DHTML_EVENT_ONFOCUS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP  
 Gère (au niveau du document) le `onhelp` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONHELP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN  
 Gère (au niveau du document) le `onkeydown` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS  
 Gère (au niveau du document) le `onkeypress` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP  
 Gère (au niveau du document) le `onkeyup` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN  
 Gère (au niveau du document) le `onmousedown` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE  
 Gère (au niveau du document) le `onmousemove` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT  
 Gère (au niveau du document) le `onmouseout` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER  
 Gère (au niveau du document) le `onmouseover` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP  
 Gère (au niveau du document) le `onmouseup` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE  
 Gère (au niveau de l’élément) le `onresize` événement. Il s’agit d’un événement nonbubbling.  
  
```  
 
DHTML_EVENT_ONRESIZE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER  
 Gère (au niveau du document) le `onrowenter` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONROWENTER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT  
 Gère (au niveau du document) le `onrowexit` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART  
 Gère (au niveau du document) le `onselectstart` événement émis par l’élément HTML identifié par *elemName*.  
  
```  
 
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *elemName*  
 Un LPCWSTR contenant l’ID de l’élément HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG  
 Gère (au niveau du document), un événement identifié par `dispid` émis par n’importe quel élément HTML avec la balise HTML identifiée par *elemName*.  
  
```   
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Paramètres  
 *DISPID*  
 L’ID de dispatch de l’événement à gérer.  
  
 *elemName*  
 La balise HTML des éléments HTML délocalisation de l’événement.  
  
 *memberFxn*  
 La fonction de gestionnaire pour l’événement.  
  
### <a name="remarks"></a>Notes  
 Cette macro permet d’ajouter une entrée à la [table d’événements DHTML](#begin_dhtml_event_map_inline) dans votre classe.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP  
 Marque la fin de la table d’événements DHTML.  
  
```   
END_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Notes  
 Doit être utilisé conjointement avec [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP  
 Démarre la définition d’une table d’événements DHTML et l’URL dans une boîte de dialogue multipage.  
  
```  
BEGIN_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>Notes  
 Placez BEGIN_DHTML_URL_EVENT_MAP dans le fichier d’implémentation de votre [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-classe dérivée. Utilisez-le avec [incorporé DHTML, tables d’événements](#begin_embed_dhtml_event_map) et [entrées d’URL](#begin_url_entries), puis fermez-le avec [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Inclure le [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) macro au sein de la définition de classe.  
  
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
 *nom de classe*  
 Le nom de la classe contenant la table d’événements. Cette classe doit dériver directement ou indirectement [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). La table d’événements DHTML incorporée doit être à l’intérieur d’un [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).  
  
 *mapName*  
 Spécifie la page Mapper dont l’événement. Cela correspond à *mapName* dans les [URL_EVENT_ENTRY](#url_event_entry) macro, définissez la ressource d’URL ou HTML.  
  
### <a name="remarks"></a>Notes  
 Parce qu’une boîte de dialogue multipage DHTML comprend plusieurs pages HTML, chacun d’eux peut déclencher des événements DHTML, tables d’événements incorporés sont utilisés pour mapper des événements aux gestionnaires sur une base par page.  
  
 Les tables d’événements incorporé au sein d’une table d’événements DHTML et l’URL se composent d’une macro BEGIN_EMBED_DHTML_EVENT_MAP suivie [DHTML_EVENT](#dhtml_event) macros et un [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) (macro).  
  
 Chaque table d’événements incorporé requiert correspondante [entrée d’événement URL](#url_event_entry) pour mapper *mapName* (spécifié dans BEGIN_EMBED_DHTML_EVENT_MAP) à une ressource URL ou HTML.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES  
 Démarre la définition d’une table d’entrée d’événement URL dans une boîte de dialogue multipage.  
  
```  
BEGIN_URL_ENTRIES(className)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *nom de classe*  
 Le nom de la classe contenant la table d’entrée d’événement URL. Cette classe doit dériver directement ou indirectement [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Table d’entrée d’événement l’URL doit être à l’intérieur d’un [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).  
  
### <a name="remarks"></a>Notes  
 Car une boîte de dialogue DHTML multipage se compose de plusieurs pages HTML, les entrées d’URL d’événements sont utilisées pour mapper des URL ou HTML ressources correspondant [incorporé DHTML, tables d’événements](#begin_embed_dhtml_event_map). Placez les macros URL_EVENT_ENTRY entre BEGIN_URL_ENTRIES et [END_URL_ENTRIES](#end_url_entries) macros.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP  
 Déclare une table d’événements DHTML et l’URL dans une définition de classe.  
  
```  
DECLARE_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>Notes  
 Cette macro doit être utilisée dans la définition de [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-classes dérivées.  
  
 Une table d’événements DHTML et l’URL contient [incorporé DHTML, tables d’événements](#begin_embed_dhtml_event_map) et [entrées d’événement URL](#begin_url_entries) pour mapper les événements DHTML aux gestionnaires sur une base par page. Utilisez [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) pour implémenter le mappage.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP  
 Marque la fin d’une table d’événements DHTML et l’URL.  
  
```  
END_DHTML_URL_EVENT_MAP(className)  
 
```  
  
### <a name="parameters"></a>Paramètres  
 *nom de classe*  
 Le nom de la classe contenant la table d’événements. Cette classe doit dériver directement ou indirectement [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Il doit correspondre à *className* correspond [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) (macro).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP  
 Marque la fin d’une table d’événements DHTML incorporée.  
  
```  
END_EMBED_DHTML_EVENT_MAP()  
 
```  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="end_url_entries"></a>  END_URL_ENTRIES  
 Marque la fin d’une table d’entrée d’événement URL.  
  
```  
END_URL_ENTRIES()  
 
```  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  
  
##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY  
 Mappe une ressource URL ou HTML à une page dans une boîte de dialogue multipage.  
  
```  
URL_EVENT_ENTRY(className, url,  mapName)   
```  
  
### <a name="parameters"></a>Paramètres  
 *nom de classe*  
 Le nom de la classe contenant la table d’entrée d’événement URL. Cette classe doit dériver directement ou indirectement [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Table d’entrée d’événement l’URL doit être à l’intérieur d’un [table d’événements DHTML et URL](#begin_dhtml_url_event_map)).  
  
 *URL*  
 La ressource d’URL ou HTML pour la page.  
  
 *mapName*  
 Spécifie la page dont l’URL est *url*. Cela correspond à *mapName* dans les [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) macro qui mappe les événements de cette page.  
  
### <a name="remarks"></a>Notes  
 Si la page est une ressource HTML, *url* doit être la représentation sous forme de chaîne de numéro d’identification de la ressource (autrement dit, « 123 », 123 pas ou ID_HTMLRES1).  
  
 L’identificateur de la page, *mapName*, est un symbole arbitraire qui permet de lier incorporé DHTML, tables d’événements pour les tables d’entrée événements URL. Il est limité à la table d’événements DHTML et l’URL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).  

  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxdhtml.h  

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE
Marque la fin de la table d’événements DHTML.  
   
### <a name="syntax"></a>Syntaxe    
```
END_DHTML_EVENT_MAP_INLINE( )    
```  
   
### <a name="remarks"></a>Notes  
 Doit être utilisé conjointement avec [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).  
   
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdhtml.h  
   
### <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](mfc-macros-and-globals.md)   
