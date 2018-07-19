---
title: Cmfctabdroptarget, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2991135d7cbb7e2e9df66e871b5d047e69b93d16
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852966"
---
# <a name="cmfctabdroptarget-class"></a>Cmfctabdroptarget, classe
Fournit le mécanisme de communication entre un contrôle onglet et les bibliothèques OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCTabDropTarget : public COleDropTarget  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|`CMFCTabDropTarget::CMFCTabDropTarget`|Constructeur par défaut.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Appelé par le framework lorsque l’utilisateur fait glisser un objet dans une fenêtre de l’onglet. (Substitue [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|  
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Appelé par le framework lorsque l’utilisateur fait glisser un objet en dehors de la fenêtre de l’onglet qui a le focus. (Substitue [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|  
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Appelé par le framework lorsque l’utilisateur fait glisser un objet sur l’onglet de fenêtre qui a le focus. (Substitue [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|  
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton de la souris à la fin d’une opération glisser. (Substitue [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|  
|[CMFCTabDropTarget::Register](#register)|Inscrit le contrôle en tant que peut être la cible d’une opération de glisser-déplacer OLE.|  
  
### <a name="remarks"></a>Notes  
 Cette classe fournit la prise en charge du glisser-déplacer à la `CMFCBaseTabCtrl` classe. Si votre application initialise les bibliothèques OLE en utilisant le [AfxOleInit](ole-initialization.md#afxoleinit) (fonction), `CMFCBaseTabCtrl` objets s’enregistrent pour les opérations de glisser-déplacer.  
  
 Le `CMFCTabDropTarget` classe étend sa classe de base en rendant l’onglet situé sous le curseur lorsqu’une opération de glissement se produit active. Pour plus d’informations sur les opérations de glisser-déplacer, consultez [glisser-déposer (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment construire un objet `CMFCTabDropTarget` et utiliser sa méthode `Register`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleDropTarget](../../mfc/reference/coledroptarget-class.md)  
  
 [CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxbasetabctrl.h  
  
##  <a name="ondragenter"></a>  CMFCTabDropTarget::OnDragEnter  
 Appelé par le framework lorsque l’utilisateur fait glisser un objet dans une fenêtre de l’onglet.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pWnd*|Non utilisé.|  
|[in] *pDataObject*|Pointeur vers l’objet de l’utilisateur fait glisser.|  
|[in] *dwKeyState*|Contient l’état des touches de modification. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.|  
|[in] *point*|L’emplacement du curseur en coordonnées clientes.|  
  
### <a name="return-value"></a>Valeur de retour  
 L’effet qui se produit si le déplacement se produit à l’emplacement spécifié par *point*. Il peut être une ou plusieurs des opérations suivantes :  
  
- DROPEFFECT_NONE  
  
- DROPEFFECT_COPY  
  
- DROPEFFECT_MOVE  
  
- DROPEFFECT_LINK  
  
- DROPEFFECT_SCROLL  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne DROPEFFECT_NONE si l’infrastructure de la barre d’outils n’est pas en mode de personnalisation ou le format de données du Presse-papiers n’est pas disponible. Sinon, elle retourne le résultat de l’appel `CMFCBaseTabCtrl::OnDragEnter` avec les paramètres fournis.  
  
 Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données du Presse-papiers, consultez [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="ondragleave"></a>  CMFCTabDropTarget::OnDragLeave  
 Appelé par le framework lorsque l’utilisateur fait glisser un objet en dehors de la fenêtre de l’onglet qui a le focus.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pWnd*|Non utilisé.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle la `CMFCBaseTabCtrl::OnDragLeave` méthode pour effectuer l’opération glisser.  
  
##  <a name="ondragover"></a>  CMFCTabDropTarget::OnDragOver  
 Appelé par le framework lorsque l’utilisateur fait glisser un objet sur l’onglet de fenêtre qui a le focus.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pWnd*|Non utilisé.|  
|[in] *pDataObject*|Pointeur vers l’objet de l’utilisateur fait glisser.|  
|[in] *dwKeyState*|Contient l’état des touches de modification. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.|  
|[in] *point*|L’emplacement du pointeur de la souris dans les coordonnées clientes.|  
  
### <a name="return-value"></a>Valeur de retour  
 L’effet qui se produit si le déplacement se produit à l’emplacement spécifié par *point*. Il peut être une ou plusieurs des opérations suivantes :  
  
- DROPEFFECT_NONE  
  
- DROPEFFECT_COPY  
  
- DROPEFFECT_MOVE  
  
- DROPEFFECT_LINK  
  
- DROPEFFECT_SCROLL  
  
### <a name="remarks"></a>Notes  
 Cette méthode rend l’onglet situé sous le curseur lorsqu’une opération de glissement se produit active. Elle retourne DROPEFFECT_NONE si l’infrastructure de la barre d’outils n’est pas en mode de personnalisation ou le format de données du Presse-papiers n’est pas disponible. Sinon, elle retourne le résultat de l’appel `CMFCBaseTabCtrl::OnDragOver` avec les paramètres fournis.  
  
 Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données du Presse-papiers, consultez [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="ondropex"></a>  CMFCTabDropTarget::OnDropEx  
 Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton de la souris à la fin d’une opération glisser.  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pWnd*|Non utilisé.|  
|[in] *pDataObject*|Pointeur vers l’objet de l’utilisateur fait glisser.|  
|[in] *dropEffect*|L’opération de liste par défaut.|  
|[in] *liste déroulante*|Non utilisé.|  
|[in] *point*|L’emplacement du pointeur de la souris dans les coordonnées clientes.|  
  
### <a name="return-value"></a>Valeur de retour  
 L’effet obtenu. Il peut être une ou plusieurs des opérations suivantes :  
  
- DROPEFFECT_NONE  
  
- DROPEFFECT_COPY  
  
- DROPEFFECT_MOVE  
  
- DROPEFFECT_LINK  
  
- DROPEFFECT_SCROLL  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle `CMFCBaseTabCtrl::OnDrop` si l’infrastructure de la barre d’outils est en mode de personnalisation et le format de données du Presse-papiers est disponible. Si l’appel à `CMFCBaseTabCtrl::OnDrop` retourne une valeur différente de zéro, cette méthode retourne l’effet de dépôt par défaut spécifié par *dropEffect*. Sinon, cette méthode retourne DROPEFFECT_NONE. Pour plus d’informations sur les effets de déplacement, consultez [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).  
  
 Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données du Presse-papiers, consultez [COleDataObject::IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).  
  
##  <a name="register"></a>  CMFCTabDropTarget::Register  
 Inscrit le contrôle en tant que peut être la cible d’une opération de glisser-déplacer OLE.  
  
```  
BOOL Register(CMFCBaseTabCtrl *pOwner);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] *pOwner*|Le contrôle onglet à inscrire comme cible de dépôt.|  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’inscription a réussi ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [COleDropTarget::Register](../../mfc/reference/coledroptarget-class.md#register) pour enregistrer le contrôle pour les opérations de glisser-déplacer.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Glisser-déposer (OLE)](../../mfc/drag-and-drop-ole.md)



