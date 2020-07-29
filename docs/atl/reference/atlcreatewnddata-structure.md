---
title: Structure _AtlCreateWndData
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: a38ddb7e3575e883c11b14a9b01004bb54fcd4a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230011"
---
# <a name="_atlcreatewnddata-structure"></a>Structure _AtlCreateWndData

Cette structure contient des données d’instance de classe dans le code de fenêtrage dans ATL.

## <a name="syntax"></a>Syntaxe

```cpp
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Membres

`m_pThis`<br/>
**`this`** Pointeur utilisé pour accéder à l’instance de classe dans les procédures de fenêtre.

`m_dwThreadID`<br/>
ID de thread de l’instance de classe en cours.

`m_pNext`<br/>
Pointeur vers l' `_AtlCreateWndData` objet suivant.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)
