---
title: CScrollBar, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 761d7e9db650c6d95e916c85bd7456d9b1c647c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318530"
---
# <a name="cscrollbar-class"></a>CScrollBar, classe

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
|[CScrollBar::Créer](#create)|Crée la barre de défilement `CScrollBar` Windows et la fixe à l’objet.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Active ou désactive une flèche (ou les deux) d'une barre de défilement.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Récupère des informations sur la `SCROLLBARINFO` barre de défilement à l’aide d’une structure.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Récupère des informations sur la barre de défilement.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Récupère la limite de la barre de défilement|
|[CScrollBar::GetScrollPos](#getscrollpos)|Récupère la position actuelle d'une case de défilement.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Récupère les positions minimales et maximales de barre de défilement pour la barre de défilement donnée.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Définit les informations sur la barre de défilement.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Définit la position actuelle d’une boîte de défilement.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Définit les valeurs de position minimale et maximale de la barre de défilement donnée.|
|[CScrollBar::ShowScrollBar](#showscrollbar)|Affiche ou cache une barre de défilement.|

## <a name="remarks"></a>Notes

Vous créez un contrôle de barre de défilement en deux étapes. Tout d’abord, `CScrollBar` appelez `CScrollBar` le constructeur pour construire l’objet, puis appelez la fonction `CScrollBar` membre [Create](#create) pour créer le contrôle de la barre de défilement Windows et l’attacher à l’objet.

Si vous `CScrollBar` créez un objet dans une boîte de `CScrollBar` dialogue (via une ressource de dialogue), le est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous `CScrollBar` créez un objet à l’intérieur d’une fenêtre, vous devrez peut-être aussi le détruire.

Si vous `CScrollBar` créez l’objet sur la pile, il est détruit automatiquement. Si vous `CScrollBar` créez l’objet sur le tas en utilisant la **nouvelle** fonction, vous devez appeler **supprimer** sur l’objet pour le détruire lorsque l’utilisateur met fin à la barre de défilement Windows.

Si vous allouez `CScrollBar` de la mémoire `CScrollBar` dans l’objet, remplacez le destructeur pour disposer des allocations.

Pour obtenir des `CScrollBar`informations connexes sur l’utilisation , voir [Contrôles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar::Créer

Crée la barre de défilement `CScrollBar` Windows et la fixe à l’objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style de la barre de défilement. Appliquez n’importe quelle combinaison de styles de [barre de défilement](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) à la barre de défilement.

*Rect*<br/>
Spécifie la taille et la position de la barre de défilement. Peut être `RECT` soit une `CRect` structure ou un objet.

*pParentWnd*<br/>
Spécifie la fenêtre parente `CDialog` de la barre de défilement, habituellement un objet. Ce ne doit pas être NULL.

*nID*<br/>
L’ID de commande de la barre de défilement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CScrollBar` objet en deux étapes. Tout d’abord, appelez le `CScrollBar` constructeur, qui construit l’objet; puis `Create`appelez , qui crée et initialise la barre de `CScrollBar` défilement Windows associée et la fixe à l’objet.

Appliquer les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants sur une barre de défilement :

- WS_CHILD toujours

- WS_VISIBLE Habituellement

- WS_DISABLED Rarement

- WS_GROUP Pour les contrôles de groupe

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar::CScrollBar

Construit un objet `CScrollBar`.

```
CScrollBar();
```

### <a name="remarks"></a>Notes

Après avoir construit l’objet, appelez la `Create` fonction membre pour créer et initialiser la barre de défilement Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

Active ou désactive une flèche (ou les deux) d'une barre de défilement.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Paramètres

*nArrowFlags (en)*<br/>
Précise si les flèches de défilement sont activées ou désactivées et quelles flèches sont activées ou désactivées. Ce paramètre peut être l’une des valeurs suivantes :

- ESB_ENABLE_BOTH Permet les deux flèches d’une barre de défilement.

- ESB_DISABLE_LTUP désactive la flèche gauche d’une barre de défilement horizontal ou la flèche vers le haut d’une barre de défilement vertical.

- ESB_DISABLE_RTDN désactive la flèche droite d’une barre de défilement horizontal ou la flèche vers le bas d’une barre de défilement vertical.

- ESB_DISABLE_BOTH désactive les deux flèches d’une barre de défilement.

### <a name="return-value"></a>Valeur de retour

Nonzero si les flèches sont activées ou désactivées comme spécifié; autrement 0, ce qui indique que les flèches sont déjà dans l’état demandé ou qu’une erreur s’est produite.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CScrollBar:SetScrollRange](#setscrollrange).

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo

Récupère les informations que la structure `SCROLLBARINFO` conserve à propos d'une barre de défilement.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Paramètres

*pScrollInfo (en anglais)*<br/>
Un pointeur à la structure [SCROLLBARINFO.](/windows/win32/api/winuser/ns-winuser-scrollbarinfo)

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité du [message SBM_SCROLLBARINFO,](/windows/win32/Controls/sbm-getscrollbarinfo) tel que décrit dans le SDK Windows.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

Récupère les informations que la structure `SCROLLINFO` conserve à propos d'une barre de défilement.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Paramètres

*lpScrollInfo*<br/>
Un pointeur vers une structure [SCROLLINFO.](/windows/win32/api/winuser/ns-winuser-scrollinfo) Consultez le Windows SDK pour plus d’informations sur cette structure.

*nMask (nMask)*<br/>
Spécifie les paramètres de la barre de défilement à récupérer. L’utilisation typique, SIF_ALL, spécifie une combinaison de SIF_PAGE, de SIF_POS, de SIF_TRACKPOS et de SIF_RANGE. Voir `SCROLLINFO` pour plus d’informations sur les valeurs nMask.

### <a name="return-value"></a>Valeur de retour

Si le message a récupéré des valeurs, le retour est VRAI. Sinon, c’est FALSE.

### <a name="remarks"></a>Notes

`GetScrollInfo`permet aux applications d’utiliser des positions de défilement 32 bits.

La structure [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) contient des informations sur une barre de défilement, y compris les positions de défilement minimales et maximales, la taille de la page et la position de la boîte de défilement (le pouce). Consultez `SCROLLINFO` le sujet de la structure dans le SDK Windows pour plus d’informations sur la modification de la structure par défaut.

Les gestionnaires de messages MFC Windows qui indiquent la position de la barre de défilement, [CWnd::OnHScroll, et [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), fournissent seulement 16 bits de données de position. `GetScrollInfo`et `SetScrollInfo` fournir 32 bits de données de position de barre de défilement. Ainsi, une application `GetScrollInfo` peut `CWnd::OnHScroll` appeler `CWnd::OnVScroll` pendant le traitement ou pour obtenir des données de position de barre de défilement 32 bits.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

Récupère la position de défilement maximale de la barre de défilement.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Valeur de retour

Spécifie la position maximale d’une barre de défilement en cas de succès; sinon 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos

Récupère la position actuelle d'une case de défilement.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valeur de retour

Spécifie la position actuelle de la boîte de parchemin en cas de succès; sinon 0.

### <a name="remarks"></a>Notes

La position actuelle est une valeur relative qui dépend de la plage de défilement actuelle. Par exemple, si la plage de défilement est de 100 à 200 et que la boîte de défilement est au milieu de la barre, la position actuelle est de 150.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange

Copie les positions minimales et maximales de barre de défilement pour la barre de défilement donnée aux *emplacements spécifiés par lpMinPos* et *lpMaxPos*.

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Paramètres

*lpMinPos (en)*<br/>
Indique la variable d’intégrerie qui doit recevoir la position minimale.

*lpMaxPos (en)*<br/>
Indique la variable d’intégrerie qui doit recevoir la position maximale.

### <a name="remarks"></a>Notes

La plage par défaut pour un contrôle de barre de défilement est vide (les deux valeurs sont 0).

### <a name="example"></a>Exemple

  Voir l’exemple pour [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

Définit les informations `SCROLLINFO` que la structure maintient sur une barre de défilement.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpScrollInfo*<br/>
Un pointeur vers une structure [SCROLLINFO.](/windows/win32/api/winuser/ns-winuser-scrollinfo)

*bRedraw (en)*<br/>
Précise si la barre de défilement doit être redessinée pour refléter les nouvelles informations. Si *bRedraw* est VRAI, la barre de défilement est redessinée. S’il s’agit de FALSE, il n’est pas redessiné. La barre de défilement est redessinée par défaut.

### <a name="return-value"></a>Valeur de retour

En cas de succès, le retour est VRAI. Sinon, c’est FALSE.

### <a name="remarks"></a>Notes

Vous devez fournir les `SCROLLINFO` valeurs requises par les paramètres de la structure, y compris les valeurs du drapeau.

La `SCROLLINFO` structure contient des informations sur une barre de défilement, y compris les positions de défilement minimum et maximum, la taille de la page et la position de la boîte de défilement (le pouce). Consultez le sujet de la structure [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) dans le SDK Windows pour plus d’informations sur la modification des défauts de la structure.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos

Définit la position actuelle d’une boîte de défilement à celle spécifiée par *nPos* et, si spécifié, redessine la barre de défilement pour refléter la nouvelle position.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Spécifie la nouvelle position pour la boîte de défilement. Il doit être dans la plage de défilement.

*bRedraw (en)*<br/>
Précise si la barre de défilement doit être redessinée pour refléter la nouvelle position. Si *bRedraw* est VRAI, la barre de défilement est redessinée. S’il s’agit de FALSE, il n’est pas redessiné. La barre de défilement est redessinée par défaut.

### <a name="return-value"></a>Valeur de retour

Spécifie la position précédente de la boîte de parchemin en cas de succès; sinon 0.

### <a name="remarks"></a>Notes

Définissez *bRedraw* à FALSE chaque fois que la barre de défilement sera redessinée par un appel ultérieur à une autre fonction pour éviter que la barre de défilement redessinée deux fois dans un court intervalle.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CScrollBar:SetScrollRange](#setscrollrange).

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange

Définit les valeurs de position minimale et maximale de la barre de défilement donnée.

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*nMinPos (en)*<br/>
Spécifie la position de défilement minimum.

*nMaxPos (en)*<br/>
Spécifie la position de défilement maximale.

*bRedraw (en)*<br/>
Précise si la barre de défilement doit être redessinée pour refléter le changement. Si *bRedraw* est VRAI, la barre de défilement est redessinée; si FALSE, il n’est pas redessiné. Il est redessiné par défaut.

### <a name="remarks"></a>Notes

Définissez *nMinPos* et *nMaxPos* à 0 pour masquer les barres de défilement standard.

N’appelez pas cette fonction pour masquer une barre de défilement pendant le traitement d’un message de notification scroll-bar.

Si un `SetScrollRange` appel pour suivre `SetScrollPos` immédiatement un appel à la `SetScrollPos` fonction membre, définissez *bRedraw* à 0 pour empêcher la barre de défilement d’être redessinée deux fois.

La différence entre les valeurs spécifiées par *nMinPos* et *nMaxPos* ne doit pas être supérieure à 32 767. La plage par défaut pour un contrôle de barre de défilement est vide *(nMinPos* et *nMaxPos* sont 0).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar::ShowScrollBar

Affiche ou cache une barre de défilement.

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
Précise si la barre de défilement est affichée ou cachée. Si ce paramètre est VRAI, la barre de défilement est affichée; sinon il est caché.

### <a name="remarks"></a>Notes

Une application ne doit pas appeler cette fonction pour masquer une barre de défilement pendant le traitement d’un message de notification scroll-bar.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CScrollBar::Créer](#create).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Classe CButton](../../mfc/reference/cbutton-class.md)<br/>
[Classe CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[Classe CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)
