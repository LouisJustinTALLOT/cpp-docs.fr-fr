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
ms.openlocfilehash: 1ab25ad26357abe9091d273637f3ae9f77457342
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230478"
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
|[CScrollBar :: Create](#create)|Crée la barre de défilement Windows et l’attache à l' `CScrollBar` objet.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Active ou désactive une flèche (ou les deux) d'une barre de défilement.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Récupère des informations sur la barre de défilement à l’aide d’une `SCROLLBARINFO` structure.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Récupère des informations sur la barre de défilement.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Récupère la limite de la barre de défilement|
|[CScrollBar::GetScrollPos](#getscrollpos)|Récupère la position actuelle d'une case de défilement.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Récupère les positions de barre de défilement minimale et maximale actuelles pour la barre de défilement donnée.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Définit les informations sur la barre de défilement.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Définit la position actuelle d’une case de défilement.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Définit les valeurs de position minimale et maximale de la barre de défilement donnée.|
|[CScrollBar :: ShowScrollBar](#showscrollbar)|Affiche ou masque une barre de défilement.|

## <a name="remarks"></a>Notes

Vous créez un contrôle de barre de défilement en deux étapes. Tout d’abord, appelez le constructeur `CScrollBar` pour construire l' `CScrollBar` objet, puis appelez la fonction membre [Create](#create) pour créer le contrôle de barre de défilement Windows et l’attacher à l' `CScrollBar` objet.

Si vous créez un `CScrollBar` objet dans une boîte de dialogue (par le biais d’une ressource de boîte de dialogue), le `CScrollBar` est automatiquement détruit lorsque l’utilisateur ferme la boîte de dialogue.

Si vous créez un `CScrollBar` objet dans une fenêtre, vous devrez peut-être également le détruire.

Si vous créez l' `CScrollBar` objet sur la pile, il est détruit automatiquement. Si vous créez l' `CScrollBar` objet sur le tas à l’aide de la **`new`** fonction, vous devez appeler **`delete`** sur l’objet pour le détruire lorsque l’utilisateur met fin à la barre de défilement Windows.

Si vous allouez de la mémoire dans l' `CScrollBar` objet, substituez le `CScrollBar` destructeur pour supprimer les allocations.

Pour plus d’informations sur l’utilisation de `CScrollBar` , consultez [contrôles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar :: Create

Crée la barre de défilement Windows et l’attache à l' `CScrollBar` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style de la barre de défilement. Applique une combinaison de [styles de barre de défilement](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) à la barre de défilement.

*rectangulaire*<br/>
Spécifie la taille et la position de la barre de défilement. Il peut s’agir d’une `RECT` structure ou d’un `CRect` objet.

*pParentWnd*<br/>
Spécifie la fenêtre parente de la barre de défilement, généralement un `CDialog` objet. Il ne doit pas être NULL.

*nID*<br/>
ID de contrôle de la barre de défilement.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CScrollBar` objet en deux étapes. Tout d’abord, appelez le constructeur, qui construit l' `CScrollBar` objet, puis appelez `Create` , qui crée et initialise la barre de défilement Windows associée et l’attache à l' `CScrollBar` objet.

Appliquez les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à une barre de défilement :

- WS_CHILD toujours

- WS_VISIBLE généralement

- WS_DISABLED rarement

- WS_GROUP des contrôles de groupe

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

*nArrowFlags*<br/>
Spécifie si les flèches de défilement sont activées ou désactivées et quelles flèches sont activées ou désactivées. Ce paramètre peut prendre l’une des valeurs suivantes :

- ESB_ENABLE_BOTH active les deux flèches d’une barre de défilement.

- ESB_DISABLE_LTUP désactive la flèche gauche d’une barre de défilement horizontale ou la flèche vers le haut d’une barre de défilement verticale.

- ESB_DISABLE_RTDN désactive la flèche droite d’une barre de défilement horizontale ou la flèche vers le bas d’une barre de défilement verticale.

- ESB_DISABLE_BOTH désactive les deux flèches d’une barre de défilement.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les flèches sont activées ou désactivées comme spécifié ; Sinon, 0, ce qui indique que les flèches sont déjà dans l’État demandé ou qu’une erreur s’est produite.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CScrollBar :: SetScrollRange](#setscrollrange).

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo

Récupère les informations que la structure `SCROLLBARINFO` conserve à propos d'une barre de défilement.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Paramètres

*pScrollInfo*<br/>
Pointeur vers la structure [SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo) .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités du message [SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo) , comme décrit dans le SDK Windows.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

Récupère les informations que la structure `SCROLLINFO` conserve à propos d'une barre de défilement.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Paramètres

*lpScrollInfo*<br/>
Pointeur vers une structure [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) . Pour plus d’informations sur cette structure, consultez la SDK Windows.

*nMask*<br/>
Spécifie les paramètres de barre de défilement à récupérer. L’utilisation classique, SIF_ALL, spécifie une combinaison de SIF_PAGE, SIF_POS, SIF_TRACKPOS et SIF_RANGE. `SCROLLINFO`Pour plus d’informations sur les valeurs de nMask, consultez.

### <a name="return-value"></a>Valeur de retour

Si le message a récupéré des valeurs, la valeur renvoyée est TRUE. Sinon, la valeur est FALSe.

### <a name="remarks"></a>Notes

`GetScrollInfo`permet aux applications d’utiliser des positions de défilement 32 bits.

La structure [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) contient des informations sur une barre de défilement, y compris les positions minimale et maximale de défilement, la taille de la page et la position de la case de défilement (le curseur de défilement). `SCROLLINFO`Pour plus d’informations sur la modification des valeurs par défaut de la structure, consultez la rubrique structure de la SDK Windows.

Les gestionnaires de messages Windows MFC qui indiquent la position de la barre de défilement, [CWnd :: OnHScroll et [CWnd :: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), fournissent uniquement 16 bits de données de position. `GetScrollInfo`et `SetScrollInfo` fournissent 32 bits de données de position de la barre de défilement. Ainsi, une application peut appeler `GetScrollInfo` lors du traitement `CWnd::OnHScroll` `CWnd::OnVScroll` de ou pour obtenir des données de position de la barre de défilement 32 bits.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd :: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

Récupère la position de défilement maximale de la barre de défilement.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Valeur de retour

Spécifie la position maximale d’une barre de défilement en cas de réussite ; Sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd :: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos

Récupère la position actuelle d'une case de défilement.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valeur de retour

Spécifie la position actuelle de la case de défilement en cas de réussite ; Sinon, 0.

### <a name="remarks"></a>Notes

La position actuelle est une valeur relative qui dépend de la plage de défilement actuelle. Par exemple, si la plage de défilement est comprise entre 100 et 200 et que la case de défilement se trouve au milieu de la barre, la position actuelle est 150.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd :: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange

Copie les positions de barre de défilement minimale et maximale actuelles pour la barre de défilement donnée vers les emplacements spécifiés par *lpMinPos* et *lpMaxPos*.

```cpp
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Paramètres

*lpMinPos*<br/>
Pointe vers la variable de type entier qui doit recevoir la position minimale.

*lpMaxPos*<br/>
Pointe vers la variable de type entier qui doit recevoir la position maximale.

### <a name="remarks"></a>Notes

La plage par défaut d’un contrôle de barre de défilement est vide (les deux valeurs sont 0).

### <a name="example"></a>Exemple

  Consultez l’exemple de [CWnd :: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

Définit les informations que la `SCROLLINFO` structure gère à propos d’une barre de défilement.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpScrollInfo*<br/>
Pointeur vers une structure [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) .

*bRedraw*<br/>
Spécifie si la barre de défilement doit être redessinée pour refléter les nouvelles informations. Si *bRedraw* a la valeur true, la barre de défilement est redessinée. Si la valeur est FALSe, il n’est pas redessiné. Par défaut, la barre de défilement est redessinée.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, la valeur renvoyée est TRUE. Sinon, la valeur est FALSe.

### <a name="remarks"></a>Notes

Vous devez fournir les valeurs requises par les `SCROLLINFO` paramètres de structure, y compris les valeurs d’indicateur.

La `SCROLLINFO` structure contient des informations sur une barre de défilement, y compris les positions minimale et maximale de défilement, la taille de la page et la position de la case de défilement (le curseur de défilement). Pour plus d’informations sur la modification des valeurs par défaut de la structure, consultez la rubrique structure [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos

Définit la position actuelle d’une case de défilement à celle spécifiée par *nPos* et, si elle est spécifiée, redessine la barre de défilement pour refléter la nouvelle position.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Spécifie la nouvelle position de la case de défilement. Elle doit être comprise dans la plage de défilement.

*bRedraw*<br/>
Spécifie si la barre de défilement doit être redessinée pour refléter la nouvelle position. Si *bRedraw* a la valeur true, la barre de défilement est redessinée. Si la valeur est FALSe, il n’est pas redessiné. Par défaut, la barre de défilement est redessinée.

### <a name="return-value"></a>Valeur de retour

Spécifie la position précédente de la case de défilement en cas de réussite ; Sinon, 0.

### <a name="remarks"></a>Notes

Affectez à *bRedraw* la valeur false chaque fois que la barre de défilement sera redessinée par un appel ultérieur à une autre fonction pour éviter que la barre de défilement ne soit redessinée deux fois dans un intervalle bref.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CScrollBar :: SetScrollRange](#setscrollrange).

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange

Définit les valeurs de position minimale et maximale de la barre de défilement donnée.

```cpp
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Paramètres

*nMinPos*<br/>
Spécifie la position de défilement minimale.

*nMaxPos*<br/>
Spécifie la position de défilement maximale.

*bRedraw*<br/>
Spécifie si la barre de défilement doit être redessinée pour refléter la modification. Si *bRedraw* a la valeur true, la barre de défilement est redessinée ; Si la valeur est FALSe, il n’est pas redessiné. Par défaut, il est redessiné.

### <a name="remarks"></a>Notes

Affectez à *nMinPos* et à *nMaxPos* la valeur 0 pour masquer les barres de défilement standard.

N’appelez pas cette fonction pour masquer une barre de défilement lors du traitement d’un message de notification de barre de défilement.

Si un appel à `SetScrollRange` suit immédiatement un appel à la `SetScrollPos` fonction membre, affectez la valeur *bRedraw* `SetScrollPos` 0 à bRedraw pour empêcher que la barre de défilement ne soit redessinée deux fois.

La différence entre les valeurs spécifiées par *nMinPos* et *nMaxPos* ne doit pas être supérieure à 32 767. La plage par défaut d’un contrôle de barre de défilement est vide (les *nMinPos* et *nMaxPos* sont 0).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar :: ShowScrollBar

Affiche ou masque une barre de défilement.

```cpp
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
Spécifie si la barre de défilement est affichée ou masquée. Si ce paramètre a la valeur TRUE, la barre de défilement est affichée ; dans le cas contraire, elle est masquée.

### <a name="remarks"></a>Notes

Une application ne doit pas appeler cette fonction pour masquer une barre de défilement lors du traitement d’un message de notification de barre de défilement.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CScrollBar :: Create](#create).

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CButton, classe](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox (classe)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)<br/>
[CListBox, classe](../../mfc/reference/clistbox-class.md)<br/>
[CStatic, classe](../../mfc/reference/cstatic-class.md)<br/>
[CDialog (classe)](../../mfc/reference/cdialog-class.md)
