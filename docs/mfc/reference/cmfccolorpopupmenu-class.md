---
title: Cmfccolorpopupmenu, classe | Microsoft Docs
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
ms.openlocfilehash: b32317f4fd67a627a272ea8eefcc949d1b0e63c8
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852992"
---
# <a name="cmfccolorpopupmenu-class"></a>Cmfccolorpopupmenu, classe
Représente un menu contextuel utilisateurs permet de sélectionner des couleurs dans un document ou une application.  
  
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
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Définit l’objet de contrôle de grille de propriété de l’embedded `CMFCColorBar` objet.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|Name|Description|  
|`m_bEnabledInCustomizeMode`|Valeur booléenne qui détermine s’il faut afficher la barre de couleurs.|  
|`m_wndColorBar`|Le `CMFCColorBar` objet qui fournit la sélection de couleur.|  
  
### <a name="remarks"></a>Notes  
 Cette classe hérite des fonctionnalités de menu contextuel de la `CMFCPopupMenu` classe et gère un `CMFCColorBar` objet qui fournit la sélection de couleur. Lorsque l’infrastructure de la barre d’outils est en mode de personnalisation et le `m_bEnabledInCustomizeMode` membre est défini sur FALSE, l’objet de barre de couleur n’est pas affiché. Pour plus d’informations sur le mode de personnalisation, consultez [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 Pour plus d’informations sur `CMFCColorBar`, consultez [cmfccolorbar, classe](../../mfc/reference/cmfccolorbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## <a name="requirements"></a>Configuration requise  
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
 [in] *couleurs*  
 Un tableau de couleurs affichée par l’infrastructure dans le menu contextuel.  
  
 [in] *couleur*  
 La couleur sélectionnée par défaut.  
  
 [in] *lpszAutoColor*  
 L’étiquette de texte de la *automatique* bouton de couleur (par défaut), ou NULL.  
  
 L’étiquette pour le bouton automatique standard est **automatique**.  
  
 [in] *lpszOtherColor*  
 L’étiquette de texte de la *autres* bouton, qui affiche plus choix de couleurs, ou NULL.  
  
 L’étiquette du bouton autre standard est **couleurs supplémentaires...** .  
  
 [in] *lpszDocColors*  
 L’étiquette de texte du bouton de couleurs de document. La palette de couleurs de document répertorie toutes les couleurs que le document utilise actuellement.  
  
 [in] *lstDocColors*  
 Une liste de couleurs que le document utilise actuellement.  
  
 [in] *nColumns*  
 Le nombre de colonnes qui a le tableau de couleurs.  
  
 [in] *nHorzDockRows*  
 Le nombre de lignes ayant la barre de couleurs lorsqu’elle est ancrée horizontalement.  
  
 [in] *nVertDockColumns*  
 Le nombre de colonnes possédant la barre de couleur lorsqu’il est ancré verticalement.  
  
 [in] *automatiqueCouleur*  
 La couleur par défaut que le framework s’applique lorsque vous cliquez sur le bouton automatique.  
  
 [in] *uiCommandID*  
 ID de la commande de contrôle de barre de couleurs.  
  
 [in] *bStdColorDlg*  
 Valeur booléenne qui indique s’il faut afficher la boîte de dialogue de couleur système standard ou le [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) boîte de dialogue.  
  
 [in] *pParentBtn*  
 Pointeur vers un bouton de parent.  
  
 [in] *nID*  
 ID de la commande.  
  
### <a name="remarks"></a>Notes  
 Chaque surchargé constructeur affecte la `m_bEnabledInCustomizeMode` membre sur FALSE.  
  
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
|[in] *pWndMain*|Pointeur vers la fenêtre parente de la barre détachable.|  
|[in] *uiID*|L’ID de commande de la barre détachable.|  
|[in] *le caractère*|Le texte de la fenêtre de la barre détachable.|  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le nouvel objet de barre de contrôle détachable.  
  
### <a name="remarks"></a>Notes  
 Cette méthode crée un [cmfccolorbar, classe](../../mfc/reference/cmfccolorbar-class.md) de l’objet et le caste vers un [CPANE, classe](../../mfc/reference/cpane-class.md) pointeur. Vous pouvez convertir cette valeur à un [cmfccolorbar, classe](../../mfc/reference/cmfccolorbar-class.md) pointeur en utilisant l’une des macros de conversion décrits dans [cast Type des objets de classe MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).  
  
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
 Définit l’objet de contrôle de grille de propriété de l’embedded `CMFCColorBar` objet.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWndList*  
 Pointeur vers un objet de contrôle de grille de propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
