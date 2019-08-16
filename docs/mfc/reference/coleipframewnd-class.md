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
ms.openlocfilehash: 483998529b83d9b28c6ab1b219c4f5288dbd8ec7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503829"
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
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Appelé par le Framework lorsqu’un élément est activé pour la modification sur place.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Appelé par l’infrastructure pour repositionner la fenêtre de modification sur place.|

## <a name="remarks"></a>Notes

Cette classe crée et positionne des barres de contrôles dans la fenêtre de document de l’application conteneur. Il gère également les notifications générées par un objet [COleResizeBar](../../mfc/reference/coleresizebar-class.md) incorporé lorsque l’utilisateur redimensionne la fenêtre d’édition sur place.

Pour plus d’informations sur `COleIPFrameWnd`l’utilisation de, consultez l’article [activation](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Configuration requise

**En-tête:** AFXOLE. h

##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd

Construit un `COleIPFrameWnd` objet et initialise ses informations d’État sur place, qui sont stockées dans une structure de type OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oifi) dans le SDK Windows.

##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars

L’infrastructure appelle la `OnCreateControlBars` fonction lorsqu’un élément est activé pour la modification sur place.

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
Pointeur vers la fenêtre frame de l’application conteneur.

*pWndDoc*<br/>
Pointeur désignant la fenêtre au niveau du document du conteneur. Peut avoir la valeur NULL si le conteneur est une application SDI.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite; Sinon, 0.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération. Substituez cette fonction pour effectuer tout traitement spécial requis lors de la création de barres de contrôles.

##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame

L’infrastructure appelle la `RepositionFrame` fonction membre pour disposer les barres de contrôle et repositionner la fenêtre de modification sur place pour qu’elle soit visible.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur vers une `RECT` structure ou un `CRect` objet contenant les coordonnées de position actuelle de la fenêtre frame sur place, en pixels, par rapport à la zone cliente.

*lpClipRect*<br/>
Pointeur vers une `RECT` structure ou un `CRect` objet contenant les coordonnées du rectangle de découpage actuel de la fenêtre frame sur place, en pixels, par rapport à la zone cliente.

### <a name="remarks"></a>Notes

La disposition des barres de contrôle dans la fenêtre de conteneur diffère de celle effectuée par une fenêtre frame non OLE. La fenêtre frame non OLE calcule les positions des barres de contrôles et d’autres objets à partir d’une taille de fenêtre frame donnée, comme dans un appel à [CFrameWnd:: RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). La zone cliente est ce qui reste après la soustraction de l’espace pour les barres de contrôle et d’autres objets. Une `COleIPFrameWnd` fenêtre, en revanche, place les barres d’outils en fonction d’une zone client donnée. En d’autres termes `CFrameWnd::RecalcLayout` , fonctionne «de l’extérieur dans,» `COleIPFrameWnd::RepositionFrame` , tandis que fonctionne «de l’intérieur vers l’extérieur».

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)
