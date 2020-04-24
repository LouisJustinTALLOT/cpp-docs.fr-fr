---
title: Classe CSplitterWnd
ms.date: 11/04/2016
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
ms.openlocfilehash: a872854af1695b8b2b347b21d73165d259b3a986
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753067"
---
# <a name="csplitterwnd-class"></a>Classe CSplitterWnd

Fournit les fonctionnalités d'une fenêtre fractionnée, qui est une fenêtre contenant plusieurs volets.

## <a name="syntax"></a>Syntaxe

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Appelez pour `CSplitterWnd` construire un objet.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|Effectue la prochaine pane ou la commande pane précédente.|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Vérifie si la prochaine pane ou la commande précédente de pane est actuellement possible.|
|[CSplitterWnd::Créer](#create)|Appelez pour créer une fenêtre de splitter dynamique et attachez-la à l’objet. `CSplitterWnd`|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Crée un contrôle partagé de barre de défilement.|
|[CSplitterWnd::CreateStatic](#createstatic)|Appelez pour créer une fenêtre de splitter statique et attachez-la à l’objet. `CSplitterWnd`|
|[CSplitterWnd::CreateView](#createview)|Appelez pour créer une vitre dans une fenêtre de splitter.|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Supprime une colonne de la fenêtre du séparaur.|
|[CSplitterWnd::DeleteRow](#deleterow)|Supprime une ligne de la fenêtre du séparaur.|
|[CSplitterWnd::DéléteView](#deleteview)|Supprime une vue de la fenêtre du séparaur.|
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Exécute la commande fendue du clavier, habituellement "Window Split."|
|[CSplitterWnd::DoScroll](#doscroll)|Effectue le défilement synchronisé des fenêtres fendues.|
|[CSplitterWnd::DoScrollBy](#doscrollby)|Les rouleaux divisent les fenêtres par un nombre donné de pixels.|
|[CSplitterWnd::GetActivePane](#getactivepane)|Détermine la vitre active à partir de la mise au point ou de la vue active dans le cadre.|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Retourne le nombre actuel de colonnes de vitres.|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Renvoie les informations sur la colonne spécifiée.|
|[CSplitterWnd::GetPane](#getpane)|Retourne la vitre à la rangée et à la colonne spécifiées.|
|[CSplitterWnd::GetRowCount](#getrowcount)|Retourne le nombre actuel de rangées de vitres.|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Renvoie les informations sur la ligne spécifiée.|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Retourne le style de scroll-bar partagé.|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Renvoie l’ID de fenêtre de l’enfant de la vitre à la rangée et à la colonne spécifiées.|
|[CSplitterWnd::IsChildPane](#ischildpane)|Appelez pour déterminer si la fenêtre est actuellement une vitre pour enfants de cette fenêtre de séparaur.|
|[CSplitterWnd::IsTracking](#istracking)|Détermine si la barre de séparation est actuellement déplacée.|
|[CSplitterWnd::RecalcLayout](#recalclayout)|Appelez pour redisjouer la fenêtre du splitter après ajustement de la taille de la ligne ou de la colonne.|
|[CSplitterWnd::SetActivePane](#setactivepane)|Définit une vitre pour être l’active dans le cadre.|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Appelez pour définir les informations de colonne spécifiées.|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Appelez pour définir les informations de ligne spécifiées.|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Spécifie le nouveau style scroll-bar pour le support partagé de la fenêtre splitter.|
|[CSplitterWnd::SplitColumn](#splitcolumn)|Indique où une fenêtre de cadre se divise verticalement.|
|[CSplitterWnd::SplitRow](#splitrow)|Indique où une fenêtre de cadre se divise horizontalement.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|Appelé par le cadre pour dessiner la fenêtre du diviseur.|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Rend une image d’une fenêtre fendue.|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Rend l’image d’une fenêtre fendue pour être la même taille et la forme que la fenêtre de cadre.|

## <a name="remarks"></a>Notes

Un volet est généralement un objet spécifique à l’application dérivé de [CView](../../mfc/reference/cview-class.md), mais il peut être n’importe quel objet [CWnd](../../mfc/reference/cwnd-class.md) qui a l’ID de fenêtre d’enfant approprié.

Un `CSplitterWnd` objet est généralement intégré dans un objet [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) parent. Créez `CSplitterWnd` un objet à l’aide des étapes suivantes :

1. Intégrer une `CSplitterWnd` variable de membre dans le cadre parent.

2. Remplacer la fonction de membre CFrameWnd du cadre parent [: :OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) fonction de membre.

3. De l’intérieur `OnCreateClient`du plus élevé , appelez la `CSplitterWnd`fonction membre [Create](#create) or [CreateStatic](#createstatic) de .

Appelez `Create` la fonction membre pour créer une fenêtre de splitter dynamique. Une fenêtre de splitter dynamique est généralement utilisée pour créer et faire défiler un certain nombre de volets individuels, ou vues, du même document. Le cadre crée automatiquement une vitre initiale pour le séparaur; puis le cadre crée, resize et dispose de vitres supplémentaires que l’utilisateur actionne les commandes de la fenêtre de splitter.

Lorsque vous `Create`appelez, vous spécifiez une hauteur de rangée minimale et la largeur de la colonne qui déterminent quand les vitres sont trop petites pour être entièrement affichées. Après votre `Create`appel, vous pouvez ajuster ces minimums en appelant les fonctions [membres SetColumnInfo](#setcolumninfo) et [SetRowInfo.](#setrowinfo)

Utilisez également `SetColumnInfo` `SetRowInfo` les fonctions et les fonctions des membres pour définir une largeur « idéale » pour une colonne et une hauteur « idéale » pour une rangée. Lorsque le cadre affiche une fenêtre de splitter, il affiche d’abord le cadre parent, puis la fenêtre du séparamètre. Le cadre établit ensuite les vitres en colonnes et en rangées selon leurs dimensions idéales, en fonction de la partie supérieure gauche au coin inférieur droit de la zone cliente de la fenêtre du séparamètre.

Tous les volets d’une fenêtre de sépara mètre dynamique doivent être de la même classe. Les applications familières qui prennent en charge les fenêtres de splitter dynamiques incluent Microsoft Word et Microsoft Excel.

Utilisez `CreateStatic` la fonction membre pour créer une fenêtre de splitter statique. L’utilisateur ne peut modifier que la taille des vitres dans une fenêtre de sépara mètre statique, et non son numéro ou son ordre.

Vous devez créer spécifiquement toutes les vitres du séparamètre statique lorsque vous créez le séparamètre statique. Assurez-vous de créer toutes les vitres `OnCreateClient` avant le retour de la fonction du membre du cadre parent, ou le cadre n’affichera pas correctement la fenêtre.

La `CreateStatic` fonction membre initialise automatiquement un séparamètre statique avec une hauteur de rangée minimale et une largeur de colonne de 0. Après votre `Create`appel, ajustez ces minimums en appelant les fonctions [membres SetColumnInfo](#setcolumninfo) et [SetRowInfo.](#setrowinfo) Utilisez `SetColumnInfo` également `SetRowInfo` et `CreateStatic` après votre appel pour indiquer les dimensions idéales souhaitées de vitre.

Les vitres individuelles d’un séparamètre statique appartiennent souvent à différentes classes. Pour des exemples de fenêtres de splitter statiques, voir l’éditeur graphique et le gestionnaire de fichiers Windows.

Une fenêtre splitter prend en charge les barres de défilement spéciales (à l’exception des barres de défilement que les vitres peuvent avoir). Ces barres de défilement sont des enfants de l’objet `CSplitterWnd` et sont partagées avec les vitres.

Vous créez ces barres de défilement spéciales lorsque vous créez la fenêtre splitter. Par exemple, `CSplitterWnd` un qui a une rangée, deux colonnes, et le style WS_VSCROLL affichera une barre de défilement vertical qui est partagée par les deux volets. Lorsque l’utilisateur déplace la barre de défilement, WM_VSCROLL messages sont envoyés aux deux volets. Lorsque les vitres réglent la position de la barre de défilement, la barre de défilement partagée est définie.

Pour plus d’informations sur les fenêtres de splitter, voir [Note technique 29](../../mfc/tn029-splitter-windows.md).

Pour plus d’informations sur la façon de créer des fenêtres de splitter dynamique, voir :

- [Scribble](../../overview/visual-cpp-samples.md) échantillon MFC

- MFC échantillon [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterWnd::ActivateNext

Appelé par le cadre pour effectuer la prochaine pane ou commande pane précédente.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Paramètres

*bPrev*<br/>
Indique quelle fenêtre activer. **VRAI** pour le précédent; **FALSE** pour la prochaine.

### <a name="remarks"></a>Notes

Cette fonction de membre est une commande de haut niveau `CSplitterWnd` qui est utilisée par la classe [CView](../../mfc/reference/cview-class.md) pour déléguer à la mise en œuvre.

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterWnd::CanActivateNext

Appelé par le cadre pour vérifier si la prochaine pane ou la commande pane précédente est actuellement possible.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Paramètres

*bPrev*<br/>
Indique quelle fenêtre activer. **VRAI** pour le précédent; **FALSE** pour la prochaine.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre est une commande de haut niveau `CSplitterWnd` qui est utilisée par la classe [CView](../../mfc/reference/cview-class.md) pour déléguer à la mise en œuvre.

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterWnd::Créer

Pour créer une fenêtre de `Create` splitter dynamique, appelez la fonction membre.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    int nMaxRows,
    int nMaxCols,
    SIZE sizeMin,
    CCreateContext* pContext,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
La fenêtre de cadre parent de la fenêtre du splitter.

*nMaxRows (en)*<br/>
Le nombre maximum de lignes dans la fenêtre du diviseur. Cette valeur ne doit pas dépasser 2.

*nMaxCols (en)*<br/>
Le nombre maximum de colonnes dans la fenêtre du séparaur. Cette valeur ne doit pas dépasser 2.

*sizeMin (en)*<br/>
Spécifie la taille minimale à laquelle une vitre peut être affichée.

*pContext*<br/>
Un pointeur vers une structure [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) Dans la plupart des cas, cela peut être le *pContext* passé à la fenêtre de cadre parent.

*dwStyle (en)*<br/>
Spécifie le style de fenêtre.

*nID*<br/>
L’id de fenêtre d’enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST à moins que la fenêtre du diviseur ne soit imbriquée à l’intérieur d’une autre fenêtre de séparaur.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez intégrer `CSplitterWnd` un objet [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) parent en prenant les mesures suivantes :

1. Intégrer une `CSplitterWnd` variable de membre dans le cadre parent.

1. Remplacer la fonction de membre CFrameWnd du cadre parent [: :OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) fonction de membre.

1. Appelez `Create` la fonction membre de `OnCreateClient`l’intérieur du dépassement .

Lorsque vous créez une fenêtre de splitter à partir d’un cadre parent, passez le *paramètre pContexte* du cadre parent à la fenêtre du splitter. Sinon, ce paramètre peut être NULL.

La hauteur minimale initiale de la rangée et la largeur de colonne d’une fenêtre de splitter dynamique sont définies par le paramètre *sizeMin.* Ces minimums, qui déterminent si une vitre est trop petite pour être montrée dans son intégralité, peuvent être modifiées avec les fonctions des membres [SetRowInfo](#setrowinfo) et [SetColumnInfo.](#setcolumninfo)

Pour en savoir plus sur les fenêtres dynamiques de splitter, voir "Splitter Windows" dans l’article [Multiple Documents Types, Vues et Frame Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), Note Technique [29](../../mfc/tn029-splitter-windows.md), et la vue d’ensemble de la `CSplitterWnd` classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl

Appelé par le cadre pour créer un contrôle partagé de barre de défilement.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style de fenêtre.

*nID*<br/>
L’id de fenêtre d’enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST à moins que la fenêtre du diviseur ne soit imbriquée à l’intérieur d’une autre fenêtre de séparaur.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Remplacer `CreateScrollBarCtrl` pour inclure des contrôles supplémentaires à côté d’une barre de défilement. Le comportement par défaut est de créer des commandes normales de barre de défilement Windows.

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterWnd::CreateStatic

Pour créer une fenêtre de `CreateStatic` splitter statique, appelez la fonction membre.

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
La fenêtre de cadre parent de la fenêtre du splitter.

*nRows*<br/>
Nombre de lignes. Cette valeur ne doit pas dépasser 16.

*nCols*<br/>
Nombre de colonnes. Cette valeur ne doit pas dépasser 16.

*dwStyle (en)*<br/>
Spécifie le style de fenêtre.

*nID*<br/>
L’id de fenêtre d’enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST à moins que la fenêtre du diviseur ne soit imbriquée à l’intérieur d’une autre fenêtre de séparaur.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

A `CSplitterWnd` est généralement intégré `CFrameWnd` dans un parent ou un objet [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) en prenant les étapes suivantes :

1. Intégrer une `CSplitterWnd` variable de membre dans le cadre parent.

1. Remplacer la fonction de `OnCreateClient` membre du cadre parent.

1. Appelez `CreateStatic` la fonction membre de l’intérieur du [CFrameWnd remplacé::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Une fenêtre de sépara teur statique contient un nombre fixe de vitres, souvent de différentes classes.

Lorsque vous créez une fenêtre de splitter statique, vous devez en même temps créer toutes ses vitres. La fonction membre [CreateView](#createview) est généralement utilisée à cette fin, mais vous pouvez également créer d’autres classes non vues.

La hauteur minimale initiale de la rangée et la largeur de colonne pour une fenêtre de sépara limite statique est de 0. Ces minimums, qui déterminent quand une vitre est trop petite pour être montrée dans son intégralité, peuvent être modifiées avec les fonctions des membres [SetRowInfo](#setrowinfo) et [SetColumnInfo.](#setcolumninfo)

Pour ajouter des barres de défilement à une fenêtre de splitter statique, ajoutez les styles WS_HSCROLL et WS_VSCROLL à *dwStyle*.

Voir "Splitter Windows" dans l’article [Multiple Document Types, Vues et Frame Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), Note Technique [29](../../mfc/tn029-splitter-windows.md), et la vue d’ensemble de la `CSplitterWnd` classe pour en savoir plus sur les fenêtres de splitter statiques.

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterWnd::CreateView

Crée les vitres pour une fenêtre de splitter statique.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Paramètres

*Ligne*<br/>
Spécifie la ligne de fenêtre du diviseur dans laquelle placer la nouvelle vue.

*col*<br/>
Spécifie la colonne de fenêtre du diviseur dans laquelle placer la nouvelle vue.

*pViewClass (en)*<br/>
Spécifie la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la nouvelle vue.

*sizeInit*<br/>
Spécifie la taille initiale de la nouvelle vue.

*pContext*<br/>
Un pointeur vers un contexte de création utilisé pour créer la vue (généralement le *pContext* passé dans le cadre parent passé dans le cadre parent passé [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) fonction membre dans lequel la fenêtre splitter est en cours de création).

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Toutes les vitres d’une fenêtre de sépara mètre statique doivent être créées avant que le cadre n’affiche le séparamètre.

Le cadre appelle également cette fonction de membre pour créer de nouvelles vitres lorsque l’utilisateur d’une fenêtre de splitter dynamique divise une vitre, une rangée ou une colonne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd

Appelez pour `CSplitterWnd` construire un objet.

```
CSplitterWnd();
```

### <a name="remarks"></a>Notes

Construire `CSplitterWnd` un objet en deux étapes. Tout d’abord, appelez le `CSplitterWnd` constructeur, qui crée l’objet, puis appelez la fonction de `CSplitterWnd` membre [Créer,](#create) qui crée la fenêtre de splitter et l’attache à l’objet.

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterWnd::DeleteColumn

Supprime une colonne de la fenêtre du séparaur.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Paramètres

*colDelete*<br/>
Spécifie la colonne à supprimer.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le cadre pour mettre en œuvre la logique de la fenêtre de splitter dynamique (c’est-à-dire, si la fenêtre de splitter a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, avec la fonction virtuelle [CreateView](#createview), pour implémenter des splitters dynamiques plus avancés.

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterWnd::DeleteRow

Supprime une ligne de la fenêtre du séparaur.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Paramètres

*rowDelete*<br/>
Spécifie la ligne à supprimer.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le cadre pour mettre en œuvre la logique de la fenêtre de splitter dynamique (c’est-à-dire, si la fenêtre de splitter a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, avec la fonction virtuelle [CreateView](#createview), pour implémenter des splitters dynamiques plus avancés.

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterWnd::DéléteView

Supprime une vue de la fenêtre du séparaur.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Paramètres

*Ligne*<br/>
Spécifie la ligne de fenêtre du splitter à laquelle supprimer la vue.

*col*<br/>
Spécifie la colonne de fenêtre du splitter à laquelle supprimer la vue.

### <a name="remarks"></a>Notes

Si la vue active est supprimée, la prochaine vue deviendra active. La mise en œuvre par défaut suppose que la vue supprimera automatiquement dans [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

Cette fonction de membre est appelée par le cadre pour mettre en œuvre la logique de la fenêtre de splitter dynamique (c’est-à-dire, si la fenêtre de splitter a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, avec la fonction virtuelle [CreateView](#createview), pour implémenter des splitters dynamiques plus avancés.

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit

Exécute la commande fendue du clavier, habituellement "Window Split."

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre est une commande de haut niveau `CSplitterWnd` qui est utilisée par la classe [CView](../../mfc/reference/cview-class.md) pour déléguer à la mise en œuvre.

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterWnd::DoScroll

Effectue le défilement synchronisé des fenêtres fendues.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*pViewDe*<br/>
Un pointeur vers la vue d’où provient le message de défilement.

*nScrollCode (en)*<br/>
Un code à barres de défilement qui indique la demande de défilement de l’utilisateur. Ce paramètre est composé de deux parties : un byte à faible ordre, qui détermine le type de défilement se produisant horizontalement, et un byte de haut ordre, qui détermine le type de défilement se produisant verticalement :

- SB_BOTTOM Faites défiler vers le bas.

- SB_LINEDOWN Parchemine une ligne vers le bas.

- SB_LINEUP Faites défiler une ligne.

- SB_PAGEDOWN parchemine une page vers le bas.

- SB_PAGEUP parchemine une page vers le haut.

- SB_TOP Faites défiler vers le haut.

*bDoScroll (en)*<br/>
Détermine si l’action de défilement spécifiée se produit. Si *bDoScroll* est VRAI (c’est-à-dire, si une fenêtre d’enfant existe, et si les fenêtres fendues ont une plage de défilement), alors l’action de défilement spécifiée peut avoir lieu; si *bDoScroll* est FALSE (c’est-à-dire, si aucune fenêtre d’enfant n’existe, ou si les vues fractionnées n’ont pas de plage de défilement), alors le défilement ne se produit pas.

### <a name="return-value"></a>Valeur de retour

Nonzero si le défilement synchronisé se produit; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le cadre pour effectuer le défilement synchronisé des fenêtres fendues lorsque la vue reçoit un message de défilement. Remplacement pour exiger une action de l’utilisateur avant que le défilement synchronisé ne soit autorisé.

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterWnd::DoScrollBy

Les rouleaux divisent les fenêtres par un nombre donné de pixels.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*pViewDe*<br/>
Un pointeur vers la vue d’où provient le message de défilement.

*tailleScroll*<br/>
Nombre de pixels à faire défiler horizontalement et verticalement.

*bDoScroll (en)*<br/>
Détermine si l’action de défilement spécifiée se produit. Si *bDoScroll* est VRAI (c’est-à-dire, si une fenêtre d’enfant existe, et si les fenêtres fendues ont une plage de défilement), alors l’action de défilement spécifiée peut avoir lieu; si *bDoScroll* est FALSE (c’est-à-dire, si aucune fenêtre d’enfant n’existe, ou si les vues fractionnées n’ont pas de plage de défilement), alors le défilement ne se produit pas.

### <a name="return-value"></a>Valeur de retour

Nonzero si le défilement synchronisé se produit; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par le cadre en réponse à un message de défilement, pour effectuer le défilement synchronisé des fenêtres fendues par la quantité, en pixels, indiqué par *sizeScroll*. Les valeurs positives indiquent le défilement vers le bas et vers la droite; valeurs négatives indiquent le défilement vers le haut et vers la gauche.

Remplacer pour exiger une action de l’utilisateur avant de permettre le parchemin.

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterWnd::GetActivePane

Détermine la vitre active à partir de la mise au point ou de la vue active dans le cadre.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Paramètres

*pRow*<br/>
Un pointeur à une **int** pour récupérer le numéro de ligne de la vitre active.

*pCol (pCol)*<br/>
Un pointeur à une **int** pour récupérer le numéro de colonne de la vitre active.

### <a name="return-value"></a>Valeur de retour

Pointeur sur la vitre active. NULL si il n’existe pas de volet actif.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le cadre pour déterminer la vitre active dans une fenêtre de splitter. Remplacer pour exiger une action de l’utilisateur avant d’obtenir le volet actif.

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterWnd::GetColumnCount

Retourne le nombre actuel de colonnes de vitres.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre actuel de colonnes dans le séparaur. Pour un séparamètre statique, il s’agira également du nombre maximum de colonnes.

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo

Renvoie les informations sur la colonne spécifiée.

```cpp
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Paramètres

*col*<br/>
Spécifie une colonne.

*cxCur (en)*<br/>
Une référence à une **int** à régler sur la largeur actuelle de la colonne.

*cxMin (en)*<br/>
Une référence à une **int** à régler à la largeur minimale actuelle de la colonne.

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterWnd::GetPane

Retourne la vitre à la rangée et à la colonne spécifiées.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Paramètres

*Ligne*<br/>
Spécifie une rangée.

*col*<br/>
Spécifie une colonne.

### <a name="return-value"></a>Valeur de retour

Retourne la vitre à la rangée et à la colonne spécifiées. Le volet retourné est généralement une classe [dérivée de CView.](../../mfc/reference/cview-class.md)

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterWnd::GetRowCount

Retourne le nombre actuel de rangées de vitres.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre actuel de lignes dans la fenêtre du diviseur. Pour une fenêtre de séparaur statique, il s’agira également du nombre maximum de rangées.

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterWnd::GetRowInfo

Renvoie les informations sur la ligne spécifiée.

```cpp
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Paramètres

*Ligne*<br/>
Spécifie une rangée.

*cyCur (cyCur)*<br/>
Référence à **int** à régler à la hauteur actuelle de la ligne en pixels.

*cyMin (en)*<br/>
Référence à **l’int** à régler à la hauteur minimale actuelle de la rangée en pixels.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour obtenir des informations sur la rangée spécifiée. Le *paramètre cyCur* est rempli de la hauteur actuelle de la rangée spécifiée, et *le cyMin* est rempli de la hauteur minimale de la rangée.

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle

Retourne le style de barre de défilement partagé pour la fenêtre splitter.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Un ou plusieurs des drapeaux de style fenêtres suivants, en cas de succès :

- WS_HSCROLL Si le séparaur gère actuellement les barres de défilement horizontales partagées.

- WS_VSCROLL Si le séparaur gère actuellement les barres de défilement verticales partagées.

Si zéro, la fenêtre splitter ne gère actuellement pas les barres de défilement partagées.

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol

Obtient l’ID de fenêtre de l’enfant pour la vitre à la rangée et à la colonne spécifiées.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Paramètres

*Ligne*<br/>
Spécifie la ligne de fenêtre du diviseur.

*col*<br/>
Spécifie la colonne de fenêtre du diviseur.

### <a name="return-value"></a>Valeur de retour

L’ID de fenêtre de l’enfant pour la vitre.

### <a name="remarks"></a>Notes

Cette fonction de membre est utilisée pour créer des non-vues comme des vitres et peut être appelée avant l’existence du volet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterWnd::IsChildPane

Détermine si *pWnd* est actuellement une vitre pour enfants de cette fenêtre de séparaur.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
Un pointeur à un objet [CWnd](../../mfc/reference/cwnd-class.md) à tester.

*pRow*<br/>
Un pointeur à une **int** dans laquelle stocker le numéro de rangée.

*pCol (pCol)*<br/>
Un pointeur à une **int** dans laquelle stocker un numéro de colonne.

### <a name="return-value"></a>Valeur de retour

Si nonzero, *pWnd* est actuellement une vitre pour enfants de cette fenêtre de splitter, et *pRow* et *pCol* sont remplis avec la position de la vitre dans la fenêtre du diviseur. Si *pWnd n’est* pas une vitre pour enfants de cette fenêtre de séparaur, 0 est retourné.

### <a name="remarks"></a>Notes

Dans les versions Visual CMD avant 6,0, cette fonction a été définie comme

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Cette version est maintenant obsolète et ne doit pas être utilisée.

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterWnd::IsTracking

Appelez cette fonction de membre pour déterminer si la barre de séparaur dans la fenêtre est actuellement déplacée.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si une opération de splitter est en cours; sinon 0.

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter

Rend une image d’une fenêtre fendue.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Un pointeur sur le contexte de l’appareil dans lequel dessiner. Si *pDC* est NULL, puis [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) est appelé par le cadre et aucune fenêtre fendue n’est tirée.

*nType*<br/>
Une valeur `enum ESplitType`de la , qui peut être l’un des suivants:

- `splitBox`La boîte à dragter splitter.

- `splitBar`La barre qui apparaît entre les deux fenêtres fendues.

- `splitIntersection`L’intersection des fenêtres fendues. Cet élément ne sera pas appelé lors de l’exécution sur Windows 95/98.

- `splitBorder`La fenêtre fendue borde.

*Rect*<br/>
Une référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) spécifiant la taille et la forme des fenêtres fendues.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le cadre pour dessiner et spécifier les caractéristiques exactes d’une fenêtre de splitter. Remplacement `OnDrawSplitter` pour la personnalisation avancée de l’imagerie pour les différents composants graphiques d’une fenêtre splitter. L’imagerie par défaut est similaire au splitter de Microsoft Works pour Windows ou Microsoft Windows 95/98, en ce temps que les intersections des barres de splitter sont mélangées.

Pour en savoir plus sur les fenêtres dynamiques de splitter, voir "Splitter Windows" dans l’article [Multiple Documents Types, Vues et Frame Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), Note Technique [29](../../mfc/tn029-splitter-windows.md), et la vue d’ensemble de la `CSplitterWnd` classe.

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker

Rend l’image d’une fenêtre fendue pour être la même taille et la forme que la fenêtre de cadre.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*Rect*<br/>
Référence à `CRect` un objet spécifiant le rectangle de suivi.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le cadre lors de la resizing des diviseurs. Remplacement `OnInvertTracker` pour la personnalisation avancée de l’imagerie de la fenêtre du séparamètre. L’imagerie par défaut est similaire au splitter de Microsoft Works pour Windows ou Microsoft Windows 95/98, en ce temps que les intersections des barres de splitter sont mélangées.

Pour en savoir plus sur les fenêtres dynamiques de splitter, voir "Splitter Windows" dans l’article [Multiple Documents Types, Vues et Frame Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), Note Technique [29](../../mfc/tn029-splitter-windows.md), et la vue d’ensemble de la `CSplitterWnd` classe.

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterWnd::RecalcLayout

Appelez pour redisjouer la fenêtre du splitter après ajustement de la taille de la ligne ou de la colonne.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour redisjouer correctement la fenêtre du splitter après avoir ajusté les tailles de la ligne et de la colonne avec les fonctions des membres [SetRowInfo](#setrowinfo) et [SetColumnInfo.](#setcolumninfo) Si vous changez la taille de la ligne et de la colonne dans le cadre du processus de création avant que la fenêtre du séparamètre ne soit visible, il n’est pas nécessaire d’appeler cette fonction de membre.

Le cadre appelle cette fonction de membre chaque fois que l’utilisateur resize la fenêtre du splitter ou déplace une fente.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CSplitterWnd::SetColumnInfo](#setcolumninfo).

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterWnd::SetActivePane

Définit une vitre pour être l’active dans le cadre.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*Ligne*<br/>
Si *pWnd* est NULL, spécifie la ligne dans la vitre qui sera active.

*col*<br/>
Si *pWnd* est NULL, spécifie la colonne dans le volet qui sera actif.

*Pwnd*<br/>
Pointeur vers un objet `CWnd`. Si NULL, le volet spécifié par *la ligne* et *le col* est mis actif. Si ce n’est pas NULL, spécifie la vitre qui est placée active.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée par le cadre pour définir une vitre aussi active lorsque l’utilisateur change la mise au point à une vitre dans la fenêtre du cadre. Vous pouvez `SetActivePane` appeler explicitement pour modifier la mise au point vers la vue spécifiée.

Spécifier la vitre en fournissant soit la ligne et la colonne, **ou** en fournissant *pWnd*.

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo

Appelez pour définir les informations de colonne spécifiées.

```cpp
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Paramètres

*col*<br/>
Spécifie une colonne de fenêtre de splitter.

*cxIdeal (en)*<br/>
Spécifie une largeur idéale pour la colonne de fenêtre splitter en pixels.

*cxMin (en)*<br/>
Specifie une largeur minimale pour la colonne de fenêtre splitter en pixels.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour définir une nouvelle largeur minimale et une largeur idéale pour une colonne. La valeur minimale de la colonne détermine quand la colonne sera trop petite pour être entièrement affichée.

Lorsque le cadre affiche la fenêtre du séparamètre, il expose les vitres en colonnes et en rangées selon leurs dimensions idéales, en fonction du coin supérieur gauche au coin inférieur droit de la zone cliente de la fenêtre du séparamètre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterWnd::SetRowInfo

Appelez pour définir les informations de ligne spécifiées.

```cpp
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Paramètres

*Ligne*<br/>
Spécifie une ligne de fenêtre de splitter.

*cyIdeal*<br/>
Specifie une hauteur idéale pour la ligne de fenêtre de splitter en pixels.

*cyMin (en)*<br/>
Specifie une hauteur minimale pour la ligne de fenêtre de splitter en pixels.

### <a name="remarks"></a>Notes

Appelez cette fonction de membre pour définir une nouvelle hauteur minimale et une hauteur idéale pour une rangée. La valeur minimale de la ligne détermine quand la ligne sera trop petite pour être entièrement affichée.

Lorsque le cadre affiche la fenêtre du séparamètre, il expose les vitres en colonnes et en rangées selon leurs dimensions idéales, en fonction du coin supérieur gauche au coin inférieur droit de la zone cliente de la fenêtre du séparamètre.

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle

Spécifie le nouveau style de défilement pour le support partagé de la fenêtre splitter.

```cpp
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Le nouveau modèle de défilement pour le support partagé de la fenêtre de splitter, qui peut être l’une des valeurs suivantes :

- WS_HSCROLL Créer/afficher des barres de défilement partagées horizontales.

- WS_VSCROLL Créer/afficher des barres verticales de défilement partagé.

### <a name="remarks"></a>Notes

Une fois qu’une barre de défilement est créée, elle ne sera pas détruite même si `SetScrollStyle` elle est appelée sans ce style; au lieu de cela ces barres de défilement sont cachées. Cela permet aux barres de défilement de conserver leur état même si elles sont cachées. Après `SetScrollStyle` avoir appelé, il est nécessaire d’appeler [RecalcLayout](#recalclayout) pour que tous les changements prennent effet.

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterWnd::SplitColumn

Indique où une fenêtre de cadre se divise verticalement.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Paramètres

*cxBefore*<br/>
La position, en pixels, avant laquelle la scission se produit.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée lorsqu’une fenêtre de splitter vertical est créée. `SplitColumn`indique l’emplacement par défaut où la scission se produit.

`SplitColumn`est appelé par le cadre pour mettre en œuvre la logique de la fenêtre de splitter dynamique (c’est-à-dire, si la fenêtre de splitter a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, avec la fonction virtuelle [CreateView](#createview), pour implémenter des splitters dynamiques plus avancés.

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterWnd::SplitRow

Indique où une fenêtre de cadre se divise horizontalement.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Paramètres

*cyBefore*<br/>
La position, en pixels, avant laquelle la scission se produit.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction de membre est appelée lorsqu’une fenêtre de splitter horizontale est créée. `SplitRow`indique l’emplacement par défaut où la scission se produit.

`SplitRow`est appelé par le cadre pour mettre en œuvre la logique de la fenêtre de splitter dynamique (c’est-à-dire, si la fenêtre de splitter a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, avec la fonction virtuelle [CreateView](#createview), pour implémenter des splitters dynamiques plus avancés.

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CSplitterWnd::OnDraw

Appelé par le cadre pour dessiner la fenêtre du diviseur.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers un contexte de périphérique.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Échantillon MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)
