---
title: Structure _ATL_BASE_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 3893e4ce4fcd24f48d9e981ad24505f82dc98833
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168642"
---
# <a name="_atl_base_module70-structure"></a>Structure _ATL_BASE_MODULE70

Utilisé par n’importe quel projet qui utilise ATL.

## <a name="syntax"></a>Syntaxe

```cpp
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
Taille de la structure, utilisée pour le contrôle de version.

`m_hInst`<br/>
`hInstance` Pour ce module (exe ou dll).

`m_hInstResource`<br/>
Descripteur de ressource d’instance par défaut.

`m_bNT5orWin98`<br/>
Informations sur la version du système d’exploitation. Utilisé en interne par ATL.

`dwAtlBuildVer`<br/>
Stocke la version de ATL. Actuellement 0x0700.

`pguidVer`<br/>
GUID interne ATL.

`m_csResource`<br/>
Utilisé pour synchroniser l' `m_rgResourceInstance` accès au tableau. Utilisé en interne par ATL.

`m_rgResourceInstance`<br/>
Tableau utilisé pour rechercher des ressources dans toutes les instances de ressource dont la prise en charge ATL est prise en charge. Utilisé en interne par ATL.

## <a name="remarks"></a>Notes

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) est défini comme un typedef de _ATL_BASE_MODULE70.

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)
