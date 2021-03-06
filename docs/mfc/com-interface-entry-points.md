---
description: En savoir plus sur les points d’entrée de l’interface COM
title: Interface COM, points d'entrée
ms.date: 03/27/2019
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 805ac906c3ccca246d1af71c689aaf768f789999
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160010"
---
# <a name="com-interface-entry-points"></a>Interface COM, points d'entrée

Pour les fonctions membres d’une interface COM, utilisez la `METHOD_PROLOGUE` macro pour conserver l’état global approprié lors de l’appel de méthodes d’une interface exportée.

En général, les fonctions membres des interfaces implémentées par `CCmdTarget` les objets dérivés de utilisent déjà cette macro pour permettre l’initialisation automatique du `pThis` pointeur. Par exemple :

[!code-cpp[NVC_MFCConnectionPoints#5](codesnippet/cpp/com-interface-entry-points_1.cpp)]

Pour plus d’informations, consultez la [note technique 38](tn038-mfc-ole-iunknown-implementation.md) sur l’implémentation de MFC/OLE `IUnknown` .

La `METHOD_PROLOGUE` macro est définie comme suit :

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

La partie de la macro concernée par la gestion de l’état global est la suivante :

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

Dans cette expression, *m_pModuleState* est supposé être une variable membre de l’objet conteneur. Elle est implémentée par la `CCmdTarget` classe de base et est initialisée à la valeur appropriée par `COleObjectFactory` , lorsque l’objet est instancié.

## <a name="see-also"></a>Voir aussi

[Gestion des données d’état des modules MFC](managing-the-state-data-of-mfc-modules.md)
