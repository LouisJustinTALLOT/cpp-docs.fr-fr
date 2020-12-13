---
description: En savoir plus sur les macros de contrôle composite
title: Macros de contrôle composite
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 0107f91350516bd0f7e35cf82a49f79ff3c5797e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141191"
---
# <a name="composite-control-macros"></a>Macros de contrôle composite

Ces macros définissent les entrées et les mappages de récepteurs d’événements.

|Macro|Description|
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Marque le début de la table de récepteurs d’événements pour le contrôle composite.|
|[END_SINK_MAP](#end_sink_map)|Marque la fin du mappage de récepteur d’événements pour le contrôle composite.|
|[SINK_ENTRY](#sink_entry)|Entrée dans la table de récepteurs d’événements.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Entrée de la table de récepteurs d’événements avec un paramètre supplémentaire.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Semblable à SINK_ENTRY_EX sauf qu’il prend un pointeur vers iid.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Entrée dans le mappage du récepteur d’événements avec les informations de type fournies manuellement pour une utilisation avec [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Semblable à SINK_ENTRY_INFO sauf qu’il prend un pointeur vers iid.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a> BEGIN_SINK_MAP

Déclare le début de la table de récepteurs d’événements pour le contrôle composite.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Paramètres

*_class*<br/>
dans Spécifie le contrôle.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Notes

L’implémentation ATL CE des récepteurs d’événements ActiveX ne prend en charge que les valeurs de retour de type HRESULT ou void de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour n’est pas prise en charge et son comportement n’est pas défini.

## <a name="end_sink_map"></a><a name="end_sink_map"></a> END_SINK_MAP

Déclare la fin de la table de récepteurs d’événements pour le contrôle composite.

```
END_SINK_MAP()
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Notes

L’implémentation ATL CE des récepteurs d’événements ActiveX ne prend en charge que les valeurs de retour de type HRESULT ou void de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour n’est pas prise en charge et son comportement n’est pas défini.

## <a name="sink_entry"></a><a name="sink_entry"></a> SINK_ENTRY

Déclare la fonction de gestionnaire (*FN*) pour l’événement spécifié (*DISPID*) du contrôle identifié par l' *ID*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identifie le contrôle.

*égal*<br/>
dans Identifie l’événement spécifié.

*FN*<br/>
dans Nom de la fonction de gestionnaire d’événements. Cette fonction doit utiliser la `_stdcall` Convention d’appel et avoir la signature de style dispinterface appropriée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Notes

L’implémentation ATL CE des récepteurs d’événements ActiveX ne prend en charge que les valeurs de retour de type HRESULT ou void de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour n’est pas prise en charge et son comportement n’est pas défini.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a> SINK_ENTRY_EX et SINK_ENTRY_EX_P

Déclare la fonction de gestionnaire (*FN*) pour l’événement spécifié (*DISPID*) de l’interface de dispatch (*IID*) pour le contrôle identifié par l' *ID*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Identifie le contrôle.

*vaut*<br/>
dans Identifie l’interface de dispatch.

*piid*<br/>
dans Pointeur vers l’interface de dispatch.

*égal*<br/>
dans Identifie l’événement spécifié.

*FN*<br/>
dans Nom de la fonction de gestionnaire d’événements. Cette fonction doit utiliser la `_stdcall` Convention d’appel et avoir la signature de style dispinterface appropriée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Notes

L’implémentation ATL CE des récepteurs d’événements ActiveX ne prend en charge que les valeurs de retour de type HRESULT ou void de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour n’est pas prise en charge et son comportement n’est pas défini.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a> SINK_ENTRY_INFO et SINK_ENTRY_INFO_P

Utilisez la macro SINK_ENTRY_INFO dans un mappage de récepteur d’événements pour fournir les informations nécessaires à [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) pour acheminer les événements vers la fonction de gestionnaire appropriée.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Paramètres

*id*<br/>
dans Entier non signé identifiant la source de l’événement. Cette valeur doit correspondre au paramètre de modèle *nid* utilisé dans la classe de base [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) associée.

*vaut*<br/>
dans IID qui identifie l’interface de dispatch.

*piid*<br/>
dans Pointeur vers l’IID qui identifie l’interface de dispatch.

*égal*<br/>
dans DISPID identifiant l’événement spécifié.

*FN*<br/>
dans Nom de la fonction de gestionnaire d’événements. Cette fonction doit utiliser la `_stdcall` Convention d’appel et avoir la signature de style dispinterface appropriée.

*info*<br/>
dans Informations de type pour la fonction de gestionnaire d’événements. Ces informations de type sont fournies sous la forme d’un pointeur vers une `_ATL_FUNC_INFO` structure. CC_CDECL est la seule option prise en charge dans Windows CE pour le champ CALLCONV de la `_ATL_FUNC_INFO` structure. Tout autre valeur n’est pas prise en charge, donc son comportement n’est pas défini.

### <a name="remarks"></a>Notes

Les quatre premiers paramètres de macro sont les mêmes que ceux de la macro [SINK_ENTRY_EX](#sink_entry_ex) . Le dernier paramètre fournit des informations de type pour l’événement. L’implémentation ATL CE des récepteurs d’événements ActiveX ne prend en charge que les valeurs de retour de type HRESULT ou void de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour n’est pas prise en charge et son comportement n’est pas défini.

## <a name="see-also"></a>Voir aussi

[Macros](../../atl/reference/atl-macros.md)<br/>
[Fonctions globales de contrôle composite](../../atl/reference/composite-control-global-functions.md)
