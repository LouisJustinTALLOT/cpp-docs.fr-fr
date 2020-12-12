---
description: 'En savoir plus sur : structure _ATL_MODULE70'
title: Structure _ATL_MODULE70
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: 8a3076cebe7cab2bce49f660e8198052af393024
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165353"
---
# <a name="_atl_module70-structure"></a>Structure _ATL_MODULE70

Contient les données utilisées par chaque module ATL.

## <a name="syntax"></a>Syntaxe

```cpp
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>Membres

`cbSize`<br/>
Taille de la structure, utilisée pour le contrôle de version.

`m_nLockCnt`<br/>
Nombre de références pour déterminer la durée pendant laquelle le module doit rester actif.

`m_pTermFuncs`<br/>
Suit les fonctions qui ont été inscrites pour être appelées lorsque ATL s’arrête.

`m_csStaticDataInitAndTypeInfo`<br/>
Utilisé pour coordonner l’accès aux données internes dans les situations multithread.

## <a name="remarks"></a>Notes

[_ATL_MODULE](atl-typedefs.md#_atl_module) est défini comme un typedef de `_ATL_MODULE70` .

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)
