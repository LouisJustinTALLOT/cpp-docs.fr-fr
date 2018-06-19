---
title: Classe de CScrollBar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
dev_langs:
- C++
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90f672cbeeee0c297e3d1deb6a6b5e83bffda3e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372767"
---
# <a name="cscrollbar-class"></a>Classe de CScrollBar
Fournit les fonctionnalités d'un contrôle de barre de défilement Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CScrollBar : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CScrollBar::CScrollBar](#cscrollbar)|Construit un objet `CScrollBar`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CScrollBar::Create](#create)|Crée la barre de défilement Windows et l’attache à le `CScrollBar` objet.|  
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Active ou désactive une flèche (ou les deux) d'une barre de défilement.|  
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Récupère des informations sur la barre à l’aide de défilement un `SCROLLBARINFO` structure.|  
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Récupère des informations sur la barre de défilement.|  
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Récupère la limite de la barre de défilement|  
|[CScrollBar::GetScrollPos](#getscrollpos)|Récupère la position actuelle d'une case de défilement.|  
|[CScrollBar::GetScrollRange](#getscrollrange)|Récupère les positions actuelles de la barre de défilement minimal et maximal pour la barre de défilement donnée.|  
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Définit les informations sur la barre de défilement.|  
|[CScrollBar::SetScrollPos](#setscrollpos)|Définit la position actuelle d’une zone de défilement.|  
|[CScrollBar::SetScrollRange](#setscrollrange)|Définit les valeurs de position minimale et maximale de la barre de défilement donnée.|  
|[CScrollBar::ShowScrollBar](#showscrollbar)|Affiche ou masque une barre de défilement.|  
  
## <a name="remarks"></a>Notes  
 Vous créez un contrôle de barre de défilement en deux étapes. Tout d’abord, appelez le constructeur `CScrollBar` pour construire le `CScrollBar` de l’objet, puis appelez le [créer](#create) fonction membre pour créer le contrôle de barre de défilement Windows et l’attacher à la `CScrollBar` objet.  
  
 Si vous créez un `CScrollBar` objet dans une boîte de dialogue (via une ressource de boîte de dialogue), le `CScrollBar` est automatiquement détruite lorsque l’utilisateur ferme la boîte de dialogue.  
  
 Si vous créez un `CScrollBar` de l’objet dans une fenêtre, vous devrez peut-être également détruire.  
  
 Si vous créez le `CScrollBar` de l’objet sur la pile, il est supprimé automatiquement. Si vous créez le `CScrollBar` objet sur le tas à l’aide de la **nouveau** (fonction), vous devez appeler **supprimer** sur l’objet pour détruire lorsque l’utilisateur met fin à la barre de défilement Windows.  
  
 Si vous allouez davantage de mémoire dans le `CScrollBar` de l’objet, substituez le `CScrollBar` destructeur pour éliminer les allocations.  
  
 Pour plus d’informations sur l’utilisation de `CScrollBar`, consultez [contrôles](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h  
  
##  <a name="create"></a>  CScrollBar::Create  
 Crée la barre de défilement Windows et l’attache à le `CScrollBar` objet.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwStyle`  
 Spécifie le défilement style de la barre. Appliquer n’importe quelle combinaison de [styles de barre de défilement](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) à la barre de défilement.  
  
 `rect`  
 Spécifie la taille de la barre de défilement et la position. Peut être un `RECT` structure ou un `CRect` objet.  
  
 `pParentWnd`  
 Spécifie le défilement fenêtre de parent de la barre, généralement un `CDialog` objet. Il ne doit pas être **NULL**.  
  
 `nID`  
 ID de contrôle de la barre de défilement.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CScrollBar` objet en deux étapes. Tout d’abord, appelez le constructeur, ce qui construit la `CScrollBar` de l’objet, puis appelez **créer**, qui crée et initialise la barre de défilement Windows associée et l’attache à le `CScrollBar` objet.  
  
 Appliquez ce qui suit [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) pour une barre de défilement :  
  
- **WS_CHILD** toujours  
  
- **WS_VISIBLE** généralement  
  
- **WS_DISABLED** rarement  
  
- **WS_GROUP** aux contrôles de groupe  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]  
  
##  <a name="cscrollbar"></a>  CScrollBar::CScrollBar  
 Construit un objet `CScrollBar`.  
  
```  
CScrollBar();
```  
  
### <a name="remarks"></a>Notes  
 Après la construction de l’objet, appelez le **créer** fonction membre pour créer et initialiser la barre de défilement Windows.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]  
  
##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar  
 Active ou désactive une flèche (ou les deux) d'une barre de défilement.  
  
```  
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```  
  
### <a name="parameters"></a>Paramètres  
 `nArrowFlags`  
 Spécifie si les flèches de défilement sont activées ou désactivées et les flèches sont activées ou désactivées. Ce paramètre peut être une des valeurs suivantes :  
  
- **ESB_ENABLE_BOTH** permet à la fois des flèches d’une barre de défilement.  
  
- **ESB_DISABLE_LTUP** désactive la flèche gauche d’une barre de défilement horizontale ou la flèche vers le haut d’une barre de défilement verticale.  
  
- **ESB_DISABLE_RTDN** désactive la flèche droite d’une barre de défilement horizontale ou la flèche vers le bas d’une barre de défilement verticale.  
  
- **ESB_DISABLE_BOTH** désactive les deux flèches d’une barre de défilement.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les flèches sont activés ou désactivés comme spécifié ; Sinon, 0, ce qui indique que les flèches sont déjà présentes dans l’état requis ou qu’une erreur s’est produite.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="getscrollbarinfo"></a>  CScrollBar::GetScrollBarInfo  
 Récupère les informations qui le **SCROLLBARINFO** structure conserve à propos d’une barre de défilement.  
  
```  
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pScrollInfo*  
 Un pointeur vers le [SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787535) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **TRUE** en cas de réussite, **FALSE** en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [SBM_SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787545) d’un message, comme décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo  
 Récupère les informations que la structure `SCROLLINFO` conserve à propos d'une barre de défilement.  
  
```  
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    UINT nMask = SIF_ALL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpScrollInfo`  
 Un pointeur vers un [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) structure. Consultez le Kit de développement logiciel Windows pour plus d’informations sur cette structure.  
  
 `nMask`  
 Spécifie les paramètres de barre de défilement à récupérer. Une utilisation normale, SIF_ALL, spécifie une combinaison de SIF_PAGE, SIF_POS, SIF_TRACKPOS et SIF_RANGE. Consultez `SCROLLINFO` pour plus d’informations sur les valeurs de nMask.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le message récupéré toutes les valeurs, la valeur de retour est **TRUE**. Sinon, il est **FALSE**.  
  
### <a name="remarks"></a>Notes  
 `GetScrollInfo` permet aux applications d’utiliser les positions de défilement de 32 bits.  
  
 Le [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) structure contient des informations sur une barre de défilement, y compris le minimum et le maximum de défilement positions, la taille de page et la position de la case de défilement (curseur de défilement). Consultez le `SCROLLINFO` rubrique structure dans le SDK Windows pour plus d’informations sur la modification des valeurs par défaut des structure.  
  
 Les gestionnaires qui indiquent la position de barre de défilement, de message Windows MFC [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), fournir uniquement 16 bits de données de la position. `GetScrollInfo` et `SetScrollInfo` fournir 32 bits de données de la position de la barre de défilement. Par conséquent, une application peut appeler `GetScrollInfo` lors du traitement soit `CWnd::OnHScroll` ou `CWnd::OnVScroll` pour obtenir des données de position de barre de défilement de 32 bits.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit  
 Récupère la valeur maximale de la barre de défilement la position du défilement.  
  
```  
int GetScrollLimit();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Spécifie la position maximale d’une barre de défilement en cas de réussite ; Sinon, 0.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollpos"></a>  CScrollBar::GetScrollPos  
 Récupère la position actuelle d'une case de défilement.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Spécifie la position actuelle du curseur de défilement en cas de réussite ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La position actuelle est une valeur relative dépend de la plage de défilement actuelle. Par exemple, si la plage de défilement est de 100 à 200 et que la case de défilement est en cours de la barre, la position actuelle est 150.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange  
 Copie les positions actuelles de la barre de défilement minimal et maximal pour la barre de défilement donnée aux emplacements spécifiés par `lpMinPos` et `lpMaxPos`.  
  
```  
void GetScrollRange(
    LPINT lpMinPos,  
    LPINT lpMaxPos) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `lpMinPos`  
 Pointe vers la variable de type entier qui doit recevoir la position minimale.  
  
 `lpMaxPos`  
 Pointe vers la variable de type entier qui doit recevoir la position maximale.  
  
### <a name="remarks"></a>Notes  
 La plage par défaut pour un contrôle de barre de défilement est vide (les deux valeurs sont 0).  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="setscrollinfo"></a>  CScrollBar::SetScrollInfo  
 Définit les informations qui le `SCROLLINFO` structure conserve à propos d’une barre de défilement.  
  
```  
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpScrollInfo`  
 Un pointeur vers un [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) structure.  
  
 `bRedraw`  
 Spécifie si la barre de défilement doit être redessinée pour refléter les nouvelles informations. Si `bRedraw` est **TRUE**, la barre de défilement est redessinée. S’il s’agit **FALSE**, il n’est pas redessiné. Par défaut, la barre de défilement est redessinée.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la réussite, la valeur de retour est **TRUE**. Sinon, il est **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Vous devez fournir les valeurs requises par le `SCROLLINFO` paramètres, y compris les valeurs d’indicateur de la structure.  
  
 Le `SCROLLINFO` structure contient des informations sur une barre de défilement, y compris le minimum et le maximum de défilement positions, la taille de page et la position de la case de défilement (curseur de défilement). Consultez le [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) rubrique structure dans le SDK Windows pour plus d’informations sur la modification des valeurs par défaut des structure.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]  
  
##  <a name="setscrollpos"></a>  CScrollBar::SetScrollPos  
 Définit la position actuelle d’une zone de défilement à celle spécifiée par `nPos` et, si spécifiée, redessine la barre de défilement pour refléter la nouvelle position.  
  
```  
int SetScrollPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `nPos`  
 Spécifie la nouvelle position de la case de défilement. Il doit être dans la plage de défilement.  
  
 `bRedraw`  
 Spécifie si la barre de défilement doit être redessinée pour refléter la nouvelle position. Si `bRedraw` est **TRUE**, la barre de défilement est redessinée. S’il s’agit **FALSE**, il n’est pas redessiné. Par défaut, la barre de défilement est redessinée.  
  
### <a name="return-value"></a>Valeur de retour  
 Spécifie la position précédente de la case de défilement, en cas de réussite ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Définissez `bRedraw` à **FALSE** par un appel ultérieur à une autre fonction pour éviter que la barre de défilement redessinée à deux reprises dans un court intervalle chaque fois que la barre de défilement est redessinée.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="setscrollrange"></a>  CScrollBar::SetScrollRange  
 Définit les valeurs de position minimale et maximale de la barre de défilement donnée.  
  
```  
void SetScrollRange(
    int nMinPos,  
    int nMaxPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `nMinPos`  
 Spécifie la valeur minimale que la position du défilement.  
  
 `nMaxPos`  
 Spécifie la valeur maximale la position du défilement.  
  
 `bRedraw`  
 Spécifie si la barre de défilement doit être redessinée pour refléter la modification. Si `bRedraw` est **TRUE**, la barre de défilement est redessinée ; si **FALSE**, il n’est pas redessiné. Il est redessiné par défaut.  
  
### <a name="remarks"></a>Notes  
 Définissez `nMinPos` et `nMaxPos` sur 0 pour masquer les barres de défilement standard.  
  
 N’appelez pas cette fonction pour masquer une barre de défilement lors du traitement d’un message de notification de barre de défilement.  
  
 Si un appel à `SetScrollRange` suit immédiatement un appel à la `SetScrollPos` fonction membre, définissez `bRedraw` dans `SetScrollPos` à 0 pour empêcher la barre de défilement redessinage à deux reprises.  
  
 La différence entre les valeurs spécifiées par `nMinPos` et `nMaxPos` ne doit pas être supérieure à 32 767. La plage par défaut pour un contrôle de barre de défilement est vide (à la fois `nMinPos` et `nMaxPos` sont 0).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]  
  
##  <a name="showscrollbar"></a>  CScrollBar::ShowScrollBar  
 Affiche ou masque une barre de défilement.  
  
```  
void ShowScrollBar(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bShow`  
 Spécifie si la barre de défilement est affichée ou masquée. Si ce paramètre est **TRUE**, la barre de défilement est affichée ; sinon, il est masqué.  
  
### <a name="remarks"></a>Notes  
 Une application ne doit pas appeler cette fonction pour masquer une barre de défilement lors du traitement d’un message de notification de barre de défilement.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CScrollBar::Create](#create).  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Classe de CButton](../../mfc/reference/cbutton-class.md)   
 [CComboBox (classe)](../../mfc/reference/ccombobox-class.md)   
 [Classe CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (classe)](../../mfc/reference/clistbox-class.md)   
 [Classe de CStatic](../../mfc/reference/cstatic-class.md)   
 [CDialog, classe](../../mfc/reference/cdialog-class.md)
