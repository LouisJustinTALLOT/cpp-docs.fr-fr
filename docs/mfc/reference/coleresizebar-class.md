---
title: Classe de COleResizeBar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3046fa4c9446afeba45fd41a6b571ccf58f2cfb
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040114"
---
# <a name="coleresizebar-class"></a>Classe de COleResizeBar
Type de barre de contrôle qui prend en charge le redimensionnement des éléments OLE sur place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleResizeBar::COleResizeBar](#coleresizebar)|Construit un objet `COleResizeBar`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleResizeBar::Create](#create)|Crée et initialise une fenêtre enfant Windows et l’associe à la `COleResizeBar` objet.|  
  
## <a name="remarks"></a>Notes  
 `COleResizeBar` les objets apparaissent en tant qu’un [CRectTracker](../../mfc/reference/crecttracker-class.md) avec une bordure hachurée et externe des poignées de redimensionnement.  
  
 `COleResizeBar` les objets sont généralement incorporés membres d’objets de fenêtre frame dérivés de la [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) classe.  
  
 Pour plus d’informations, consultez l’article [Activation](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="coleresizebar"></a>  COleResizeBar::COleResizeBar  
 Construit un objet `COleResizeBar`.  
  
```  
COleResizeBar();
```  
  
### <a name="remarks"></a>Notes  
 Appelez **créer** pour créer l’objet de barre de redimensionnement.  
  
##  <a name="create"></a>  COleResizeBar::Create  
 Crée une fenêtre enfant et l’associe le `COleResizeBar` objet.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_RESIZE_BAR);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParentWnd*  
 Pointeur vers la fenêtre parente de la barre de redimensionnement.  
  
 *dwStyle*  
 Spécifie le [style de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) attributs.  
  
 *nID*  
 ID de fenêtre enfant de la barre de redimensionnement.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la barre de redimensionnement a été créée ; Sinon, 0.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC SUPERPAD](../../visual-cpp-samples.md)   
 [CControlBar (classe)](../../mfc/reference/ccontrolbar-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)
