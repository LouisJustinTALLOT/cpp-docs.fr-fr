---
title: Macro de contrôle composite
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 67ad18c07a92cfecca44667908a8488e8c2da234
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331515"
---
# <a name="composite-control-macros"></a>Macro de contrôle composite

Ces macros définissent les cartes et les entrées des éviers d’événements.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Marque le début de la carte de l’évier de l’événement pour le contrôle composite.|
|[END_SINK_MAP](#end_sink_map)|Marque la fin de la carte de l’évier de l’événement pour le contrôle composite.|
|[SINK_ENTRY](#sink_entry)|Entrée à la carte de l’évier de l’événement.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Entrée à la carte de l’évier de l’événement avec un paramètre supplémentaire.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Studio visuel 2017) Semblable à SINK_ENTRY_EX sauf qu’il faut un pointeur pour iid.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Entrée à la carte de l’évier de l’événement avec des informations de type fournie manuellement pour une utilisation avec [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Studio visuel 2017) Semblable à SINK_ENTRY_INFO sauf qu’il faut un pointeur pour iid.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a>BEGIN_SINK_MAP

Déclare le début de la carte de l’évier de l’événement pour le contrôle composite.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Paramètres

*_class*<br/>
[dans] Spécifie le contrôle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Notes

La mise en œuvre d’ActiveX d’activeX n’appuie que les valeurs de retour du type HRESULT ou les vides de vos méthodes de gestionnaire d’événements; toute autre valeur de retour n’est pas supportée et son comportement n’est pas défini.

## <a name="end_sink_map"></a><a name="end_sink_map"></a>END_SINK_MAP

Déclare la fin de la carte de l’évier de l’événement pour le contrôle composite.

```
END_SINK_MAP()
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Notes

La mise en œuvre d’ActiveX d’activeX n’appuie que les valeurs de retour du type HRESULT ou les vides de vos méthodes de gestionnaire d’événements; toute autre valeur de retour n’est pas supportée et son comportement n’est pas défini.

## <a name="sink_entry"></a><a name="sink_entry"></a>SINK_ENTRY

Déclare la fonction de gestionnaire (*fn*) pour l’événement spécifié (*dispid*), du contrôle identifié par *id*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] Identifie le contrôle.

*dispid*<br/>
[dans] Identifie l’événement spécifié.

*Fn*<br/>
[dans] Nom de la fonction de gestionnaire d’événements. Cette fonction doit `_stdcall` utiliser la convention d’appel et avoir la signature appropriée de style dispinterface.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Notes

La mise en œuvre d’ActiveX d’activeX n’appuie que les valeurs de retour du type HRESULT ou les vides de vos méthodes de gestionnaire d’événements; toute autre valeur de retour n’est pas supportée et son comportement n’est pas défini.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a>SINK_ENTRY_EX et SINK_ENTRY_EX_P

Déclare la fonction de gestionnaire (*fn*) pour l’événement spécifié (*dispid*), de l’interface de répartition (*iid*), pour le contrôle identifié par *id*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] Identifie le contrôle.

*Iid*<br/>
[dans] Identifie l’interface de répartition.

*piid*<br/>
[dans] Pointeur à l’interface de répartition.

*dispid*<br/>
[dans] Identifie l’événement spécifié.

*Fn*<br/>
[dans] Nom de la fonction de gestionnaire d’événements. Cette fonction doit `_stdcall` utiliser la convention d’appel et avoir la signature appropriée de style dispinterface.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Notes

La mise en œuvre d’ActiveX d’activeX n’appuie que les valeurs de retour du type HRESULT ou les vides de vos méthodes de gestionnaire d’événements; toute autre valeur de retour n’est pas supportée et son comportement n’est pas défini.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a>SINK_ENTRY_INFO et SINK_ENTRY_INFO_P

Utilisez la macro SINK_ENTRY_INFO dans une carte d’évier d’événement pour fournir les informations nécessaires par [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) pour acheminer les événements à la fonction de gestionnaire concerné.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*id*<br/>
[dans] Insigned integer identifiant la source de l’événement. Cette valeur doit correspondre au paramètre de modèle *nID* utilisé dans la classe de base [IDispEventSimpleimple](../../atl/reference/idispeventsimpleimpl-class.md) connexe.

*Iid*<br/>
[dans] IID qui identifie l’interface de répartition.

*piid*<br/>
[dans] Pointeur à iID qui identifie l’interface de répartition.

*dispid*<br/>
[dans] DISPID identifiant l’événement spécifié.

*Fn*<br/>
[dans] Nom de la fonction de gestionnaire d’événements. Cette fonction doit `_stdcall` utiliser la convention d’appel et avoir la signature appropriée de style dispinterface.

*info*<br/>
[dans] Tapez des informations pour la fonction de gestionnaire d’événements. Ces informations de type sont fournies sous `_ATL_FUNC_INFO` la forme d’un pointeur à une structure. CC_CDECL est la seule option prise en charge dans Windows `_ATL_FUNC_INFO` CE pour le champ CALLCONV de la structure. Toute autre valeur n’est pas étayée donc son comportement indéfini.

### <a name="remarks"></a>Notes

Les quatre premiers paramètres macro sont les mêmes que ceux pour le [macro SINK_ENTRY_EX.](#sink_entry_ex) Le paramètre final fournit des informations de type pour l’événement. La mise en œuvre d’ActiveX d’activeX n’appuie que les valeurs de retour du type HRESULT ou les vides de vos méthodes de gestionnaire d’événements; toute autre valeur de retour n’est pas supportée et son comportement n’est pas défini.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions mondiales de contrôle composite](../../atl/reference/composite-control-global-functions.md)
