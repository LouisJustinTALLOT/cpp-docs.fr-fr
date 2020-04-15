---
title: COleDropSource, classe
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: 324c4b7273f021b43c319fb0a494ac843856c78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375021"
---
# <a name="coledropsource-class"></a>COleDropSource, classe

Permet de traînéer les données vers une cible de drop.

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
|[COleDropSource::GiveFeedback](#givefeedback)|Change le curseur lors d’une opération de drag-and-drop.|
|[COleDropSource::OnBeginDrag](#onbegindrag)|Gère la capture de la souris lors d’une opération de drag-and-drop.|
|[COleDropSource::QueryContinueDrag](#querycontinuedrag)|Vérifications pour voir si le dragage doit se poursuivre.|

## <a name="remarks"></a>Notes

La classe [COleDropTarget](../../mfc/reference/coledroptarget-class.md) gère la partie réceptrice de l’opération de drag-and-drop. L’objet `COleDropSource` est responsable de déterminer quand une opération de traînée commence, de fournir des commentaires pendant l’opération de traînée, et de déterminer quand l’opération de traînée se termine.

Pour utiliser `COleDropSource` un objet, il suffit d’appeler le constructeur. Cela simplifie le processus de détermination des événements, tels qu’un clic de souris, commencer une opération de dragage en utilisant [COleDataSource::DoDragDrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem::DoDragDrop](../../mfc/reference/coleclientitem-class.md#dodragdrop), ou [COleServerItem::DoDragDrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) fonction. Ces fonctions créeront un `COleDropSource` objet pour vous. Vous voudrez peut-être modifier `COleDropSource` le comportement par défaut des fonctions primordiales. Ces fonctions de membre seront appelées aux heures appropriées par le cadre.

Pour plus d’informations sur les opérations de drag-and-drop à l’aide d’OLE, voir l’article [OLE glisser et baisser](../../mfc/drag-and-drop-ole.md).

Pour plus d’informations, voir [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) dans windows SDK.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a>COleDropSource::COleDropSource

Construit un objet `COleDropSource`.

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a>COleDropSource::GiveFeedback

Appelé par le cadre après avoir appelé [COleDropTarget::OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) ou [COleDropTarget::DragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Paramètres

*dropEffect*<br/>
L’effet que vous souhaitez afficher à l’utilisateur, indiquant généralement ce qui se passerait si une baisse s’est produite à ce stade avec les données sélectionnées. Typiquement, c’est la valeur retournée par l’appel le plus récent à [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) ou [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover). Il peut s’agir d’un ou de plusieurs des éléments suivants :

- DROPEFFECT_NONE Une baisse ne serait pas autorisée.

- DROPEFFECT_COPY une opération de copie serait effectuée.

- DROPEFFECT_MOVE Une opération de déménagement serait effectuée.

- DROPEFFECT_LINK Un lien entre les données abandonnées et les données originales serait établi.

- DROPEFFECT_SCROLL Une opération de drag scroll est sur le point de se produire ou se produit dans la cible.

### <a name="return-value"></a>Valeur de retour

Les retours DRAGDROP_S_USEDEFAULTCURSORS si le dragage est en cours, NOERROR si ce n’est pas le cas.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour fournir des commentaires à l’utilisateur sur ce qui se passerait si une baisse s’est produite à ce stade. L’implémentation par défaut utilise les curseurs par défaut OLE. Pour plus d’informations sur les opérations de drag-and-drop à l’aide d’OLE, voir l’article [OLE glisser et baisser](../../mfc/drag-and-drop-ole.md).

Pour plus d’informations, voir [IDropSource::GiveFeedback](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget::DragOver](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover), et [IDropTarget::DragEnter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) in the Windows SDK.

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a>COleDropSource::OnBeginDrag

Appelé par le cadre quand un événement se produit qui pourrait commencer une opération de traînée, comme appuyer sur le bouton de la souris gauche.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Points à la fenêtre qui contient les données sélectionnées.

### <a name="return-value"></a>Valeur de retour

Nonzero si le dragage est autorisé, sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction si vous souhaitez modifier la façon dont le processus de dragage est lancé. L’implémentation par défaut capture la souris et reste en mode traîné jusqu’à ce que l’utilisateur clique sur le bouton de la souris gauche ou droite ou frappe ESC, date à laquelle il libère la souris.

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a>COleDropSource::QueryContinueDrag

Après le dragage a commencé, cette fonction est appelée à plusieurs reprises par le cadre jusqu’à ce que l’opération de traînée est soit annulée ou terminée.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Paramètres

*bEscapePressed (en anglais)*<br/>
Indique si la clé escAS a `COleDropSource::QueryContinueDrag`été pressée depuis le dernier appel à .

*dwKeyState (en)*<br/>
Contient l’état des touches modificateur sur le clavier. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.

### <a name="return-value"></a>Valeur de retour

DRAGDROP_S_CANCEL si la clé ESC ou le bouton droit est appuyé, ou le bouton gauche est soulevé avant de faire glisser. DRAGDROP_S_DROP si une opération de chute doit se produire. Sinon, S_OK.

### <a name="remarks"></a>Notes

Remplacez cette fonction si vous souhaitez modifier le point où le dragage est annulé ou une goutte se produit.

L’implémentation par défaut initie la baisse ou annule la traînée comme suit. Il annule une opération de traînée lorsque la clé ESC ou le bouton de la souris droite est pressé. Il initie une opération de chute lorsque le bouton de la souris gauche est soulevé après le dragage a commencé. Dans le cas contraire, il retourne S_OK et n’effectue aucune autre opération.

Parce que cette fonction est appelée fréquemment, elle doit être optimisée autant que possible.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
