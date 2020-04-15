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
ms.openlocfilehash: 01e259cf01c42add26088b0cbd2f6dab311eb9b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374959"
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
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Appelé par le cadre lorsqu’un élément est activé pour l’édition en place.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Appelé par le cadre pour repositionner la fenêtre d’édition en place.|

## <a name="remarks"></a>Notes

Cette classe crée et positionne les barres de contrôle dans la fenêtre de document de l’application de conteneurs. Il gère également les notifications générées par un objet [COleResizeBar](../../mfc/reference/coleresizebar-class.md) intégré lorsque l’utilisateur redimensionne la fenêtre d’édition en place.

Pour plus d’informations sur l’utilisation `COleIPFrameWnd`, voir l’article [Activation](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd

Construit un `COleIPFrameWnd` objet et initialise ses informations d’état sur place, qui sont stockées dans une structure de type OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo) dans windows SDK.

## <a name="coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars

Le cadre `OnCreateControlBars` appelle la fonction lorsqu’un élément est activé pour l’édition sur place.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>Paramètres

*pWndFrame (en)*<br/>
Pointeur vers la fenêtre de cadre de l’application de conteneur.

*pWndDoc*<br/>
Pointeur vers la fenêtre de niveau document du conteneur. Peut être NULL si le conteneur est une application SDI.

### <a name="return-value"></a>Valeur de retour

Nonzero sur le succès; autrement, 0.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Remplacer cette fonction pour effectuer tout traitement spécial requis lors de la création des barres de contrôle.

## <a name="coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame

Le cadre `RepositionFrame` appelle la fonction membre à établir des barres de contrôle et à repositionner la fenêtre d’édition sur place afin que tout soit visible.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur `RECT` vers une `CRect` structure ou un objet contenant les coordonnées de position actuelles de la fenêtre de cadre sur place, en pixels, par rapport à la zone client.

*lpClipRect*<br/>
Pointeur `RECT` vers une `CRect` structure ou un objet contenant les coordonnées actuelles de la fenêtre de l’image en place, en pixels, par rapport à la zone client.

### <a name="remarks"></a>Notes

La disposition des barres de commande dans la fenêtre du conteneur diffère de celle effectuée par une fenêtre de cadre non OLE. La fenêtre de cadre non-OLE calcule les positions des barres de contrôle et d’autres objets à partir d’une taille donnée de fenêtre de cadre, comme dans un appel à [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). La zone client est ce qui reste après l’espace pour les barres de contrôle et d’autres objets est soustrait. Une `COleIPFrameWnd` fenêtre, d’autre part, positionne les barres d’outils en fonction d’une zone client donnée. En d’autres termes, `CFrameWnd::RecalcLayout` fonctionne «de l’extérieur», tandis que `COleIPFrameWnd::RepositionFrame` fonctionne «de l’intérieur vers l’extérieur."

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)
