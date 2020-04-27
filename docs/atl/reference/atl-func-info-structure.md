---
title: Structure _ATL_FUNC_INFO
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: b1c740cf1a1ed344dbceb028bd1f39a87fc09363
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168590"
---
# <a name="_atl_func_info-structure"></a>Structure _ATL_FUNC_INFO

Contient les informations de type utilisées pour décrire une méthode ou une propriété sur une dispinterface.

## <a name="syntax"></a>Syntaxe

```cpp
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>Membres

`cc`<br/>
Convention d’appel. Lors de l’utilisation de cette structure avec la classe [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) , ce membre doit être CC_STDCALL. `CC_CDECL`est la seule option prise en charge dans Windows CE `CALLCONV` pour le champ `_ATL_FUNC_INFO` de la structure. Tout autre valeur n’est pas prise en charge, donc son comportement n’est pas défini.

`vtReturn`<br/>
Type variant de la valeur de retour de la fonction.

`nParams`<br/>
Nombre de paramètres de fonction.

`pVarTypes`<br/>
Tableau de types variant des paramètres de fonction.

## <a name="remarks"></a>Notes

En interne, ATL utilise cette structure pour conserver les informations obtenues à partir d’une bibliothèque de types. Vous devrez peut-être manipuler cette structure directement si vous fournissez des informations de type pour un gestionnaire d’événements utilisé avec la classe [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) et [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) macro.

## <a name="example"></a>Exemple

À partir d’une méthode dispinterface définie dans IDL :

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

vous devez définir une `_ATL_FUNC_INFO` structure :

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>Spécifications

En-tête : atlcom.h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl, classe](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
