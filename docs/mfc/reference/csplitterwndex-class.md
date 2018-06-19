---
title: Classe de CSplitterWndEx | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0dfacc6bf08aa5b36288a9933ffa9980937f2b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368873"
---
# <a name="csplitterwndex-class"></a>Classe de CSplitterWndEx



Représente une fenêtre fractionnée personnalisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|Constructeur par défaut.|  
|`CSplitterWndEx::~CSplitterWndEx`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Appelé par l’infrastructure pour dessiner une fenêtre fractionnée. (Substitue [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|  
  
## <a name="remarks"></a>Notes  
 Remplacer la `OnDrawSplitter` méthode pour personnaliser l’apparence des composants de graphiques d’une fenêtre fractionnée.  
  
 Le `CSplitterWndEx` classe est utilisée conjointement avec la [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), et [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) , ces méthodes sont implémentée par un gestionnaire visuel. Pour qu’un gestionnaire visuel dessiner une fenêtre fractionnée dans votre application, remplacez les déclarations de la `CSplitterWnd` classe avec la `CSplitterWndEx` classe. Pour les applications de fenêtre frame, la classe de fenêtre fractionnée est déclarée dans la classe CMainFrame qui se trouve dans mainfrm.h. Pour obtenir un exemple, consultez le `OutlookDemo` présenté dans le répertoire Samples.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxsplitterwndex.h  
  
##  <a name="ondrawsplitter"></a>  CSplitterWndEx::OnDrawSplitter  
 Appelé par l’infrastructure pour dessiner une fenêtre fractionnée.  
  
```  
virtual void OnDrawSplitter(  
   CDC* pDC,  
   ESplitType nType,  
   const CRect& rect   
);  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers le contexte de périphérique. Si ce paramètre est `NULL`, le framework redessine la fenêtre active.  
  
 [in] `nType`  
 Parmi les `CSplitterWnd::ESplitType` des valeurs d’énumération qui spécifie l’élément de la fenêtre fractionnée à dessiner. Les valeurs valides sont `splitBox`, `splitBar`, `splitIntersection` et `splitBorder`.  
  
 [in] `rect`  
 Un rectangle englobant qui spécifie les dimensions et l’emplacement pour dessiner l’élément de fenêtre de fractionnement spécifiée.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../hierarchy-chart.md)   
 [Classes](mfc-classes.md)   
 [Classe de CSplitterWnd](csplitterwnd-class.md)   
 [CMFCVisualManager, classe](cmfcvisualmanager-class.md)