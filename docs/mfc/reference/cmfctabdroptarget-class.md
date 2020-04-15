---
title: Classe CMFCTabDropTarget
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
ms.openlocfilehash: 83432fdb90fe28214fb1faaf843556deb2f44750
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367357"
---
# <a name="cmfctabdroptarget-class"></a>Classe CMFCTabDropTarget

Fournit le mécanisme de communication entre un contrôle d’onglet et les bibliothèques OLE.

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
|[CMFCTabDropTarget::OnDragEnter](#ondragenter)|Appelé par le cadre lorsque l’utilisateur traîne un objet dans une fenêtre d’onglet. (Overrides [COleDropTarget::OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).)|
|[CMFCTabDropTarget::OnDragLeave](#ondragleave)|Appelé par le cadre lorsque l’utilisateur traîne un objet à l’extérieur de la fenêtre de l’onglet qui a mise au point. (Overrides [COleDropTarget::OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave).)|
|[CMFCTabDropTarget::OnDragOver](#ondragover)|Appelé par le cadre lorsque l’utilisateur traîne un objet sur la fenêtre de l’onglet qui a mise au point. (Overrides [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover).)|
|[CMFCTabDropTarget::OnDropEx](#ondropex)|Appelé par le cadre lorsque l’utilisateur libère le bouton de la souris à la fin d’une opération de traînée. (Overrides [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).)|
|[CMFCTabDropTarget::Enregistrement](#register)|Enregistre le contrôle comme un qui peut être la cible d’une opération de drag-and-drop OLE.|

### <a name="remarks"></a>Notes

Cette classe fournit un soutien de `CMFCBaseTabCtrl` drag-and-drop à la classe. Si votre application initialise les bibliothèques OLE en utilisant `CMFCBaseTabCtrl` la fonction [AfxOleInit,](ole-initialization.md#afxoleinit) les objets s’inscrivent pour les opérations de drag-and-drop.

La `CMFCTabDropTarget` classe étend sa classe de base en faisant l’onglet qui est sous le curseur quand une opération de traînée se produit active. Pour plus d’informations sur les opérations de drag-and-drop, voir [OLE glisser et baisser](../../mfc/drag-and-drop-ole.md).

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

## <a name="cmfctabdroptargetondragenter"></a><a name="ondragenter"></a>CMFCTabDropTarget::OnDragEnter

Appelé par le cadre lorsque l’utilisateur traîne un objet dans une fenêtre d’onglet.

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
|*Pwnd*|[in] Inutilisé.|
|*pDataObject*|[dans] Un pointeur sur l’objet que l’utilisateur traîne.|
|*dwKeyState (en)*|[dans] Contient l’état des touches modificateur. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.|
|*Point*|[dans] L’emplacement du curseur dans les coordonnées des clients.|

### <a name="return-value"></a>Valeur de retour

L’effet qui résulte si la baisse se produit à l’endroit spécifié par *point*. Il peut s’agir d’un ou de plusieurs des éléments suivants :

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Notes

Cette méthode renvoie DROPEFFECT_NONE si le cadre de la barre d’outils n’est pas en mode personnalisation ou si le format de données Clipboard n’est pas disponible. Dans le cas contraire, `CMFCBaseTabCtrl::OnDragEnter` il renvoie le résultat de l’appel avec les paramètres fournis.

Pour plus d’informations sur le mode de personnalisation, voir [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données Clipboard, voir [COleDataObject:IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondragleave"></a><a name="ondragleave"></a>CMFCTabDropTarget::OnDragLeave

Appelé par le cadre lorsque l’utilisateur traîne un objet à l’extérieur de la fenêtre de l’onglet qui a mise au point.

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*Pwnd*|[in] Inutilisé.|

### <a name="remarks"></a>Notes

Cette méthode `CMFCBaseTabCtrl::OnDragLeave` appelle la méthode pour effectuer le fonctionnement de la traînée.

## <a name="cmfctabdroptargetondragover"></a><a name="ondragover"></a>CMFCTabDropTarget::OnDragOver

Appelé par le cadre lorsque l’utilisateur traîne un objet sur la fenêtre de l’onglet qui a mise au point.

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
|*Pwnd*|[in] Inutilisé.|
|*pDataObject*|[dans] Un pointeur sur l’objet que l’utilisateur traîne.|
|*dwKeyState (en)*|[dans] Contient l’état des touches modificateur. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.|
|*Point*|[dans] L’emplacement du pointeur de souris dans les coordonnées du client.|

### <a name="return-value"></a>Valeur de retour

L’effet qui résulte si la baisse se produit à l’endroit spécifié par *point*. Il peut s’agir d’un ou de plusieurs des éléments suivants :

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Notes

Cette méthode rend l’onglet qui est sous le curseur quand une opération de traînée se produit active. Il renvoie DROPEFFECT_NONE si le cadre de la barre d’outils n’est pas en mode personnalisation ou si le format de données Clipboard n’est pas disponible. Dans le cas contraire, `CMFCBaseTabCtrl::OnDragOver` il renvoie le résultat de l’appel avec les paramètres fournis.

Pour plus d’informations sur le mode de personnalisation, voir [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données Clipboard, voir [COleDataObject:IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetondropex"></a><a name="ondropex"></a>CMFCTabDropTarget::OnDropEx

Appelé par le cadre lorsque l’utilisateur libère le bouton de la souris à la fin d’une opération de traînée.

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
|*Pwnd*|[in] Inutilisé.|
|*pDataObject*|[dans] Un pointeur sur l’objet que l’utilisateur traîne.|
|*dropEffect*|[dans] L’opération de chute par défaut.|
|*dropList (en)*|[in] Inutilisé.|
|*Point*|[dans] L’emplacement du pointeur de souris dans les coordonnées du client.|

### <a name="return-value"></a>Valeur de retour

L’effet de chute qui en résulte. Il peut s’agir d’un ou de plusieurs des éléments suivants :

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>Notes

Cette méthode `CMFCBaseTabCtrl::OnDrop` s’appelle si le cadre de la barre d’outils est en mode personnalisation et que le format de données Clipboard est disponible. Si l’appel pour `CMFCBaseTabCtrl::OnDrop` retourner une valeur non zéro, cette méthode renvoie l’effet de chute par défaut spécifié par *dropEffect*. Sinon, cette méthode revient DROPEFFECT_NONE. Pour plus d’informations sur les effets de chute, voir [COleDropTarget::OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex).

Pour plus d’informations sur le mode de personnalisation, voir [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode). Pour plus d’informations sur les formats de données Clipboard, voir [COleDataObject:IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable).

## <a name="cmfctabdroptargetregister"></a><a name="register"></a>CMFCTabDropTarget::Enregistrement

Enregistre le contrôle comme un qui peut être la cible d’une opération de drag-and-drop OLE.

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*pOwner (en)*|[dans] Le contrôle de l’onglet pour s’inscrire comme cible de chute.|

### <a name="return-value"></a>Valeur de retour

Nonzero si l’enregistrement a été réussi; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode appelle [COleDropTarget::Inscrivez-vous](../../mfc/reference/coledroptarget-class.md#register) pour enregistrer le contrôle des opérations de drag-and-drop.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Glisser-déposer OLE](../../mfc/drag-and-drop-ole.md)
