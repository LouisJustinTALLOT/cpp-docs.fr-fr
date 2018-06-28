---
title: Classe de COleIPFrameWnd | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9136f3c57358a71186b196a4223b401e6abad2a9
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040023"
---
# <a name="coleipframewnd-class"></a>Classe de COleIPFrameWnd
Base pour la fenêtre de modification sur place de votre application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Construit un objet `COleIPFrameWnd`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Appelé par l’infrastructure lorsqu’un élément est activé pour la modification sur place.|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Appelé par l’infrastructure pour repositionner la fenêtre de modification sur place.|  
  
## <a name="remarks"></a>Notes  
 Cette classe crée et les positions des barres dans la fenêtre de document de l’application conteneur de contrôles. Il gère également les notifications générées par incorporé [COleResizeBar](../../mfc/reference/coleresizebar-class.md) lorsque l’utilisateur redimensionne la fenêtre de modification sur place de l’objet.  
  
 Pour plus d’informations sur l’utilisation de `COleIPFrameWnd`, consultez l’article [Activation](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd  
 Construit un `COleIPFrameWnd` de l’objet et initialise ses informations d’état de la place, ce qui sont stockées dans une structure de type **OLEINPLACEFRAMEINFO**.  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) dans le Kit de développement logiciel Windows.  
  
##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars  
 Le framework appelle la `OnCreateControlBars` lorsqu’un élément est activé pour la modification sur place de la fonction.  
  
```  
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,  
    CWnd* pWndDoc);

 
virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,  
    CFrameWnd* pWndDoc);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWndFrame*  
 Pointeur vers la fenêtre frame de l’application conteneur.  
  
 *pWndDoc*  
 Pointeur vers la fenêtre du conteneur au niveau du document. Peut être **NULL** si le conteneur est une application SDI.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction pour effectuer tout traitement spécial requis lors de la création de barres de contrôles.  
  
##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame  
 Le framework appelle la `RepositionFrame` fonction membre pour disposer les barres de contrôles et repositionner la fenêtre de modification sur place sont visibles.  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpPosRect*  
 Pointeur vers un `RECT` structure ou un `CRect` objet contenant l’à la place frame actuelle coordonnées de position de fenêtre, en pixels, par rapport à la zone cliente.  
  
 *lpClipRect*  
 Pointeur vers un `RECT` structure ou un `CRect` objet contenant l’à la place frame rectangle de découpage coordonnées actuelles de fenêtre, en pixels, par rapport à la zone cliente.  
  
### <a name="remarks"></a>Notes  
 Diffère de la disposition des barres de contrôles dans la fenêtre de conteneur qui effectuées par une fenêtre frame de non-OLE. La fenêtre frame de non-OLE calcule les positions des barres de contrôles et d’autres objets à partir d’une taille de fenêtre frame donné, comme dans un appel à [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). La zone cliente est ce qui reste après la soustraction de l’espace pour les barres de contrôles et d’autres objets. A `COleIPFrameWnd` fenêtre, positionne quant à eux, les barres d’outils conformément à une zone client donné. En d’autres termes, `CFrameWnd::RecalcLayout` fonctionne « depuis l’extérieur, », tandis que `COleIPFrameWnd::RepositionFrame` fonctionne « de l’intérieur. »  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd (classe)](../../mfc/reference/cframewnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)
