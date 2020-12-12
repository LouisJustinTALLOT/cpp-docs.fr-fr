---
description: 'En savoir plus sur : classe COleDropSource'
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
ms.openlocfilehash: 069c1b2a3cb46f0824da55bca8e97041e9b0b2e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227141"
---
# <a name="coledropsource-class"></a>COleDropSource, classe

Permet de faire glisser des données vers une cible de déplacement.

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
|[COleDropSource :: GiveFeedback](#givefeedback)|Modifie le curseur pendant une opération de glisser-déplacer.|
|[COleDropSource::OnBeginDrag](#onbegindrag)|Gère la capture de la souris pendant une opération de glisser-déplacer.|
|[COleDropSource :: QueryContinueDrag](#querycontinuedrag)|Vérifie si le glisser-déplacer doit continuer.|

## <a name="remarks"></a>Notes

La classe [COleDropTarget](../../mfc/reference/coledroptarget-class.md) gère la partie réceptrice de l’opération de glisser-déplacer. L' `COleDropSource` objet est chargé de déterminer quand une opération glisser commence, de fournir des commentaires pendant l’opération glisser et de déterminer à quel moment l’opération glisser se termine.

Pour utiliser un `COleDropSource` objet, il vous suffit d’appeler le constructeur. Cela simplifie le processus de détermination des événements, tels qu’un clic de souris, à commencer une opération glisser à l’aide de [COleDataSource ::D odragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop), [COleClientItem ::D odragdrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)ou [COleServerItem ::D fonction odragdrop](../../mfc/reference/coleserveritem-class.md#dodragdrop) . Ces fonctions vont créer un `COleDropSource` objet pour vous. Vous souhaiterez peut-être modifier le comportement par défaut des `COleDropSource` fonctions substituables. Ces fonctions membres seront appelées aux moments appropriés par l’infrastructure.

Pour plus d’informations sur les opérations de glisser-déplacer à l’aide d’OLE, consultez l’article [glisser-déplacer OLE](../../mfc/drag-and-drop-ole.md).

Pour plus d’informations, consultez [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="coledropsourcecoledropsource"></a><a name="coledropsource"></a> COleDropSource::COleDropSource

Construit un objet `COleDropSource`.

```
COleDropSource();
```

## <a name="coledropsourcegivefeedback"></a><a name="givefeedback"></a> COleDropSource :: GiveFeedback

Appelée par l’infrastructure après l’appel de [COleDropTarget :: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover) ou [COleDropTarget ::D ragenter](../../mfc/reference/coledroptarget-class.md#ondragenter).

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>Paramètres

*dropEffect*<br/>
L’effet que vous souhaitez afficher à l’utilisateur, en général qui indique ce qui se passe si une chute a eu lieu à ce stade avec les données sélectionnées. En règle générale, il s’agit de la valeur retournée par l’appel le plus récent à [CView :: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter) ou [CView :: OnDragOver](../../mfc/reference/cview-class.md#ondragover). Il peut s’agir d’un ou plusieurs des éléments suivants :

- DROPEFFECT_NONE une suppression n’est pas autorisée.

- DROPEFFECT_COPY une opération de copie est effectuée.

- DROPEFFECT_MOVE une opération de déplacement est effectuée.

- DROPEFFECT_LINK un lien des données déplacées vers les données d’origine serait établi.

- DROPEFFECT_SCROLL une opération de défilement de glissement est sur le lieu de se produire ou se produit dans la cible.

### <a name="return-value"></a>Valeur renvoyée

Retourne DRAGDROP_S_USEDEFAULTCURSORS si le glissement est en cours, NOERROR si ce n’est pas le cas.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour fournir des commentaires à l’utilisateur sur ce qui se passerait si une suppression se produisait à ce stade. L’implémentation par défaut utilise les curseurs OLE par défaut. Pour plus d’informations sur les opérations de glisser-déplacer à l’aide d’OLE, consultez l’article [glisser-déplacer OLE](../../mfc/drag-and-drop-ole.md).

Pour plus d’informations, consultez [IDropSource :: GiveFeedback](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback), [IDropTarget ::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)et [IDropTarget ::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) dans le SDK Windows.

## <a name="coledropsourceonbegindrag"></a><a name="onbegindrag"></a> COleDropSource::OnBeginDrag

Appelée par l’infrastructure quand un événement qui peut commencer une opération glisser, par exemple en appuyant sur le bouton gauche de la souris.

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointe vers la fenêtre qui contient les données sélectionnées.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si le glissement est autorisé ; sinon, 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction si vous souhaitez modifier le mode de démarrage du processus de glissement. L’implémentation par défaut capture la souris et reste en mode glisser jusqu’à ce que l’utilisateur clique sur le bouton gauche ou droit de la souris ou appuie sur ÉCHAP, moment où il relâche la souris.

## <a name="coledropsourcequerycontinuedrag"></a><a name="querycontinuedrag"></a> COleDropSource :: QueryContinueDrag

Une fois que le glissement a commencé, cette fonction est appelée à plusieurs reprises par l’infrastructure jusqu’à ce que l’opération glisser soit annulée ou terminée.

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>Paramètres

*bEscapePressed*<br/>
Indique si la touche ÉCHAP a été enfoncée depuis le dernier appel à `COleDropSource::QueryContinueDrag` .

*dwKeyState*<br/>
Contient l’état des touches de modification du clavier. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

### <a name="return-value"></a>Valeur renvoyée

DRAGDROP_S_CANCEL si l’utilisateur appuie sur la touche Échap ou sur le bouton droit, ou si le bouton gauche est déclenché avant le début du glissement. DRAGDROP_S_DROP si une opération de déplacement doit se produire. Sinon S_OK.

### <a name="remarks"></a>Notes

Substituez cette fonction si vous souhaitez modifier le point à partir duquel le glissement est annulé ou une opération de déplacement.

L’implémentation par défaut initie la suppression ou annule le glissement comme suit. Elle annule une opération glisser quand l’utilisateur appuie sur la touche Échap ou sur le bouton droit de la souris. Elle lance une opération de déplacement lorsque le bouton gauche de la souris est déclenché après le début du glissement. Dans le cas contraire, elle retourne S_OK et n’effectue aucune opération supplémentaire.

Étant donné que cette fonction est souvent appelée, elle doit être optimisée autant que possible.

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
