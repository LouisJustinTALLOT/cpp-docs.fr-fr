---
title: _AtlCreateWndData Structure
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: d6e3168b5c86de5bce3c3b9d3b0fbdea28ae604f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286926"
---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData Structure

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

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)
