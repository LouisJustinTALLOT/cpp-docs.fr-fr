---
title: Structure _ATL_WIN_MODULE70
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 770e78e4ad87338528aa654f5ecaa08b45315846
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168551"
---
# <a name="_atl_win_module70-structure"></a>Structure _ATL_WIN_MODULE70

Utilisé par le code de fenêtrage dans ATL.

## <a name="syntax"></a>Syntaxe

```cpp
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>Membres

`cbSize`<br/>
Taille de la structure, utilisée pour le contrôle de version.

`m_csWindowCreate`<br/>
Utilisé pour sérialiser l’accès au code d’inscription de fenêtre. Utilisé en interne par ATL.

`m_pCreateWndList`<br/>
Utilisé pour lier des fenêtres à leurs objets. Utilisé en interne par ATL.

`m_rgWindowClassAtoms`<br/>
Utilisé pour suivre les inscriptions de classe de fenêtre afin qu’elles puissent être désinscrites correctement à l’arrêt. Utilisé en interne par ATL.

## <a name="remarks"></a>Notes

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) est défini comme un typedef de `_ATL_WIN_MODULE70`.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)
