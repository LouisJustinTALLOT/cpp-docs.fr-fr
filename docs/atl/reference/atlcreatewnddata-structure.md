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
ms.openlocfilehash: 6453156a59b73bcb06c7c86920e1dc524874cef8
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168538"
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
Pointeur **This** utilisé pour accéder à l’instance de classe dans les procédures de fenêtre.

`m_dwThreadID`<br/>
ID de thread de l’instance de classe en cours.

`m_pNext`<br/>
Pointeur vers l’objet `_AtlCreateWndData` suivant.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)
