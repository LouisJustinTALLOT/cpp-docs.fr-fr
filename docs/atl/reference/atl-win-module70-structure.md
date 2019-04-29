---
title: _Atl_win_module70, structure
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 0b636d328852daf821269230aae443cef084578b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260751"
---
# <a name="atlwinmodule70-structure"></a>_Atl_win_module70, structure

Utilisé par le code de fenêtrage dans ATL.

## <a name="syntax"></a>Syntaxe

```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>Membres

`cbSize`<br/>
La taille de la structure, utilisée pour le contrôle de version.

`m_csWindowCreate`<br/>
Utilisé pour sérialiser l’accès au code de l’inscription de fenêtre. Utilisé en interne par ATL.

`m_pCreateWndList`<br/>
Utilisé pour lier windows à leurs objets. Utilisé en interne par ATL.

`m_rgWindowClassAtoms`<br/>
Utilisé pour le suivi des inscriptions de classe de fenêtre afin qu’ils puissent être correctement annulées à la fin. Utilisé en interne par ATL.

## <a name="remarks"></a>Notes

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) est défini comme un typedef de `_ATL_WIN_MODULE70`.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)
