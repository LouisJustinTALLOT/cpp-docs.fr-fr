---
description: 'En savoir plus sur : classe COleDropTarget'
title: COleDropTarget, classe
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
ms.openlocfilehash: ff911caa98031899ab018434d87d813d3c45362e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227102"
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
|[COleDropTarget :: OnDragEnter](#ondragenter)|Appelé lorsque le curseur entre en première place dans la fenêtre.|
|[COleDropTarget :: OnDragLeave](#ondragleave)|Appelé lorsque le curseur est déplacé hors de la fenêtre.|
|[COleDropTarget :: OnDragOver](#ondragover)|Appelée à plusieurs reprises lorsque le curseur est déplacé sur la fenêtre.|
|[COleDropTarget::OnDragScroll](#ondragscroll)|Appelé pour déterminer si le curseur est déplacé dans la zone de défilement de la fenêtre.|
|[COleDropTarget :: OnDrop](#ondrop)|Appelé lorsque des données sont déposées dans la fenêtre, gestionnaire par défaut.|
|[COleDropTarget::OnDropEx](#ondropex)|Appelé lorsque des données sont déposées dans la fenêtre, le gestionnaire initial.|
|[COleDropTarget :: Register](#register)|Inscrit la fenêtre comme cible de déplacement valide.|
|[COleDropTarget :: Revoke](#revoke)|Entraîne l’arrêt de la fenêtre en tant que cible de dépôt valide.|

## <a name="remarks"></a>Notes

La création d’un objet de cette classe permet à une fenêtre d’accepter des données par le biais du mécanisme de glisser-déplacer OLE.

Pour obtenir une fenêtre qui accepte les commandes Drop, vous devez d’abord créer un objet de la `COleDropTarget` classe, puis appeler la fonction [Register](#register) avec un pointeur vers l' `CWnd` objet souhaité comme seul paramètre.

Pour plus d’informations sur les opérations de glisser-déplacer à l’aide d’OLE, consultez l’article [glisser-déplacer OLE](../../mfc/drag-and-drop-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="coledroptargetcoledroptarget"></a><a name="coledroptarget"></a> COleDropTarget::COleDropTarget

Construit un objet de classe `COleDropTarget` .

```
COleDropTarget();
```

### <a name="remarks"></a>Notes

Appelez [Register](#register) pour associer cet objet à une fenêtre.

## <a name="coledroptargetondragenter"></a><a name="ondragenter"></a> COleDropTarget :: OnDragEnter

Appelée par l’infrastructure quand le curseur est déplacé pour la première fois dans la fenêtre.

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre entrée par le curseur.

*pDataObject*<br/>
Pointe vers l’objet de données contenant les données qui peuvent être supprimées.

*dwKeyState*<br/>
Contient l’état des touches de modification. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
Contient l’emplacement actuel du curseur dans les coordonnées clientes.

### <a name="return-value"></a>Valeur renvoyée

Effet qui se produit si un déplacement a été tenté à l’emplacement spécifié par *point*. Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_NONE une suppression n’est pas autorisée.

- DROPEFFECT_COPY une opération de copie est effectuée.

- DROPEFFECT_MOVE une opération de déplacement est effectuée.

- DROPEFFECT_LINK un lien des données déplacées vers les données d’origine serait établi.

- DROPEFFECT_SCROLL une opération de défilement de glissement est sur le lieu de se produire ou se produit dans la cible.

### <a name="remarks"></a>Notes

Substituez cette fonction pour permettre aux opérations de suppression de se produire dans la fenêtre. L’implémentation par défaut appelle [CView :: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), qui retourne simplement DROPEFFECT_NONE par défaut.

Pour plus d’informations, consultez [IDropTarget ::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) dans le SDK Windows.

## <a name="coledroptargetondragleave"></a><a name="ondragleave"></a> COleDropTarget :: OnDragLeave

Appelée par l’infrastructure quand le curseur quitte la fenêtre pendant qu’une opération de glissement est en vigueur.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre que le curseur quitte.

### <a name="remarks"></a>Notes

Substituez cette fonction si vous souhaitez un comportement spécial lorsque l’opération glisser quitte la fenêtre spécifiée. L’implémentation par défaut de cette fonction appelle [CView :: OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).

Pour plus d’informations, consultez [IDropTarget ::D ragleave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) dans le SDK Windows.

## <a name="coledroptargetondragover"></a><a name="ondragover"></a> COleDropTarget :: OnDragOver

Appelé par le Framework lorsque le curseur est glissé sur la fenêtre.

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre sur laquelle se trouve le curseur.

*pDataObject*<br/>
Pointe vers l’objet de données qui contient les données à supprimer.

*dwKeyState*<br/>
Contient l’état des touches de modification. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
Contient l’emplacement actuel du curseur dans les coordonnées clientes.

### <a name="return-value"></a>Valeur renvoyée

Effet qui se produit si un déplacement a été tenté à l’emplacement spécifié par *point*. Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_NONE une suppression n’est pas autorisée.

- DROPEFFECT_COPY une opération de copie est effectuée.

- DROPEFFECT_MOVE une opération de déplacement est effectuée.

- DROPEFFECT_LINK un lien des données déplacées vers les données d’origine serait établi.

- DROPEFFECT_SCROLL indique qu’une opération de défilement de glissement est sur le ou se produit dans la cible.

### <a name="remarks"></a>Notes

Cette fonction doit être substituée pour permettre aux opérations de suppression de se produire dans la fenêtre. L’implémentation par défaut de cette fonction appelle [CView :: OnDragOver](../../mfc/reference/cview-class.md#ondragover), qui retourne DROPEFFECT_NONE par défaut. Étant donné que cette fonction est fréquemment appelée pendant une opération de glisser-déplacer, elle doit être optimisée autant que possible.

Pour plus d’informations, consultez [IDropTarget ::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

## <a name="coledroptargetondragscroll"></a><a name="ondragscroll"></a> COleDropTarget::OnDragScroll

Appelée par l’infrastructure avant d’appeler [OnDragEnter](#ondragenter) ou [OnDragOver](#ondragover) pour déterminer si le *point* se trouve dans la zone de défilement.

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre sur laquelle le curseur se trouve actuellement.

*dwKeyState*<br/>
Contient l’état des touches de modification. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur renvoyée

Effet qui se produit si un déplacement a été tenté à l’emplacement spécifié par *point*. Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_NONE une suppression n’est pas autorisée.

- DROPEFFECT_COPY une opération de copie est effectuée.

- DROPEFFECT_MOVE une opération de déplacement est effectuée.

- DROPEFFECT_LINK un lien des données déplacées vers les données d’origine serait établi.

- DROPEFFECT_SCROLL indique qu’une opération de défilement de glissement est sur le ou se produit dans la cible.

### <a name="remarks"></a>Notes

Substituez cette fonction lorsque vous souhaitez fournir un comportement spécial pour cet événement. L’implémentation par défaut de cette fonction appelle [CView :: OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), qui retourne DROPEFFECT_NONE et fait défiler la fenêtre lorsque le curseur est déplacé dans la zone de défilement par défaut à l’intérieur de la bordure de la fenêtre.

## <a name="coledroptargetondrop"></a><a name="ondrop"></a> COleDropTarget :: OnDrop

Appelé par le Framework lorsqu’une opération de déplacement doit se produire.

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre sur laquelle le curseur se trouve actuellement.

*pDataObject*<br/>
Pointe vers l’objet de données qui contient les données à supprimer.

*dropEffect*<br/>
Effet choisi par l’utilisateur pour l’opération de déplacement. Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_COPY une opération de copie est effectuée.

- DROPEFFECT_MOVE une opération de déplacement est effectuée.

- DROPEFFECT_LINK un lien des données déplacées vers les données d’origine serait établi.

*point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si la suppression réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

L’infrastructure appelle d’abord [OnDropEx](#ondropex). Si la `OnDropEx` fonction ne gère pas la suppression, le Framework appelle ensuite cette fonction membre, `OnDrop` . En règle générale, l’application substitue [OnDropEx](../../mfc/reference/cview-class.md#ondropex) dans la classe d’affichage pour gérer le glissement-déplacement du bouton droit de la souris. En règle générale, la classe d’affichage [OnDrop](../../mfc/reference/cview-class.md#ondrop) est utilisée pour gérer une opération glisser-déplacer simple.

L’implémentation par défaut de `COleDropTarget::OnDrop` appelle [CView :: OnDrop](../../mfc/reference/cview-class.md#ondrop), qui retourne simplement la valeur false par défaut.

Pour plus d’informations, consultez [IDropTarget ::D ROP](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) dans le SDK Windows.

## <a name="coledroptargetondropex"></a><a name="ondropex"></a> COleDropTarget::OnDropEx

Appelé par le Framework lorsqu’une opération de déplacement doit se produire.

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre sur laquelle le curseur se trouve actuellement.

*pDataObject*<br/>
Pointe vers l’objet de données qui contient les données à supprimer.

*dropDefault*<br/>
Effet choisi par l’utilisateur pour l’opération de suppression par défaut en fonction de l’état de la clé actuelle. Il peut être DROPEFFECT_NONE. Les effets de la suppression sont décrits dans la section Notes.

*Roulant*<br/>
Liste des effets de suppression pris en charge par la source de déplacement. Les valeurs d’effet de dépôt peuvent être combinées à l’aide de l’opération or au niveau du bit (**&#124;**). Les effets de la suppression sont décrits dans la section Notes.

*point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur renvoyée

Effet de déplacement résultant de la tentative de suppression à l’emplacement spécifié par *point*. Les effets de la suppression sont décrits dans la section Notes.

### <a name="remarks"></a>Notes

L’infrastructure appelle d’abord cette fonction. Si elle ne gère pas la suppression, le Framework appelle ensuite [OnDrop](#ondrop). En règle générale, vous substituez [OnDropEx](../../mfc/reference/cview-class.md#ondropex) dans la classe d’affichage pour prendre en charge le glisser-déplacer avec le bouton droit de la souris. En règle générale, la classe d’affichage [OnDrop](../../mfc/reference/cview-class.md#ondrop) est utilisée pour gérer la prise en charge d’un simple glisser-déplacer.

L’implémentation par défaut de `COleDropTarget::OnDropEx` appelle [CView :: OnDropEx](../../mfc/reference/cview-class.md#ondropex). Par défaut, [CView :: OnDropEx](../../mfc/reference/cview-class.md#ondropex) retourne simplement une valeur factice pour indiquer que la fonction membre [OnDrop](#ondrop) doit être appelée.

Drop Effects décrit l’action associée à une opération de déplacement. Consultez la liste des effets de dépôt suivante :

- DROPEFFECT_NONE une suppression n’est pas autorisée.

- DROPEFFECT_COPY une opération de copie est effectuée.

- DROPEFFECT_MOVE une opération de déplacement est effectuée.

- DROPEFFECT_LINK un lien des données déplacées vers les données d’origine serait établi.

- DROPEFFECT_SCROLL indique qu’une opération de défilement de glissement est sur le ou se produit dans la cible.

Pour plus d’informations, consultez [IDropTarget ::D ROP](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) dans le SDK Windows.

## <a name="coledroptargetregister"></a><a name="register"></a> COleDropTarget :: Register

Appelez cette fonction pour inscrire votre fenêtre avec les dll OLE comme cible de dépôt valide.

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre qui doit être enregistrée en tant que cible de déplacement.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si l’inscription réussit ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée pour que les opérations de suppression soient acceptées.

Pour plus d’informations, consultez [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) dans le SDK Windows.

## <a name="coledroptargetrevoke"></a><a name="revoke"></a> COleDropTarget :: Revoke

Appelez cette fonction avant de détruire une fenêtre qui a été inscrite en tant que cible de déplacement à l’aide d’un appel à [Register](#register) pour la supprimer de la liste des cibles de dépôt.

```
virtual void Revoke();
```

### <a name="remarks"></a>Notes

Cette fonction étant automatiquement appelée à partir du gestionnaire [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) pour la fenêtre qui a été inscrite, il n’est généralement pas nécessaire d’appeler cette fonction explicitement.

Pour plus d’informations, consultez [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource, classe](../../mfc/reference/coledropsource-class.md)
