---
title: COleIPFrameWnd, classe
ms.date: 11/04/2016
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
ms.openlocfilehash: 78b846a6b17fb18f533139e9ac6444babd4baac5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498830"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd, classe

Base pour la fenêtre de modification sur place de votre application.

## <a name="syntax"></a>Syntaxe

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Construit un objet `COleIPFrameWnd`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Appelé par le framework lorsqu’un élément est activé pour la modification sur place.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Appelé par l’infrastructure pour repositionner la fenêtre d’édition sur place.|

## <a name="remarks"></a>Notes

Cette classe crée et positions des barres dans la fenêtre de document de l’application de conteneur de contrôle. Il gère également les notifications générées par un embedded [COleResizeBar](../../mfc/reference/coleresizebar-class.md) quand l’utilisateur redimensionne la fenêtre d’édition sur place de l’objet.

Pour plus d’informations sur l’utilisation de `COleIPFrameWnd`, consultez l’article [Activation](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxole.h

##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd

Construit un `COleIPFrameWnd` de l’objet et initialise ses informations d’état de la place, ce qui sont stockées dans une structure de type oleinplaceframeinfo que.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [oleinplaceframeinfo que](/windows/desktop/api/oleidl/ns-oleidl-tagoifi) dans le SDK Windows.

##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars

Le framework appelle la `OnCreateControlBars` fonctionner lorsqu’un élément est activé pour la modification sur place.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>Paramètres

*pWndFrame*<br/>
Pointeur vers la fenêtre frame de l’application de conteneur.

*pWndDoc*<br/>
Pointeur vers la fenêtre du conteneur au niveau du document. Peut d’être NULL si le conteneur est une application SDI.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; Sinon, 0.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Remplacez cette fonction pour effectuer tout traitement spécial requis lors de la création de barres de contrôles.

##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame

Le framework appelle la `RepositionFrame` fonction membre pour présenter les barres de contrôle et repositionner la fenêtre d’édition sur place pour que tout cela soit visible.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur vers un `RECT` structure ou un `CRect` objet contenant l’emplacement dans le frame actuelle coordonnées de position de fenêtre, en pixels, par rapport à la zone cliente.

*lpClipRect*<br/>
Pointeur vers un `RECT` structure ou un `CRect` objet contenant l’emplacement dans le frame actuelle rectangle de découpage coordonnées de fenêtre, en pixels, par rapport à la zone cliente.

### <a name="remarks"></a>Notes

Diffère de la disposition des barres de contrôle dans la fenêtre du conteneur qui émane d’une fenêtre frame de non-OLE. La fenêtre frame de non-OLE calcule les positions des barres de contrôles et d’autres objets à partir d’une taille de fenêtre frame donné, comme dans un appel à [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). La zone cliente est ce qui reste après la soustraction de l’espace pour les barres de contrôles et d’autres objets. Un `COleIPFrameWnd` fenêtre, positionne quant à eux, les barres d’outils conformément à une zone cliente donnée. En d’autres termes, `CFrameWnd::RecalcLayout` fonctionne « depuis l’extérieur, », tandis que `COleIPFrameWnd::RepositionFrame` fonctionne « de l’intérieur. »

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)
