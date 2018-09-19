---
title: _Atl_base_module70, structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8ee35df4b6ee792cd91f1b294259544e8944509
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089045"
---
# <a name="atlbasemodule70-structure"></a>_Atl_base_module70, structure

Utilisé par n’importe quel projet qui utilise ATL.

## <a name="syntax"></a>Syntaxe

```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```

## <a name="members"></a>Membres

`cbSize`<br/>
La taille de la structure, utilisée pour le contrôle de version.

`m_hInst`<br/>
Le `hInstance` pour ce module (exe ou dll).

`m_hInstResource`<br/>
Handle de ressource d’instance par défaut.

`m_bNT5orWin98`<br/>
Informations de version du système d’exploitation. Utilisé en interne par ATL.

`dwAtlBuildVer`<br/>
Stocke la version de l’ATL. Actuellement 0x0700.

`pguidVer`<br/>
GUID interne d’ATL.

`m_csResource`<br/>
Utilisé pour synchroniser l’accès à la `m_rgResourceInstance` tableau. Utilisé en interne par ATL.

`m_rgResourceInstance`<br/>
Tableau utilisé pour rechercher des ressources dans toutes les instances de ressources dont est prenant en charge ATL. Utilisé en interne par ATL.

## <a name="remarks"></a>Notes

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) est défini comme un typedef de _ATL_BASE_MODULE70.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcore.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)

