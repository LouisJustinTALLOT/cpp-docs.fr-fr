---
title: Classe COleDropTarget
ms.date: 11/04/2016
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
ms.openlocfilehash: 01eb277da029d06ee44d8e048cf3244f4371a9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374995"
---
# <a name="coledroptarget-class"></a>Classe COleDropTarget

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
|[COleDropTarget::OnDragEnter](#ondragenter)|Appelé lorsque le curseur entre pour la première fois dans la fenêtre.|
|[COleDropTarget::OnDragLeave](#ondragleave)|Appelé quand le curseur est traîné par la fenêtre.|
|[COleDropTarget::OnDragOver](#ondragover)|Appelé à plusieurs reprises lorsque le curseur est traîné par-dessus la fenêtre.|
|[COleDropTarget::OnDragScroll](#ondragscroll)|Appelé pour déterminer si le curseur est traîné dans la région de défilement de la fenêtre.|
|[COleDropTarget::OnDrop](#ondrop)|Appelé lorsque les données sont tombées dans la fenêtre, gestionnaire par défaut.|
|[COleDropTarget::OnDropEx](#ondropex)|Appelé lorsque les données sont tombées dans la fenêtre, le gestionnaire initial.|
|[COleDropTarget::Enregistrement](#register)|Enregistre la fenêtre comme cible de chute valide.|
|[COleDropTarget::Revoke](#revoke)|La fenêtre cesse d’être une cible de chute valide.|

## <a name="remarks"></a>Notes

La création d’un objet de cette classe permet à une fenêtre d’accepter des données à travers le mécanisme de drag-and-drop OLE.

Pour obtenir une fenêtre pour accepter les commandes de `COleDropTarget` goutte, vous devez d’abord créer un `CWnd` objet de la classe, puis appeler la fonction De [registre](#register) avec un pointeur à l’objet désiré comme seul paramètre.

Pour plus d’informations sur les opérations de drag-and-drop à l’aide d’OLE, voir l’article [OLE glisser et baisser](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a>COleDropTarget::COleDropTarget

Construit un objet `COleDropTarget`de classe .

```
COleDropTarget();
```

### <a name="remarks"></a>Notes

Appelez [inscrivez-vous](#register) pour associer cet objet à une fenêtre.

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a>COleDropTarget::OnDragEnter

Appelé par le cadre lorsque le curseur est d’abord traîné dans la fenêtre.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre le curseur entre.

*pDataObject*<br/>
Points à l’objet de données contenant les données qui peuvent être abandonnées.

*dwKeyState (en)*<br/>
Contient l’état des touches modificateur. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.

*Point*<br/>
Contient l’emplacement actuel du curseur dans les coordonnées des clients.

### <a name="return-value"></a>Valeur de retour

L’effet qui en résulterait si une baisse était tentée à l’endroit spécifié par *point*. Il peut s’agir d’un ou de plusieurs des éléments suivants :

- DROPEFFECT_NONE Une baisse ne serait pas autorisée.

- DROPEFFECT_COPY une opération de copie serait effectuée.

- DROPEFFECT_MOVE Une opération de déménagement serait effectuée.

- DROPEFFECT_LINK Un lien entre les données abandonnées et les données originales serait établi.

- DROPEFFECT_SCROLL Une opération de drag scroll est sur le point de se produire ou se produit dans la cible.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour permettre aux opérations de chute de se produire dans la fenêtre. La implémentation par défaut appelle [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), qui renvoie simplement DROPEFFECT_NONE par défaut.

Pour plus d’informations, voir [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) in the Windows SDK.

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a>COleDropTarget::OnDragLeave

Appelé par le cadre lorsque le curseur quitte la fenêtre pendant qu’une opération de dragage est en vigueur.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre le curseur part.

### <a name="remarks"></a>Notes

Remplacer cette fonction si vous voulez un comportement spécial lorsque l’opération de traînée quitte la fenêtre spécifiée. La mise en œuvre par défaut de cette fonction appelle [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Pour plus d’informations, voir [IDropTarget::DragLeave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) dans le SDK Windows.

## <a name="coledroptargetondragover"></a><a name="ondragover"></a>COleDropTarget::OnDragOver

Appelé par le cadre lorsque le curseur est traîné par-dessus la fenêtre.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Indique à la fenêtre que le curseur est terminé.

*pDataObject*<br/>
Indique l’objet de données qui contient les données à laisser tomber.

*dwKeyState (en)*<br/>
Contient l’état des touches modificateur. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.

*Point*<br/>
Contient l’emplacement actuel du curseur dans les coordonnées des clients.

### <a name="return-value"></a>Valeur de retour

L’effet qui en résulterait si une baisse était tentée à l’endroit spécifié par *point*. Il peut s’agir d’un ou de plusieurs des éléments suivants :

- DROPEFFECT_NONE Une baisse ne serait pas autorisée.

- DROPEFFECT_COPY une opération de copie serait effectuée.

- DROPEFFECT_MOVE Une opération de déménagement serait effectuée.

- DROPEFFECT_LINK Un lien entre les données abandonnées et les données originales serait établi.

- DROPEFFECT_SCROLL indique qu’une opération de drag scroll est sur le point de se produire ou se produit dans la cible.

### <a name="remarks"></a>Notes

Cette fonction doit être remplacée pour permettre aux opérations de chute de se produire dans la fenêtre. La mise en œuvre par défaut de cette fonction appelle [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), qui retourne DROPEFFECT_NONE par défaut. Parce que cette fonction est appelée fréquemment lors d’une opération de drag-and-drop, elle doit être optimisée autant que possible.

Pour plus d’informations, voir [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) in the Windows SDK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a>COleDropTarget::OnDragScroll

Appelé par le cadre avant d’appeler [OnDragEnter](#ondragenter) ou [OnDragOver](#ondragover) pour déterminer si le *point* est dans la région de défilement.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre le curseur est actuellement terminée.

*dwKeyState (en)*<br/>
Contient l’état des touches modificateur. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.

*Point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur de retour

L’effet qui en résulterait si une baisse était tentée à l’endroit spécifié par *point*. Il peut s’agir d’un ou de plusieurs des éléments suivants :

- DROPEFFECT_NONE Une baisse ne serait pas autorisée.

- DROPEFFECT_COPY une opération de copie serait effectuée.

- DROPEFFECT_MOVE Une opération de déménagement serait effectuée.

- DROPEFFECT_LINK Un lien entre les données abandonnées et les données originales serait établi.

- DROPEFFECT_SCROLL indique qu’une opération de drag scroll est sur le point de se produire ou se produit dans la cible.

### <a name="remarks"></a>Notes

Remplacez cette fonction lorsque vous souhaitez fournir un comportement spécial pour cet événement. La mise en œuvre par défaut de cette fonction appelle [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), qui retourne DROPEFFECT_NONE et fait défiler la fenêtre lorsque le curseur est traîné dans la région de défilement par défaut à l’intérieur de la bordure de la fenêtre.

## <a name="coledroptargetondrop"></a><a name="ondrop"></a>COleDropTarget::OnDrop

Appelé par le cadre quand une opération de chute doit se produire.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre le curseur est actuellement terminée.

*pDataObject*<br/>
Indique l’objet de données qui contient les données à laisser tomber.

*dropEffect*<br/>
L’effet que l’utilisateur a choisi pour l’opération de chute. Il peut s’agir d’un ou de plusieurs des éléments suivants :

- DROPEFFECT_COPY une opération de copie serait effectuée.

- DROPEFFECT_MOVE Une opération de déménagement serait effectuée.

- DROPEFFECT_LINK Un lien entre les données abandonnées et les données originales serait établi.

*Point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur de retour

Nonzero si la baisse est réussie; sinon 0.

### <a name="remarks"></a>Notes

Le cadre appelle [d’abord OnDropEx](#ondropex). Si `OnDropEx` la fonction ne gère pas la baisse, `OnDrop`le cadre appelle alors cette fonction de membre, . Typiquement, l’application remplace [OnDropEx](../../mfc/reference/cview-class.md#ondropex) dans la classe de vue pour gérer la traînée et la baisse droite de bouton de souris. Typiquement, la classe de vue [OnDrop](../../mfc/reference/cview-class.md#ondrop) est utilisé pour gérer la traînée simple et la baisse.

La mise `COleDropTarget::OnDrop` en œuvre par défaut des appels [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), qui renvoie simplement FALSE par défaut.

Pour plus d’informations, voir [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) dans le SDK Windows.

## <a name="coledroptargetondropex"></a><a name="ondropex"></a>COleDropTarget::OnDropEx

Appelé par le cadre quand une opération de chute doit se produire.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre le curseur est actuellement terminée.

*pDataObject*<br/>
Indique l’objet de données qui contient les données à laisser tomber.

*dropDefault*<br/>
L’effet que l’utilisateur a choisi pour l’opération de chute par défaut en fonction de l’état clé actuel. Il peut être DROPEFFECT_NONE. Les effets de chute sont discutés dans la section Remarques.

*dropList (en)*<br/>
Une liste des effets de chute que la source de goutte prend en charge. Les valeurs d’effet de chute peuvent être combinées à l’aide de l’opération bitwise OU (**&#124;). ** Les effets de chute sont discutés dans la section Remarques.

*Point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur de retour

L’effet de chute résultant de la tentative de chute à l’emplacement spécifié par *point*. Les effets de chute sont discutés dans la section Remarques.

### <a name="remarks"></a>Notes

Le cadre appelle d’abord cette fonction. S’il ne gère pas la baisse, le cadre appelle alors [OnDrop](#ondrop). En règle générale, vous remplacerez [OnDropEx](../../mfc/reference/cview-class.md#ondropex) dans la classe de vue pour prendre en charge la drague et la baisse droites de bouton de souris. Typiquement, la classe de vue [OnDrop](../../mfc/reference/cview-class.md#ondrop) est utilisé pour gérer le cas de prise en charge pour la traînée simple et la baisse.

La mise `COleDropTarget::OnDropEx` en œuvre par défaut des appels [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Par défaut, [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) renvoie simplement une valeur factice pour indiquer que la fonction membre [OnDrop](#ondrop) doit être appelée.

Les effets de chute décrivent l’action associée à une opération de chute. Voir la liste suivante des effets de chute :

- DROPEFFECT_NONE Une baisse ne serait pas autorisée.

- DROPEFFECT_COPY une opération de copie serait effectuée.

- DROPEFFECT_MOVE Une opération de déménagement serait effectuée.

- DROPEFFECT_LINK Un lien entre les données abandonnées et les données originales serait établi.

- DROPEFFECT_SCROLL indique qu’une opération de drag scroll est sur le point de se produire ou se produit dans la cible.

Pour plus d’informations, voir [IDropTarget::Drop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) dans le SDK Windows.

## <a name="coledroptargetregister"></a><a name="register"></a>COleDropTarget::Enregistrement

Appelez cette fonction pour enregistrer votre fenêtre avec les DLL OLE comme cible de chute valide.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre qui doit être enregistré comme une cible de chute.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’enregistrement est réussi; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction doit être demandée pour que les opérations de largage soient acceptées.

Pour plus d’informations, voir [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) dans le SDK Windows.

## <a name="coledroptargetrevoke"></a><a name="revoke"></a>COleDropTarget::Revoke

Appelez cette fonction avant de détruire toute fenêtre qui a été enregistrée comme une cible de chute par un appel à [s’inscrire](#register) pour le supprimer de la liste des cibles de chute.

```
virtual void Revoke();
```

### <a name="remarks"></a>Notes

Cette fonction est appelée automatiquement à partir du gestionnaire [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) pour la fenêtre qui a été enregistrée, il n’est généralement pas nécessaire d’appeler cette fonction explicitement.

Pour plus d’informations, voir [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource, classe](../../mfc/reference/coledropsource-class.md)
