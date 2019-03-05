---
title: Classe de CSplitterWndEx
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: 8dedad4e99a37b13dc618859c8e6d8a83a65ea76
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265143"
---
# <a name="csplitterwndex-class"></a>Classe de CSplitterWndEx

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
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Appelé par l’infrastructure pour dessiner une fenêtre fractionnée. (Substitue [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Notes

Remplacer le `OnDrawSplitter` méthode pour personnaliser l’apparence des composants graphiques d’une fenêtre fractionnée.

Le `CSplitterWndEx` classe est utilisée conjointement avec la [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), et [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) méthodes qui sont implémenté par un gestionnaire visuel. Pour déclencher un gestionnaire visuel dessiner une fenêtre fractionnée dans votre application, remplacez les déclarations de la `CSplitterWnd` classe avec la `CSplitterWndEx` classe. Pour les applications de fenêtre frame, la classe de fenêtre de séparateur est déclarée dans la classe CMainFrame qui se trouve dans mainfrm.h. Pour obtenir un exemple, consultez le `OutlookDemo` exemple dans le répertoire d’exemples.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxsplitterwndex.h

##  <a name="ondrawsplitter"></a>  CSplitterWndEx::OnDrawSplitter

Appelé par l’infrastructure pour dessiner une fenêtre fractionnée.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers le contexte de périphérique. Si ce paramètre est NULL, le framework redessine la fenêtre active.

*nType*<br/>
[in] Parmi les `CSplitterWnd::ESplitType` des valeurs d’énumération qui spécifie l’élément de fenêtre de séparateur à dessiner. Les valeurs valides sont `splitBox`, `splitBar`, `splitIntersection` et `splitBorder`.

*rect*<br/>
[in] Un rectangle englobant qui spécifie les dimensions et l’emplacement où dessiner l’élément de fenêtre de séparateur spécifié.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../hierarchy-chart.md)<br/>
[Classes](mfc-classes.md)<br/>
[CSplitterWnd, classe](csplitterwnd-class.md)<br/>
[CMFCVisualManager, classe](cmfcvisualmanager-class.md)
