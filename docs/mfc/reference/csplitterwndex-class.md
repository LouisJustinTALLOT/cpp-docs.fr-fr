---
title: Classe CSplitterWndEx
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: d7952e3082bf68cff7ad9ba218073081ee522320
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363923"
---
# <a name="csplitterwndex-class"></a>Classe CSplitterWndEx

Représente une fenêtre fractionnée personnalisée.

## <a name="syntax"></a>Syntaxe

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|Constructeur par défaut.|
|`CSplitterWndEx::~CSplitterWndEx`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Appelé par le cadre pour dessiner une fenêtre de splitter. (Overrides [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Notes

Remplacer la `OnDrawSplitter` méthode pour personnaliser l’apparence des composants graphiques d’une fenêtre de splitter.

La `CSplitterWndEx` classe est utilisée avec les méthodes [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), et [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) méthodes, qui sont mis en œuvre par un gestionnaire visuel. Pour amener un gestionnaire visuel à dessiner une fenêtre de `CSplitterWnd` splitter `CSplitterWndEx` dans votre application, remplacez les déclarations de la classe par la classe. Pour les applications de fenêtre de cadre, la classe de fenêtre de splitter est déclarée dans la classe CMainFrame qui est située dans mainfrm.h. Par exemple, voir `OutlookDemo` l’échantillon dans le répertoire Échantillons.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxsplitterwndex.h

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter

Appelé par le cadre pour dessiner une fenêtre de splitter.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur sur le contexte de l’appareil. Si ce paramètre est NULL, le cadre redessiner la fenêtre active.

*nType*<br/>
[dans] Une des `CSplitterWnd::ESplitType` valeurs de recensement qui spécifie l’élément de fenêtre de splitter à dessiner. Les valeurs valides sont `splitBox`, `splitBar`, `splitIntersection` et `splitBorder`.

*Rect*<br/>
[dans] Un rectangle de délimitation qui spécifie les dimensions et l’emplacement pour dessiner l’élément de fenêtre de splitter spécifié.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../hierarchy-chart.md)<br/>
[Classes](mfc-classes.md)<br/>
[Classe CSplitterWnd](csplitterwnd-class.md)<br/>
[Classe CMFCVisualManager](cmfcvisualmanager-class.md)
