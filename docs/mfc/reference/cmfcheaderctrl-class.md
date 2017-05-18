---
title: Classe de CMFCHeaderCtrl | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCHeaderCtrl class
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
caps.latest.revision: 29
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c49ee61b6441e79a0c3c4c1aa133b4bce1578103
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class
La `CMFCHeaderCtrl` classe prend en charge le tri de plusieurs colonnes dans un contrôle d’en-tête.  
  
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
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Indique si une colonne n’est pas triée, ou est triée en ordre croissant ou décroissant.|  
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Récupère l’index de base zéro de la première colonne de tri dans le contrôle header.|  
|`CMFCHeaderCtrl::GetThisClass`|Utilisé par le framework d’obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet associé à ce type de classe.|  
|[CMFCHeaderCtrl::IsAscending](#isascending)|Indique si une colonne dans le contrôle header est triée par ordre croissant.|  
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Indique si la fenêtre parent du contrôle d’en-tête actuel est une boîte de dialogue.|  
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Indique si le contrôle d’en-tête actuel est dans *tri sur plusieurs colonnes* mode.|  
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Supprime la colonne spécifiée dans la liste des colonnes de tri.|  
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Définit l’ordre de tri d’une colonne spécifiée dans un contrôle d’en-tête.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Appelé par l’infrastructure pour dessiner une colonne de contrôle d’en-tête.|  
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Appelé par l’infrastructure pour dessiner la flèche de tri.|  
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Appelé par l’infrastructure pour remplir l’arrière-plan d’une colonne de contrôle d’en-tête.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCHeaderCtrl` (classe) et comment activer *tri sur plusieurs colonnes* mode pour le contrôle d’en-tête actuel.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#24;](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]  
  
## <a name="remarks"></a>Remarques  
 La `CMFCHeaderCtrl` classe dessine une flèche de tri sur une colonne de contrôle d’en-tête pour indiquer que la colonne est triée. Utilisez *tri sur plusieurs colonnes* mode si un ensemble de colonnes dans le contrôle de liste parente ( [CMFCListCtrl classe](../../mfc/reference/cmfclistctrl-class.md)) peuvent être triés en même temps.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxheaderctrl.h  
  
##  <a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl  
 Construit un objet `CMFCHeaderCtrl`.  
  
```  
CMFCHeaderCtrl::CMFCHeaderCtrl()  
```  
  
### <a name="remarks"></a>Notes  
 Ce constructeur initialise les variables de membre suivantes avec les valeurs spécifiées :  
  
|Variable membre|Valeur|  
|---------------------|-----------|  
|`m_bIsMousePressed`|`FALSE`|  
|`m_bMultipleSort`|`FALSE`|  
|`m_bAscending`|`TRUE`|  
|`m_nHighlightedItem`|-1|  
|`m_bTracked`|`FALSE`|  
|`m_bIsDlgControl`|`FALSE`|  
|`m_hFont`|`NULL`|  
  
##  <a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort  
 Active ou désactive *tri sur plusieurs colonnes* mode pour le contrôle d’en-tête actuel.  
  
```  
void EnableMultipleSort(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour activer le mode de trier plusieurs colonnes ; `FALSE` pour désactiver le mode de trier plusieurs colonnes et pour supprimer des colonnes dans la liste des colonnes triées. La valeur par défaut est `TRUE`.  
  
### <a name="remarks"></a>Remarques  
 Utilisez cette méthode pour activer ou désactiver le mode de trier plusieurs colonnes. Deux ou plusieurs colonnes peuvent participer à un tri si le contrôle d’en-tête est en mode de trier plusieurs colonnes.  
  
##  <a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState  
 Indique si une colonne n’est pas triée, ou est triée en ordre croissant ou décroissant.  
  
```  
int GetColumnState(int iColumn) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iColumn`  
 Index de base zéro d’une colonne.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui indique l’état de tri de la colonne spécifiée. Le tableau suivant répertorie les valeurs possibles :  
  
|Valeur|Description|  
|-----------|-----------------|  
|-1|Triés par ordre décroissant.|  
|0|Non trié.|  
|1|Trié par ordre croissant.|  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn  
 Récupère l’index de base zéro de la première colonne de tri dans le contrôle header.  
  
```  
int GetSortColumn() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’index d’une colonne triée, ou -1 si aucune colonne triée n’est trouvée.  
  
### <a name="remarks"></a>Remarques  
 Si le contrôle header est *tri sur plusieurs colonnes* mode et compilé l’application en mode débogage, cette méthode déclare et vous conseille d’utiliser la [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) méthode à la place. Si le contrôle header est en mode de trier plusieurs colonnes et compilé de l’application en mode de vente au détail, cette méthode retourne -1.  
  
##  <a name="isascending"></a>CMFCHeaderCtrl::IsAscending  
 Indique si une colonne dans le contrôle header est triée par ordre croissant.  
  
```  
BOOL IsAscending() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si une colonne dans le contrôle header est triée dans l’ordre croissant ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 La valeur retournée par cette méthode est utilisée pour afficher la flèche de tri approprié sur l’élément de contrôle d’en-tête. Utilisez le [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) pour définir l’ordre de tri.  
  
##  <a name="isdialogcontrol"></a>CMFCHeaderCtrl::IsDialogControl  
 Indique si la fenêtre parent du contrôle d’en-tête actuel est une boîte de dialogue.  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la fenêtre parent du contrôle d’en-tête actuel est une boîte de dialogue. dans le cas contraire, `FALSE`.  
  
##  <a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort  
 Indique si le contrôle d’en-tête actuel est dans *tri sur plusieurs colonnes* mode.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si plusieurs mode de tri des colonnes est activé ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) méthode pour activer ou désactiver le mode de trier plusieurs colonnes. Deux ou plusieurs colonnes peuvent participer à un tri si le contrôle d’en-tête est en mode de trier plusieurs colonnes.  
  
##  <a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem  
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
 `TRUE`Pour dessiner l’élément dans l’état enfoncé ; dans le cas contraire, `FALSE`.  
  
 [in] `bIsHighlighted`  
 `TRUE`Pour dessiner l’élément dans l’état mis en surbrillance ; dans le cas contraire, `FALSE`.  
  
##  <a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow  
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
  
##  <a name="onfillbackground"></a>CMFCHeaderCtrl::OnFillBackground  
 Appelé par l’infrastructure pour remplir l’arrière-plan d’une colonne de contrôle d’en-tête.  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="removesortcolumn"></a>CMFCHeaderCtrl::RemoveSortColumn  
 Supprime la colonne spécifiée dans la liste des colonnes de tri.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iColumn`  
 Index de base zéro de la colonne à supprimer.  
  
##  <a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn  
 Définit l’ordre de tri d’une colonne spécifiée dans un contrôle d’en-tête.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending=TRUE,  
    BOOL bAdd=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iColumn`  
 Index de base zéro d’une colonne de contrôle d’en-tête. Si ce paramètre est inférieure à zéro, cette méthode supprime toutes les colonnes de la liste des colonnes de tri.  
  
 [in] `bAscending`  
 Spécifie l’ordre de tri de la colonne qui le `iColumn` paramètre spécifie. `TRUE`Pour définir l’ordre croissant ; `FALSE` pour définir l’ordre décroissant. La valeur par défaut est `TRUE`.  
  
 [in] `bAdd`  
 `TRUE`Pour définir l’ordre de tri de la colonne qui le `iColumn` paramètre spécifie.  
  
 Si le contrôle d’en-tête actuel se trouve dans *tri sur plusieurs colonnes* mode, cette méthode ajoute la colonne spécifiée à la liste des colonnes de tri. Utilisez [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) pour définir le mode de trier plusieurs colonnes.  
  
 Si plusieurs mode de tri de colonne n’est pas défini et que cette méthode est compilée en mode débogage, cette méthode déclare. Si plusieurs mode de tri de colonne n’est pas défini et que cette méthode est compilée en mode de vente au détail, cette méthode supprime d’abord toutes les colonnes de la liste des colonnes de tri et puis ajoute la colonne spécifiée à la liste.  
  
 `FALSE`d’abord supprimer toutes les colonnes de la liste des colonnes de tri, puis ajouter la colonne spécifiée à la liste. La valeur par défaut est `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour définir l’ordre de tri d’une colonne. Si nécessaire, cette méthode ajoute la colonne à la liste des colonnes de tri. Le contrôle header utilise l’ordre de tri pour dessiner une flèche de tri pointant vers le haut ou vers le bas.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl (classe)](../../mfc/reference/cmfclistctrl-class.md)

