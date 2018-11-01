---
title: _Atlcreatewnddata, structure
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 860d5772279d0ca0581a8cac1e0ef224f829586d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534184"
---
# <a name="atlcreatewnddata-structure"></a>_Atlcreatewnddata, structure

Cette structure contient des données d’instance de classe dans le code de fenêtrage dans ATL.

## <a name="syntax"></a>Syntaxe

```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Membres

`m_pThis`<br/>
Le **cela** pointeur utilisé pour accéder à l’instance de classe dans les procédures de fenêtre.

`m_dwThreadID`<br/>
L’ID de thread de l’instance actuelle de la classe.

`m_pNext`<br/>
Pointeur vers la prochaine `_AtlCreateWndData` objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)

