---
title: _Atl_win_module70, structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c000175c031868136aad44e59644d0fa122d213e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084508"
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

