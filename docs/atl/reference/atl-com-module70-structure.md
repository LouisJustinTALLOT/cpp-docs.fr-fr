---
title: Structure _ATL_COM_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c2e9e3d6695a7fbbcc87c489edf2e96fcdffb835
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168629"
---
# <a name="_atl_com_module70-structure"></a>Structure _ATL_COM_MODULE70

Utilisé par le code COM dans ATL.

## <a name="syntax"></a>Syntaxe

```cpp
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>Membres

`cbSize`<br/>
Taille de la structure, utilisée pour le contrôle de version.

`m_hInstTypeLib`<br/>
Instance de handle vers la bibliothèque de types pour ce module.

`m_ppAutoObjMapFirst`<br/>
Adresse de l’élément de tableau indiquant le début des entrées de mappage d’objets pour ce module.

`m_ppAutoObjMapLast`<br/>
Adresse de l’élément de tableau indiquant la fin des entrées de mappage d’objet pour ce module.

`m_csObjMap`<br/>
Section critique pour sérialiser l’accès aux entrées de mappage d’objets. Utilisé en interne par ATL.

## <a name="remarks"></a>Notes

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) est défini comme un typedef de _ATL_COM_MODULE70.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)
