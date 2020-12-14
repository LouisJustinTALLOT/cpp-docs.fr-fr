---
description: 'En savoir plus sur : classe CSplitterWndEx'
title: CSplitterWndEx, classe
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: 357f650551871cc9768c8e4e693bd62bb5e69bc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345093"
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx, classe

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
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Appelé par l’infrastructure pour dessiner une fenêtre fractionnée. (Substitue [CSplitterWnd :: OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|

## <a name="remarks"></a>Notes

Substituez la `OnDrawSplitter` méthode pour personnaliser l’apparence des composants graphiques d’une fenêtre fractionnée.

La `CSplitterWndEx` classe est utilisée avec les méthodes [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)et [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) , qui sont implémentées par un gestionnaire visuel. Pour faire en sorte qu’un gestionnaire visuel dessine une fenêtre fractionnée dans votre application, remplacez les déclarations de la `CSplitterWnd` classe par la `CSplitterWndEx` classe. Pour les applications de fenêtres frames, la classe de fenêtre fractionnée est déclarée dans la classe CMainFrame qui se trouve dans MainFrm. h. Pour obtenir un exemple, consultez l' `OutlookDemo` exemple dans le répertoire Samples.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxsplitterwndex. h

## <a name="csplitterwndexondrawsplitter"></a><a name="ondrawsplitter"></a> CSplitterWndEx::OnDrawSplitter

Appelé par l’infrastructure pour dessiner une fenêtre fractionnée.

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers le contexte de périphérique (Device Context). Si ce paramètre a la valeur NULL, le Framework redessine la fenêtre active.

*nType*<br/>
dans L’une des `CSplitterWnd::ESplitType` valeurs d’énumération qui spécifie l’élément de fenêtre fractionnée à dessiner. Les valeurs valides sont `splitBox`, `splitBar`, `splitIntersection` et `splitBorder`.

*rectangulaire*<br/>
dans Rectangle englobant qui spécifie les dimensions et l’emplacement de dessin de l’élément de fenêtre fractionnée spécifié.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../hierarchy-chart.md)<br/>
[Classes](mfc-classes.md)<br/>
[CSplitterWnd, classe](csplitterwnd-class.md)<br/>
[CMFCVisualManager, classe](cmfcvisualmanager-class.md)
