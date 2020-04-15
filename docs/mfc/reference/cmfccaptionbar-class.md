---
title: CMFCCaptionBar, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: 3a1e8890176fe686b54fe4756dfd578869cbcdfb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367794"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar, classe

Un `CMFCCaptionBar` objet est une barre de contrôle qui peut afficher trois éléments : un bouton, une étiquette de texte et une bitmap. Elle ne peut afficher qu'un élément de chaque type à la fois. Vous pouvez aligner chaque élément sur le bord gauche ou droit du contrôle ou le centrer. Vous pouvez également appliquer un style 2D ou 3D aux bordures supérieure et inférieure de la barre de légende.

## <a name="syntax"></a>Syntaxe

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCCaptionBar::Créer](#create)|Crée le contrôle de la barre `CMFCCaptionBar` de légende et l’attache à l’objet.|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Indique si un autre volet peut être inséré dynamiquement entre la barre de légende et son cadre parent. (Overrides [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCCaptionBar::EnableButton](#enablebutton)|Permet ou désactive le bouton sur la barre de légende.|
|[CMFCCaptionBar::GetAlignment](#getalignment)|Retourne l’alignement de l’élément spécifié.|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Retourne la taille de la bordure de la barre de légende.|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Récupère le rectangle de délimitation du bouton sur la barre de légende.|
|[CMFCCaptionBar::GetMargin](#getmargin)|Retourne la distance entre le bord des éléments de barre de légende et le bord du contrôle de la barre de légende.|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Précise si la barre de légende est en mode barre de message.|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Supprime l’image de bitmap de la barre de légende.|
|[CMFCCaptionBar::RemoveButton](#removebutton)|Supprime le bouton de la barre de légende.|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Retire l’icône de la barre de légende.|
|[CMFCCaptionBar::SupprimerText](#removetext)|Supprime l’étiquette de texte de la barre de légende.|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Définit l’image de bitmap pour la barre de légende.|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Définit la taille de la bordure de la barre de légende.|
|[CMFCCaptionBar::SetButton](#setbutton)|Définit le bouton pour la barre de légende.|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Précise si le bouton reste pressé.|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Définit la pointe d’outils pour le bouton.|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Définit le style frontière de la barre de légende.|
|[CMFCCaptionBar::SetIcon](#seticon)|Définit l’icône pour une barre de légende.|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Définit la pointe d’outil pour l’image pour la barre de légende.|
|[CMFCCaptionBar::SetMargin](#setmargin)|Définit la distance entre le bord de l’élément de barre de légende et le bord du contrôle de la barre de légende.|
|[CMFCCaptionBar::SetText](#settext)|Définit l’étiquette de texte pour la barre de légende.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Appelé par le cadre pour remplir l’arrière-plan de la barre de légende.|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Appelé par le cadre pour dessiner la frontière de la barre de légende.|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Appelé par le cadre pour dessiner le bouton de barre de légende.|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Appelé par le cadre pour dessiner l’image de la barre de légende.|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Appelé par le cadre pour dessiner le texte de la barre de légende.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCCaptionBar:m_clrBarBackground](#m_clrbarbackground)|La couleur de fond de la barre de légende.|
|[CMFCCaptionBar:m_clrBarBorder](#m_clrbarborder)|La couleur de la bordure de la barre de légende.|
|[CMFCCaptionBar:m_clrBarText](#m_clrbartext)|La couleur du texte de la barre de légende.|

## <a name="remarks"></a>Notes

Pour créer une barre de légende, suivez ces étapes :

1. Construisez `CMFCCaptionBar` l’objet. En règle générale, vous ajoutez la barre de légende à un cours de fenêtre de cadre.

1. Appelez le [CMFCCaptionBar: :Créer](#create) la méthode pour créer `CMFCCaptionBar` le contrôle de la barre de légende et l’attacher à l’objet.

1. Appelez [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon), et [CMFCCaptionBar::SetBitmap](#setbitmap) pour définir les éléments de barre de légende.

Lorsque vous définissez l’élément bouton, vous devez affecter un IDENTIFIANT de commande au bouton. Lorsque l’utilisateur clique sur le bouton, la barre de légende achemine les WM_COMMAND les messages qui ont cet ID à la fenêtre du cadre parent.

La barre de légende peut également fonctionner en mode barre de message, ce qui imite la barre de message qui apparaît dans les applications Microsoft Office 2007. En mode barre de message, la barre de légende affiche un bitmap, un message et un bouton (qui ouvre généralement une boîte de dialogue.) Vous pouvez attribuer un tooltip à la bitmap.

Pour activer le mode barre de message, appelez [CMFCCaptionBar ::Créer](#create) et définir le quatrième paramètre (bIsMessageBarMode) à TRUE.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCCaptionBar` . L’exemple montre comment créer le contrôle de la barre de légende, définir une bordure 3D de la barre de légende, régler la distance, en pixels, entre le bord des éléments de barre de légende et le bord du contrôle de la barre de légende, régler le bouton pour la barre de légende, définir l’outil pour le bouton, définir l’étiquette de texte pour la barre de légende, définir l’image de bitmap pour la barre de légende , et définissez l’outil pour l’image dans la barre de légende. Cet extrait de code fait partie de [l’échantillon de démonstration ms Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxcaptionbar.h

## <a name="cmfccaptionbarcreate"></a><a name="create"></a>CMFCCaptionBar::Créer

Crée le contrôle de la barre `CMFCCaptionBar` de légende et l’attache à l’objet.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
La combinaison logique ou de la légende des styles de barre.

*pParentWnd*<br/>
La fenêtre parente du contrôle de barre de légende.

*Uid*<br/>
L’ID du contrôle de barre de légende.

*nHeight (en)*<br/>
La hauteur, en pixels, du contrôle de la barre de légende. S’il est de -1, la hauteur est calculée en fonction de la hauteur de l’icône, du texte et du bouton que la barre de légende affiche.

*bIsMessageBarMode (en)*<br/>
VRAI si la barre de légende est en mode barre de message; FALSE autrement.

### <a name="return-value"></a>Valeur de retour

VRAI si le contrôle de barre de légende est créé avec succès ; FALSE autrement.

### <a name="remarks"></a>Notes

Vous construisez un `CMFCCaptionBar` objet en deux étapes. D’abord vous appelez le constructeur, `Create` puis vous appelez la méthode, qui `CMFCCaptionBar` crée le contrôle Windows et l’attache à l’objet.

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCCaptionBar::DoesAllowDynInsertBefore

Indique si un autre volet peut être inséré dynamiquement entre la barre de légende et son cadre parent.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne FALSE à moins d’être dépassé.

### <a name="remarks"></a>Notes

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a>CMFCCaptionBar::EnableButton

Permet ou désactive le bouton sur la barre de légende.

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour activer le bouton, FALSE pour désactiver le bouton.

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a>CMFCCaptionBar::GetAlignment

Retourne l’alignement de l’élément spécifié.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>Paramètres

*Elem*<br/>
[dans] Un élément de barre de légende pour lequel récupérer l’alignement.

### <a name="return-value"></a>Valeur de retour

L’alignement d’un élément, tel qu’un bouton, une bitmap, du texte ou une icône.

### <a name="remarks"></a>Notes

L’alignement de l’élément peut être l’une des valeurs suivantes :

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a>CMFCCaptionBar::GetBorderSize

Retourne la taille de la bordure de la barre de légende.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille, en pixels, de la frontière.

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a>CMFCCaptionBar::GetButtonRect

Récupère le rectangle de délimitation du bouton sur la barre de légende.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>Valeur de retour

Un `CRect` objet qui contient les coordonnées du rectangle de délimitation du bouton sur la barre de légende.

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a>CMFCCaptionBar::GetMargin

Retourne la distance entre le bord des éléments de barre de légende et le bord du contrôle de la barre de légende.

```
int GetMargin() const;
```

### <a name="return-value"></a>Valeur de retour

La distance, en pixels, entre le bord des éléments de barre de légende et le bord du contrôle de la barre de légende.

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a>CMFCCaptionBar::IsMessageBarMode

Précise si la barre de légende est en mode barre de message.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la barre de légende est en mode barre de message; FALSE autrement.

### <a name="remarks"></a>Notes

En mode barre de message, la barre de légende affiche une image avec un tooltip, un texte de message et un bouton.

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a>CMFCCaptionBar:m_clrBarBackground

La couleur de fond de la barre de légende.

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a>CMFCCaptionBar:m_clrBarBorder

La couleur de la bordure de la barre de légende.

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a>CMFCCaptionBar:m_clrBarText

La couleur du texte de la barre de légende.

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a>CMFCCaptionBar::OnDrawBackground

Appelé par le cadre pour remplir l’arrière-plan de la barre de légende.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur sur le contexte de l’appareil de la barre de légende.

*Rect*<br/>
[dans] Le rectangle de délimitation à remplir.

### <a name="remarks"></a>Notes

La `OnDrawBackground` méthode est appelée lorsque l’arrière-plan de la barre de légende est sur le point d’être rempli. L’implémentation par défaut remplit l’arrière-plan en utilisant le [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) couleur.

Remplacer cette méthode `CMFCCaptionBar` dans une classe dérivée pour personnaliser l’apparence de la barre de légende.

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a>CMFCCaptionBar::OnDrawBorder

Appelé par le cadre pour dessiner la frontière de la barre de légende.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un contexte d’appareil qui est utilisé pour afficher les frontières.

*Rect*<br/>
[dans] Le rectangle de délimitation.

### <a name="remarks"></a>Notes

Par défaut, les frontières ont le style plat.

Remplacer cette méthode `CMFCCaptionBar` dans une classe dérivée pour personnaliser l’apparence des bordures de la barre de légende.

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a>CMFCCaptionBar::OnDrawButton

Appelé par le cadre pour dessiner le bouton de barre de légende.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil qui est utilisé pour afficher le bouton.

*Rect*<br/>
[dans] Le rectangle de délimitation du bouton.

*strButton (en)*<br/>
[dans] L’étiquette de texte du bouton.

*bEnabled*<br/>
[dans] VRAI si le bouton est activé; FALSE autrement.

### <a name="remarks"></a>Notes

Remplacer cette méthode `CMFCCaptionBar` dans une classe dérivée pour personnaliser l’apparence du bouton de la barre de légende.

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a>CMFCCaptionBar::OnDrawImage

Appelé par le cadre pour dessiner l’image de la barre de légende.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil qui est utilisé pour afficher l’image.

*Rect*<br/>
[dans] Spécifie le rectangle de délimitation de l’image.

### <a name="remarks"></a>Notes

Remplacer cette méthode `CMFCCaptionBar` dans une classe dérivée pour personnaliser l’apparence de l’image.

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a>CMFCCaptionBar::OnDrawText

Appelé par le cadre pour dessiner le texte de la barre de légende.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil qui est utilisé pour afficher le bouton.

*Rect*<br/>
[dans] Le rectangle de délimitation du texte.

*strText (en)*<br/>
[dans] La chaîne de texte à afficher.

### <a name="remarks"></a>Notes

L’implémentation par `CDC::DrawText` défaut affiche le texte à l’aide et [CMFCCaptionBar:m_clrBarText](#m_clrbartext) couleur.

Remplacer cette méthode `CMFCCaptionBar` dans une classe dérivée pour personnaliser l’apparence du texte de la barre de légende.

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a>CMFCCaptionBar::RemoveBitmap

Supprime l’image de bitmap de la barre de légende.

```
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a>CMFCCaptionBar::RemoveButton

Supprime le bouton de la barre de légende.

```
void RemoveButton();
```

### <a name="remarks"></a>Notes

La disposition des éléments de barre de légende est ajustée automatiquement.

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a>CMFCCaptionBar::RemoveIcon

Retire l’icône de la barre de légende.

```
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a>CMFCCaptionBar::SupprimerText

Supprime l’étiquette de texte de la barre de légende.

```
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a>CMFCCaptionBar::SetBitmap

Définit l’image de bitmap pour la barre de légende.

```
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Paramètres

*hBitmap (en)*<br/>
[dans] La poignée à la bitmap à régler.

*clrTransparent*<br/>
[dans] Une valeur RGB qui spécifie la couleur transparente de la bitmap.

*bStretch*<br/>
[dans] Si VRAI, le bitmap est étiré s’il ne s’adapte pas au rectangle de délimitation de l’image. Sinon, la bitmap n’est pas étirée.

*bmpAlignement*<br/>
[dans] L’alignement de la bitmap.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour régler un bitmap sur une barre de légende.

Le bitmap précédent est détruit automatiquement. Si la barre de légende affiche une icône parce que vous avez appelé le [CMFCCaptionBar::SetIcon](#seticon) méthode, le bitmap ne sera pas affiché à moins que vous supprimez l’icône en appelant [CMFCCaptionBar::RemoveIcon](#removeicon).

Le bitmap est aligné comme spécifié par le paramètre *bmpAlignment.*  Ce paramètre peut avoir l'une des valeurs `BarElementAlignment` suivantes :

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a>CMFCCaptionBar::SetBorderSize

Définit la taille de la bordure de la barre de légende.

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize (en)*<br/>
[dans] La nouvelle taille, en pixels, de la frontière de la barre de légende.

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a>CMFCCaptionBar::SetButton

Définit le bouton pour la barre de légende.

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
L’étiquette de commande du bouton.

*uiCmdUI*<br/>
L’ID de commande du bouton.

*btnAlignmnet*<br/>
L’alignement du bouton.

*bHasDropDownArrow (en anglais seulement)*<br/>
VRAI si le bouton affiche une flèche de chute vers le bas, FALSE autrement.

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a>CMFCCaptionBar::SetButtonPressed

Précise si le bouton reste pressé.

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>Paramètres

*bPrésed*<br/>
VRAI si le bouton garde son état pressé, FALSE autrement.

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a>CMFCCaptionBar::SetButtonToolTip

Définit la pointe d’outils pour le bouton.

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszToolTip*<br/>
[dans] La légende de l’outiltip.

*lpszDescription*<br/>
[dans] La description de l’outiltip.

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a>CMFCCaptionBar::SetFlatBorder

Définit le style frontière de la barre de légende.

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Paramètres

*bFlat (en)*<br/>
[dans] VRAI si la bordure d’une barre de légende est plate. FALSE si la frontière est 3D.

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a>CMFCCaptionBar::SetIcon

Définit l’icône pour une barre de légende.

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Paramètres

*hIcon (en)*<br/>
[dans] Le manche à l’icône à régler.

*iconAlignment*<br/>
[dans] L’alignement de l’icône.

### <a name="remarks"></a>Notes

Les barres de légende peuvent afficher des icônes ou des bitmaps. Voir [CMFCCaptionBar:SetBitmap](#setbitmap) pour savoir comment afficher un bitmap. Si vous définissez à la fois une icône et une bitmap, l’icône est toujours affichée. Appelez [CMFCCaptionBar::RemoveIcon](#removeicon) pour supprimer une icône de la barre de légende.

L’icône est alignée selon le *paramètre iconalignement.* Il peut s’agir `BarElementAlignment` de l’une des valeurs suivantes :

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a>CMFCCaptionBar::SetImageToolTip

Définit la pointe d’outil pour l’image dans la barre de légende.

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszToolTip*<br/>
[dans] Le texte de l’outiltip.

*lpszDescription*<br/>
[dans] La description de l’outiltip.

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a>CMFCCaptionBar::SetMargin

Définit la distance entre le bord de l’élément de barre de légende et le bord du contrôle de la barre de légende.

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>Paramètres

*nMargin (en)*<br/>
[dans] La distance, en pixels, entre le bord des éléments de barre de légende et le bord du contrôle de la barre de légende.

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a>CMFCCaptionBar::SetText

Définit l’étiquette de texte pour la barre de légende.

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Paramètres

*strText (en)*<br/>
[dans] La chaîne de texte à régler.

*texteAlignation*<br/>
[dans] L’alignement du texte.

### <a name="remarks"></a>Notes

L’étiquette de texte est alignée comme spécifié par le *paramètre textalignment.* Il peut s’agir `BarElementAlignment` de l’une des valeurs suivantes :

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
