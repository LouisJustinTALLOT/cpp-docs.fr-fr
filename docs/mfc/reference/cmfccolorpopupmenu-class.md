---
title: Classe de CMFCColorPopupMenu | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66bdd0cdf9e9c13ceac6eb01716ae8c859462524
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372374"
---
# <a name="cmfccolorpopupmenu-class"></a>Classe de CMFCColorPopupMenu
Représente un menu contextuel qui utilisent des utilisateurs à sélectionner des couleurs dans un document ou une application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Construit un objet `CMFCColorPopupMenu`.|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Crée une barre de couleur ancrable détachable. (Substitue [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|  
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Retourne le [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) qui est incorporé dans le menu contextuel. (Substitue [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|  
|`CMFCColorPopupMenu::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Définit l’objet de contrôle de grille de propriété de l’élément incorporé `CMFCColorBar` objet.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|Name|Description|  
|`m_bEnabledInCustomizeMode`|Valeur booléenne qui détermine s’il faut afficher la barre de couleurs.|  
|`m_wndColorBar`|Le `CMFCColorBar` objet qui fournit la sélection de couleur.|  
  
### <a name="remarks"></a>Notes  
 Cette classe hérite de la fonctionnalité de menu contextuel de la `CMFCPopupMenu` classe et gère un `CMFCColorBar` objet qui fournit la sélection de couleur. Lorsque l’infrastructure de la barre d’outils est en mode de personnalisation et le `m_bEnabledInCustomizeMode` membre a la valeur `FALSE`, l’objet de barre de couleur n’est pas affiché. Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 Pour plus d’informations sur `CMFCColorBar`, consultez [CMFCColorBar classe](../../mfc/reference/cmfccolorbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxcolorpopupmenu.h  
  
##  <a name="cmfccolorpopupmenu"></a>  CMFCColorPopupMenu::CMFCColorPopupMenu  
 Construit un objet `CMFCColorPopupMenu`.  
  
```  
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    int nHorzDockRows,  
    int nVertDockColumns,  
    COLORREF colorAutomatic,  
    UINT uiCommandID,  
    BOOL bStdColorDlg = FALSE);

 
CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic);

 
CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `colors`  
 Un tableau de couleurs affichée par l’infrastructure dans le menu contextuel.  
  
 [in] `color`  
 La couleur sélectionnée par défaut.  
  
 [in] `lpszAutoColor`  
 L’étiquette de texte de la *automatique* bouton de couleur (par défaut), ou `NULL`.  
  
 L’étiquette standard pour le bouton automatique est **automatique**.  
  
 [in] `lpszOtherColor`  
 L’étiquette de texte de la *autres* bouton qui affiche d’autres options de couleur, ou `NULL`.  
  
 L’étiquette standard pour l’autre bouton est **autres couleurs...** .  
  
 [in] `lpszDocColors`  
 L’étiquette de texte du bouton de couleurs de document. La palette de couleurs du document répertorie toutes les couleurs que le document utilise actuellement.  
  
 [in] `lstDocColors`  
 Une liste de couleurs que le document utilise actuellement.  
  
 [in] `nColumns`  
 Le nombre de colonnes qui a le groupe de couleurs.  
  
 [in] `nHorzDockRows`  
 Le nombre de lignes de la barre de couleur lorsqu’il est ancré horizontalement.  
  
 [in] `nVertDockColumns`  
 Le nombre de colonnes de la barre de couleur lorsqu’il est ancré verticalement.  
  
 [in] `colorAutomatic`  
 La couleur par défaut que le framework s’applique lorsque vous cliquez sur le bouton automatique.  
  
 [in] `uiCommandID`  
 ID de la commande de contrôle de barre de couleur.  
  
 [in] `bStdColorDlg`  
 Valeur booléenne qui indique s’il faut afficher la boîte de dialogue couleur système standard ou [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue.  
  
 [in] `pParentBtn`  
 Pointeur vers un bouton parent.  
  
 [in] `nID`  
 ID de la commande.  
  
### <a name="remarks"></a>Notes  
 Chaque surcharge de constructeur définit la `m_bEnabledInCustomizeMode` membre à `FALSE`.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un `CMFCColorPopupMenu` objet.  
  
 [!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]  
  
##  <a name="createtearoffbar"></a>  CMFCColorPopupMenu::CreateTearOffBar  
 Crée une barre de couleur ancrable détachable.  
  
```  
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,  
    UINT uiID,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `pWndMain`|Pointeur vers la fenêtre parente de la barre détachable.|  
|[in] `uiID`|L’ID de commande de la barre détachable.|  
|[in] `lpszName`|Texte de la fenêtre de la barre détachable.|  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le nouvel objet de barre de contrôle détachable.  
  
### <a name="remarks"></a>Notes  
 Cette méthode crée un [CMFCColorBar classe](../../mfc/reference/cmfccolorbar-class.md) de l’objet et le caste vers une [classe CPane](../../mfc/reference/cpane-class.md) pointeur. Vous pouvez convertir cette valeur à un [CMFCColorBar classe](../../mfc/reference/cmfccolorbar-class.md) pointeur en utilisant l’une des macros de conversion décrites dans [effectuer un cast de MFC classe d’objets de Type](../../mfc/reference/type-casting-of-mfc-class-objects.md).  
  
##  <a name="getmenubar"></a>  CMFCColorPopupMenu::GetMenuBar  
 Retourne le [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) qui est incorporé dans le menu contextuel.  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’embedded `CMFCPopupMenuBar`.  
  
### <a name="remarks"></a>Notes  
 Le menu contextuel couleur a incorporé [cmfcpopupmenubar, classe](../../mfc/reference/cmfcpopupmenubar-class.md) objet. Substituez cette méthode dans une classe dérivée si votre application utilise un autre type incorporé.  
  
##  <a name="setproplist"></a>  CMFCColorPopupMenu::SetPropList  
 Définit l’objet de contrôle de grille de propriété de l’élément incorporé `CMFCColorBar` objet.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndList`  
 Pointeur vers un objet de contrôle de grille de propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
