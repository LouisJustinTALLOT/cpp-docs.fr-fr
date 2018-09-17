---
title: Classe de CSplitterWndEx | Microsoft Docs
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
ms.openlocfilehash: a2b7abb9cbc3f75c2b4f50f87a1bfdd818e6a3f8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707341"
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
 Remplacer le `OnDrawSplitter` méthode pour personnaliser l’apparence des composants graphiques d’une fenêtre fractionnée.  
  
 Le `CSplitterWndEx` classe est utilisée conjointement avec la [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), et [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) méthodes qui sont implémenté par un gestionnaire visuel. Pour déclencher un gestionnaire visuel dessiner une fenêtre fractionnée dans votre application, remplacez les déclarations de la `CSplitterWnd` classe avec la `CSplitterWndEx` classe. Pour les applications de fenêtre frame, la classe de fenêtre de séparateur est déclarée dans la classe CMainFrame qui se trouve dans mainfrm.h. Pour obtenir un exemple, consultez le `OutlookDemo` exemple dans le répertoire d’exemples.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>Configuration requise  
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
*contrôleur de domaine principal*<br/>
[in] Pointeur vers le contexte de périphérique. Si ce paramètre est NULL, le framework redessine la fenêtre active.  
  
*%nLes*<br/>
[in] Parmi les `CSplitterWnd::ESplitType` des valeurs d’énumération qui spécifie l’élément de fenêtre de séparateur à dessiner. Les valeurs valides sont `splitBox`, `splitBar`, `splitIntersection` et `splitBorder`.  
  
*Rect*<br/>
[in] Un rectangle englobant qui spécifie les dimensions et l’emplacement où dessiner l’élément de fenêtre de séparateur spécifié.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../hierarchy-chart.md)   
 [Classes](mfc-classes.md)   
 [CSplitterWnd, classe](csplitterwnd-class.md)   
 [CMFCVisualManager, classe](cmfcvisualmanager-class.md)