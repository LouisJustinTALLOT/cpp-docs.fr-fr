---
title: _Atlcreatewnddata, structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5751fa3c5c8bc20f287ca3c48d885fc41c60ba0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764327"
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

`m_pThis`  
Le **cela** pointeur utilisé pour accéder à l’instance de classe dans les procédures de fenêtre.

`m_dwThreadID`  
L’ID de thread de l’instance actuelle de la classe.

`m_pNext`  
Pointeur vers la prochaine `_AtlCreateWndData` objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)

