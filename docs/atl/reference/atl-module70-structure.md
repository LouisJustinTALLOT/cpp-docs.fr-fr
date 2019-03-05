---
title: _Atl_module70, structure
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: d05683383fab64f027f198d49bfbf42aa593d582
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263427"
---
# <a name="atlmodule70-structure"></a>_Atl_module70, structure

Contient les données utilisées par chaque module ATL.

## <a name="syntax"></a>Syntaxe

```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>Membres

`cbSize`<br/>
La taille de la structure, utilisée pour le contrôle de version.

`m_nLockCnt`<br/>
Décompte de références pour déterminer la durée pendant laquelle le module doit rester actif.

`m_pTermFuncs`<br/>
Fonctions de pistes qui ont été inscrits pour être appelée lorsque ATL s’arrête.

`m_csStaticDataInitAndTypeInfo`<br/>
Utilisé pour coordonner l’accès aux données internes dans les situations multithreads.

## <a name="remarks"></a>Notes

[_ATL_MODULE](atl-typedefs.md#_atl_module) est défini comme un typedef de `_ATL_MODULE70`.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)
