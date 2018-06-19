---
title: Interface COM Points d’entrée | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02aa70706df65318f2fbfd8103dff04a47ae2155
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341409"
---
# <a name="com-interface-entry-points"></a>Interface COM, points d'entrée
Pour les fonctions membres d’une interface COM, utilisez la [METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue) macro pour maintenir l’état global approprié lors de l’appel de méthodes d’une interface exportée.  
  
 En général, les fonctions membres des interfaces implémentées par `CCmdTarget`-objets dérivés utilisent déjà cette macro pour fournir l’initialisation automatique de la `pThis` pointeur. Par exemple :  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]  
  
 Pour plus d’informations, consultez [Technical Note 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) sur MFC/OLE **IUnknown** implémentation.  
  
 Le `METHOD_PROLOGUE` macro est définie en tant que :  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 La partie de la macro concernée par la gestion de l’état global est la suivante :  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 Dans cette expression, *pointeur m_pModuleState* est censé pour être une variable membre de l’objet conteneur. Il est implémenté par le `CCmdTarget` classe de base et est initialisée à la valeur appropriée par `COleObjectFactory`, lorsque l’objet est instancié.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des données d’état des modules MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

