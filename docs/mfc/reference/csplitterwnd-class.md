---
title: CSplitterWnd, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f01452a2a8f8b4a50b9aa7723eb4ded24b3f3cc9
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027922"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd, classe
Fournit les fonctionnalités d'une fenêtre fractionnée, qui est une fenêtre contenant plusieurs volets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSplitterWnd : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Appel à construire un `CSplitterWnd` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|Exécute la commande volet suivant ou volet précédent.|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Vérifie si la commande volet suivant ou volet précédent est actuellement possible.|  
|[CSplitterWnd::Create statiques](#create)|Appel pour créer une fenêtre fractionnée dynamique et l’attacher à la `CSplitterWnd` objet.|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Crée un contrôle de barre de défilement partagé.|  
|[CSplitterWnd::CreateStatic](#createstatic)|Appel pour créer une fenêtre fractionnée statique et l’attacher à la `CSplitterWnd` objet.|  
|[CSplitterWnd::CreateView](#createview)|Appel pour créer un volet dans une fenêtre fractionnée.|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Supprime une colonne de la fenêtre de séparateur.|  
|[CSplitterWnd::DeleteRow](#deleterow)|Supprime une ligne à partir de la fenêtre de séparateur.|  
|[CSplitterWnd::DeleteView](#deleteview)|Supprime une vue de la fenêtre de séparateur.|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Effectue le clavier fractionner la commande, généralement « fractionnement de la fenêtre ».|  
|[CSplitterWnd::DoScroll](#doscroll)|Exécute un défilement synchronisé des fenêtres fractionnées.|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|Fait défiler les fenêtres fractionnées selon un nombre donné de pixels.|  
|[CSplitterWnd::GetActivePane](#getactivepane)|Détermine le volet actif à partir du focus ou de la vue active dans le frame.|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Retourne le nombre actuel de colonnes de volet.|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Retourne des informations sur la colonne spécifiée.|  
|[CSplitterWnd::GetPane](#getpane)|Retourne le volet à la ligne spécifiée et la colonne.|  
|[CSplitterWnd::GetRowCount](#getrowcount)|Retourne le nombre de lignes de volet en cours.|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Retourne des informations sur la ligne spécifiée.|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Retourne le style de barre de défilement partagé.|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Retourne les enfants du volet à la ligne spécifiée et la colonne ID de la fenêtre.|  
|[CSplitterWnd::IsChildPane](#ischildpane)|L’appel pour déterminer si la fenêtre est actuellement un volet enfant de cette fenêtre de séparateur.|  
|[CSplitterWnd::IsTracking](#istracking)|Détermine si la barre de fractionnement est en cours de déplacement.|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|L’appel pour réafficher la fenêtre de séparateur après modification de la taille de ligne ou une colonne.|  
|[CSplitterWnd::SetActivePane](#setactivepane)|Définit un volet être celle active dans le frame.|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|L’appel pour définir les informations de la colonne spécifiée.|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|L’appel pour définir les informations de la ligne spécifiée.|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Spécifie que le nouveau style de barre de défilement pour la fenêtre de séparateur partagé prise en charge de la barre de défilement.|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|Indique où une fenêtre frame divise verticalement.|  
|[CSplitterWnd::SplitRow](#splitrow)|Indique où du fractionnement horizontal d’une fenêtre frame.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner la fenêtre de séparateur.|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Restitue une image d’une fenêtre fractionnée.|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Affiche l’image d’une fenêtre fractionnée à la même taille et la même forme que la fenêtre frame.|  
  
## <a name="remarks"></a>Notes  
Un volet est généralement un objet spécifique à l’application dérivée de [CView](../../mfc/reference/cview-class.md), mais il peut s’agir [CWnd](../../mfc/reference/cwnd-class.md) objet ayant l’ID de fenêtre enfant approprié.  
  
 Un `CSplitterWnd` objet est généralement incorporé dans un parent [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objet. Créer un `CSplitterWnd` de l’objet en procédant comme suit :  
  
 1. Incorporer un `CSplitterWnd` variable de membre dans le frame parent.  
  
 2.  Remplacer le frame parent [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) fonction membre.  
  
 3.  À partir de dans substituées `OnCreateClient`, appelez le [créer](#create) ou [CreateStatic](#createstatic) fonction membre de `CSplitterWnd`.  
  
Appelez le `Create` fonction membre pour créer une fenêtre fractionnée dynamique. Une fenêtre fractionnée dynamique est généralement utilisée pour créer et faire défiler un nombre de volets individuels ou des vues, du même document. L’infrastructure crée automatiquement un volet initial pour le séparateur ; le framework crée, redimensionne et supprime des volets supplémentaires comme l’utilisateur opère des contrôles de la fenêtre de séparateur.  
  
Lorsque vous appelez `Create`, vous spécifiez une largeur de colonnes et la hauteur minimale des lignes qui déterminent quand les volets sont trop petits pour être complètement affichée. Après avoir appelé `Create`, vous pouvez ajuster ces valeurs minimales en appelant le [SetColumnInfo](#setcolumninfo) et [SetRowInfo](#setrowinfo) fonctions membres.  
  
Utilisez également le `SetColumnInfo` et `SetRowInfo` des fonctions membres pour définir une largeur « idéale » pour une colonne et la hauteur de « idéale » pour une ligne. Lorsque l’infrastructure affiche une fenêtre fractionnée, elle affiche d’abord le frame parent, puis la fenêtre de séparateur. Le framework présente ensuite les volets disponibles dans les colonnes et lignes en fonction de leurs dimensions idéale, chargé à partir de l’angle supérieur gauche de l’angle inférieur droit de la zone cliente de la fenêtre de séparateur.  
  
Tous les volets dans une fenêtre fractionnée dynamique doivent être de la même classe. Les applications courantes qui prennent en charge les fenêtres fractionnées dynamiques incluent Microsoft Word et Microsoft Excel.  
  
Utilisez le `CreateStatic` fonction membre pour créer une fenêtre fractionnée statique. L’utilisateur peut modifier uniquement la taille des volets dans un séparateur statique fenêtre, pas leur nombre ou la commande.  
  
Vous devez spécifiquement créer tous les statiques de volets de fractionnement lorsque vous créez la fractionnées statiques. Veillez à créer tous les volets avant le frame parent `OnCreateClient` retours de fonction membre, ou la volonté de framework ne pas afficher correctement la fenêtre.  
  
Le `CreateStatic` fonction membre initialise automatiquement un séparateur statique avec une largeur de colonnes et la hauteur minimale des lignes de 0. Après avoir appelé `Create`, ajuster ces valeurs minimales en appelant le [SetColumnInfo](#setcolumninfo) et [SetRowInfo](#setrowinfo) fonctions membres. Utilisez également `SetColumnInfo` et `SetRowInfo` après avoir appelé `CreateStatic` pour indiquer souhaité dimensions du volet idéale.  
  
Souvent, les volets individuels d’un séparateur statique appartiennent à différentes classes. Pour obtenir des exemples de fenêtres fractionnées statiques, consultez l’éditeur graphique et le Gestionnaire de fichiers Windows.  
  
Une fenêtre fractionnée prend en charge les barres de défilement spécial (mis à part les barres de défilement qui devront peut-être des volets). Ces barres de défilement sont des enfants de le `CSplitterWnd` de l’objet et sont partagés avec les volets.  
  
Vous créez ces barres de défilement spéciaux lors de la création de la fenêtre de séparateur. Par exemple, un `CSplitterWnd` qui a une ligne, deux colonnes et le style WS_VSCROLL affiche une barre de défilement verticale qui est partagée par les deux volets. Lorsque l’utilisateur déplace la barre de défilement, WM_VSCROLL sont envoyés dans les deux volets. Lorsque les volets définir la position de la barre de défilement, la barre de défilement partagé est définie.  
  
Pour plus d’informations sur les fenêtres fractionnées, consultez :  
  
 - [Note technique 29](../../mfc/tn029-splitter-windows.md)  
  
 - Article de la Base de connaissances Q262024 : HOWTO : CPropertySheet utilisation comme un enfant de CSplitterWnd  
  
Pour plus d’informations sur la création de fenêtres fractionnées dynamiques, consultez :  
  
 - Exemple MFC [Scribble](../../visual-cpp-samples.md)  
  
 - Exemple MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxext.h  
  
##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext  
 Appelé par l’infrastructure pour exécuter la commande volet suivant ou volet précédent.  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bPrev*  
 Indique la fenêtre à activer. **TRUE** pour le précédent. **FALSE** suivant.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est une commande de haut niveau qui est utilisée par le [CView](../../mfc/reference/cview-class.md) classe déléguer à la `CSplitterWnd` implémentation.  
  
##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext  
 Appelé par l’infrastructure pour vérifier si la commande volet suivant ou volet précédent est actuellement possible.  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bPrev*  
 Indique la fenêtre à activer. **TRUE** pour le précédent. **FALSE** suivant.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est une commande de haut niveau qui est utilisée par le [CView](../../mfc/reference/cview-class.md) classe déléguer à la `CSplitterWnd` implémentation.  
  
##  <a name="create"></a>  CSplitterWnd::Create statiques  
 Pour créer une fenêtre fractionnée dynamique, appelez le `Create` fonction membre.  
  
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
 *pParentWnd*  
 La fenêtre frame parente de la fenêtre de séparateur.  
  
 *nMaxRows*  
 Le nombre maximal de lignes dans la fenêtre de séparateur. Cette valeur ne doit pas dépasser 2.  
  
 *nMaxCols*  
 Le nombre maximal de colonnes dans la fenêtre de séparateur. Cette valeur ne doit pas dépasser 2.  
  
 *sizeMin*  
 Spécifie la taille minimale à laquelle un volet peut être affiché.  
  
 *pContext*  
 Un pointeur vers un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) structure. Dans la plupart des cas, il peut s’agir du *pContext* passé à la fenêtre frame parente.  
  
 *dwStyle*  
 Spécifie le style de fenêtre.  
  
 *nID*  
 L’ID de fenêtre enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST, sauf si la fenêtre de séparateur est imbriquée dans une autre fenêtre de séparateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez incorporer un `CSplitterWnd` dans un parent [CFrameWnd](../../mfc/reference/cframewnd-class.md) ou [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objet en effectuant les étapes suivantes :  
  
1.  Incorporer un `CSplitterWnd` variable de membre dans le frame parent.  
  
2.  Remplacer le frame parent [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) fonction membre.  
  
3.  Appelez le `Create` fonction membre dans substituées `OnCreateClient`.  
  
 Lorsque vous créez une fenêtre fractionnée à partir d’au sein d’un frame parent, transmettez le frame parent *pContext* paramètre à la fenêtre de séparateur. Sinon, ce paramètre peut être NULL.  
  
 La largeur de colonnes et la hauteur minimale de ligne initiale d’une fenêtre fractionnée dynamique sont définies par le *sizeMin* paramètre. Ces valeurs minimales, qui déterminent si un volet est trop petit pour être affichée dans son intégralité, peuvent être modifiés avec le [SetRowInfo](#setrowinfo) et [SetColumnInfo](#setcolumninfo) fonctions membres.  
  
 Pour plus d’informations sur les fenêtres fractionnées dynamiques, voir « Fractionnement Windows » dans l’article [plusieurs Types de documents, vues et Frame Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technical Note 29](../../mfc/tn029-splitter-windows.md)et le `CSplitterWnd` vue d’ensemble de la classe.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]  
  
##  <a name="createscrollbarctrl"></a>  CSplitterWnd::CreateScrollBarCtrl  
 Appelé par le framework pour créer un contrôle de barre de défilement partagé.  
  
```  
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwStyle*  
 Spécifie le style de fenêtre.  
  
 *nID*  
 L’ID de fenêtre enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST, sauf si la fenêtre de séparateur est imbriquée dans une autre fenêtre de séparateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Substituer `CreateScrollBarCtrl` pour inclure les contrôles supplémentaires en regard d’une barre de défilement. Le comportement par défaut consiste à créer des contrôles de barre de défilement Windows normales.  
  
##  <a name="createstatic"></a>  CSplitterWnd::CreateStatic  
 Pour créer une fenêtre fractionnée statique, appelez le `CreateStatic` fonction membre.  
  
```  
virtual BOOL CreateStatic(
    CWnd* pParentWnd,  
    int nRows,  
    int nCols,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParentWnd*  
 La fenêtre frame parente de la fenêtre de séparateur.  
  
 *nRows*  
 Nombre de lignes. Cette valeur ne doit pas dépasser 16.  
  
 *nCols*  
 Nombre de colonnes. Cette valeur ne doit pas dépasser 16.  
  
 *dwStyle*  
 Spécifie le style de fenêtre.  
  
 *nID*  
 L’ID de fenêtre enfant de la fenêtre. L’ID peut être AFX_IDW_PANE_FIRST, sauf si la fenêtre de séparateur est imbriquée dans une autre fenêtre de séparateur.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Un `CSplitterWnd` est généralement incorporé dans un parent `CFrameWnd` ou [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objet en effectuant les étapes suivantes :  
  
1.  Incorporer un `CSplitterWnd` variable de membre dans le frame parent.  
  
2.  Remplacer le frame parent `OnCreateClient` fonction membre.  
  
3.  Appelez le `CreateStatic` fonction membre dans substituées [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).  
  
 Une fenêtre fractionnée statique contient un nombre fixe de volets, souvent à partir de différentes classes.  
  
 Lorsque vous créez une fenêtre fractionnée statique, vous devez créer en même temps tous ses volets. Le [CreateView](#createview) fonction membre est généralement utilisée à cet effet, mais vous pouvez créer d’autres classes nonview également.  
  
 La largeur de colonnes et la hauteur minimale de ligne initiale pour une fenêtre fractionnée statique est 0. Ces valeurs minimales, qui déterminent quand un volet est trop petit pour être affichée dans son intégralité, peuvent être modifiés avec le [SetRowInfo](#setrowinfo) et [SetColumnInfo](#setcolumninfo) fonctions membres.  
  
 Pour ajouter des barres de défilement pour une fenêtre fractionnée statique, ajoutez les styles WS_HSCROLL et WS_VSCROLL à *dwStyle*.  
  
 Voir « Fractionnement Windows » dans l’article [plusieurs Types de documents, vues et Frame Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technical Note 29](../../mfc/tn029-splitter-windows.md)et le `CSplitterWnd` vue d’ensemble de la classe pour plus d’informations sur les fenêtres fractionnées statiques.  
  
##  <a name="createview"></a>  CSplitterWnd::CreateView  
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
 *ligne*  
 Spécifie la ligne de la fenêtre fractionnée dans lequel placer la nouvelle vue.  
  
 *col*  
 Spécifie la colonne de la fenêtre fractionnée dans lequel placer la nouvelle vue.  
  
 *pViewClass*  
 Spécifie le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la nouvelle vue.  
  
 *sizeInit*  
 Spécifie la taille initiale de la nouvelle vue.  
  
 *pContext*  
 Un pointeur vers un contexte de création utilisé pour créer la vue (généralement le *pContext* passé dans le frame parent substituée [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) fonction membre dans lequel la fenêtre de séparateur en cours de création).  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Tous les volets d’une fenêtre fractionnée statique doivent être créés avant que le framework affiche le séparateur.  
  
 Le framework appelle également cette fonction membre pour créer de nouveaux volets lorsque l’utilisateur d’une fenêtre fractionnée dynamique fractionne un volet, la ligne ou la colonne.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd  
 Appel à construire un `CSplitterWnd` objet.  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>Notes  
 Construire un `CSplitterWnd` objet en deux étapes. Tout d’abord, appelez le constructeur, ce qui crée le `CSplitterWnd` de l’objet, puis appelez le [créer](#create) fonction membre, ce qui crée la fenêtre de séparateur et l’attache à la `CSplitterWnd` objet.  
  
##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn  
 Supprime une colonne de la fenêtre de séparateur.  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>Paramètres  
 *colDelete*  
 Spécifie la colonne à supprimer.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de séparateur a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fenêtres fractionnées dynamiques plus avancées.  
  
##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow  
 Supprime une ligne à partir de la fenêtre de séparateur.  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>Paramètres  
 *ligneSupprimer*  
 Spécifie la ligne à supprimer.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de séparateur a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fenêtres fractionnées dynamiques plus avancées.  
  
##  <a name="deleteview"></a>  CSplitterWnd::DeleteView  
 Supprime une vue de la fenêtre de séparateur.  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>Paramètres  
 *ligne*  
 Spécifie la ligne de la fenêtre fractionnée à partir duquel supprimer la vue.  
  
 *col*  
 Spécifie la colonne de la fenêtre fractionnée à partir duquel supprimer la vue.  
  
### <a name="remarks"></a>Notes  
 Si la vue active est en cours de suppression, la vue suivante devient active. L’implémentation par défaut suppose que la vue est automatiquement supprimer dans [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).  
  
 Cette fonction membre est appelée par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de séparateur a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fenêtres fractionnées dynamiques plus avancées.  
  
##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit  
 Effectue le clavier fractionner la commande, généralement « fractionnement de la fenêtre ».  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est une commande de haut niveau qui est utilisée par le [CView](../../mfc/reference/cview-class.md) classe déléguer à la `CSplitterWnd` implémentation.  
  
##  <a name="doscroll"></a>  CSplitterWnd::DoScroll  
 Exécute un défilement synchronisé des fenêtres fractionnées.  
  
```  
virtual BOOL DoScroll(
    CView* pViewFrom,  
    UINT nScrollCode,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *pViewFrom*  
 Un pointeur vers la vue d'où provient le message de défilement.  
  
 *nScrollCode*  
 Un code de la barre de défilement qui indique que l’utilisateur du défilement de demande. Ce paramètre est composé de deux parties : un octet de poids faible, qui détermine le type de défilement se produisant horizontalement, et un octet de poids fort, qui détermine le type de défilement se produisant verticalement :  
  
    - Fait défiler les SB_BOTTOM vers le bas.  
      
    - Fait défiler SB_LINEDOWN une ligne vers le bas.  
      
    - Fait défiler SB_LINEUP jusqu'à la ligne.  
      
    - SB_PAGEDOWN défiler une page vers le bas.  
      
    - Fait défiler SB_PAGEUP une page haut.  
      
    - Fait défiler les SB_TOP vers le haut.  
  
 *bDoScroll*  
 Détermine si l’action de défilement spécifiée se produit. Si *bDoScroll* est TRUE (autrement dit, si une fenêtre enfant existe et si les fenêtres fractionnées dispose d’une plage de défilement), l’action de défilement spécifiée peut avoir lieu ; si *bDoScroll* est FALSE (autrement dit, si aucune fenêtre enfant Il existe, ou les affichages fractionnés n’ont aucune plage de défilement), puis le défilement ne se produit pas.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le défilement synchronisé se produit ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure pour effectuer un défilement synchronisé des fenêtres fractionnées lorsque la vue reçoit un message de défilement. Méthode override pour nécessitent une action de l’utilisateur avant le défilement synchronisé est autorisé.  
  
##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy  
 Fait défiler les fenêtres fractionnées selon un nombre donné de pixels.  
  
```  
virtual BOOL DoScrollBy(
    CView* pViewFrom,  
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *pViewFrom*  
 Un pointeur vers la vue d'où provient le message de défilement.  
  
 *sizeScroll*  
 Nombre de pixels utilisés pour faire défiler horizontalement et verticalement.  
  
 *bDoScroll*  
 Détermine si l’action de défilement spécifiée se produit. Si *bDoScroll* est TRUE (autrement dit, si une fenêtre enfant existe et si les fenêtres fractionnées dispose d’une plage de défilement), l’action de défilement spécifiée peut avoir lieu ; si *bDoScroll* est FALSE (autrement dit, si aucune fenêtre enfant Il existe, ou les affichages fractionnés n’ont aucune plage de défilement), puis le défilement ne se produit pas.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le défilement synchronisé se produit ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure en réponse à un message de défilement, pour effectuer synchronisé le défilement des fenêtres de fractionnement par la quantité, en pixels, indiqué par *sizeScroll*. Les valeurs positives indiquent le défilement vers le bas et vers la droite. les valeurs négatives indiquent le défilement de haut et vers la gauche.  
  
 Méthode override pour nécessitent une action de l’utilisateur avant d’autoriser le défilement.  
  
##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane  
 Détermine le volet actif à partir du focus ou de la vue active dans le frame.  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pRow*  
 Un pointeur vers un **int** pour récupérer le numéro de ligne du volet actif.  
  
 *pCol*  
 Un pointeur vers un **int** pour récupérer le numéro de colonne du volet actif.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le volet actif. NULL si aucun volet actif n’existe.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure pour déterminer le volet actif dans une fenêtre fractionnée. Méthode override pour nécessitent une action de l’utilisateur avant d’obtenir le volet actif.  
  
##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount  
 Retourne le nombre actuel de colonnes de volet.  
  
```  
int GetColumnCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre actuel de colonnes dans l’outil de fractionnement. Pour un séparateur statique, ce sera également le nombre maximal de colonnes.  
  
##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo  
 Retourne des informations sur la colonne spécifiée.  
  
```  
void GetColumnInfo(
    int col,  
    int& cxCur,  
    int& cxMin) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *col*  
 Spécifie une colonne.  
  
 *cxCur*  
 Une référence à un **int** à définir à la largeur actuelle de la colonne.  
  
 *cxMin*  
 Une référence à un **int** à définir à la largeur minimale actuelle de la colonne.  
  
##  <a name="getpane"></a>  CSplitterWnd::GetPane  
 Retourne le volet à la ligne spécifiée et la colonne.  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *ligne*  
 Spécifie une ligne.  
  
 *col*  
 Spécifie une colonne.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le volet à la ligne spécifiée et la colonne. Le volet retourné est généralement un [CView](../../mfc/reference/cview-class.md)-classe dérivée.  
  
##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount  
 Retourne le nombre de lignes de volet en cours.  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre actuel de lignes dans la fenêtre de séparateur. Pour une fenêtre fractionnée statique, ce sera également le nombre maximal de lignes.  
  
##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo  
 Retourne des informations sur la ligne spécifiée.  
  
```  
void GetRowInfo(
    int row,  
    int& cyCur,  
    int& cyMin) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *ligne*  
 Spécifie une ligne.  
  
 *cyCur*  
 Référence à **int** à définir à la hauteur actuelle de la ligne en pixels.  
  
 *cyMin*  
 Référence à **int** à définir à la hauteur minimale en cours de la ligne en pixels.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour obtenir des informations sur la ligne spécifiée. Le *cyCur* paramètre est renseigné avec la hauteur actuelle de la ligne spécifiée, et *cyMin* est rempli avec la hauteur minimale de la ligne.  
  
##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle  
 Retourne le style de barre de défilement partagé pour la fenêtre de séparateur.  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un ou plusieurs des fenêtres suivantes de style indicateurs, en cas de réussite :  
  
    - WS_HSCROLL si que le séparateur gère actuellement partagé des barres de défilement horizontale.  
      
    - WS_VSCROLL si que le séparateur gère actuellement partagé des barres de défilement verticale.  
  
 Si zéro, la fenêtre de séparateur ne gère pas actuellement toutes les barres de défilement partagé.  
  
##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol  
 Obtient l’enfant pour le volet à la ligne spécifiée et la colonne ID de la fenêtre.  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *ligne*  
 Spécifie la ligne de la fenêtre fractionnée.  
  
 *col*  
 Spécifie la colonne de la fenêtre fractionnée.  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID de fenêtre enfant pour le volet.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est utilisée pour la création de nonviews sous forme de volets et peut être appelée avant que le volet existe.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane  
 Détermine si *pWnd* est actuellement un volet enfant de cette fenêtre de séparateur.  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet à tester.  
  
 *pRow*  
 Un pointeur vers un **int** dans lequel stocker le numéro de ligne.  
  
 *pCol*  
 Un pointeur vers un **int** dans lequel stocker un numéro de colonne.  
  
### <a name="return-value"></a>Valeur de retour  
 Si elle est différente de zéro, *pWnd* est actuellement un volet enfant de cette fenêtre fractionnée, et *pRow* et *pCol* sont renseignés avec la position du volet dans la fenêtre de séparateur. Si *pWnd* n’est pas un volet enfant de cette fenêtre fractionnée, 0 est retourné.  
  
### <a name="remarks"></a>Notes  
 Dans les versions de Visual C++ antérieures à 6.0, cette fonction a été définie en tant que  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 Cette version est désormais obsolète et ne doit pas être utilisée.  
  
##  <a name="istracking"></a>  CSplitterWnd::IsTracking  
 Appelez cette fonction membre pour déterminer si la barre de fractionnement dans la fenêtre est en cours de déplacement.  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si une opération de fractionnement est en cours ; sinon 0.  
  
##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter  
 Restitue une image d’une fenêtre fractionnée.  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Paramètres  
 *contrôleur de domaine principal*  
 Pointeur vers le contexte de périphérique dans lequel dessiner. Si *pDC* est NULL, puis [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) est appelée par le framework et aucun fractionnement fenêtre est dessinée.  
  
 *%nLes*  
 Une valeur de la `enum ESplitType`, ce qui peut prendre l’une des opérations suivantes :  
  
    - `splitBox` La zone de glisser du séparateur.  
      
    - `splitBar` La barre qui apparaît entre les fenêtres de fractionnement de deux.  
      
    - `splitIntersection` L’intersection des fenêtres de fractionnement. Cet élément ne sera pas appelé lors de l’exécution sur Windows 95/98.  
      
    - `splitBorder` Les bordures de fenêtre fractionné.  
  
 *Rect*  
 Une référence à un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet spécifiant la taille et la forme des fenêtres de fractionnement.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure pour dessiner et spécifier les caractéristiques exacts d’une fenêtre fractionnée. Substituer `OnDrawSplitter` pour la personnalisation avancée de l’imagerie pour les différents composants de graphiques d’une fenêtre fractionnée. L’imagerie par défaut est similaire au séparateur dans Microsoft Works pour Windows ou Microsoft Windows 95/98, car les intersections des barres de fractionnement sont fusionnées en.  
  
 Pour plus d’informations sur les fenêtres fractionnées dynamiques, voir « Fractionnement Windows » dans l’article [plusieurs Types de documents, vues et Frame Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technical Note 29](../../mfc/tn029-splitter-windows.md)et le `CSplitterWnd` vue d’ensemble de la classe.  
  
##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker  
 Affiche l’image d’une fenêtre fractionnée à la même taille et la même forme que la fenêtre frame.  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>Paramètres  
 *Rect*  
 Référence à un `CRect` objet qui spécifie le rectangle de suivi.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure lors du redimensionnement des fenêtres fractionnées. Substituer `OnInvertTracker` pour la personnalisation avancée de l’imagerie de la fenêtre de séparateur. L’imagerie par défaut est similaire au séparateur dans Microsoft Works pour Windows ou Microsoft Windows 95/98, car les intersections des barres de fractionnement sont fusionnées en.  
  
 Pour plus d’informations sur les fenêtres fractionnées dynamiques, voir « Fractionnement Windows » dans l’article [plusieurs Types de documents, vues et Frame Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [Technical Note 29](../../mfc/tn029-splitter-windows.md)et le `CSplitterWnd` vue d’ensemble de la classe.  
  
##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout  
 L’appel pour réafficher la fenêtre de séparateur après modification de la taille de ligne ou une colonne.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour réafficher correctement la fenêtre de séparateur après avoir ajusté les tailles de ligne et de colonne avec le [SetRowInfo](#setrowinfo) et [SetColumnInfo](#setcolumninfo) fonctions membres. Si vous modifiez les tailles de lignes et de colonnes dans le cadre du processus de création avant la fenêtre de séparateur est visible, il n’est pas nécessaire d’appeler cette fonction membre.  
  
 L’infrastructure appelle cette fonction membre chaque fois que l’utilisateur redimensionne la fenêtre de séparateur ou déplace un fractionnement.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CSplitterWnd::SetColumnInfo](#setcolumninfo).  
  
##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane  
 Définit un volet être celle active dans le frame.  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *ligne*  
 Si *pWnd* est NULL, spécifie la ligne dans le volet qui est actif.  
  
 *col*  
 Si *pWnd* est NULL, spécifie la colonne dans le volet qui est actif.  
  
 *pWnd*  
 Un pointeur vers un `CWnd` objet. Si NULL, le volet spécifié par *ligne* et *col* a la valeur active. Si non NULL, spécifie le volet a la valeur actif.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par l’infrastructure pour définir un volet active lorsque l’utilisateur déplace la sélection vers un volet dans la fenêtre frame. Vous pouvez appeler explicitement `SetActivePane` pour déplacer le focus vers la vue spécifiée.  
  
 Spécifiez le volet en fournissant la ligne et colonne, **ou** en fournissant *pWnd*.  
  
##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo  
 L’appel pour définir les informations de la colonne spécifiée.  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>Paramètres  
 *col*  
 Spécifie une colonne de la fenêtre fractionnée.  
  
 *cxIdeal*  
 Spécifie une largeur idéale pour la colonne de la fenêtre du séparateur en pixels.  
  
 *cxMin*  
 Spécifie une largeur minimale de la colonne de la fenêtre du séparateur en pixels.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour définir une nouvelle largeur minimale et la largeur idéale pour une colonne. La valeur minimale de colonne détermine quand la colonne sera trop petite pour être complètement affichée.  
  
 Lorsque l’infrastructure affiche la fenêtre fractionnée, elle dispose les volets disponibles dans les colonnes et lignes en fonction de leurs dimensions idéale, chargé à partir de l’angle supérieur gauche de l’angle inférieur droit de la zone cliente de la fenêtre de séparateur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo  
 L’appel pour définir les informations de la ligne spécifiée.  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>Paramètres  
 *ligne*  
 Spécifie une ligne de la fenêtre fractionnée.  
  
 *cyIdeal*  
 Spécifie une hauteur idéale de la ligne de la fenêtre du séparateur en pixels.  
  
 *cyMin*  
 Spécifie une hauteur minimale de la ligne de la fenêtre du séparateur en pixels.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour définir une nouvelle hauteur minimale et la hauteur idéale pour une ligne. La valeur minimale de ligne détermine quand la ligne seront trop petite pour être complètement affichée.  
  
 Lorsque l’infrastructure affiche la fenêtre fractionnée, elle dispose les volets disponibles dans les colonnes et lignes en fonction de leurs dimensions idéale, chargé à partir de l’angle supérieur gauche de l’angle inférieur droit de la zone cliente de la fenêtre de séparateur.  
  
##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle  
 Spécifie que le nouveau style de défilement pour la fenêtre de séparateur partagé prise en charge de la barre de défilement.  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwStyle*  
 Le nouveau style de défilement pour la fenêtre de séparateur partagé prise en charge de barre de défilement, qui peut prendre l’une des valeurs suivantes :  
  
- Barres de défilement partagé horizontale WS_HSCROLL créer/afficher.  
  
- Barres de défilement partagé verticale WS_VSCROLL créer/afficher.  
  
### <a name="remarks"></a>Notes  
 Une fois une barre de défilement est créée qu’il ne sera pas détruit même si `SetScrollStyle` est appelée sans ce style ; à la place ces barres de défilement sont masquées. Ainsi, les barres de défilement à conserver leur état, même si elles sont masquées. Après avoir appelé `SetScrollStyle` il est nécessaire d’appeler [RecalcLayout](#recalclayout) pour toutes les modifications entrent en vigueur.  
  
##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn  
 Indique où une fenêtre frame divise verticalement.  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>Paramètres  
 *cxBefore*  
 La position, en pixels, avant laquelle la division se produit.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée lorsqu’une fenêtre de séparateur vertical est créée. `SplitColumn` Indique l’emplacement par défaut où la division se produit.  
  
 `SplitColumn` est appelée par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de séparateur a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fenêtres fractionnées dynamiques plus avancées.  
  
##  <a name="splitrow"></a>  CSplitterWnd::SplitRow  
 Indique où du fractionnement horizontal d’une fenêtre frame.  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>Paramètres  
 *cyBefore*  
 La position, en pixels, avant laquelle la division se produit.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée lorsqu’une fenêtre de séparateur horizontal est créée. `SplitRow` Indique l’emplacement par défaut où la division se produit.  
  
 `SplitRow` est appelée par l’infrastructure pour implémenter la logique de la fenêtre fractionnée dynamique (autrement dit, si la fenêtre de séparateur a le style SPLS_DYNAMIC_SPLIT). Il peut être personnalisé, ainsi que la fonction virtuelle [CreateView](#createview), pour implémenter des fenêtres fractionnées dynamiques plus avancées.  
  
##  <a name="ondraw"></a>  CSplitterWnd::OnDraw  
 Appelé par l’infrastructure pour dessiner la fenêtre de séparateur.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC VIEWEX](../../visual-cpp-samples.md)   
 [CWnd, classe](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CView (classe)](../../mfc/reference/cview-class.md)   
 [CWnd, classe](../../mfc/reference/cwnd-class.md)
