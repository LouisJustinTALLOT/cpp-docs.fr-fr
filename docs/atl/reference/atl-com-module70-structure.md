---
description: 'En savoir plus sur : structure _ATL_COM_MODULE70'
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
ms.openlocfilehash: db2139d1c816c13e6da104f6a6d785ef35a07721
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165406"
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
