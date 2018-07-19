---
title: COleDropTarget, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
dev_langs:
- C++
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d54a22bd215a80f3e7cab3770a4ba12cd7baffb
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027440"
---
# <a name="coledroptarget-class"></a>COleDropTarget, classe
Fournit le mécanisme de communication entre une fenêtre et les bibliothèques OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDropTarget::COleDropTarget](#coledroptarget)|Construit un objet `COleDropTarget`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDropTarget::OnDragEnter](#ondragenter)|Appelé lorsque le curseur passe tout d’abord la fenêtre.|  
|[COleDropTarget::OnDragLeave](#ondragleave)|Appelé lorsque le curseur est déplacé en dehors de la fenêtre.|  
|[COleDropTarget::OnDragOver](#ondragover)|Appelée à plusieurs reprises lorsque le curseur glisse par-dessus la fenêtre.|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|Appelé pour déterminer si le curseur est déplacé dans la zone de défilement de la fenêtre.|  
|[COleDropTarget::OnDrop](#ondrop)|Appelé lorsque les données sont déplacées dans la fenêtre, le gestionnaire par défaut.|  
|[COleDropTarget::OnDropEx](#ondropex)|Appelé lorsque les données sont déposées dans la fenêtre, gestionnaire initiale.|  
|[COleDropTarget::Register](#register)|Inscrit la fenêtre comme cible de déplacement valide.|  
|[COleDropTarget::Revoke](#revoke)|Provoque la fenêtre faire cesser en cours d’une cible de dépôt valide.|  
  
## <a name="remarks"></a>Notes  
 Création d’un objet de cette classe permet à une fenêtre accepter des données par le biais du mécanisme de glisser-déplacer OLE.  
  
 Pour obtenir une fenêtre pour accepter les commandes de suppression, vous devez tout d’abord créer un objet de la `COleDropTarget` classe, puis appelez le [inscrire](#register) fonction avec un pointeur vers le texte souhaité `CWnd` objet comme seul paramètre.  
  
 Pour plus d’informations sur les opérations de glisser-déplacer à l’aide de OLE, consultez l’article [glisser-déposer (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxole.h  
  
##  <a name="coledroptarget"></a>  COleDropTarget::COleDropTarget  
 Construit un objet de classe `COleDropTarget`.  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>Notes  
 Appelez [inscrire](#register) à associer à cet objet avec une fenêtre.  
  
##  <a name="ondragenter"></a>  COleDropTarget::OnDragEnter  
 Appelé par l’infrastructure quand le curseur est tout d’abord déplacé dans la fenêtre.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointe vers la fenêtre que le curseur est saisie.  
  
 *pDataObject*  
 Pointe vers l’objet de données contenant les données qui peuvent être supprimées.  
  
 *dwKeyState*  
 Contient l’état des touches de modification. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.  
  
 *point*  
 Contient l’emplacement actuel du curseur en coordonnées clientes.  
  
### <a name="return-value"></a>Valeur de retour  
 L’effet qui serait utilisé si une opération déplacer ont été tentée à l’emplacement spécifié par *point*. Il peut être une ou plusieurs des opérations suivantes :  
  
- DROPEFFECT_NONE une chute ne serait pas autorisée.  
  
- DROPEFFECT_COPY une opération de copie est réalisée.  
  
- DROPEFFECT_MOVE serait exécutée une opération de déplacement.  
  
- Lien d’un DROPEFFECT_LINK à partir de données déplacées vers les données d’origine serait être établi.  
  
- Opération de défilement DROPEFFECT_SCROLL un glissement doit se produire ou se produit dans la cible.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour autoriser les opérations de suppression peut se produire dans la fenêtre. L’implémentation par défaut appelle [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), qui renvoie simplement DROPEFFECT_NONE par défaut.  
  
 Pour plus d’informations, consultez [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) dans le SDK Windows.  
  
##  <a name="ondragleave"></a>  COleDropTarget::OnDragLeave  
 Appelé par le framework lorsque le curseur quitte la fenêtre lorsqu’une opération de glisser-déplacer est en vigueur.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointe vers la fenêtre que le curseur quitte.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction si vous souhaitez un comportement spécial lorsque l’opération glisser quitte la fenêtre spécifiée. L’implémentation par défaut de cette fonction appelle [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).  
  
 Pour plus d’informations, consultez [IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110) dans le SDK Windows.  
  
##  <a name="ondragover"></a>  COleDropTarget::OnDragOver  
 Appelé par le framework lorsque le curseur glisse par-dessus la fenêtre.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointe vers la fenêtre qui est placé le curseur.  
  
 *pDataObject*  
 Pointe vers l’objet de données qui contient les données à supprimer.  
  
 *dwKeyState*  
 Contient l’état des touches de modification. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.  
  
 *point*  
 Contient l’emplacement actuel du curseur en coordonnées clientes.  
  
### <a name="return-value"></a>Valeur de retour  
 L’effet qui serait utilisé si une opération déplacer ont été tentée à l’emplacement spécifié par *point*. Il peut être une ou plusieurs des opérations suivantes :  
  
- DROPEFFECT_NONE une chute ne serait pas autorisée.  
  
- DROPEFFECT_COPY une opération de copie est réalisée.  
  
- DROPEFFECT_MOVE serait exécutée une opération de déplacement.  
  
- Lien d’un DROPEFFECT_LINK à partir de données déplacées vers les données d’origine serait être établi.  
  
- DROPEFFECT_SCROLL indique qu’une opération glisser de défilement est sur le point de se produire ou se produit dans la cible.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être substituée pour autoriser les opérations de suppression peut se produire dans la fenêtre. L’implémentation par défaut de cette fonction appelle [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), qui renvoie DROPEFFECT_NONE par défaut. Étant donné que cette fonction est appelée fréquemment pendant une opération de glisser-déplacer, il doit être optimisé autant que possible.  
  
 Pour plus d’informations, consultez [IDropTarget::DragOver](http://msdn.microsoft.com/library/windows/desktop/ms680129) dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>  COleDropTarget::OnDragScroll  
 Appelé par le framework avant d’appeler [OnDragEnter](#ondragenter) ou [OnDragOver](#ondragover) pour déterminer si *point* est dans la zone de défilement.  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointe vers la fenêtre, sur que le curseur se trouve actuellement.  
  
 *dwKeyState*  
 Contient l’état des touches de modification. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.  
  
 *point*  
 Contient l’emplacement du curseur, en pixels, par rapport à l’écran.  
  
### <a name="return-value"></a>Valeur de retour  
 L’effet qui serait utilisé si une opération déplacer ont été tentée à l’emplacement spécifié par *point*. Il peut être une ou plusieurs des opérations suivantes :  
  
- DROPEFFECT_NONE une chute ne serait pas autorisée.  
  
- DROPEFFECT_COPY une opération de copie est réalisée.  
  
- DROPEFFECT_MOVE serait exécutée une opération de déplacement.  
  
- Lien d’un DROPEFFECT_LINK à partir de données déplacées vers les données d’origine serait être établi.  
  
- DROPEFFECT_SCROLL indique qu’une opération glisser de défilement est sur le point de se produire ou se produit dans la cible.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction lorsque vous souhaitez fournir un comportement spécial pour cet événement. L’implémentation par défaut de cette fonction appelle [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), qui renvoie DROPEFFECT_NONE et fait défiler la fenêtre lorsque le curseur est déplacé dans la zone de défilement par défaut à l’intérieur de la bordure de la fenêtre.  
  
##  <a name="ondrop"></a>  COleDropTarget::OnDrop  
 Appelé par le framework lorsqu’une opération de déplacement doit se produire.  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
*pWnd*  
 Pointe vers la fenêtre, sur que le curseur se trouve actuellement.  
  
*pDataObject*  
Pointe vers l’objet de données qui contient les données à supprimer.  
  
*dropEffect*  
L’effet que l’utilisateur a choisi pour l’opération de déplacement. Il peut être une ou plusieurs des opérations suivantes :  
  
 - DROPEFFECT_COPY une opération de copie est réalisée.  
       
 - DROPEFFECT_MOVE serait exécutée une opération de déplacement.  
      
 - Lien d’un DROPEFFECT_LINK à partir de données déplacées vers les données d’origine serait être établi.  
  
*point*  
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le déplacement a réussi ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Le framework appelle d’abord [OnDropEx](#ondropex). Si le `OnDropEx` fonction ne gère pas la liste déroulante, puis, l’infrastructure appelle cette fonction membre, `OnDrop`. En règle générale, l’application remplace [OnDropEx](../../mfc/reference/cview-class.md#ondropex) dans la classe d’affichage pour gérer le bouton droit de la souris glisser -déplacer. En règle générale, la classe d’affichage [OnDrop](../../mfc/reference/cview-class.md#ondrop) sert à gérer simple glisser -déplacer.  
  
 L’implémentation par défaut de `COleDropTarget::OnDrop` appels [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), qui renvoie simplement FALSE par défaut.  
  
 Pour plus d’informations, consultez [IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) dans le SDK Windows.  
  
##  <a name="ondropex"></a>  COleDropTarget::OnDropEx  
 Appelé par le framework lorsqu’une opération de déplacement doit se produire.  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointe vers la fenêtre, sur que le curseur se trouve actuellement.  
  
 *pDataObject*  
 Pointe vers l’objet de données qui contient les données à supprimer.  
  
 *dropDefault*  
 L’effet que l’utilisateur a choisi pour l’opération de déplacement par défaut en fonction de l’état actuel de la clé. Il peut être DROPEFFECT_NONE. Effets de déplacement sont décrits dans la section Notes.  
  
 *liste déroulante*  
 Liste des effets de déplacement qui prend en charge de la source de dépôt. Valeurs d’effet de déplacement peuvent être combinées à l’aide de l’opération OR au niveau du bit (**&#124;**) opération. Effets de déplacement sont décrits dans la section Notes.  
  
 *point*  
 Contient l’emplacement du curseur, en pixels, par rapport à l’écran.  
  
### <a name="return-value"></a>Valeur de retour  
 L’effet résultant de la tentative de déplacement à l’emplacement spécifié par *point*. Effets de déplacement sont décrits dans la section Notes.  
  
### <a name="remarks"></a>Notes  
 Tout d’abord, l’infrastructure appelle cette fonction. S’il ne gère pas la liste déroulante, le framework appelle ensuite [OnDrop](#ondrop). En règle générale, vous remplacerez [OnDropEx](../../mfc/reference/cview-class.md#ondropex) dans la classe d’affichage pour prendre en charge le bouton droit de la souris glisser -déplacer. En règle générale, la classe d’affichage [OnDrop](../../mfc/reference/cview-class.md#ondrop) est utilisé pour gérer le cas de prise en charge pour un simple glisser -déplacer.  
  
 L’implémentation par défaut de `COleDropTarget::OnDropEx` appels [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Par défaut, [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) renvoie simplement une valeur factice pour indiquer la [OnDrop](#ondrop) fonction membre doit être appelée.  
  
 Effets de déplacement décrivent l’action associée à une opération de déplacement. Consultez la liste des effets de la liste suivante :  
  
 - DROPEFFECT_NONE une chute ne serait pas autorisée.  
  
 - DROPEFFECT_COPY une opération de copie est réalisée.  
  
 - DROPEFFECT_MOVE serait exécutée une opération de déplacement.  
  
 - Lien d’un DROPEFFECT_LINK à partir de données déplacées vers les données d’origine serait être établi.  
  
 - DROPEFFECT_SCROLL indique qu’une opération glisser de défilement est sur le point de se produire ou se produit dans la cible.  
  
 Pour plus d’informations, consultez [IDropTarget::Drop](http://msdn.microsoft.com/library/windows/desktop/ms687242) dans le SDK Windows.  
  
##  <a name="register"></a>  COleDropTarget::Register  
 Appelez cette fonction pour inscrire votre fenêtre avec les DLL OLE comme cible de déplacement valide.  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointe vers la fenêtre qui doit être enregistré en tant que cible de dépôt.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’inscription a réussi ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée pour les opérations de suppression d’être acceptés.  
  
 Pour plus d’informations, consultez [RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405) dans le SDK Windows.  
  
##  <a name="revoke"></a>  COleDropTarget::Revoke  
 Appelez cette fonction avant la destruction de n’importe quelle fenêtre qui a été enregistré comme une cible de dépôt via un appel à [inscrire](#register) pour le supprimer de la liste des cibles de dépôt.  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction est appelée automatiquement à partir de la [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) gestionnaire pour la fenêtre qui a été inscrite, donc il n’est généralement pas nécessaire d’appeler cette fonction explicitement.  
  
 Pour plus d’informations, consultez [RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643) dans le SDK Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [Exemple MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleDropSource, classe](../../mfc/reference/coledropsource-class.md)
