---
title: Classe de COleDropSource | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
dev_langs:
- C++
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e510811fcaac81aa54699250ef37f48ffe1f40e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374895"
---
# <a name="coledropsource-class"></a>Classe de COleDropSource
Permet de faire glisser vers une cible de déplacement des données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDropSource : public CCmdTarget  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDropSource::COleDropSource](#coledropsource)|Construit un objet `COleDropSource`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDropSource::GiveFeedback](#givefeedback)|Modifie le curseur lors d’une opération de glisser-déplacer.|  
|[COleDropSource::OnBeginDrag](#onbegindrag)|Gère la capture de la souris pendant une opération de glisser-déplacer.|  
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Vérifie si le glissement doit continuer.|  
  
## <a name="remarks"></a>Notes  
 Le [COleDropTarget](../../mfc/reference/coledroptarget-class.md) classe gère la partie réception de l’opération de glisser-déplacer. Le `COleDropSource` objet est chargé de déterminer quand une opération glisser commence, fournir des commentaires pendant l’opération de glissement et déterminer quand l’opération de glissement se termine.  
  
 Pour utiliser un `COleDropSource` d’objet, simplement appeler le constructeur. Cela simplifie le processus permettant de déterminer quels événements, par exemple un clic de souris, commencent une opération glisser à l’aide [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), ou [ COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) (fonction). Ces fonctions créera un `COleDropSource` objet pour vous. Vous souhaiterez peut-être modifier le comportement par défaut de la `COleDropSource` fonctions substituables. Ces fonctions de membre seront appelées au moment voulu par l’infrastructure.  
  
 Pour plus d’informations sur les opérations de glisser-déplacer à l’aide de OLE, consultez l’article [glisser-déplacer (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Pour plus d’informations, consultez [IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071) dans le Kit de développement logiciel Windows.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxole.h  
  
##  <a name="coledropsource"></a>  COleDropSource::COleDropSource  
 Construit un objet `COleDropSource`.  
  
```  
COleDropSource();
```  
  
##  <a name="givefeedback"></a>  COleDropSource::GiveFeedback  
 Appelé par l’infrastructure après l’appel [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) ou [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).  
  
```  
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```  
  
### <a name="parameters"></a>Paramètres  
 `dropEffect`  
 L’effet que vous souhaitez afficher à l’utilisateur, ce qui indique généralement ce qui se produit si la suppression s’est produite au niveau de ce point avec les données sélectionnées. Il s’agit généralement de la valeur retournée par l’appel le plus récent à [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) ou [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Il peut être un ou plusieurs des opérations suivantes :  
  
- `DROPEFFECT_NONE` La suppression ne serait pas autorisée.  
  
- `DROPEFFECT_COPY` Une opération de copie doit être effectuée.  
  
- `DROPEFFECT_MOVE` Une opération de déplacement doit être effectuée.  
  
- `DROPEFFECT_LINK` Un lien entre les données déplacées et les données d’origine est établi.  
  
- `DROPEFFECT_SCROLL` Une opération de glissement de défilement est sur le point de se produire ou se produit dans la cible.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **DRAGDROP_S_USEDEFAULTCURSORS** si le déplacement est en cours d’exécution, **NOERROR** si elle n’est pas.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour fournir des commentaires à l’utilisateur sur ce qui se passerait si la suppression s’est produite à ce stade. L’implémentation par défaut utilise les curseurs par défaut OLE. Pour plus d’informations sur les opérations de glisser-déplacer à l’aide de OLE, consultez l’article [glisser-déplacer (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Pour plus d’informations, consultez [IDropSource::GiveFeedback](http://msdn.microsoft.com/library/windows/desktop/ms693723), [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129), et [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) dans le Kit de développement logiciel Windows.  
  
##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag  
 Appelé par le framework lorsqu’un événement qui produit pourrait commencer une opération de glissement, par exemple en appuyant sur le bouton gauche de la souris.  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `pWnd`  
 Pointe vers la fenêtre qui contient les données sélectionnées.  
  
### <a name="return-value"></a>Valeur de retour  
 Non nul en faisant glisser est autorisée, sinon 0.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction si vous souhaitez modifier la manière dont le processus de déplacement est démarré. L’implémentation par défaut capture la souris et reste en mode glisser jusqu'à ce que l’utilisateur clique sur le bouton gauche ou droit de la souris ou appuie sur ÉCHAP, le moment où il relâche la souris.  
  
##  <a name="querycontinuedrag"></a>  COleDropSource::QueryContinueDrag  
 Lorsque vous commencez, cette fonction est appelée plusieurs fois par l’infrastructure jusqu'à ce que l’opération glisser soit annulée ou terminée.  
  
```  
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed, 
    DWORD dwKeyState);
```  
  
### <a name="parameters"></a>Paramètres  
 *bEscapePressed*  
 Indique si la touche ÉCHAP a été enfoncée depuis le dernier appel à `COleDropSource::QueryContinueDrag`.  
  
 `dwKeyState`  
 Contient l’état des touches de modification du clavier. Il s’agit d’une combinaison de plusieurs des opérations suivantes : **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_ MBUTTON**, et **MK_RBUTTON**.  
  
### <a name="return-value"></a>Valeur de retour  
 **DRAGDROP_S_CANCEL** si vous appuyez sur la touche ÉCHAP ou avec le bouton droit, ou du bouton gauche est déclenché avant de faire glisser commence. **DRAGDROP_S_DROP** si une opération de suppression doit se produire. Dans le cas contraire `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Remplacement de que cette fonction si vous souhaitez modifier le point en les faisant glisser est annulée ou une suppression se produit.  
  
 L’implémentation par défaut, lance la liste déroulante ou annule l’opération glisser comme suit. Elle annule une opération glisser lorsque la touche ÉCHAP ou le bouton droit de la souris est enfoncé. Commence une opération de suppression lorsque le bouton gauche de la souris est déclenché après le démarrage de glissement. Sinon, elle retourne `S_OK` et n’exécute aucune opération supplémentaire.  
  
 Étant donné que cette fonction est appelée fréquemment, il doit être optimisé autant que possible.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



