---
title: _ATL_FUNC_INFO, structure
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: 8398bc999e9a62d03990fd1b205ad438b6428431
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554022"
---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO, structure

Contient des informations de type utilisées pour décrire une méthode ou propriété sur une dispinterface.

## <a name="syntax"></a>Syntaxe

```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>Membres

`cc`<br/>
Convention d’appel. Lors de l’utilisation de cette structure avec le [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) (classe), ce membre doit être CC_STDCALL. `CC_CDECL` est la seule option prise en charge dans CE Windows pour le `CALLCONV` champ la `_ATL_FUNC_INFO` structure. Toute autre valeur est non pris en charge par conséquent, son comportement non défini.

`vtReturn`<br/>
Le type variant de la fonction retourne la valeur.

`nParams`<br/>
Le nombre de paramètres de fonction.

`pVarTypes`<br/>
Tableau de types variant des paramètres de fonction.

## <a name="remarks"></a>Notes

ATL utilise en interne, cette structure pour conserver les informations obtenues à partir d’une bibliothèque de types. Vous devrez peut-être manipuler cette structure directement si vous fournissez des informations de type pour un gestionnaire d’événements utilisé avec le [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) classe et [macro SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) macro.

## <a name="example"></a>Exemple

Soit une méthode dispinterface définie dans un IDL :

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

vous définissez un `_ATL_FUNC_INFO` structure :

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>Configuration requise

En-tête : atlcom.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl, classe](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[MACRO SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)

