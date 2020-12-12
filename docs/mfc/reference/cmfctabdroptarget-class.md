---
description: 'En savoir plus sur : classe CMFCTabDropTarget'
title: CMFCTabDropTarget, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: 2a12d171a934912993a61ba4ae915d9e1f3a5cf6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306779"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget, classe

Fournit le mécanisme de communication entre un contrôle onglet et les bibliothèques OLE.

## <a name="syntax"></a>Syntaxe

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|`CMFCTabDropTarget::CMFCTabDropTarget`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[CMFCTabDropTarget :: OnDragEnter](#ondragenter)|Appelée par l’infrastructure quand l’utilisateur fait glisser un objet dans une fenêtre d’onglets. (Substitue [COleDropTarget :: OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget :: OnDragLeave](#ondragleave)|Appelée par l’infrastructure quand l’utilisateur fait glisser un objet en dehors de la fenêtre d’onglets qui a le focus. (Substitue [COleDropTarget :: OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget :: OnDragOver](#ondragover)|Appelée par l’infrastructure quand l’utilisateur fait glisser un objet sur la fenêtre d’onglet qui a le focus. (Substitue [COleDropTarget :: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Appelée par l’infrastructure quand l’utilisateur relâche le bouton de la souris à la fin d’une opération glisser. (Substitue [COleDropTarget :: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget :: Register](#register)|Inscrit le contrôle comme pouvant être la cible d’une opération glisser-déplacer OLE.|

### <a name="remarks"></a>Notes

Cette classe fournit la prise en charge de la fonction glisser-déplacer à la `CMFCBaseTabCtrl` classe. Si votre application initialise les bibliothèques OLE à l’aide de la fonction [AfxOLEInit](ole-initialization.md#afxoleinit) , les `CMFCBaseTabCtrl` objets s’inscrivent pour les opérations de glisser-déplacer.

La `CMFCTabDropTarget` classe étend sa classe de base en faisant en sorte que l’onglet se trouve sous le curseur quand une opération glisser est activée. Pour plus d’informations sur les opérations de glisser-déplacer, consultez glisser-déplacer [OLE](../../mfc/drag-and-drop-ole.md).

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet `CMFCTabDropTarget` et utiliser sa méthode `Register`.

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxbasetabctrl.h

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a> CMFCTabDropTarget :: OnDragEnter

Appelée par l’infrastructure quand l’utilisateur fait glisser un objet dans une fenêtre d’onglets.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWnd*\
[in] Inutilisé.

*pDataObject*\
dans Pointeur vers l’objet que l’utilisateur fait glisser.

*dwKeyState*\
dans Contient l’état des touches de modification. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*\
dans Emplacement du curseur dans les coordonnées clientes.

### <a name="return-value"></a>Valeur renvoyée

Résultat obtenu si le déplacement se produit à l’emplacement spécifié par *point*. Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Notes

Cette méthode retourne DROPEFFECT_NONE si l’infrastructure de barre d’outils n’est pas en mode de personnalisation ou si le format de données du presse-papiers n’est pas disponible. Sinon, elle retourne le résultat de l’appel `CMFCBaseTabCtrl::OnDragEnter` avec les paramètres fournis.

Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar :: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données du presse-papiers, consultez [COleDataObject :: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a> CMFCTabDropTarget :: OnDragLeave

Appelée par l’infrastructure quand l’utilisateur fait glisser un objet en dehors de la fenêtre d’onglets qui a le focus.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*\
[in] Inutilisé.

### <a name="remarks"></a>Notes

Cette méthode appelle la `CMFCBaseTabCtrl::OnDragLeave` méthode pour effectuer l’opération glisser.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a> CMFCTabDropTarget :: OnDragOver

Appelée par l’infrastructure quand l’utilisateur fait glisser un objet sur la fenêtre d’onglet qui a le focus.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWnd*\
[in] Inutilisé.

*pDataObject*\
dans Pointeur vers l’objet que l’utilisateur fait glisser.

*dwKeyState*\
dans Contient l’état des touches de modification. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*\
dans Emplacement du pointeur de la souris dans les coordonnées clientes.

### <a name="return-value"></a>Valeur renvoyée

Résultat obtenu si le déplacement se produit à l’emplacement spécifié par *point*. Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Notes

Cette méthode fait en sorte que l’onglet se trouve sous le curseur lorsqu’une opération glisser est active. Elle retourne DROPEFFECT_NONE si l’infrastructure de barre d’outils n’est pas en mode de personnalisation ou si le format de données du presse-papiers n’est pas disponible. Sinon, elle retourne le résultat de l’appel `CMFCBaseTabCtrl::OnDragOver` avec les paramètres fournis.

Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar :: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données du presse-papiers, consultez [COleDataObject :: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a> CMFCTabDropTarget::OnDropEx

Appelée par l’infrastructure quand l’utilisateur relâche le bouton de la souris à la fin d’une opération glisser.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWnd*\
[in] Inutilisé.

*pDataObject*\
dans Pointeur vers l’objet que l’utilisateur fait glisser.

*dropEffect*\
dans Opération de suppression par défaut.

*Roulant*\
[in] Inutilisé.

*point*\
dans Emplacement du pointeur de la souris dans les coordonnées clientes.

### <a name="return-value"></a>Valeur renvoyée

Effet d’abandon obtenu. Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Notes

Cette méthode appelle `CMFCBaseTabCtrl::OnDrop` si l’infrastructure de barre d’outils est en mode de personnalisation et si le format de données du presse-papiers est disponible. Si l’appel à `CMFCBaseTabCtrl::OnDrop` retourne une valeur différente de zéro, cette méthode retourne l’effet de déplacement par défaut spécifié par *dropEffect*. Sinon, cette méthode retourne DROPEFFECT_NONE. Pour plus d’informations sur les effets de suppression, consultez [COleDropTarget :: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar :: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données du presse-papiers, consultez [COleDataObject :: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetregister"></a><a name="register"></a> CMFCTabDropTarget :: Register

Inscrit le contrôle comme pouvant être la cible d’une opération glisser-déplacer OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Paramètres

*pOwner*\
dans Contrôle onglet à inscrire comme cible de déplacement.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si l’inscription a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode appelle [COleDropTarget :: Register](../../mfc/reference/coledroptarget-class.md#register) pour inscrire le contrôle pour les opérations de glisser-déplacer.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Glisser-déposer OLE](../../mfc/drag-and-drop-ole.md)
