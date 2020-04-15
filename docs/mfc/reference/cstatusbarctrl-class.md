---
title: CStatusBarCtrl, classe
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
ms.openlocfilehash: 7a594fdb2d3a35ce905b7790026f7418b7435f3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366032"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl, classe

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
|[CStatusBarCtrl::Créer](#create)|Crée un contrôle de barre d’état et l’attache à un `CStatusBarCtrl` objet.|
|[CStatusBarCtrl::CreateEx](#createex)|Crée un contrôle de barre d’état avec les `CStatusBarCtrl` styles Windows étendus spécifiés et l’attache à un objet.|
|[CStatusBarCtrl::DrawItem](#drawitem)|Appelé lorsqu’un aspect visuel d’un contrôle de barre d’état propriétaire-tirage change.|
|[CStatusBarCtrl::GetBorders](#getborders)|Récupère les largeurs actuelles des bordures horizontales et verticales d’un contrôle de barre d’état.|
|[CStatusBarCtrl::GetIcon](#geticon)|Récupère l’icône pour une pièce (également connue sous le nom de volet) dans le contrôle actuel de la barre d’état.|
|[CStatusBarCtrl::GetParts](#getparts)|Récupère un compte des pièces dans un contrôle de barre d’état.|
|[CStatusBarCtrl::GetRect](#getrect)|Récupère le rectangle de délimitation d’une pièce dans un contrôle de barre d’état.|
|[CStatusBarCtrl::GetText](#gettext)|Récupère le texte de la partie donnée d’un contrôle de barre d’état.|
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Récupérez la longueur, en caractères, du texte de la partie donnée d’un contrôle de barre d’état.|
|[CStatusBarCtrl::GetTipText](#gettiptext)|Récupère le texte de la pointe d’outils pour une vitre dans une barre d’état.|
|[CStatusBarCtrl::IsSimple](#issimple)|Vérifie un contrôle de fenêtre d’état pour déterminer si elle est en mode simple.|
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Définit la couleur de fond dans une barre d’état.|
|[CStatusBarCtrl::SetIcon](#seticon)|Définit l’icône pour une vitre dans une barre d’état.|
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Définit la hauteur minimale de la zone de dessin d’un contrôle de barre d’état.|
|[CStatusBarCtrl::SetParts](#setparts)|Définit le nombre de pièces dans un contrôle de barre d’état et la coordonnées du bord droit de chaque pièce.|
|[CStatusBarCtrl::SetSimple](#setsimple)|Précise si un contrôle de barre d’état affiche un texte `SetParts`simple ou affiche toutes les parties de contrôle définies par un appel précédent à .|
|[CStatusBarCtrl::SetText](#settext)|Définit le texte dans la partie spécifiée d'un contrôle de barre d'état.|
|[CStatusBarCtrl::SetTipText](#settiptext)|Définit le texte de pointe d’outil pour une vitre dans une barre d’état.|

## <a name="remarks"></a>Notes

Un « contrôle de barre d’état » est une fenêtre horizontale, généralement affichée au bas d’une fenêtre parente, dans laquelle une application peut afficher divers types d’informations d’état. Le contrôle de barre d’état peut être divisé en pièces pour afficher plus d’un type d’information.

Ce contrôle (et `CStatusBarCtrl` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT version 3.51 et plus tard.

Pour plus d’informations sur l’utilisation `CStatusBarCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation de [CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a>CStatusBarCtrl::Créer

Crée un contrôle de barre d’état et l’attache à un `CStatusBarCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du contrôle de la barre d’état. Appliquez toute combinaison de styles de contrôle des barres d’état répertoriés dans [les styles de contrôle commun](/windows/win32/Controls/common-control-styles) dans le SDK Windows. Ce paramètre doit inclure le style WS_CHILD. Il devrait également inclure le style WS_VISIBLE.

*Rect*<br/>
Spécifie la taille et la position du contrôle de la barre d’état. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Spécifie la fenêtre parente du `CDialog`contrôle de la barre d’état, généralement un . Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de la barre d’état.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Vous construisez un `CStatusBarCtrl` en deux étapes. Tout d’abord, appelez le `Create`constructeur, puis appelez , ce qui `CStatusBarCtrl` crée le contrôle de barre d’état et le fixe à l’objet.

La position par défaut d’une fenêtre de statut est le long du bas de la fenêtre parente, mais vous pouvez spécifier le style CCS_TOP pour qu’il apparaisse en haut de la zone client de la fenêtre mère. Vous pouvez spécifier le style SBARS_SIZEGRIP pour inclure une poignée de dimensionnement à l’extrémité droite de la fenêtre d’état. La combinaison des styles CCS_TOP et SBARS_SIZEGRIP n’est pas recommandée, car l’adhérence qui en résulte n’est pas fonctionnelle même si le système l’attire dans la fenêtre d’état.

Pour créer une barre de statut avec des styles de fenêtre étendue, appelez [CStatusBarCtrl::CreateEx](#createex) au lieu de `Create`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a>CStatusBarCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CStatusBarCtrl` et l’associe à l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle (en anglais)*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour une liste de styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

*dwStyle (en)*<br/>
Spécifie le style du contrôle de la barre d’état. Appliquez toute combinaison de styles de contrôle des barres d’état répertoriés dans [les styles de contrôle commun](/windows/win32/Controls/common-control-styles) dans le SDK Windows. Ce paramètre doit inclure le style WS_CHILD. Il devrait également inclure le style WS_VISIBLE.

*Rect*<br/>
Une référence à une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl

Construit un objet `CStatusBarCtrl`.

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl::DrawItem

Appelé par le cadre quand un aspect visuel d’un contrôle de barre d’état propriétaire-tirage change.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Paramètres

*lpDrawItemStruct*<br/>
Un long pointeur vers une structure [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) qui contient des informations sur le type de dessin requis.

### <a name="remarks"></a>Notes

Le `itemAction` membre `DRAWITEMSTRUCT` de la structure définit l’action de dessin qui doit être effectuée.

Par défaut, cette fonction de membre ne fait rien. Remplacer cette fonction de membre pour implémenter le dessin d’un objet de dessin du `CStatusBarCtrl` propriétaire.

L’application doit restaurer tous les objets d’interface graphique (GDI) sélectionnés pour le contexte d’affichage fourni dans *lpDrawItemStruct* avant la fin de cette fonction de membre.

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a>CStatusBarCtrl::GetBorders

Récupère les largeurs actuelles du contrôle de la barre d’état des bordures horizontales et verticales et de l’espace entre les rectangles.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Paramètres

*pBorders (en)*<br/>
Adresse d’un tableau d’un tout-en-un ayant trois éléments. Le premier élément reçoit la largeur de la bordure horizontale, le second reçoit la largeur de la bordure verticale, et le troisième reçoit la largeur de la bordure entre les rectangles.

*nHorz (en)*<br/>
Référence à un intégrant qui reçoit la largeur de la bordure horizontale.

*nVert (en)*<br/>
Référence à un intégrant qui reçoit la largeur de la bordure verticale.

*nSpacing (en)*<br/>
Référence à un intégrant qui reçoit la largeur de la bordure entre les rectangles.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Ces bordures déterminent l’espacement entre le bord extérieur du contrôle et les rectangles dans le contrôle qui contiennent du texte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a>CStatusBarCtrl::GetIcon

Récupère l’icône pour une pièce (également connue sous le nom de volet) dans le contrôle actuel de la barre d’état.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*iPart (en)*|[dans] L’index zéro de la pièce qui contient l’icône à récupérer. Si ce paramètre est de -1, la barre d’état est supposée être une barre de statut simple mode.|

### <a name="return-value"></a>Valeur de retour

Le manche à l’icône si la méthode a réussi; autrement, NULL.

### <a name="remarks"></a>Notes

Cette méthode envoie le [message SB_GETICON,](/windows/win32/Controls/sb-geticon) qui est décrit dans le SDK Windows.

Un contrôle de barre d’état se compose d’une rangée de volets de sortie de texte, qui sont également connus sous le nom de pièces. Pour plus d’informations sur la barre d’état, voir [La mise en œuvre de la barre d’état dans MFC](../../mfc/status-bar-implementation-in-mfc.md) et [le réglage du mode d’un objet CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Exemple

L’exemple de code suivant `m_statusBar`définit une variable, qui est utilisée pour accéder au contrôle actuel de barre d’état. Cette variable est utilisée dans l'exemple suivant.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant copie une icône à deux volets du contrôle actuel de barre d’état. Dans une section antérieure de l’exemple de code, nous avons créé un contrôle de barre de statut avec trois volets, puis ajouté une icône à la première vitre. Cet exemple récupère l’icône du premier volet, puis l’ajoute au deuxième et troisième volet.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarCtrl::GetParts

Récupère un compte des pièces dans un contrôle de barre d’état.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Paramètres

*nParts (en)*<br/>
Nombre de pièces pour lesquelles récupérer les coordonnées. Si ce paramètre est supérieur au nombre de pièces dans le contrôle, le message récupère les coordonnées pour les pièces existantes seulement.

*pParts (en)*<br/>
Adresse d’un tableau d’un élément ayant le même nombre d’éléments que le nombre de pièces spécifiées par *les Parties n.* Chaque élément du tableau reçoit la coordonnées du client du bord droit de la pièce correspondante. Si un élément est réglé à - 1, la position du bord droit pour cette partie s’étend au bord droit de la barre d’état.

### <a name="return-value"></a>Valeur de retour

Le nombre de pièces dans le contrôle en cas de succès, ou zéro autrement.

### <a name="remarks"></a>Notes

Cette fonction de membre récupère également la coordonnées du bord droit du nombre donné de pièces.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarCtrl::GetRect

Récupère le rectangle de délimitation d’une pièce dans un contrôle de barre d’état.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
Indice à base zéro de la pièce dont le rectangle de délimitation doit être récupéré.

*lpRect*<br/>
Adresse d’une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) qui reçoit le rectangle de délimitation.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a>CStatusBarCtrl::GetText

Récupère le texte de la partie donnée d’un contrôle de barre d’état.

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
Adresse du tampon qui reçoit le texte. Ce paramètre est une chaîne non terminée.

*nPane*<br/>
Index à base zéro de la pièce à partir de laquelle récupérer le texte.

*pType (en)*<br/>
Pointeur vers un intégreur qui reçoit les informations de type. Le type peut être l’une de ces valeurs :

- **0** Le texte est dessiné avec une bordure pour apparaître plus bas que le plan de la barre d’état.

- SBT_NOBORDERS Le texte est tiré sans frontières.

- SBT_POPOUT Le texte est dessiné avec une bordure pour apparaître plus haut que le plan de la barre d’état.

- SBT_OWNERDRAW Si le texte a le type de dessin SBT_OWNERDRAW, *pType* reçoit ce message et renvoie la valeur 32 bits associée au texte au lieu de la longueur et le type de fonctionnement.

### <a name="return-value"></a>Valeur de retour

La longueur, en caractères, du texte ou [d’un CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le texte actuel.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStatusBarCtrl::GetTextLength

Récupère la longueur, en caractères, du texte de la partie donnée d’un contrôle de barre d’état.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
Index à base zéro de la pièce à partir de laquelle récupérer le texte.

*pType (en)*<br/>
Pointeur vers un intégreur qui reçoit les informations de type. Le type peut être l’une de ces valeurs :

- **0** Le texte est dessiné avec une bordure pour apparaître plus bas que le plan de la barre d’état.

- SBT_NOBORDERS Le texte est tiré sans frontières.

- SBT_OWNERDRAW Le texte est dessiné par la fenêtre parente.

- SBT_POPOUT Le texte est dessiné avec une bordure pour apparaître plus haut que le plan de la barre d’état.

### <a name="return-value"></a>Valeur de retour

La longueur, en caractères, du texte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>CStatusBarCtrl::GetTipText

Récupère le texte de la pointe d’outils pour une vitre dans une barre d’état.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
L’index à base de zéro du volet de barre d’état pour recevoir le texte de bout d’outil.

### <a name="return-value"></a>Valeur de retour

Un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenant le texte à utiliser dans l’outiltip.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a>CStatusBarCtrl::IsSimple

Vérifie un contrôle de fenêtre d’état pour déterminer si elle est en mode simple.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le contrôle de la fenêtre d’état est en mode simple; autrement zéro.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple), tel que décrit dans le SDK Windows.

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor

Définit la couleur de fond dans une barre d’état.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Paramètres

*Cr*<br/>
Valeur COLORREF qui spécifie la nouvelle couleur de fond. Spécifiez la valeur CLR_DEFAULT pour faire en sorte que la barre d’état utilise sa couleur de fond par défaut.

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) qui représente la couleur de fond par défaut précédente.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a>CStatusBarCtrl::SetIcon

Définit l’icône pour une vitre dans une barre d’état.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
L’index zéro de la vitre qui recevra l’icône. Si ce paramètre est de -1, la barre d’état est supposée être une barre de statut simple.

*hIcon (en)*<br/>
Manipuler à l’icône à définir. Si cette valeur est NULL, l’icône est supprimée de la pièce.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [SB_SETICON](/windows/win32/Controls/sb-seticon), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CStatusBarCtrl:SetBkColor](#setbkcolor).

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarCtrl::SetMinHeight

Définit la hauteur minimale de la zone de dessin d’un contrôle de barre d’état.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
Hauteur minimale, en pixels, du contrôle.

### <a name="remarks"></a>Notes

La hauteur minimale est la somme de *nMin* et deux fois la largeur, en pixels, de la bordure verticale du contrôle de barre d’état.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a>CStatusBarCtrl::SetParts

Définit le nombre de pièces dans un contrôle de barre d’état et la coordonnées du bord droit de chaque pièce.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Paramètres

*nParts (en)*<br/>
Nombre de pièces à définir. Le nombre de pièces ne peut pas être supérieur à 255.

*pWidths (pWidths)*<br/>
Adresse d’un tableau d’un élément ayant le même nombre d’éléments que les pièces spécifiées par *les Parties n.* Chaque élément du tableau spécifie la position, dans les coordonnées du client, du bord droit de la pièce correspondante. Si un élément est - 1, la position du bord droit pour cette partie s’étend au bord droit du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStatusBarCtrl::SetSimple

Précise si un contrôle de barre d’état affiche un texte simple ou affiche toutes les parties de contrôle définies par un appel précédent à [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSimple (en)*<br/>
[dans] Drapeau de type affichage. Si ce paramètre est VRAI, le contrôle affiche un texte simple; s’il est FALSE, il affiche plusieurs pièces.

### <a name="return-value"></a>Valeur de retour

Retourne toujours 0.

### <a name="remarks"></a>Notes

Si votre application modifie le contrôle de la barre d’état de non-simple à simple, ou vice versa, le système redessine immédiatement le contrôle.

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a>CStatusBarCtrl::SetText

Définit le texte dans la partie spécifiée d'un contrôle de barre d'état.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
Adresse d'une chaîne se terminant par null spécifiant le texte à définir. Si *nType* est SBT_OWNERDRAW, *lpszText* représente 32 bits de données.

*nPane*<br/>
Index de base zéro de la partie à définir. Si cette valeur est égale à 255, le contrôle de barre d'état est considéré comme un simple contrôle constitué d'une seule partie.

*nType*<br/>
Type d'opération de dessin. Consultez [SB_SETTEXT message](/windows/win32/Controls/sb-settext) pour une liste de valeurs possibles.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; sinon, zéro.

### <a name="remarks"></a>Notes

Le message invalide la partie du contrôle qui a changé, ce qui l’amène à afficher le nouveau texte lorsque le contrôle suivant reçoit le message WM_PAINT.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a>CStatusBarCtrl::SetTipText

Définit le texte de pointe d’outil pour une vitre dans une barre d’état.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Paramètres

*nPane*<br/>
L’index à base de zéro du volet de barre d’état pour recevoir le texte de bout d’outil.

*pszTipText*<br/>
Un pointeur à une chaîne contenant le texte de bout d’outil.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext), tel que décrit dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl, classe](../../mfc/reference/ctoolbarctrl-class.md)
