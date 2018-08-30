---
title: COleDropSource, classe | Microsoft Docs
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
ms.openlocfilehash: f0994eb1b0293bb31fdb1cd4659256b978ebd69d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219363"
---
# <a name="coledropsource-class"></a>COleDropSource, classe
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
 Le [COleDropTarget](../../mfc/reference/coledroptarget-class.md) classe gère la partie réception de l’opération de glisser-déplacer. Le `COleDropSource` objet est chargé de déterminer quand une opération glisser commence, fournir des commentaires pendant l’opération glisser et déterminer quand l’opération glisser se termine.  
  
 Pour utiliser un `COleDropSource` d’objet, appelez simplement le constructeur. Cela simplifie le processus permettant de déterminer quels événements, tels qu’un clic de souris, commenceront une opération de glisser à l’aide [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), ou [ COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) (fonction). Ces fonctions créera un `COleDropSource` objet pour vous. Vous souhaiterez peut-être modifier le comportement par défaut de la `COleDropSource` fonctions substituables. Ces fonctions de membre seront appelées aux moments appropriés par l’infrastructure.  
  
 Pour plus d’informations sur les opérations de glisser-déplacer à l’aide de OLE, consultez l’article [glisser-déposer (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Pour plus d’informations, consultez [IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource) dans le SDK Windows.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropSource`  
  
## <a name="requirements"></a>Configuration requise  
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
 *dropEffect*  
 L’effet que vous souhaitez afficher à l’utilisateur, ce qui indique généralement ce qui se passe si une opération déplacer est effectuée à ce stade, avec les données sélectionnées. En règle générale, c’est la valeur retournée par l’appel le plus récent à [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) ou [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Il peut être une ou plusieurs des opérations suivantes :  
  
- DROPEFFECT_NONE une chute ne serait pas autorisée.  
  
- DROPEFFECT_COPY une opération de copie est réalisée.  
  
- DROPEFFECT_MOVE serait exécutée une opération de déplacement.  
  
- Lien d’un DROPEFFECT_LINK à partir de données déplacées vers les données d’origine serait être établi.  
  
- Opération de défilement DROPEFFECT_SCROLL un glissement doit se produire ou se produit dans la cible.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur DRAGDROP_S_USEDEFAULTCURSORS si glisser est en cours d’exécution, NOERROR si elle n’est pas.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour fournir des commentaires à l’utilisateur sur ce qui se passerait si une opération déplacer est effectuée à ce stade. L’implémentation par défaut utilise les curseurs par défaut OLE. Pour plus d’informations sur les opérations de glisser-déplacer à l’aide de OLE, consultez l’article [glisser-déposer (OLE)](../../mfc/drag-and-drop-ole.md).  
  
 Pour plus d’informations, consultez [IDropSource::GiveFeedback](/windows/desktop/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::DragOver](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragover), et [IDropTarget::DragEnter](/windows/desktop/api/oleidl/nf-oleidl-idroptarget-dragenter) dans le SDK Windows.  
  
##  <a name="onbegindrag"></a>  COleDropSource::OnBeginDrag  
 Appelé par le framework lorsque survient un événement qui pourrait commencer une opération glisser, par exemple en appuyant sur le bouton gauche de la souris.  
  
```  
virtual BOOL OnBeginDrag(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointe vers la fenêtre qui contient les données sélectionnées.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le glissement est autorisé, sinon 0.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction si vous souhaitez modifier la façon dont le processus de déplacement est démarré. L’implémentation par défaut capture la souris et reste en mode glisser jusqu'à ce que l’utilisateur clique sur le bouton gauche ou droit de la souris ou appuie sur ÉCHAP, moment auquel il relâche la souris.  
  
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
  
 *dwKeyState*  
 Contient l’état des touches de modification du clavier. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.  
  
### <a name="return-value"></a>Valeur de retour  
 DRAGDROP_S_CANCEL si la touche ÉCHAP ou le bouton droit est appuyé ou le bouton gauche est déclenché avant de faire glisser commence. DRAGDROP_S_DROP si une opération de déplacement doit se produire. Sinon S_OK.  
  
### <a name="remarks"></a>Notes  
 Remplacement de que cette fonction si vous souhaitez modifier le point en les faisant glisser est annulée ou une opération déplacer se produit.  
  
 L’implémentation par défaut initialise la liste déroulante ou annule l’opération glisser comme suit. Il annule une opération glisser lorsque la touche ÉCHAP ou le bouton droit de la souris est enfoncé. Il lance une opération de déplacement lorsque le bouton gauche de la souris est déclenché après le démarrage de glissement. Sinon, elle retourne S_OK et n’exécute aucune opération supplémentaire.  
  
 Étant donné que cette fonction est appelée fréquemment, il doit être optimisé autant que possible.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



