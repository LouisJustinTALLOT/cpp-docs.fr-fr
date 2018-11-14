---
title: Interface COM, points d'entrée
ms.date: 11/04/2016
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 0a8db9c6920b4223296f700d084e0b59b9b3ef15
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521217"
---
# <a name="com-interface-entry-points"></a>Interface COM, points d'entrée

Pour les fonctions de membre d’une interface COM, utilisez la [METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue) macro pour maintenir l’état global approprié lors de l’appel de méthodes d’une interface exportée.

En règle générale, les fonctions membres des interfaces implémentées par `CCmdTarget`-objets dérivés utilisent déjà cette macro pour fournir l’initialisation automatique de la `pThis` pointeur. Exemple :

[!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]

Pour plus d’informations, consultez [Technical Note 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) sur MFC/OLE `IUnknown` implémentation.

Le `METHOD_PROLOGUE` macro est définie en tant que :

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

La partie de la macro concernée par la gestion de l’état global est :

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

Dans cette expression, *pointeur m_pModuleState* est supposé pour être une variable de membre de l’objet conteneur. Il est implémenté par le `CCmdTarget` classe de base et est initialisé avec la valeur appropriée en `COleObjectFactory`, lorsque l’objet est instancié.

## <a name="see-also"></a>Voir aussi

[Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

