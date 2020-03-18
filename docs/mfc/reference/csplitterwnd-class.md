---
title: CSplitterWnd, classe
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
ms.openlocfilehash: bee6deed3052d6cc923e432e97ad9a7904060cb6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447439"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd, classe

Fournit les fonctionnalités d'une fenêtre fractionnée, qui est une fenêtre contenant plusieurs volets.

## <a name="syntax"></a>Syntaxe

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CSplitterWnd :: CSplitterWnd](#csplitterwnd)|Appelez pour construire un objet `CSplitterWnd`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CSplitterWnd :: ActivateNext](#activatenext)|Exécute la commande volet suivant ou volet précédent.|
|[CSplitterWnd :: CanActivateNext](#canactivatenext)|Vérifie si la commande volet suivant ou volet précédent est actuellement possible.|
|[CSplitterWnd :: Create](#create)|Appelez pour créer une fenêtre fractionnée dynamique et l’attacher à l’objet `CSplitterWnd`.|
|[CSplitterWnd :: CreateScrollBarCtrl](#createscrollbarctrl)|Crée un contrôle de barre de défilement partagé.|
|[CSplitterWnd :: CreateStatic](#createstatic)|Appelez pour créer une fenêtre fractionnée statique et l’attacher à l’objet `CSplitterWnd`.|
|[CSplitterWnd :: CreateView](#createview)|Appelez pour créer un volet dans une fenêtre fractionnée.|
|[CSplitterWnd ::D eleteColumn](#deletecolumn)|Supprime une colonne de la fenêtre fractionnée.|
|[CSplitterWnd ::D eleteRow](#deleterow)|Supprime une ligne de la fenêtre de fractionnement.|
|[CSplitterWnd ::D eleteView](#deleteview)|Supprime une vue de la fenêtre fractionnée.|
|[CSplitterWnd ::D oKeyboardSplit](#dokeyboardsplit)|Exécute la commande de fractionnement du clavier, généralement « fractionnement de fenêtre ».|
|[CSplitterWnd ::D oScroll](#doscroll)|Effectue le défilement synchronisé des fenêtres fractionnées.|
|[CSplitterWnd ::D oScrollBy](#doscrollby)|Fait défiler les fenêtres fractionnées d’un nombre donné de pixels.|
|[CSplitterWnd :: GetActivePane](#getactivepane)|Détermine le volet actif à partir du focus ou de l’affichage actif dans le frame.|
|[CSplitterWnd :: GetColumnCount](#getcolumncount)|Retourne le nombre de colonnes du volet actuel.|
|[CSplitterWnd :: GetColumnInfo](#getcolumninfo)|Retourne des informations sur la colonne spécifiée.|
|[CSplitterWnd :: GetPane](#getpane)|Retourne le volet au niveau de la ligne et de la colonne spécifiées.|
|[CSplitterWnd :: GetRowCount](#getrowcount)|Retourne le nombre de lignes du volet actuel.|
|[CSplitterWnd :: GetRowInfo](#getrowinfo)|Retourne des informations sur la ligne spécifiée.|
|[CSplitterWnd :: GetScrollStyle](#getscrollstyle)|Retourne le style de barre de défilement partagé.|
|[CSplitterWnd :: IdFromRowCol](#idfromrowcol)|Retourne l’ID de fenêtre enfant du volet au niveau de la ligne et de la colonne spécifiées.|
|[CSplitterWnd :: IsChildPane](#ischildpane)|Appelez pour déterminer si la fenêtre est actuellement un volet enfant de cette fenêtre fractionnée.|
|[CSplitterWnd :: IsTracking](#istracking)|Détermine si la barre de fractionnement est en cours de déplacement.|
|[CSplitterWnd :: RecalcLayout](#recalclayout)|Appelez pour réafficher la fenêtre de fractionnement après avoir ajusté la taille de ligne ou de colonne.|
|[CSplitterWnd :: SetActivePane](#setactivepane)|Définit un volet comme actif dans le cadre.|
|[CSplitterWnd :: SetColumnInfo](#setcolumninfo)|Appelez pour définir les informations de colonne spécifiées.|
|[CSplitterWnd :: SetRowInfo](#setrowinfo)|Appelez pour définir les informations de ligne spécifiées.|
|[CSplitterWnd :: SetScrollStyle](#setscrollstyle)|Spécifie le nouveau style de barre de défilement pour la prise en charge de la barre de défilement partagée de la fenêtre fractionnée.|
|[CSplitterWnd :: SplitColumn](#splitcolumn)|Indique l’emplacement de fractionnement vertical d’une fenêtre frame.|
|[CSplitterWnd :: SplitRow](#splitrow)|Indique l’emplacement de fractionnement horizontal d’une fenêtre frame.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[CSplitterWnd :: OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner la fenêtre fractionnée.|
|[CSplitterWnd :: OnDrawSplitter](#ondrawsplitter)|Génère le rendu d’une image d’une fenêtre fractionnée.|
|[CSplitterWnd :: OnInvertTracker](#oninverttracker)|Restitue l’image d’une fenêtre fractionnée avec une taille et une forme identiques à celles de la fenêtre frame.|

## <a name="remarks"></a>Notes

Un volet est généralement un objet spécifique à l’application dérivé de [CView](../../mfc/reference/cview-class.md), mais il peut s’agir de n’importe quel objet [CWND](../../mfc/reference/cwnd-class.md) avec l’ID de fenêtre enfant approprié.

Un objet `CSplitterWnd` est généralement incorporé dans un objet [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) parent. Créez un objet `CSplitterWnd` en procédant comme suit :

1. Incorporez une variable membre `CSplitterWnd` dans le frame parent.

2. Substituez la fonction membre [CFrameWnd :: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) du frame parent.

3. À partir de la `OnCreateClient`substituée, appelez la fonction membre [Create](#create) ou [CreateStatic](#createstatic) de `CSplitterWnd`.

Appelez la fonction membre `Create` pour créer une fenêtre fractionnée dynamique. Une fenêtre fractionnée dynamique est généralement utilisée pour créer et faire défiler un certain nombre de volets individuels, ou vues, du même document. L’infrastructure crée automatiquement un volet initial pour le séparateur. Ensuite, l’infrastructure crée, redimensionne et supprime des volets supplémentaires lorsque l’utilisateur exécute les contrôles de la fenêtre fractionnée.

Lorsque vous appelez `Create`, vous spécifiez une hauteur de ligne et une largeur de colonne minimales qui déterminent le moment où les volets sont trop petits pour être affichés entièrement. Après avoir appelé `Create`, vous pouvez ajuster ces valeurs minimales en appelant les fonctions membres [SetColumnInfo](#setcolumninfo) et [SetRowInfo](#setrowinfo) .

Utilisez également les fonctions membres `SetColumnInfo` et `SetRowInfo` pour définir une largeur « idéale » pour une colonne et une hauteur « idéale » pour une ligne. Lorsque l’infrastructure affiche une fenêtre fractionnée, elle affiche tout d’abord le frame parent, puis la fenêtre fractionnée. Le Framework aligne ensuite les volets dans les colonnes et les lignes en fonction de leurs dimensions idéales, en travaillant à partir de l’angle supérieur gauche vers le coin inférieur droit de la zone cliente de la fenêtre fractionnée.

Tous les volets d’une fenêtre fractionnée dynamique doivent être de la même classe. Les applications familières qui prennent en charge les fenêtres fractionnées dynamiques sont Microsoft Word et Microsoft Excel.

Utilisez la fonction membre `CreateStatic` pour créer une fenêtre fractionnée statique. L’utilisateur ne peut modifier que la taille des volets dans une fenêtre fractionnée statique, et non leur nombre ou ordre.

Vous devez spécifiquement créer tous les volets du séparateur statique lorsque vous créez le séparateur statique. Veillez à créer tous les volets avant le retour de la fonction membre `OnCreateClient` du frame parent, sans quoi l’infrastructure n’affichera pas correctement la fenêtre.

La fonction membre `CreateStatic` Initialise automatiquement un séparateur statique avec une hauteur de ligne minimale et une largeur de colonne de 0. Après avoir appelé `Create`, ajustez ces valeurs minimales en appelant les fonctions membres [SetColumnInfo](#setcolumninfo) et [SetRowInfo](#setrowinfo) . Utilisez également `SetColumnInfo` et `SetRowInfo` après avoir appelé `CreateStatic` pour indiquer les dimensions souhaitées du volet idéal.

Les volets individuels d’un séparateur statique appartiennent souvent à des classes différentes. Pour obtenir des exemples de fenêtres fractionnées statiques, consultez l’éditeur graphique et le gestionnaire de fichiers Windows.

Une fenêtre fractionnée prend en charge les barres de défilement spéciales (à l’exception des barres de défilement que les volets peuvent avoir). Ces barres de défilement sont des enfants de l’objet `CSplitterWnd` et sont partagées avec les volets.

Vous créez ces barres de défilement spéciales lorsque vous créez la fenêtre fractionnée. Par exemple, un `CSplitterWnd` qui a une ligne, deux colonnes et le style WS_VSCROLL affichent une barre de défilement verticale qui est partagée par les deux volets. Lorsque l’utilisateur déplace la barre de défilement, WM_VSCROLL messages sont envoyés aux deux volets. Quand les volets définissent la position de la barre de défilement, la barre de défilement partagée est définie.

Pour plus d’informations sur les fenêtres fractionnées, consultez la [note technique 29](../../mfc/tn029-splitter-windows.md).

Pour plus d’informations sur la création de fenêtres fractionnées dynamiques, consultez :

- Exemple [Scribble](../../overview/visual-cpp-samples.md) MFC

- Exemple MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

##  <a name="activatenext"></a>CSplitterWnd :: ActivateNext

Appelé par le Framework pour exécuter la commande suivante du volet ou du volet précédent.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Paramètres

*bPrev*<br/>
Indique la fenêtre à activer. **True** pour le précédent ; **False** pour Next.

### <a name="remarks"></a>Notes

Cette fonction membre est une commande de haut niveau qui est utilisée par la classe [CView](../../mfc/reference/cview-class.md) pour déléguer à l’implémentation de `CSplitterWnd`.

##  <a name="canactivatenext"></a>CSplitterWnd :: CanActivateNext

Appelé par l’infrastructure pour vérifier si la commande volet suivant ou volet précédent est actuellement possible.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Paramètres

*bPrev*<br/>
Indique la fenêtre à activer. **True** pour le précédent ; **False** pour Next.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est une commande de haut niveau qui est utilisée par la classe [CView](../../mfc/reference/cview-class.md) pour déléguer à l’implémentation de `CSplitterWnd`.

##  <a name="create"></a>CSplitterWnd :: Create

Pour créer une fenêtre fractionnée dynamique, appelez la fonction membre `Create`.

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
Fenêtre frame parente de la fenêtre fractionnée.

*nMaxRows*<br/>
Nombre maximal de lignes dans la fenêtre fractionnée. Cette valeur ne doit pas dépasser 2.

*nMaxCols*<br/>
Nombre maximal de colonnes dans la fenêtre fractionnée. Cette valeur ne doit pas dépasser 2.

*sizeMin*<br/>
Spécifie la taille minimale à laquelle un volet peut s’afficher.

*pContext*<br/>
Pointeur vers une structure [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Dans la plupart des cas, il peut s’agir du *pContext* passé à la fenêtre frame parente.

*dwStyle*<br/>
Spécifie le style de la fenêtre.

*nID*<br/>
ID de fenêtre enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST, sauf si la fenêtre fractionnée est imbriquée dans une autre fenêtre fractionnée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous pouvez incorporer un `CSplitterWnd` dans un objet [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) parent en procédant comme suit :

1. Incorporez une variable membre `CSplitterWnd` dans le frame parent.

1. Substituez la fonction membre [CFrameWnd :: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) du frame parent.

1. Appelez la fonction membre `Create` à partir de la `OnCreateClient`substituée.

Quand vous créez une fenêtre fractionnée à partir d’un frame parent, transmettez le paramètre *pContext* du frame parent à la fenêtre fractionnée. Dans le cas contraire, ce paramètre peut avoir la valeur NULL.

La hauteur de ligne minimale et la largeur de colonne initiales d’une fenêtre fractionnée dynamique sont définies par le paramètre *sizeMin* . Ces valeurs minimales, qui déterminent si un volet est trop petit pour être affiché dans son intégralité, peuvent être modifiées avec les fonctions membres [SetRowInfo](#setrowinfo) et [SetColumnInfo](#setcolumninfo) .

Pour plus d’informations sur les fenêtres fractionnées dynamiques, consultez « fenêtres fractionnées » dans l’article [types de documents multiples, vues et fenêtres Frame](../../mfc/multiple-document-types-views-and-frame-windows.md), [note technique 29](../../mfc/tn029-splitter-windows.md)et vue d’ensemble de la classe `CSplitterWnd`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>CSplitterWnd :: CreateScrollBarCtrl

Appelé par l’infrastructure pour créer un contrôle de barre de défilement partagé.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style de la fenêtre.

*nID*<br/>
ID de fenêtre enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST, sauf si la fenêtre fractionnée est imbriquée dans une autre fenêtre fractionnée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Substituez `CreateScrollBarCtrl` pour inclure des contrôles supplémentaires en regard d’une barre de défilement. Le comportement par défaut consiste à créer des contrôles de barre de défilement Windows normaux.

##  <a name="createstatic"></a>CSplitterWnd :: CreateStatic

Pour créer une fenêtre fractionnée statique, appelez la fonction membre `CreateStatic`.

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
Fenêtre frame parente de la fenêtre fractionnée.

*nRows*<br/>
Nombre de lignes. Cette valeur ne doit pas dépasser 16.

*nCols*<br/>
Nombre de colonnes. Cette valeur ne doit pas dépasser 16.

*dwStyle*<br/>
Spécifie le style de la fenêtre.

*nID*<br/>
ID de fenêtre enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST, sauf si la fenêtre fractionnée est imbriquée dans une autre fenêtre fractionnée.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Une `CSplitterWnd` est généralement incorporée dans un objet `CFrameWnd` ou [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) parent en procédant comme suit :

1. Incorporez une variable membre `CSplitterWnd` dans le frame parent.

1. Substituez la fonction membre `OnCreateClient` du frame parent.

1. Appelez la fonction membre `CreateStatic` à partir de l’élément [CFrameWnd :: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)substitué.

Une fenêtre fractionnée statique contient un nombre fixe de volets, souvent issus de différentes classes.

Lorsque vous créez une fenêtre fractionnée statique, vous devez en même temps créer tous ses volets. La fonction membre [CreateView](#createview) est généralement utilisée à cet effet, mais vous pouvez également créer d’autres classes non vues.

La hauteur de ligne minimale et la largeur de colonne initiales d’une fenêtre fractionnée statique sont 0. Ces valeurs minimales, qui déterminent le moment où un volet est trop petit pour être affiché dans son intégralité, peuvent être modifiées avec les fonctions membres [SetRowInfo](#setrowinfo) et [SetColumnInfo](#setcolumninfo) .

Pour ajouter des barres de défilement à une fenêtre fractionnée statique, ajoutez les styles WS_HSCROLL et WS_VSCROLL à *dwStyle*.

Pour plus d’informations sur les fenêtres fractionnées statiques, consultez « fenêtres fractionnées » dans l’article [types de documents multiples, vues et fenêtres Frame](../../mfc/multiple-document-types-views-and-frame-windows.md), [note technique 29](../../mfc/tn029-splitter-windows.md)et vue d’ensemble de la classe `CSplitterWnd`.

##  <a name="createview"></a>CSplitterWnd :: CreateView

Crée les volets d’une fenêtre fractionnée statique.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Paramètres

*row*<br/>
Spécifie la ligne de la fenêtre fractionnée dans laquelle placer la nouvelle vue.

*col*<br/>
Spécifie la colonne de la fenêtre fractionnée dans laquelle placer la nouvelle vue.

*pViewClass*<br/>
Spécifie la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) du nouvel affichage.

*sizeInit*<br/>
Spécifie la taille initiale de la nouvelle vue.

*pContext*<br/>
Pointeur vers un contexte de création utilisé pour créer la vue (généralement le *pContext* passé dans la fonction membre [CFrameWnd :: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) substituée par le frame parent dans lequel la fenêtre fractionnée est créée).

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Tous les volets d’une fenêtre fractionnée statique doivent être créés avant que le Framework n’affiche le séparateur.

L’infrastructure appelle également cette fonction membre pour créer des volets lorsque l’utilisateur d’une fenêtre fractionnée dynamique fractionne un volet, une ligne ou une colonne.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>CSplitterWnd :: CSplitterWnd

Appelez pour construire un objet `CSplitterWnd`.

```
CSplitterWnd();
```

### <a name="remarks"></a>Notes

Construisez un objet `CSplitterWnd` en deux étapes. Tout d’abord, appelez le constructeur, qui crée l’objet `CSplitterWnd`, puis appelez la fonction membre [Create](#create) , qui crée la fenêtre fractionnée et l’attache à l’objet `CSplitterWnd`.

##  <a name="deletecolumn"></a>CSplitterWnd ::D eleteColumn

Supprime une colonne de la fenêtre fractionnée.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Paramètres

*colDelete*<br/>
Spécifie la colonne à supprimer.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de fractionnement a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fractionnements dynamiques plus avancés.

##  <a name="deleterow"></a>CSplitterWnd ::D eleteRow

Supprime une ligne de la fenêtre de fractionnement.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Paramètres

*rowDelete*<br/>
Spécifie la ligne à supprimer.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de fractionnement a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fractionnements dynamiques plus avancés.

##  <a name="deleteview"></a>CSplitterWnd ::D eleteView

Supprime une vue de la fenêtre fractionnée.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Paramètres

*row*<br/>
Spécifie la ligne de la fenêtre fractionnée à laquelle la vue doit être supprimée.

*col*<br/>
Spécifie la colonne de la fenêtre fractionnée au niveau de laquelle la vue doit être supprimée.

### <a name="remarks"></a>Notes

Si la vue active est en cours de suppression, la vue suivante devient active. L’implémentation par défaut suppose que la vue est automatiquement supprimée dans [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

Cette fonction membre est appelée par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de fractionnement a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fractionnements dynamiques plus avancés.

##  <a name="dokeyboardsplit"></a>CSplitterWnd ::D oKeyboardSplit

Exécute la commande de fractionnement du clavier, généralement « fractionnement de fenêtre ».

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est une commande de haut niveau qui est utilisée par la classe [CView](../../mfc/reference/cview-class.md) pour déléguer à l’implémentation de `CSplitterWnd`.

##  <a name="doscroll"></a>CSplitterWnd ::D oScroll

Effectue le défilement synchronisé des fenêtres fractionnées.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*pViewFrom*<br/>
Pointeur vers la vue d’origine du message de défilement.

*nScrollCode*<br/>
Code-barres de défilement qui indique la requête de défilement de l’utilisateur. Ce paramètre est composé de deux parties : un octet de poids faible, qui détermine le type de défilement horizontalement et un octet de poids fort, qui détermine le type de défilement qui se produit verticalement :

- SB_BOTTOM fait défiler vers le bas.

- SB_LINEDOWN fait défiler d’une ligne vers le dessous.

- SB_LINEUP fait défiler d’une ligne vers le haut.

- SB_PAGEDOWN fait défiler une page vers le dessous.

- SB_PAGEUP fait défiler d’une page vers le haut.

- SB_TOP fait défiler vers le haut.

*bDoScroll*<br/>
Détermine si l’action de défilement spécifiée se produit. Si *bDoScroll* a la valeur true (autrement dit, s’il existe une fenêtre enfant et si les fenêtres fractionnées comportent une plage de défilement), l’action de défilement spécifiée peut avoir lieu ; Si *bDoScroll* a la valeur false (autrement dit, s’il n’existe aucune fenêtre enfant ou si les vues fractionnées n’ont pas de plage de défilement), le défilement ne se produit pas.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le défilement synchronisé se produit ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure pour effectuer le défilement synchronisé des fenêtres fractionnées lorsque la vue reçoit un message de défilement. Substituez pour exiger une action de l’utilisateur avant le défilement synchronisé.

##  <a name="doscrollby"></a>CSplitterWnd ::D oScrollBy

Fait défiler les fenêtres fractionnées d’un nombre donné de pixels.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*pViewFrom*<br/>
Pointeur vers la vue d’origine du message de défilement.

*sizeScroll*<br/>
Nombre de pixels à faire défiler horizontalement et verticalement.

*bDoScroll*<br/>
Détermine si l’action de défilement spécifiée se produit. Si *bDoScroll* a la valeur true (autrement dit, s’il existe une fenêtre enfant et si les fenêtres fractionnées comportent une plage de défilement), l’action de défilement spécifiée peut avoir lieu ; Si *bDoScroll* a la valeur false (autrement dit, s’il n’existe aucune fenêtre enfant ou si les vues fractionnées n’ont pas de plage de défilement), le défilement ne se produit pas.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le défilement synchronisé se produit ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure en réponse à un message de défilement, pour effectuer le défilement synchronisé des fenêtres fractionnées en fonction de la quantité, en pixels, indiquée par *sizeScroll*. Les valeurs positives indiquent le défilement vers le dessous et vers la droite ; les valeurs négatives indiquent le défilement vers le haut et vers la gauche.

Substituez pour exiger une action de l’utilisateur avant d’autoriser le défilement.

##  <a name="getactivepane"></a>CSplitterWnd :: GetActivePane

Détermine le volet actif à partir du focus ou de l’affichage actif dans le frame.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Paramètres

*pRow*<br/>
Pointeur vers un **entier** pour récupérer le numéro de ligne du volet actif.

*pCol*<br/>
Pointeur vers un **entier** pour récupérer le numéro de colonne du volet actif.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le volet actif. NULL si aucun volet actif n’existe.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure pour déterminer le volet actif dans une fenêtre fractionnée. Remplacez pour demander à l’utilisateur d’effectuer une action avant d’obtenir le volet actif.

##  <a name="getcolumncount"></a>CSplitterWnd :: GetColumnCount

Retourne le nombre de colonnes du volet actuel.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre actuel de colonnes dans le séparateur. Pour un séparateur statique, il s’agit également du nombre maximal de colonnes.

##  <a name="getcolumninfo"></a>CSplitterWnd :: GetColumnInfo

Retourne des informations sur la colonne spécifiée.

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Paramètres

*col*<br/>
Spécifie une colonne.

*cxCur*<br/>
Référence à un **entier** à définir sur la largeur actuelle de la colonne.

*cxMin*<br/>
Référence à un **entier** à affecter à la largeur minimale actuelle de la colonne.

##  <a name="getpane"></a>CSplitterWnd :: GetPane

Retourne le volet au niveau de la ligne et de la colonne spécifiées.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Paramètres

*row*<br/>
Spécifie une ligne.

*col*<br/>
Spécifie une colonne.

### <a name="return-value"></a>Valeur de retour

Retourne le volet au niveau de la ligne et de la colonne spécifiées. Le volet retourné est généralement une classe dérivée de [CView](../../mfc/reference/cview-class.md).

##  <a name="getrowcount"></a>CSplitterWnd :: GetRowCount

Retourne le nombre de lignes du volet actuel.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre actuel de lignes dans la fenêtre de fractionnement. Pour une fenêtre fractionnée statique, il s’agit également du nombre maximal de lignes.

##  <a name="getrowinfo"></a>CSplitterWnd :: GetRowInfo

Retourne des informations sur la ligne spécifiée.

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Paramètres

*row*<br/>
Spécifie une ligne.

*cyCur*<br/>
Référence à **int** à définir à la hauteur actuelle de la ligne, en pixels.

*cyMin*<br/>
Référence à **int** à définir à la hauteur minimale actuelle de la ligne, en pixels.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour obtenir des informations sur la ligne spécifiée. Le paramètre *cyCur* est rempli avec la hauteur actuelle de la ligne spécifiée et *cyMin* est rempli avec la hauteur minimale de la ligne.

##  <a name="getscrollstyle"></a>CSplitterWnd :: GetScrollStyle

Retourne le style de barre de défilement partagé pour la fenêtre fractionnée.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Valeur de retour

Un ou plusieurs des indicateurs de style Windows suivants, en cas de réussite :

- WS_HSCROLL si le séparateur gère actuellement des barres de défilement horizontales partagées.

- WS_VSCROLL si le séparateur gère actuellement des barres de défilement verticales partagées.

Si la valeur est zéro, la fenêtre fractionnée ne gère pas actuellement les barres de défilement partagées.

##  <a name="idfromrowcol"></a>CSplitterWnd :: IdFromRowCol

Obtient l’ID de fenêtre enfant pour le volet au niveau de la ligne et de la colonne spécifiées.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Paramètres

*row*<br/>
Spécifie la ligne de la fenêtre fractionnée.

*col*<br/>
Spécifie la colonne de la fenêtre fractionnée.

### <a name="return-value"></a>Valeur de retour

ID de fenêtre enfant pour le volet.

### <a name="remarks"></a>Notes

Cette fonction membre est utilisée pour créer des vues non-vues comme des volets et peut être appelée avant l’existence du volet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>CSplitterWnd :: IsChildPane

Détermine si *pwnd* est actuellement un volet enfant de cette fenêtre fractionnée.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
Pointeur vers un objet [CWnd](../../mfc/reference/cwnd-class.md) à tester.

*pRow*<br/>
Pointeur vers un **entier** dans lequel stocker le numéro de ligne.

*pCol*<br/>
Pointeur vers un **entier** dans lequel stocker un numéro de colonne.

### <a name="return-value"></a>Valeur de retour

Si la valeur est différente de zéro, *pwnd* est actuellement un volet enfant de cette fenêtre fractionnée, et *Prow* et *pCol* sont renseignés avec la position du volet dans la fenêtre fractionnée. Si *pwnd* n’est pas un volet enfant de cette fenêtre fractionnée, la valeur 0 est retournée.

### <a name="remarks"></a>Notes

Dans les C++ versions de Visual antérieures à 6,0, cette fonction était définie comme

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Cette version est désormais obsolète et ne doit pas être utilisée.

##  <a name="istracking"></a>CSplitterWnd :: IsTracking

Appelez cette fonction membre pour déterminer si la barre de fractionnement dans la fenêtre est en cours de déplacement.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si une opération de fractionnement est en cours ; Sinon, 0.

##  <a name="ondrawsplitter"></a>CSplitterWnd :: OnDrawSplitter

Génère le rendu d’une image d’une fenêtre fractionnée.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers le contexte de périphérique dans lequel dessiner. Si le *contrôleur de domaine principal* a la valeur null, [CWnd :: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) est appelé par l’infrastructure et aucune fenêtre fractionnée n’est dessinée.

*nType*<br/>
Valeur de la `enum ESplitType`, qui peut être l’une des suivantes :

- `splitBox` la zone de glissement du séparateur.

- `splitBar` la barre qui apparaît entre les deux fenêtres fractionnées.

- `splitIntersection` l’intersection des fenêtres fractionnées. Cet élément n’est pas appelé lors de l’exécution sur Windows 95/98.

- `splitBorder` les bordures de la fenêtre fractionnée.

*rectangulaire*<br/>
Référence à un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) spécifiant la taille et la forme des fenêtres fractionnées.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure pour dessiner et spécifier les caractéristiques exactes d’une fenêtre fractionnée. Substituez `OnDrawSplitter` pour une personnalisation avancée de l’image des différents composants graphiques d’une fenêtre fractionnée. L’image par défaut est similaire au séparateur dans Microsoft Works pour Windows ou Microsoft Windows 95/98, dans le cas où les intersections des barres de fractionnement sont fusionnées ensemble.

Pour plus d’informations sur les fenêtres fractionnées dynamiques, consultez « fenêtres fractionnées » dans l’article [types de documents multiples, vues et fenêtres Frame](../../mfc/multiple-document-types-views-and-frame-windows.md), [note technique 29](../../mfc/tn029-splitter-windows.md)et vue d’ensemble de la classe `CSplitterWnd`.

##  <a name="oninverttracker"></a>CSplitterWnd :: OnInvertTracker

Restitue l’image d’une fenêtre fractionnée avec une taille et une forme identiques à celles de la fenêtre frame.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Paramètres

*rectangulaire*<br/>
Référence à un objet `CRect` spécifiant le rectangle de suivi.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure pendant le redimensionnement des séparateurs. Substituez `OnInvertTracker` pour une personnalisation avancée de l’image de la fenêtre fractionnée. L’image par défaut est similaire au séparateur dans Microsoft Works pour Windows ou Microsoft Windows 95/98, dans le cas où les intersections des barres de fractionnement sont fusionnées ensemble.

Pour plus d’informations sur les fenêtres fractionnées dynamiques, consultez « fenêtres fractionnées » dans l’article [types de documents multiples, vues et fenêtres Frame](../../mfc/multiple-document-types-views-and-frame-windows.md), [note technique 29](../../mfc/tn029-splitter-windows.md)et vue d’ensemble de la classe `CSplitterWnd`.

##  <a name="recalclayout"></a>CSplitterWnd :: RecalcLayout

Appelez pour réafficher la fenêtre de fractionnement après avoir ajusté la taille de ligne ou de colonne.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour réafficher correctement la fenêtre de fractionnement après avoir ajusté les tailles de ligne et de colonne avec les fonctions membres [SetRowInfo](#setrowinfo) et [SetColumnInfo](#setcolumninfo) . Si vous modifiez la taille des lignes et des colonnes dans le cadre du processus de création avant que la fenêtre fractionnée ne soit visible, il n’est pas nécessaire d’appeler cette fonction membre.

L’infrastructure appelle cette fonction membre chaque fois que l’utilisateur redimensionne la fenêtre fractionnée ou déplace une division.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CSplitterWnd :: SetColumnInfo](#setcolumninfo).

##  <a name="setactivepane"></a>CSplitterWnd :: SetActivePane

Définit un volet comme actif dans le cadre.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*row*<br/>
Si *pwnd* a la valeur null, spécifie la ligne dans le volet qui sera actif.

*col*<br/>
Si *pwnd* a la valeur null, spécifie la colonne qui sera active dans le volet.

*pWnd*<br/>
Pointeur vers un objet `CWnd`. Si la valeur est NULL, le volet spécifié par *Row* et *col* est défini comme actif. Si la valeur n’est pas NULL, spécifie le volet actif.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par l’infrastructure pour définir un volet comme actif lorsque l’utilisateur change le focus en un volet dans la fenêtre frame. Vous pouvez appeler explicitement `SetActivePane` pour modifier le focus sur la vue spécifiée.

Spécifiez Pane en fournissant une ligne et une colonne, **ou** en fournissant *pwnd*.

##  <a name="setcolumninfo"></a>CSplitterWnd :: SetColumnInfo

Appelez pour définir les informations de colonne spécifiées.

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Paramètres

*col*<br/>
Spécifie une colonne de fenêtre fractionnée.

*cxIdeal*<br/>
Spécifie une largeur idéale pour la colonne de la fenêtre fractionnée en pixels.

*cxMin*<br/>
Spécifie la largeur minimale, en pixels, de la colonne de la fenêtre fractionnée.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour définir une nouvelle largeur minimale et une largeur idéale pour une colonne. La valeur minimale de la colonne détermine le moment où la colonne sera trop petite pour être entièrement affichée.

Lorsque l’infrastructure affiche la fenêtre de fractionnement, elle dispose les volets dans les colonnes et les lignes en fonction de leurs dimensions idéales, en travaillant à partir de l’angle supérieur gauche vers le coin inférieur droit de la zone cliente de la fenêtre fractionnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>CSplitterWnd :: SetRowInfo

Appelez pour définir les informations de ligne spécifiées.

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Paramètres

*row*<br/>
Spécifie une ligne de fenêtre fractionnée.

*cyIdeal*<br/>
Spécifie une hauteur idéale pour la ligne de la fenêtre fractionnée en pixels.

*cyMin*<br/>
Spécifie la hauteur minimale de la ligne de la fenêtre fractionnée en pixels.

### <a name="remarks"></a>Notes

Appelez cette fonction membre pour définir une nouvelle hauteur minimale et une hauteur idéale pour une ligne. La valeur minimale de la ligne détermine le moment où la ligne est trop petite pour être entièrement affichée.

Lorsque l’infrastructure affiche la fenêtre de fractionnement, elle dispose les volets dans les colonnes et les lignes en fonction de leurs dimensions idéales, en travaillant à partir de l’angle supérieur gauche vers le coin inférieur droit de la zone cliente de la fenêtre fractionnée.

##  <a name="setscrollstyle"></a>CSplitterWnd :: SetScrollStyle

Spécifie le nouveau style de défilement pour la prise en charge de la barre de défilement partagée de la fenêtre fractionnée.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Nouveau style de défilement pour la prise en charge de la barre de défilement partagée de la fenêtre fractionnée, qui peut prendre l’une des valeurs suivantes :

- WS_HSCROLL créer/afficher des barres de défilement horizontales partagées.

- WS_VSCROLL créer/afficher des barres de défilement partagées verticales.

### <a name="remarks"></a>Notes

Une fois qu’une barre de défilement est créée, elle ne sera pas détruite même si `SetScrollStyle` est appelé sans ce style. au lieu de cela, ces barres de défilement sont masquées. Cela permet aux barres de défilement de conserver leur état même si elles sont masquées. Après l’appel de `SetScrollStyle` il est nécessaire d’appeler [RecalcLayout](#recalclayout) pour que toutes les modifications soient prises en compte.

##  <a name="splitcolumn"></a>CSplitterWnd :: SplitColumn

Indique l’emplacement de fractionnement vertical d’une fenêtre frame.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Paramètres

*cxBefore*<br/>
Position, en pixels, avant laquelle le fractionnement se produit.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée lorsqu’une fenêtre fractionnée verticale est créée. `SplitColumn` indique l’emplacement par défaut où le fractionnement se produit.

`SplitColumn` est appelé par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de fractionnement a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fractionnements dynamiques plus avancés.

##  <a name="splitrow"></a>CSplitterWnd :: SplitRow

Indique l’emplacement de fractionnement horizontal d’une fenêtre frame.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Paramètres

*cyBefore*<br/>
Position, en pixels, avant laquelle le fractionnement se produit.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée lors de la création d’une fenêtre fractionnée horizontale. `SplitRow` indique l’emplacement par défaut où le fractionnement se produit.

`SplitRow` est appelé par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de fractionnement a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fractionnements dynamiques plus avancés.

##  <a name="ondraw"></a>CSplitterWnd :: OnDraw

Appelé par l’infrastructure pour dessiner la fenêtre fractionnée.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers un contexte de périphérique.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Exemple MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CView, classe](../../mfc/reference/cview-class.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)
