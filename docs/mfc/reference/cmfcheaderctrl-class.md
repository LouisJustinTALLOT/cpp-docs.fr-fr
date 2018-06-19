---
title: Classe CMFCHeaderCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
dev_langs:
- C++
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a1c10cd6242f2845d64965d914093455da21c8a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370027"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class
La `CMFCHeaderCtrl` classe prend en charge le tri de plusieurs colonnes dans un contrôle header.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCHeaderCtrl : public CHeaderCtrl  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Construit un objet `CMFCHeaderCtrl`.|  
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Active ou désactive *tri sur plusieurs colonnes* mode pour le contrôle d’en-tête actuel.|  
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Indique si une colonne n’est pas triée, ou qu’il est triée dans l’ordre croissant ou décroissant.|  
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Récupère l’index de base zéro de la première colonne triée dans le contrôle header.|  
|`CMFCHeaderCtrl::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|  
|[CMFCHeaderCtrl::IsAscending](#isascending)|Indique si une colonne dans le contrôle header est triée par ordre croissant.|  
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Indique si la fenêtre parente du contrôle d’en-tête actuel est une boîte de dialogue.|  
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Indique si le contrôle header actuel est en *tri sur plusieurs colonnes* mode.|  
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Supprime la colonne spécifiée dans la liste des colonnes de tri.|  
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Définit l’ordre de tri d’une colonne spécifiée dans un contrôle header.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Appelé par l’infrastructure pour dessiner une colonne de contrôle d’en-tête.|  
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Appelé par l’infrastructure pour dessiner la flèche de tri.|  
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Appelé par l’infrastructure pour remplir l’arrière-plan d’une colonne de contrôle d’en-tête.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCHeaderCtrl` classe et comment activer *tri sur plusieurs colonnes* mode pour le contrôle d’en-tête actuel.  
  
 [!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]  
  
## <a name="remarks"></a>Notes  
 La `CMFCHeaderCtrl` classe dessine une flèche de tri sur une colonne de contrôle d’en-tête pour indiquer que la colonne est triée. Utilisez *tri sur plusieurs colonnes* mode si un ensemble de colonnes dans le contrôle de liste parente ( [CMFCListCtrl classe](../../mfc/reference/cmfclistctrl-class.md)) peuvent être triées en même temps.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxheaderctrl.h  
  
##  <a name="cmfcheaderctrl"></a>  CMFCHeaderCtrl::CMFCHeaderCtrl  
 Construit un objet `CMFCHeaderCtrl`.  
  
```  
CMFCHeaderCtrl::CMFCHeaderCtrl()  
```  
  
### <a name="remarks"></a>Notes  
 Ce constructeur initialise les variables de membre suivantes avec les valeurs spécifiées :  
  
|Variable membre|Value|  
|---------------------|-----------|  
|`m_bIsMousePressed`|`FALSE`|  
|`m_bMultipleSort`|`FALSE`|  
|`m_bAscending`|`TRUE`|  
|`m_nHighlightedItem`|-1|  
|`m_bTracked`|`FALSE`|  
|`m_bIsDlgControl`|`FALSE`|  
|`m_hFont`|`NULL`|  
  
##  <a name="enablemultiplesort"></a>  CMFCHeaderCtrl::EnableMultipleSort  
 Active ou désactive *tri sur plusieurs colonnes* mode pour le contrôle d’en-tête actuel.  
  
```  
void EnableMultipleSort(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE` Pour activer le mode de tri sur plusieurs colonnes ; `FALSE` pour désactiver le mode de trier plusieurs colonnes et pour supprimer des colonnes dans la liste des colonnes triées. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour activer ou désactiver le mode de tri basé sur plusieurs colonnes. Deux ou plusieurs colonnes peuvent participer à un tri si le contrôle header est en mode de trier plusieurs colonnes.  
  
##  <a name="getcolumnstate"></a>  CMFCHeaderCtrl::GetColumnState  
 Indique si une colonne n’est pas triée, ou qu’il est triée dans l’ordre croissant ou décroissant.  
  
```  
int GetColumnState(int iColumn) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iColumn`  
 Index de base zéro d’une colonne.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui indique l’état de tri de la colonne spécifiée. Le tableau suivant répertorie les valeurs possibles :  
  
|Value|Description|  
|-----------|-----------------|  
|-1|Triés par ordre décroissant.|  
|0|Non trié.|  
|1|Trié par ordre croissant.|  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getsortcolumn"></a>  CMFCHeaderCtrl::GetSortColumn  
 Récupère l’index de base zéro de la première colonne triée dans le contrôle header.  
  
```  
int GetSortColumn() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’index d’une colonne triée ou -1 si aucune colonne triée n’est trouvée.  
  
### <a name="remarks"></a>Notes  
 Si le contrôle header est dans *tri sur plusieurs colonnes* mode et compilé l’application en mode débogage, cette méthode déclare et vous indique d’utiliser le [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) méthode à la place. Si le contrôle header est en mode de trier plusieurs colonnes et compilé de l’application en mode de vente au détail, cette méthode retourne -1.  
  
##  <a name="isascending"></a>  CMFCHeaderCtrl::IsAscending  
 Indique si une colonne dans le contrôle header est triée par ordre croissant.  
  
```  
BOOL IsAscending() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si une colonne dans le contrôle header est triée dans l’ordre croissant ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 La valeur retournée par cette méthode est utilisée pour afficher la flèche de tri approprié sur l’élément de contrôle d’en-tête. Utilisez le [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) pour définir l’ordre de tri.  
  
##  <a name="isdialogcontrol"></a>  CMFCHeaderCtrl::IsDialogControl  
 Indique si la fenêtre parente du contrôle d’en-tête actuel est une boîte de dialogue.  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la fenêtre parente du contrôle d’en-tête actuel est une boîte de dialogue ; dans le cas contraire, `FALSE`.  
  
##  <a name="ismultiplesort"></a>  CMFCHeaderCtrl::IsMultipleSort  
 Indique si le contrôle header actuel est en *tri sur plusieurs colonnes* mode.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si plusieurs colonnes de tri est activé ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) méthode pour activer ou désactiver le mode de tri basé sur plusieurs colonnes. Deux ou plusieurs colonnes peuvent participer à un tri si le contrôle header est en mode de trier plusieurs colonnes.  
  
##  <a name="ondrawitem"></a>  CMFCHeaderCtrl::OnDrawItem  
 Appelé par l’infrastructure pour dessiner une colonne de contrôle d’en-tête.  
  
```  
virtual void OnDrawItem(
    CDC* pDC,  
    int iItem,  
    CRect rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `iItem`  
 Index de base zéro de l’élément à dessiner.  
  
 [in] `rect`  
 Le rectangle englobant de l’élément à dessiner.  
  
 [in] `bIsPressed`  
 `TRUE` Pour dessiner l’élément dans l’état enfoncé ; dans le cas contraire, `FALSE`.  
  
 [in] `bIsHighlighted`  
 `TRUE` Pour dessiner l’élément dans l’état mis en surbrillance ; dans le cas contraire, `FALSE`.  
  
##  <a name="ondrawsortarrow"></a>  CMFCHeaderCtrl::OnDrawSortArrow  
 Appelé par l’infrastructure pour dessiner la flèche de tri.  
  
```  
virtual void OnDrawSortArrow(
    CDC* pDC,  
    CRect rectArrow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
 [in] `rectArrow`  
 Le rectangle englobant de la flèche de tri.  
  
##  <a name="onfillbackground"></a>  CMFCHeaderCtrl::OnFillBackground  
 Appelé par l’infrastructure pour remplir l’arrière-plan d’une colonne de contrôle d’en-tête.  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="removesortcolumn"></a>  CMFCHeaderCtrl::RemoveSortColumn  
 Supprime la colonne spécifiée dans la liste des colonnes de tri.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iColumn`  
 Index de base zéro de la colonne à supprimer.  
  
##  <a name="setsortcolumn"></a>  CMFCHeaderCtrl::SetSortColumn  
 Définit l’ordre de tri d’une colonne spécifiée dans un contrôle header.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending=TRUE,  
    BOOL bAdd=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iColumn`  
 Index de base zéro d’une colonne de contrôle d’en-tête. Si ce paramètre est inférieur à zéro, cette méthode supprime toutes les colonnes de la liste des colonnes de tri.  
  
 [in] `bAscending`  
 Spécifie l’ordre de tri de la colonne qui le `iColumn` paramètre spécifie. `TRUE` Pour définir l’ordre croissant ; `FALSE` pour définir l’ordre décroissant. La valeur par défaut est `TRUE`.  
  
 [in] `bAdd`  
 `TRUE` Pour définir l’ordre de tri de la colonne qui le `iColumn` paramètre spécifie.  
  
 Si le contrôle header actuel se trouve dans *tri sur plusieurs colonnes* mode, cette méthode ajoute la colonne spécifiée à la liste des colonnes de tri. Utilisez [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) pour définir le mode de tri plusieurs colonnes.  
  
 Si plusieurs mode de tri de colonne n’est pas défini, et cette méthode est compilée en mode débogage, cette méthode déclare. Si plusieurs mode de tri de colonne n’est pas défini et que cette méthode est compilée en mode de vente au détail, cette méthode supprime d’abord toutes les colonnes de la liste des colonnes de tri, puis ajoute la colonne spécifiée à la liste.  
  
 `FALSE` d’abord supprimer toutes les colonnes dans la liste des colonnes de tri et puis ajouter la colonne spécifiée à la liste. La valeur par défaut est `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour définir l’ordre de tri d’une colonne. Si nécessaire, cette méthode ajoute la colonne à la liste des colonnes de tri. Le contrôle header utilise l’ordre de tri pour dessiner une flèche de tri qui pointe vers le haut ou vers le bas.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl, classe](../../mfc/reference/cmfclistctrl-class.md)
