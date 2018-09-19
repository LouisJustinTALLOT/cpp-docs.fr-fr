---
title: _Atl_module70, structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f84b90613bcf542a9ace44505565951819fcaa91
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108441"
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

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)

