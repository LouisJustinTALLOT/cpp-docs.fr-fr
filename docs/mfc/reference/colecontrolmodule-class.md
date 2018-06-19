---
title: Classe de COleControlModule | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- OleControlModule
dev_langs:
- C++
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 597639145385f4aabcba0e83fef855f7a0779f9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369737"
---
# <a name="colecontrolmodule-class"></a>Classe de COleControlModule
Classe de base à partir de laquelle vous dérivez un objet de module de contrôle OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleControlModule : public CWinApp  
```  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des fonctions membres pour l’initialisation du module de votre contrôle. Chaque module de contrôle OLE qui utilise les classes Microsoft Foundation ne peut contenir un objet dérivé de `COleControlModule`. Cet objet est construit lors de l’établissement d’autres objets globaux de C++. Déclarez votre dérivée `COleControlModule` objet au niveau global.  
  
 Pour plus d’informations sur l’utilisation de la `COleControlModule` de classe, consultez la [CWinApp](../../mfc/reference/cwinapp-class.md) classe et l’article [contrôles ActiveX](../../mfc/mfc-activex-controls.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxctl.h  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC TESTHELP](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



