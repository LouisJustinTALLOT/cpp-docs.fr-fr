---
title: CStatusBarCtrl (classe)
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 8c33aa4d77eeeeca69e50dc63982ff4d7e8bd505
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502319"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl (classe)

Fournit les fonctionnalités du contrôle commun de barre d'état Windows.

## <a name="syntax"></a>Syntaxe

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Construit un objet `CStatusBarCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStatusBarCtrl::Create](#create)|Crée un contrôle de barre d’État et l’attache à `CStatusBarCtrl` un objet.|
|[CStatusBarCtrl::CreateEx](#createex)|Crée un contrôle de barre d’État avec les styles étendus Windows spécifiés et l' `CStatusBarCtrl` attache à un objet.|
|[CStatusBarCtrl::DrawItem](#drawitem)|Appelé en cas de modification de l’aspect visuel d’un contrôle de barre d’État owner-draw.|
|[CStatusBarCtrl::GetBorders](#getborders)|Récupère les largeurs actuelles des bordures horizontale et verticale d’un contrôle de barre d’État.|
|[CStatusBarCtrl::GetIcon](#geticon)|Récupère l’icône d’un composant (également appelé volet) dans le contrôle de barre d’état actuel.|
|[CStatusBarCtrl::GetParts](#getparts)|Récupère le nombre de parties dans un contrôle de barre d’État.|
|[CStatusBarCtrl::GetRect](#getrect)|Récupère le rectangle englobant d’un composant dans un contrôle de barre d’État.|
|[CStatusBarCtrl::GetText](#gettext)|Récupère le texte à partir de la partie donnée d’un contrôle de barre d’État.|
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Récupère la longueur, en caractères, du texte à partir de la partie donnée d’un contrôle de barre d’État.|
|[CStatusBarCtrl::GetTipText](#gettiptext)|Récupère le texte d’info-bulle d’un volet dans une barre d’État.|
|[CStatusBarCtrl::IsSimple](#issimple)|Vérifie un contrôle de fenêtre d’État pour déterminer s’il est en mode simple.|
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan dans une barre d’État.|
|[CStatusBarCtrl::SetIcon](#seticon)|Définit l’icône d’un volet dans une barre d’État.|
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Définit la hauteur minimale de la zone de dessin d’un contrôle de barre d’État.|
|[CStatusBarCtrl::SetParts](#setparts)|Définit le nombre de parties dans un contrôle de barre d’État et la coordonnée du bord droit de chaque partie.|
|[CStatusBarCtrl::SetSimple](#setsimple)|Spécifie si un contrôle de barre d’état affiche du texte simple ou toutes les parties de contrôle définies `SetParts`par un appel précédent à.|
|[CStatusBarCtrl::SetText](#settext)|Définit le texte dans la partie spécifiée d'un contrôle de barre d'état.|
|[CStatusBarCtrl::SetTipText](#settiptext)|Définit le texte d’info-bulle d’un volet dans une barre d’État.|

## <a name="remarks"></a>Notes

Un « contrôle de barre d’État » est une fenêtre horizontale, généralement affichée en bas d’une fenêtre parente, dans laquelle une application peut afficher différents types d’informations d’État. Le contrôle de barre d’État peut être divisé en parties pour afficher plusieurs types d’informations.

Ce contrôle (et par conséquent `CStatusBarCtrl` la classe) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT version 3,51 et versions ultérieures.

Pour plus d’informations sur `CStatusBarCtrl`l’utilisation de, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="create"></a>  CStatusBarCtrl::Create

Crée un contrôle de barre d’État et l’attache à `CStatusBarCtrl` un objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle de barre d’État. Appliquez n’importe quelle combinaison de styles de contrôle de barre d’État listés dans les [styles de contrôle communs](/windows/win32/Controls/common-control-styles) de la SDK Windows. Ce paramètre doit inclure le style WS_CHILD. Il doit également inclure le style WS_VISIBLE.

*rect*<br/>
Spécifie la taille et la position du contrôle de barre d’État. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle de barre d' `CDialog`État, généralement. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de barre d’État.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Vous construisez `CStatusBarCtrl` un en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`appelez, qui crée le contrôle de barre d’État et l’attache `CStatusBarCtrl` à l’objet.

La position par défaut d’une fenêtre d’État se trouve en bas de la fenêtre parente, mais vous pouvez spécifier le style CCS_TOP pour qu’il apparaisse en haut de la zone cliente de la fenêtre parente. Vous pouvez spécifier le style SBARS_SIZEGRIP pour inclure une poignée de dimensionnement à l’extrémité droite de la fenêtre d’État. La combinaison des styles CCS_TOP et SBARS_SIZEGRIP n’est pas recommandée, car la poignée de redimensionnement résultante n’est pas fonctionnelle même si le système la dessine dans la fenêtre d’État.

Pour créer une barre d’État avec des styles de fenêtre étendus, appelez [CStatusBarCtrl :: CreateEx](#createex) au lieu de `Create`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

##  <a name="createex"></a>  CStatusBarCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à `CStatusBarCtrl` l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle de barre d’État. Appliquez n’importe quelle combinaison de styles de contrôle de barre d’État listés dans les [styles de contrôle communs](/windows/win32/Controls/common-control-styles) de la SDK Windows. Ce paramètre doit inclure le style WS_CHILD. Il doit également inclure le style WS_VISIBLE.

*rect*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [Create](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_** .

##  <a name="cstatusbarctrl"></a>  CStatusBarCtrl::CStatusBarCtrl

Construit un objet `CStatusBarCtrl`.

```
CStatusBarCtrl();
```

##  <a name="drawitem"></a>  CStatusBarCtrl::DrawItem

Appelée par l’infrastructure quand un aspect visuel d’un contrôle de barre d’État owner-draw change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Pointeur long vers une structure [drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` membre de la `DRAWITEMSTRUCT` structure définit l’action de dessin à effectuer.

Par défaut, cette fonction membre ne fait rien. Substituez cette fonction membre pour implémenter le dessin pour un objet `CStatusBarCtrl` owner-draw.

L’application doit restaurer tous les objets GDI (Graphics Device Interface) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction membre.

##  <a name="getborders"></a>  CStatusBarCtrl::GetBorders

Récupère les largeurs actuelles du contrôle de barre d’état des bordures horizontale et verticale et de l’espace entre les rectangles.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Paramètres

*pBorders*<br/>
Adresse d’un tableau d’entiers ayant trois éléments. Le premier élément reçoit la largeur de la bordure horizontale, le deuxième reçoit la largeur de la bordure verticale et le troisième reçoit la largeur de la bordure entre les rectangles.

*nHorz*<br/>
Référence à un entier qui reçoit la largeur de la bordure horizontale.

*nVert*<br/>
Référence à un entier qui reçoit la largeur de la bordure verticale.

*nSpacing*<br/>
Référence à un entier qui reçoit la largeur de la bordure entre les rectangles.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Ces bordures déterminent l’espacement entre le bord extérieur du contrôle et les rectangles dans le contrôle qui contiennent du texte.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

##  <a name="geticon"></a>  CStatusBarCtrl::GetIcon

Récupère l’icône d’un composant (également appelé volet) dans le contrôle de barre d’état actuel.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iPart*|dans Index de base zéro du composant qui contient l’icône à récupérer. Si ce paramètre a la valeur-1, la barre d’État est supposée être une barre d’état de mode simple.|

### <a name="return-value"></a>Valeur de retour

Handle de l’icône si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

Cette méthode envoie le message [SB_GETICON](/windows/win32/Controls/sb-geticon) , qui est décrit dans le SDK Windows.

Un contrôle de barre d’État se compose d’une ligne de volets de sortie de texte, également appelés parties. Pour plus d’informations sur la barre d’État, consultez Implémentation de la [barre d’État dans MFC](../../mfc/status-bar-implementation-in-mfc.md) et [définition du mode d’un objet CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Exemples

L’exemple de code suivant définit une variable `m_statusBar`,, qui est utilisée pour accéder au contrôle de barre d’état actuel. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant copie une icône vers deux volets du contrôle de barre d’état actuel. Dans une section précédente de l’exemple de code, nous avons créé un contrôle de barre d’État avec trois volets, puis ajouté une icône au premier volet. Cet exemple récupère l’icône du premier volet, puis l’ajoute au deuxième et au troisième volet.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

##  <a name="getparts"></a>  CStatusBarCtrl::GetParts

Récupère le nombre de parties dans un contrôle de barre d’État.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Paramètres

*nParts*<br/>
Nombre de parties pour lesquelles récupérer les coordonnées. Si ce paramètre est supérieur au nombre de parties dans le contrôle, le message récupère les coordonnées des parties existantes uniquement.

*pParts*<br/>
Adresse d’un tableau d’entiers ayant le même nombre d’éléments que le nombre de parties spécifié par *nParts*. Chaque élément du tableau reçoit la coordonnée cliente du bord droit du composant correspondant. Si un élément a la valeur-1, la position du bord droit de cette partie s’étend jusqu’au bord droit de la barre d’État.

### <a name="return-value"></a>Valeur de retour

Nombre de parties dans le contrôle en cas de réussite, ou zéro dans le cas contraire.

### <a name="remarks"></a>Notes

Cette fonction membre récupère également la coordonnée du bord droit du nombre donné de parties.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

##  <a name="getrect"></a>  CStatusBarCtrl::GetRect

Récupère le rectangle englobant d’un composant dans un contrôle de barre d’État.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
Index de base zéro du composant dont le rectangle englobant doit être récupéré.

*lpRect*<br/>
Adresse d’une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) qui reçoit le rectangle englobant.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

##  <a name="gettext"></a>  CStatusBarCtrl::GetText

Récupère le texte à partir de la partie donnée d’un contrôle de barre d’État.

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Adresse de la mémoire tampon qui reçoit le texte. Ce paramètre est une chaîne terminée par le caractère null.

*nPane*<br/>
Index de base zéro du composant à partir duquel récupérer du texte.

*pType*<br/>
Pointeur vers un entier qui reçoit les informations de type. Le type peut prendre l’une des valeurs suivantes :

- **0** le texte est dessiné avec une bordure qui doit apparaître en dessous du plan de la barre d’État.

- SBT_NOBORDERS le texte est dessiné sans bordures.

- SBT_POPOUT le texte est dessiné avec une bordure qui doit apparaître plus haut que le plan de la barre d’État.

- SBT_OWNERDRAW si le texte a le type de dessin SBT_OWNERDRAW, *PTYPE* reçoit ce message et retourne la valeur 32 bits associée au texte au lieu de la longueur et du type d’opération.

### <a name="return-value"></a>Valeur de retour

Longueur, en caractères, du texte ou d’un [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le texte actuel.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

##  <a name="gettextlength"></a>  CStatusBarCtrl::GetTextLength

Récupère la longueur, en caractères, du texte à partir de la partie donnée d’un contrôle de barre d’État.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
Index de base zéro du composant à partir duquel récupérer du texte.

*pType*<br/>
Pointeur vers un entier qui reçoit les informations de type. Le type peut prendre l’une des valeurs suivantes :

- **0** le texte est dessiné avec une bordure qui doit apparaître en dessous du plan de la barre d’État.

- SBT_NOBORDERS le texte est dessiné sans bordures.

- SBT_OWNERDRAW le texte est dessiné par la fenêtre parente.

- SBT_POPOUT le texte est dessiné avec une bordure qui doit apparaître plus haut que le plan de la barre d’État.

### <a name="return-value"></a>Valeur de retour

Longueur, en caractères, du texte.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

##  <a name="gettiptext"></a>  CStatusBarCtrl::GetTipText

Récupère le texte d’info-bulle d’un volet dans une barre d’État.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
Index de base zéro du volet de la barre d’État pour recevoir le texte d’info-bulle.

### <a name="return-value"></a>Valeur de retour

Objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le texte à utiliser dans l’info-bulle.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)de message Win32, comme décrit dans la SDK Windows.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

##  <a name="issimple"></a>  CStatusBarCtrl::IsSimple

Vérifie un contrôle de fenêtre d’État pour déterminer s’il est en mode simple.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le contrôle de fenêtre d’État est en mode simple ; Sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)de message Win32, comme décrit dans la SDK Windows.

##  <a name="setbkcolor"></a>  CStatusBarCtrl::SetBkColor

Définit la couleur d’arrière-plan dans une barre d’État.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Paramètres

*cr*<br/>
Valeur COLORREF qui spécifie la nouvelle couleur d’arrière-plan. Spécifiez la valeur CLR_DEFAULT pour faire en sorte que la barre d’État utilise sa couleur d’arrière-plan par défaut.

### <a name="return-value"></a>Valeur de retour

Valeur [COLORREF](/windows/win32/gdi/colorref) qui représente la couleur d’arrière-plan par défaut précédente.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor)de message Win32, comme décrit dans la SDK Windows.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

##  <a name="seticon"></a>  CStatusBarCtrl::SetIcon

Définit l’icône d’un volet dans une barre d’État.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
Index de base zéro du volet qui doit recevoir l’icône. Si ce paramètre a la valeur-1, la barre d’État est supposée être une barre d’état simple.

*hIcon*<br/>
Handle de l’icône à définir. Si cette valeur est NULL, l’icône est supprimée de la partie.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [SB_SETICON](/windows/win32/Controls/sb-seticon)de message Win32, comme décrit dans la SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CStatusBarCtrl :: SetBkColor](#setbkcolor).

##  <a name="setminheight"></a>  CStatusBarCtrl::SetMinHeight

Définit la hauteur minimale de la zone de dessin d’un contrôle de barre d’État.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
Hauteur minimale, en pixels, du contrôle.

### <a name="remarks"></a>Notes

La hauteur minimale est la somme de *nMin* et deux fois la largeur, en pixels, de la bordure verticale du contrôle de barre d’État.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

##  <a name="setparts"></a>  CStatusBarCtrl::SetParts

Définit le nombre de parties dans un contrôle de barre d’État et la coordonnée du bord droit de chaque partie.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Paramètres

*nParts*<br/>
Nombre de parties à définir. Le nombre de parties ne peut pas être supérieur à 255.

*pWidths*<br/>
Adresse d’un tableau d’entiers ayant le même nombre d’éléments que les éléments spécifiés par *nParts*. Chaque élément du tableau spécifie la position, en coordonnées clientes, du bord droit du composant correspondant. Si un élément est-1, la position du bord droit de cette partie s’étend jusqu’au bord droit du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

##  <a name="setsimple"></a>  CStatusBarCtrl::SetSimple

Spécifie si un contrôle de barre d’état affiche du texte simple ou affiche toutes les parties de contrôle définies par un appel précédent à [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSimple*<br/>
dans Indicateur de type d’affichage. Si ce paramètre a la valeur TRUE, le contrôle affiche du texte simple ; Si la valeur est FALSe, elle affiche plusieurs parties.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 0.

### <a name="remarks"></a>Notes

Si votre application fait passer le contrôle de barre d’état de la valeur non simple à simple, ou vice versa, le système redessine immédiatement le contrôle.

##  <a name="settext"></a>  CStatusBarCtrl::SetText

Définit le texte dans la partie spécifiée d'un contrôle de barre d'état.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Adresse d'une chaîne se terminant par null spécifiant le texte à définir. Si *ndéclarations* est SBT_OWNERDRAW, *lpszText* représente 32 bits de données.

*nPane*<br/>
Index de base zéro de la partie à définir. Si cette valeur est égale à 255, le contrôle de barre d'état est considéré comme un simple contrôle constitué d'une seule partie.

*nType*<br/>
Type d'opération de dessin. Pour obtenir la liste des valeurs possibles, consultez [message SB_SETTEXT](/windows/win32/Controls/sb-settext) .

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Le message invalide la partie du contrôle qui a changé, provoquant l’affichage du nouveau texte lorsque le contrôle reçoit ensuite le message WM_PAINT.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

##  <a name="settiptext"></a>  CStatusBarCtrl::SetTipText

Définit le texte d’info-bulle d’un volet dans une barre d’État.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
Index de base zéro du volet de la barre d’État pour recevoir le texte d’info-bulle.

*pszTipText*<br/>
Pointeur vers une chaîne contenant le texte d’info-bulle.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)de message Win32, comme décrit dans la SDK Windows.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl, classe](../../mfc/reference/ctoolbarctrl-class.md)
