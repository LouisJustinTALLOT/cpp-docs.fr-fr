---
title: Classe de CMFCRibbonCategory | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddHidden
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CopyFrom
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindPanelWithElem
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetContextID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetDroppedDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElementsByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFirstVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFocused
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetHighlighted
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageSize
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetItemIDsList
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLastVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLargeImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetMaxHeight
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelFromPoint
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelIndex
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentButton
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentMenuBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentRibbonBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetSmallImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabColor
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTextTopLine
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetVisibleElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HighlightPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTest
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestEx
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestScrollButtons
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsActive
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsVisible
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsWindows7Look
- AFXRIBBONCATEGORY/CMFCRibbonCategory::NotifyControlCommand
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnCancelMode
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDraw
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawImage
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawMenuBorder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnKey
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonUp
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnMouseMove
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnRTLChanged
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnScrollHorz
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnUpdateCmdUI
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RecalcLayout
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RemovePanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::ReposPanels
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetCollapseOrder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetKeys
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetTabColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCategory class
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
caps.latest.revision: 38
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dccbaac6450985f0d5255a790d83f374b52f06f9
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncategory-class"></a>Classe de CMFCRibbonCategory
Le `CMFCRibbonCategory` classe implémente un onglet du ruban qui contient un groupe de [ruban panneaux](../../mfc/reference/cmfcribbonpanel-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonCategory : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="protected-constructors"></a>Constructeurs protégés  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonCategory::CMFCRibbonCategory](#cmfcribboncategory)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonCategory::AddHidden](#addhidden)|Ajoute un élément masqué à la catégorie de ruban.|  
|[CMFCRibbonCategory::AddPanel](#addpanel)|Ajoute un nouveau volet à la catégorie de ruban.|  
|[CMFCRibbonCategory::CopyFrom](#copyfrom)||  
|[CMFCRibbonCategory::FindByData](#findbydata)||  
|[CMFCRibbonCategory::FindByID](#findbyid)||  
|[CMFCRibbonCategory::FindPanelWithElem](#findpanelwithelem)||  
|[CMFCRibbonCategory::GetContextID](#getcontextid)|Retourne l’ID de contexte de la catégorie de ruban.|  
|[CMFCRibbonCategory::GetData](#getdata)|Retourne les données définies par l’utilisateur qui sont associées à la catégorie de ruban.|  
|[CMFCRibbonCategory::GetDroppedDown](#getdroppeddown)||  
|[CMFCRibbonCategory::GetElements](#getelements)||  
|[CMFCRibbonCategory::GetElementsByID](#getelementsbyid)||  
|[CMFCRibbonCategory::GetFirstVisibleElement](#getfirstvisibleelement)|Obtenir le premier élément visible qui appartiennent à la catégorie de ruban.|  
|[CMFCRibbonCategory::GetFocused](#getfocused)|Retourne un élément qui a le focus.|  
|[CMFCRibbonCategory::GetHighlighted](#gethighlighted)|Retourne un élément en surbrillance.|  
|[CMFCRibbonCategory::GetImageCount](#getimagecount)||  
|[CMFCRibbonCategory::GetImageSize](#getimagesize)||  
|[CMFCRibbonCategory::GetItemIDsList](#getitemidslist)||  
|[CMFCRibbonCategory::GetLastVisibleElement](#getlastvisibleelement)|Obtenir un dernier élément visible qui appartiennent à la catégorie de ruban|  
|[CMFCRibbonCategory::GetLargeImages](#getlargeimages)|Retourne une référence à la liste des images de grande taille qui utilise la catégorie de ruban.|  
|[CMFCRibbonCategory::GetMaxHeight](#getmaxheight)||  
|[CMFCRibbonCategory::GetName](#getname)||  
|[CMFCRibbonCategory::GetPanel](#getpanel)|Retourne un pointeur vers le volet du ruban qui se trouve à l’index spécifié.|  
|[CMFCRibbonCategory::GetPanelCount](#getpanelcount)|Retourne le nombre de volets de ruban dans la catégorie de ruban.|  
|[CMFCRibbonCategory::GetPanelFromPoint](#getpanelfrompoint)||  
|[CMFCRibbonCategory::GetPanelIndex](#getpanelindex)|Retourne l’index du panneau spécifié du ruban.|  
|[CMFCRibbonCategory::GetParentButton](#getparentbutton)||  
|[CMFCRibbonCategory::GetParentMenuBar](#getparentmenubar)||  
|[CMFCRibbonCategory::GetParentRibbonBar](#getparentribbonbar)||  
|[CMFCRibbonCategory::GetRect](#getrect)||  
|[CMFCRibbonCategory::GetSmallImages](#getsmallimages)|Retourne une référence à la liste des petites images qui utilise la catégorie.|  
|[CMFCRibbonCategory::GetTabColor](#gettabcolor)|Retourne la couleur actuelle de l’onglet de catégorie de ruban.|  
|[CMFCRibbonCategory::GetTabRect](#gettabrect)||  
|[CMFCRibbonCategory::GetTextTopLine](#gettexttopline)||  
|[CMFCRibbonCategory::GetVisibleElements](#getvisibleelements)|Obtenir tous les éléments visibles qui appartiennent à la catégorie de ruban.|  
|[CMFCRibbonCategory::HighlightPanel](#highlightpanel)||  
|[CMFCRibbonCategory::HitTest](#hittest)||  
|[CMFCRibbonCategory::HitTestEx](#hittestex)||  
|[CMFCRibbonCategory::HitTestScrollButtons](#hittestscrollbuttons)||  
|[CMFCRibbonCategory::IsActive](#isactive)||  
|[CMFCRibbonCategory::IsVisible](#isvisible)|Détermine si la catégorie de ruban est visible.|  
|[CMFCRibbonCategory::IsWindows7Look](#iswindows7look)|Indique si le ruban parent a Windows 7 similaire (bouton petite application rectangulaire)|  
|[CMFCRibbonCategory::NotifyControlCommand](#notifycontrolcommand)||  
|[CMFCRibbonCategory::OnCancelMode](#oncancelmode)||  
|[CMFCRibbonCategory::OnDraw](#ondraw)||  
|[CMFCRibbonCategory::OnDrawImage](#ondrawimage)||  
|[CMFCRibbonCategory::OnDrawMenuBorder](#ondrawmenuborder)||  
|[CMFCRibbonCategory::OnKey](#onkey)|Appelé par l’infrastructure lorsque l’utilisateur appuie sur un bouton de clavier.|  
|[CMFCRibbonCategory::OnLButtonDown](#onlbuttondown)||  
|[CMFCRibbonCategory::OnLButtonUp](#onlbuttonup)||  
|[CMFCRibbonCategory::OnMouseMove](#onmousemove)||  
|[CMFCRibbonCategory::OnRTLChanged](#onrtlchanged)||  
|[CMFCRibbonCategory::OnScrollHorz](#onscrollhorz)||  
|[CMFCRibbonCategory::OnUpdateCmdUI](#onupdatecmdui)||  
|[CMFCRibbonCategory::RecalcLayout](#recalclayout)||  
|[CMFCRibbonCategory::RemovePanel](#removepanel)||  
|[CMFCRibbonCategory::ReposPanels](#repospanels)||  
|[CMFCRibbonCategory::SetCollapseOrder](#setcollapseorder)|Définit l’ordre de réduction des volets de ruban qui sont présents dans la catégorie de ruban.|  
|[CMFCRibbonCategory::SetData](#setdata)|Stocke les données définies par l’utilisateur dans la catégorie de ruban.|  
|[CMFCRibbonCategory::SetKeys](#setkeys)|Assigne une touche d’accès à la catégorie de ruban.|  
|[CMFCRibbonCategory::SetName](#setname)||  
|[CMFCRibbonCategory::SetTabColor](#settabcolor)|Définit la couleur de la catégorie de ruban.|  
  
## <a name="remarks"></a>Remarques  
 En général, vous créez une catégorie de ruban indirectement en appelant [CMFCRibbonBar::AddCategory](../../mfc/reference/cmfcribbonbar-class.md#addcategory), qui retourne un pointeur à la catégorie de ruban qui vient d’être créé. Ajouter des panneaux à la catégorie en appelant [CMFCRibbonCategory::AddPanel](#addpanel).  
  
 La `CMFCRibbonTab` classe dessine des catégories du ruban. Elle est dérivée de [CMFCRibbonBaseElement classe](../../mfc/reference/cmfcribbonbaseelement-class.md).  
  
 L’exemple suivant montre comment créer une catégorie de ruban et ajouter un panneau de configuration.  
  
 `// Create a new ribbon category and get a pointer to it`  
  
 `CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory`  
  
 `(_T("&Write"),           // Category name`  
  
 `IDB_WRITE,              // Category small images (16 x 16)`  
  
 `IDB_WRITE_LARGE);   // Category large images (32 x 32)`  
  
 `// Add a panel to the new category`  
  
 `CMFCRibbonPanel* pPanel = pCategory->AddPanel (`  
  
 `_T("Clipboard"),                       // Panel name`  
  
 `m_PanelIcons.ExtractIcon (0));  // Panel icon`  
  
 Le diagramme suivant illustre une figure de la catégorie d’accueil de l’exemple d’application RibbonApp.  
  
 ![Image CMFCRibbonCategory](../../mfc/reference/media/cmfcribboncategory.png "cmfcribboncategory")  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCRibbonCategory`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxribboncategory.h  
  
##  <a name="addhidden"></a>CMFCRibbonCategory::AddHidden  
 Ajoute l’élément de ruban spécifié dans le tableau d’éléments de ruban qui sont affichés dans la boîte de dialogue Personnalisation.  
  
```  
void AddHidden(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pElem`  
 Pointeur vers un élément de ruban.  
  
### <a name="remarks"></a>Remarques  
 Les éléments de ruban dans la boîte de dialogue de personnalisation sont les commandes que vous pouvez ajouter à la barre d’outils Accès rapide.  
  
##  <a name="addpanel"></a>CMFCRibbonCategory::AddPanel  
 Crée un panneau de ruban pour la catégorie de ruban.  
  
```  
CMFCRibbonPanel* AddPanel(
    LPCTSTR lpszPanelName,  
    HICON hIcon = 0,  
    CRuntimeClass* pRTI = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszPanelName`  
 Pointeur vers le nom du nouveau panneau de ruban.  
  
 [in] `hIcon`  
 Handle de l’icône par défaut pour le nouveau panneau de ruban.  
  
 [in] `pRTI`  
 Pointeur vers les informations de classe d’exécution pour un panneau de ruban personnalisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le nouveau panneau de ruban si la méthode a réussi ; dans le cas contraire `NULL` si le panneau de configuration n’a pas été créé.  
  
### <a name="remarks"></a>Remarques  
 Si vous souhaitez créer un panneau de ruban personnalisé, vous devez spécifier ses informations de classe d’exécution dans `pRTI`. La classe de panneau de ruban personnalisé doit être dérivée du `CMFCRibbonPanel` classe.  
  
 L’icône par défaut pour le volet du ruban s’affiche lorsque l’espace est insuffisant pour afficher les éléments de ruban.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `AddPanel` méthode dans la `CMFCRibbonCategory` classe.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#10;](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_1.cpp)]  
  
##  <a name="cmfcribboncategory"></a>CMFCRibbonCategory::CMFCRibbonCategory  
 Construit et initialise un [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) objet.  
  
```  
CMFCRibbonCategory(
    CMFCRibbonBar* pParenrRibbonBar,  
    LPCTSTR lpszName,  
    UINT uiSmallImagesResID,  
    UINT uiLargeImagesResID,  
    CSize sizeSmallImage = CSize(16,
    16),  
    CSize sizeLargeImage = CSize(32,
    32));
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pParenrRibbonBar`  
 Pointeur vers la barre de ruban parent de la catégorie de ruban.  
  
 [in] `lpszName`  
 Nom de la catégorie de ruban.  
  
 [in] `uiSmallImagesResID`  
 ID de ressource de la liste d’images pour les petites images qui sont utilisées par les éléments de ruban dans la catégorie de ruban.  
  
 [in] `uiLargeImagesResID`  
 ID de ressource de la liste d’images pour les grandes images qui sont utilisées par les éléments de ruban dans la catégorie de ruban.  
  
 [in] `sizeSmallImage`  
 Taille de petites images pour les éléments de ruban dans la catégorie de ruban par défaut.  
  
 [in] `sizeLargeImage`  
 Taille des images de grande taille pour les éléments de ruban dans la catégorie de ruban par défaut.  
  
##  <a name="copyfrom"></a>CMFCRibbonCategory::CopyFrom  
 Copie de l’état de l’objet [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) actuel [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) objet.  
  
```  
virtual void CopyFrom(CMFCRibbonCategory& src);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `src`  
 Objet `CMFCRibbonCategory` source.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="findbydata"></a>CMFCRibbonCategory::FindByData  
 Récupère l’élément de ruban associé avec les données spécifiées.  
  
```  
CMFCRibbonBaseElement* FindByData(
    DWORD_PTR dwData,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwData`  
 Les données associées à un élément de ruban.  
  
 [in] `bVisibleOnly`  
 `TRUE`Pour inclure les éléments de ruban d’accès rapide dans la recherche ; `FALSE` pour exclure les éléments de ruban d’accès rapide dans la recherche.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un élément de ruban si la méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="findbyid"></a>CMFCRibbonCategory::FindByID  
 Récupère l’élément de ruban associé à l’ID de commande spécifié.  
  
```  
CMFCRibbonBaseElement* FindByID(
    UINT uiCmdID,  
    BOOL bVisibleOnly = TRUE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmdID`  
 ID de commande associé à un élément de ruban.  
  
 [in] `bVisibleOnly`  
 `TRUE`Pour inclure les éléments de ruban d’accès rapide dans la recherche ; `FALSE` pour exclure les éléments de ruban d’accès rapide dans la recherche.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un élément de ruban si la méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="findpanelwithelem"></a>CMFCRibbonCategory::FindPanelWithElem  
 Récupère le volet du ruban qui contient l’élément spécifié du ruban.  
  
```  
CMFCRibbonPanel* FindPanelWithElem(const CMFCRibbonBaseElement* pElement);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pElement`  
 Pointeur vers un élément de ruban.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un panneau de ruban si la méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getcontextid"></a>CMFCRibbonCategory::GetContextID  
 Récupère l’ID de contexte de la catégorie de ruban.  
  
```  
UINT GetContextID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 ID de contexte de la catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
 L’ID de contexte est 0 si la catégorie de ruban n’est pas une catégorie de ruban de contexte.  
  
##  <a name="getdata"></a>CMFCRibbonCategory::GetData  
 Récupère les données définies par l’utilisateur qui sont associées à la catégorie de ruban.  
  
```  
DWORD_PTR GetData() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Les données définies par l’utilisateur qui sont associées à la catégorie de ruban.  
  
##  <a name="getdroppeddown"></a>CMFCRibbonCategory::GetDroppedDown  
 Récupère un pointeur vers l’élément de ruban qui a son menu contextuel qui s’affiche.  
  
```  
CMFCRibbonBaseElement* GetDroppedDown();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un élément de ruban si la méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getelements"></a>CMFCRibbonCategory::GetElements  
 Récupère tous les éléments de ruban dans la catégorie de ruban.  
  
```  
void GetElements(
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Paramètres  
 [in, out] `arElements`  
 Référence à un [CArray](../../mfc/reference/carray-class.md) d’éléments de ruban.  
  
### <a name="remarks"></a>Remarques  
 Les éléments de ruban qui sont conçus pour fonctionner sur la barre d’outils Accès rapide sont inclus dans le tableau.  
  
##  <a name="getelementsbyid"></a>CMFCRibbonCategory::GetElementsByID  
 Récupère tous les éléments de ruban qui sont associés à l’ID de commande spécifié.  
  
```  
void GetElementsByID(
    UINT uiCmdID,  
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmdID`  
 ID de commande associé à un élément de ruban.  
  
 [in, out] `arElements`  
 Référence à un [CArray](../../mfc/reference/carray-class.md) d’éléments de ruban.  
  
### <a name="remarks"></a>Remarques  
 Les éléments de ruban qui sont conçus pour fonctionner sur la barre d’outils Accès rapide sont inclus dans le tableau.  
  
##  <a name="getfirstvisibleelement"></a>CMFCRibbonCategory::GetFirstVisibleElement  
 Récupère le premier élément visible qui appartient à la catégorie de ruban.  
  
```  
CMFCRibbonBaseElement* GetFirstVisibleElement() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le premier élément visible ; peut être `NULL` si la catégorie n’a pas d’éléments visibles.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getfocused"></a>CMFCRibbonCategory::GetFocused  
 Retourne un élément qui a le focus.  
  
```  
CMFCRibbonBaseElement* GetFocused();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un élément ayant le focus ou `NULL`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="gethighlighted"></a>CMFCRibbonCategory::GetHighlighted  
 Retourne un élément en surbrillance.  
  
```  
CMFCRibbonBaseElement* GetHighlighted();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un élément en surbrillance ou `NULL` si aucun élément n’est mises en surbrillance.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getimagecount"></a>CMFCRibbonCategory::GetImageCount  
 Récupère le nombre d’images dans la liste de l’image spécifiée qui est contenue dans la catégorie de ruban.  
  
```  
int GetImageCount(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bIsLargeImage`  
 `TRUE`pour le nombre d’images dans la liste d’images de grande taille ; `FALSE` pour le nombre d’images dans la liste d’images miniatures.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’images dans la liste d’images spécifiés.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getimagesize"></a>CMFCRibbonCategory::GetImageSize  
 Récupère la taille d’une image dans la liste de l’image spécifiée qui est contenue dans la catégorie de ruban.  
  
```  
CSize GetImageSize(BOOL bIsLargeImage) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bIsLargeImage`  
 `TRUE`pour la taille des images de grande taille ; `FALSE` pour la taille des petites images.  
  
### <a name="return-value"></a>Valeur de retour  
 La taille d’une image dans la liste d’images spécifiés.  
  
### <a name="remarks"></a>Notes  
 La taille récupérée inclut le facteur d’échelle image globale.  
  
##  <a name="getitemidslist"></a>CMFCRibbonCategory::GetItemIDsList  
 Récupère l’ID de commande pour les éléments de ruban qui sont contenus dans la catégorie de ruban.  
  
```  
void GetItemIDsList(
    CList<UINT, UINT>& lstItems,  
    BOOL bHiddenOnly = FALSE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `lstItems`  
 La liste des ID de commandes pour les éléments de ruban dans la catégorie de ruban.  
  
 [in] `bHiddenOnly`  
 `TRUE`Pour exclure les éléments de ruban affichées sur les panneaux de ruban dans la catégorie de ruban ; `FALSE` pour inclure tous les éléments de ruban dans la catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getlargeimages"></a>CMFCRibbonCategory::GetLargeImages  
 Récupère la liste des images de grande taille qui figurent dans la catégorie de ruban.  
  
```  
CMFCToolBarImages& GetLargeImages();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La liste des images de grande taille qui figurent dans la catégorie de ruban.  
  
##  <a name="getlastvisibleelement"></a>CMFCRibbonCategory::GetLastVisibleElement  
 Récupère le dernier élément visible qui appartient à la catégorie de ruban.  
  
```  
CMFCRibbonBaseElement* GetLastVisibleElement() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le dernier élément visible ; peut être `NULL` si la catégorie n’a pas d’éléments visibles.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getmaxheight"></a>CMFCRibbonCategory::GetMaxHeight  
 Récupère la hauteur maximale de volets de ruban qui sont contenus dans la catégorie de ruban.  
  
```  
int GetMaxHeight(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour les volets de ruban.  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur maximale de volets de ruban qui sont contenus dans la catégorie de ruban.  
  
### <a name="remarks"></a>Notes  
 La valeur extraite inclut la hauteur des marges supérieure et inférieure pour les volets de ruban.  
  
##  <a name="getname"></a>CMFCRibbonCategory::GetName  
 Récupère le nom de la catégorie de ruban.  
  
```  
LPCTSTR GetName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom de la catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getpanel"></a>CMFCRibbonCategory::GetPanel  
 Retourne un pointeur vers le volet du ruban qui se trouve à l’index spécifié.  
  
```  
CMFCRibbonPanel* GetPanel(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nIndex`  
 Index de base zéro d’un panneau de ruban.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le volet du ruban qui se trouve à l’index spécifié.  
  
### <a name="remarks"></a>Remarques  
 Une exception est levée si `nIndex` est hors limites.  
  
##  <a name="getpanelcount"></a>CMFCRibbonCategory::GetPanelCount  
 Retourne le nombre de volets de ruban dans la catégorie de ruban.  
  
```  
int GetPanelCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de volets de ruban dans la catégorie de ruban.  
  
##  <a name="getpanelfrompoint"></a>CMFCRibbonCategory::GetPanelFromPoint  
 Récupère un pointeur vers un panneau de ruban si le point spécifié se trouve dans celui-ci.  
  
```  
CMFCRibbonPanel* GetPanelFromPoint(CPoint point) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Les coordonnées x et y du pointeur, par rapport à l’angle supérieur gauche de la fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un panneau de ruban si la méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Remarques  
 Uniquement les volets de ruban qui sont contenus dans la catégorie de ruban sont testés.  
  
##  <a name="getpanelindex"></a>CMFCRibbonCategory::GetPanelIndex  
 Récupère l’index de base zéro du Panneau de ruban spécifié.  
  
```  
int GetPanelIndex(const CMFCRibbonPanel* pPanel) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pPanel`  
 Pointeur vers un panneau de ruban.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro du Panneau de ruban spécifié si la méthode a réussi ; sinon -1.  
  
### <a name="remarks"></a>Remarques  
 Uniquement les volets de ruban qui sont contenus dans la catégorie de ruban sont recherchés.  
  
##  <a name="getparentbutton"></a>CMFCRibbonCategory::GetParentButton  
 Récupère l’élément parent du ruban de la catégorie de ruban.  
  
```  
CMFCRibbonBaseElement* GetParentButton() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers l’élément de ruban parent, ou `NULL` s’il n’existe aucun élément parent.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getparentmenubar"></a>CMFCRibbonCategory::GetParentMenuBar  
 Retourne un pointeur vers la barre de menu parent de le `CMFCRibbonCategory` objet.  
  
```  
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le contenu de la `m_pParentMenuBar` protégé de membre.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getparentribbonbar"></a>CMFCRibbonCategory::GetParentRibbonBar  
 Récupère le ruban parent pour la catégorie de ruban.  
  
```  
CMFCRibbonBar* GetParentRibbonBar() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la barre de ruban parent pour la catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getrect"></a>CMFCRibbonCategory::GetRect  
 Récupère le rectangle d’affichage de la catégorie de ruban.  
  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le rectangle d’affichage de la catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
 Le rectangle d’affichage de la catégorie de ruban n’inclut pas l’onglet catégorie.  
  
##  <a name="getsmallimages"></a>CMFCRibbonCategory::GetSmallImages  
 Récupère la liste des petites images qui figurent dans la catégorie de ruban.  
  
```  
CMFCToolBarImages& GetSmallImages();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La liste des petites images qui figurent dans la catégorie de ruban.  
  
##  <a name="gettabcolor"></a>CMFCRibbonCategory::GetTabColor  
 Retourne la couleur actuelle de l’onglet de catégorie de ruban.  
  
```  
AFX_RibbonCategoryColor GetTabColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur actuelle de l’onglet de catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
 La valeur retournée peut être une des valeurs énumérées suivantes :  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
##  <a name="gettabrect"></a>CMFCRibbonCategory::GetTabRect  
 Récupère le rectangle d’affichage de l’onglet de catégorie de ruban.  
  
```  
CRect GetTabRect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le rectangle d’affichage de l’onglet de catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="gettexttopline"></a>CMFCRibbonCategory::GetTextTopLine  
 Récupère l’emplacement vertical du texte sur les boutons de ruban dans la catégorie de ruban qui affichent des images de grande taille.  
  
```  
int GetTextTopLine() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Emplacement vertical du texte, en pixels, des boutons de ruban qui affichent des images de grande taille.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getvisibleelements"></a>CMFCRibbonCategory::GetVisibleElements  
 Récupère tous les éléments visibles qui appartiennent à la catégorie de ruban.  
  
```  
void GetVisibleElements(
    CArray <CMFCRibbonBaseElement*,  
    CMFCRibbonBaseElement*>& arElements);
```  
  
### <a name="parameters"></a>Paramètres  
 `arElements`  
 Tableau de tous les éléments visibles.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="highlightpanel"></a>CMFCRibbonCategory::HighlightPanel  
 Met en évidence le volet du ruban spécifié.  
  
```  
CMFCRibbonPanel* HighlightPanel(
    CMFCRibbonPanel* pHLPanel,  
    CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pHLPanel`  
 Pointeur vers le volet du ruban pour mettre en surbrillance.  
  
 [in] `point`  
 Les coordonnées x et y du pointeur, par rapport à l’angle supérieur gauche de la fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le volet du ruban précédemment mis en surbrillance ; dans le cas contraire `NULL` si aucun panneau de ruban n’est mis en surbrillance lorsque cette méthode est appelée.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations sur la mise en surbrillance un panneau de ruban, consultez [CMFCRibbonPanel::Highlight](../../mfc/reference/cmfcribbonpanel-class.md#highlight).  
  
##  <a name="hittest"></a>CMFCRibbonCategory::HitTest  
 Récupère un pointeur vers un élément de ruban si le point spécifié se trouve dans celui-ci.  
  
```  
CMFCRibbonBaseElement* HitTest(
    CPoint point,  
    BOOL bCheckPanelCaption = FALSE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Les coordonnées x et y du pointeur de la souris, par rapport à l’angle supérieur gauche de la fenêtre.  
  
 [in] `bCheckPanelCaption`  
 `TRUE`Pour tester la légende du Panneau de ruban ; `FALSE` à exclure de la légende du Panneau de ruban.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un élément de ruban si la méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Notes  
 Uniquement les éléments de ruban qui sont contenus dans la catégorie de ruban sont testés.  
  
##  <a name="hittestex"></a>CMFCRibbonCategory::HitTestEx  
 Récupère l’index de base zéro d’un élément de ruban si le point spécifié se trouve dans celui-ci.  
  
```  
int HitTestEx(CPoint point) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Les coordonnées x et y du pointeur de la souris, par rapport à l’angle supérieur gauche de la fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro d’un élément de ruban si la méthode a réussi ; sinon -1.  
  
### <a name="remarks"></a>Remarques  
 Uniquement les éléments de ruban qui sont contenus dans la catégorie de ruban sont testés.  
  
##  <a name="hittestscrollbuttons"></a>CMFCRibbonCategory::HitTestScrollButtons  
 Si un point se situe dans un bouton de défilement gauche ou droit d’une catégorie de ruban, retourne un pointeur vers ce bouton.  
  
```  
CMFCRibbonBaseElement* HitTestScrollButtons(CPoint point) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Point à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 Si `point` se trouve dans le rectangle englobant de la gauche ou le bouton de défilement vers la droite de la catégorie de ruban, retourne un pointeur vers ce bouton ou dans le cas contraire, retourne `NULL`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="isactive"></a>CMFCRibbonCategory::IsActive  
 Indique si la catégorie de ruban est la catégorie active dans la barre de ruban.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la catégorie de ruban est la catégorie active ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 La catégorie de ruban active affiche ses volets de ruban.  
  
##  <a name="isvisible"></a>CMFCRibbonCategory::IsVisible  
 Indique si la catégorie de ruban est visible.  
  
```  
BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la catégorie de ruban est visible ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Les catégories du ruban qui sont visibles s’affichent un onglet de catégorie.  
  
##  <a name="iswindows7look"></a>CMFCRibbonCategory::IsWindows7Look  
 Indique si le ruban parent a Windows 7 Rechercher (bouton petite application rectangulaire).  
  
```  
BOOL IsWindows7Look() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le ruban parent compose Windows 7 de recherche ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="notifycontrolcommand"></a>CMFCRibbonCategory::NotifyControlCommand  
 Remet un message de commande WM_NOTIFY à tous les `CMFCRibbonPanel` les éléments dans le `CMFCRibbonCategory` jusqu'à ce que le message est traité.  
  
```  
virtual BOOL NotifyControlCommand(
    BOOL bAccelerator,  
    int nNotifyCode,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bAccelerator`  
 `TRUE`Si cette commande provenance d’un accélérateur, ou `FALSE` dans le cas contraire.  
  
 [in] `nNotifyCode`  
 Le code de notification.  
  
 [in] `wParam`  
 Le champ WPARAM du message.  
  
 [in] `lParam`  
 Le champ LPARAM du message.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `TRUE` si le message a été géré, ou `FALSE` si ce n’est pas le cas.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="oncancelmode"></a>CMFCRibbonCategory::OnCancelMode  
 Appelle mode annulation dans tous les `CMFCRibbonPanel` éléments de la `CMFCRibbonCategory`.  
  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="ondraw"></a>CMFCRibbonCategory::OnDraw  
 Appelé par l’infrastructure pour dessiner la catégorie de ruban.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour la catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="ondrawimage"></a>CMFCRibbonCategory::OnDrawImage  
 Appelée par l’infrastructure pour dessiner l’image spécifiée dans la catégorie de ruban.  
  
```  
virtual BOOL OnDrawImage(
    CDC* pDC,  
    CRect rect,  
    CMFCRibbonBaseElement* pElement,  
    BOOL bIsLargeImage,  
    BOOL nImageIndex,  
    BOOL bCenter);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour l’image.  
  
 [in] `rect`  
 Rectangle d’affichage de l’image.  
  
 [in] `pElement`  
 Pointeur vers l’élément de ruban qui contient l’image.  
  
 [in] `bIsLargeImage`  
 `TRUE`Si l’image est la taille volumineuse ; `FALSE` si l’image est la petite taille.  
  
 [in] `nImageIndex`  
 Index de base zéro de l’image dans le tableau d’image est contenu dans la catégorie de ruban.  
  
 [in] `bCenter`  
 `TRUE`Pour centrer l’image dans le rectangle d’affichage ; `FALSE` pour dessiner l’image dans le coin supérieur gauche du rectangle d’affichage.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode a réussi ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondrawmenuborder"></a>CMFCRibbonCategory::OnDrawMenuBorder  
 Appelé par l’infrastructure pour dessiner la bordure d’un menu contextuel.  
  
```  
virtual void OnDrawMenuBorder(
    CDC* pDC,  
    CMFCRibbonPanelMenuBar* pMenuBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Ce paramètre n'est pas utilisé.  
  
 [in] `pMenuBar`  
 Ce paramètre n'est pas utilisé.  
  
### <a name="remarks"></a>Remarques  
 Par défaut, cette méthode ne fait rien. Substituez cette méthode pour dessiner la bordure d’un menu contextuel.  
  
##  <a name="onkey"></a>CMFCRibbonCategory::OnKey  
 Appelé par l’infrastructure lorsque l’utilisateur appuie sur un bouton de clavier.  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>Paramètres  
 `nChar`  
 Le code de touche virtuelle pour un utilisateur a appuyé sur la clé.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onlbuttondown"></a>CMFCRibbonCategory::OnLButtonDown  
 Appelé par l’infrastructure pour récupérer l’élément de ruban sous le point spécifié lorsque l’utilisateur appuie sur le bouton gauche de la souris.  
  
```  
virtual CMFCRibbonBaseElement* OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Les coordonnées x et y du pointeur de la souris, par rapport à l’angle supérieur gauche de la fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un élément de ruban si la méthode a réussi ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onlbuttonup"></a>CMFCRibbonCategory::OnLButtonUp  
 Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton gauche de la souris et que le pointeur est sur la catégorie de ruban.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Les coordonnées x et y du pointeur, par rapport à l’angle supérieur gauche de la fenêtre.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onmousemove"></a>CMFCRibbonCategory::OnMouseMove  
 Appelé par l’infrastructure lorsque le pointeur se déplace sur le ruban pour mettre à jour l’affichage catégorie du ruban.  
  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Les coordonnées x et y du pointeur, par rapport à l’angle supérieur gauche de la fenêtre.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onrtlchanged"></a>CMFCRibbonCategory::OnRTLChanged  
 Appelé par l’infrastructure lorsque la disposition change de direction.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bIsRTL`  
 `TRUE`Si la disposition est de droite à gauche ; `FALSE` si la disposition est de gauche à droite.  
  
### <a name="remarks"></a>Notes  
 Cette méthode ajuste la disposition de tous les volets de ruban et les éléments de ruban qui sont contenus dans la catégorie de ruban.  
  
##  <a name="onscrollhorz"></a>CMFCRibbonCategory::OnScrollHorz  
 Fait défiler la catégorie de ruban dans le sens horizontal.  
  
```  
virtual BOOL OnScrollHorz(
    BOOL bScrollLeft,  
    int nScrollOffset = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bScrollLeft`  
 `TRUE`Pour faire défiler vers la gauche. `FALSE` pour faire défiler vers la droite.  
  
 [in] `nScrollOffset`  
 La distance de défilement, en pixels.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la catégorie de ruban est déplacé dans le sens horizontal ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onupdatecmdui"></a>CMFCRibbonCategory::OnUpdateCmdUI  
 Appelle le `OnUpdateCmdUI` fonction membre dans chacune de la `CMFCRibbonPanel` les éléments de la `CMFCRibbonCategory` pour activer ou désactiver les éléments d’interface utilisateur dans les.  
  
```  
virtual void OnUpdateCmdUI(
    CMFCRibbonCmdUI* pCmdUI,  
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pCmdUI`  
 Pointeur vers le `CMFCRibbonCmdUI` objet qui spécifie les éléments d’interface utilisateur doit être activé et qui doivent être désactivées.  
  
 [in] `pTarget`  
 Pointeur vers la fenêtre qui contrôle l’activation ou la désactivation des éléments d’interface utilisateur.  
  
 [in] `bDisableIfNoHndler`  
 `TRUE`Pour désactiver l’élément d’interface utilisateur si aucun gestionnaire n’est défini dans une table des messages ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="recalclayout"></a>CMFCRibbonCategory::RecalcLayout  
 Ajuste la disposition de tous les contrôles de la catégorie de ruban.  
  
```  
virtual void RecalcLayout(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour la catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="removepanel"></a>CMFCRibbonCategory::RemovePanel  
 Supprime un panneau de ruban de la catégorie de ruban.  
  
```cpp  
BOOL RemovePanel(
    int nIndex,  
    BOOL bDelete = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nIndex`  
 Le numéro d’index du panneau à supprimer. Obtenu en appelant le [CMFCRibbonCategory::GetPanelIndex](#getpanelindex) (méthode).  
  
 [in] `bDelete`  
 `TRUE`Pour supprimer l’objet de panneau de configuration de la mémoire. `FALSE` pour supprimer l’objet de panneau de configuration sans le supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` si la méthode a réussi ; sinon, `FALSE`.  
  
##  <a name="repospanels"></a>CMFCRibbonCategory::ReposPanels  
 Ajuste la disposition de tous les contrôles de volets de ruban qui sont contenus dans la catégorie de ruban.  
  
```  
virtual void ReposPanels(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour les volets de ruban qui sont contenus dans la catégorie de ruban.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="setcollapseorder"></a>CMFCRibbonCategory::SetCollapseOrder  
 Définit l’ordre dans lequel les panneaux de ruban de la catégorie de ruban réduits.  
  
```  
void SetCollapseOrder(const CArray<int,int>& arCollapseOrder);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `arCollapseOrder`  
 Spécifie l’ordre de réduction. Le tableau contient des index de base zéro de volets de ruban.  
  
### <a name="remarks"></a>Remarques  
 La bibliothèque définit l’ordre de réduction. Toutefois, vous pouvez personnaliser ce comportement en fournissant la catégorie à la liste des index qui spécifie l’ordre de réduction.  
  
 Lorsque la catégorie détecte qu’il doit réduire un panneau de ruban, il recherche l’élément suivant dans la liste spécifiée. Si la liste est vide, ou si vous n’avez pas spécifié suffisamment d’éléments, la catégorie utilise l’algorithme interne.  
  
 Par exemple, la catégorie comporte trois volets de ruban et peut être réduite à plusieurs reprises jusqu'à ce que tous les panneaux sont dans l’état réduit entièrement. Vous pouvez définir l’ordre de réduction suivant : 0, 0, 2, 2. Dans ce cas, la catégorie réduira le panneau 0 deux fois, le panneau de configuration 2 à deux reprises. Le panneau de configuration qui a l’index 1 reste développée.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `SetCollapseOrder` méthode dans la `CMFCRibbonCategory` classe. L’exemple montre comment créer un tableau pour la commande de réduction et comment définir l’ordre de réduction à la catégorie de ruban.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#13;](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_2.cpp)]  
  
##  <a name="setdata"></a>CMFCRibbonCategory::SetData  
 Définit les données définies par l’utilisateur à associer à la catégorie de ruban.  
  
```  
void SetData(DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwData`  
 Données définies par l'utilisateur.  
  
##  <a name="setkeys"></a>CMFCRibbonCategory::SetKeys  
 Assigne une touche d’accès à la catégorie de ruban.  
  
```  
void SetKeys(LPCTSTR lpszKeys);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszKeys`  
 Le texte de la touche d’accès.  
  
### <a name="remarks"></a>Remarques  
 Info-bulles sont affichent lorsque l’utilisateur appuie sur la touche Alt ou F10.  
  
##  <a name="setname"></a>CMFCRibbonCategory::SetName  
 Attribue un nom et une touche d’accès à la catégorie de ruban.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `lpszName`  
 Le nom et la touche d’accès de la catégorie de ruban.  
  
### <a name="remarks"></a>Notes  
 Pour définir la touche d’accès pour la catégorie de ruban, ajoutez une séquence d’échappement suivie par les caractères de la touche d’accès à `lpszName`.  
  
##  <a name="settabcolor"></a>CMFCRibbonCategory::SetTabColor  
 Définit la couleur de la catégorie de ruban.  
  
```  
void SetTabColor(AFX_RibbonCategoryColor color);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `color`  
 Spécifie la nouvelle couleur de la catégorie de ruban.  
  
### <a name="remarks"></a>Notes  
 Couleur peut être une des valeurs suivantes :  
  
-   AFX_CategoryColor_None  
  
-   AFX_CategoryColor_Red  
  
-   AFX_CategoryColor_Orange  
  
-   AFX_CategoryColor_Yellow  
  
-   AFX_CategoryColor_Green  
  
-   AFX_CategoryColor_Blue  
  
-   AFX_CategoryColor_Indigo  
  
-   AFX_CategoryColor_Violet  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)

