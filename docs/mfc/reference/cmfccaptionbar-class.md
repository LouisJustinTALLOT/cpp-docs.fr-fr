---
description: 'En savoir plus sur : classe CMFCCaptionBar,'
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
ms.openlocfilehash: a5dd5f968c52268935b6176115e8723a9d82e8a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327733"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar, classe

Un `CMFCCaptionBar` objet est une barre de contrôle qui peut afficher trois éléments : un bouton, une étiquette de texte et une bitmap. Elle ne peut afficher qu'un élément de chaque type à la fois. Vous pouvez aligner chaque élément sur le bord gauche ou droit du contrôle ou le centrer. Vous pouvez également appliquer un style 2D ou 3D aux bordures supérieure et inférieure de la barre de légende.

## <a name="syntax"></a>Syntaxe

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCCaptionBar, :: Create](#create)|Crée le contrôle de barre de légende et l’attache à l' `CMFCCaptionBar` objet.|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Indique si un autre volet peut être inséré dynamiquement entre la barre de légende et son frame parent. (Substitue [CBasePane ::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCCaptionBar, :: EnableButton](#enablebutton)|Active ou désactive le bouton dans la barre de légende.|
|[CMFCCaptionBar, :: GetAlignment](#getalignment)|Retourne l’alignement de l’élément spécifié.|
|[CMFCCaptionBar, :: GetBorderSize](#getbordersize)|Retourne la taille de bordure de la barre de légende.|
|[CMFCCaptionBar, :: GetButtonRect](#getbuttonrect)|Récupère le rectangle englobant du bouton sur la barre de légende.|
|[CMFCCaptionBar, :: GetMargin](#getmargin)|Retourne la distance entre le bord des éléments de barre de légende et le bord du contrôle de barre de légende.|
|[CMFCCaptionBar, :: IsMessageBarMode](#ismessagebarmode)|Spécifie si la barre de légende est en mode barre de message.|
|[CMFCCaptionBar, :: RemoveBitmap](#removebitmap)|Supprime l’image bitmap de la barre de légende.|
|[CMFCCaptionBar, :: RemoveButton](#removebutton)|Supprime le bouton de la barre de légende.|
|[CMFCCaptionBar, :: RemoveIcon](#removeicon)|Supprime l’icône de la barre de légende.|
|[CMFCCaptionBar, :: RemoveText](#removetext)|Supprime l’étiquette de texte de la barre de légende.|
|[CMFCCaptionBar, :: SetBitmap](#setbitmap)|Définit l’image bitmap pour la barre de légende.|
|[CMFCCaptionBar, :: SetBorderSize](#setbordersize)|Définit la taille de la bordure de la barre de légende.|
|[CMFCCaptionBar, :: SetButton](#setbutton)|Définit le bouton pour la barre de légende.|
|[CMFCCaptionBar, :: SetButtonPressed](#setbuttonpressed)|Spécifie si le bouton reste enfoncé.|
|[CMFCCaptionBar, :: SetButtonToolTip](#setbuttontooltip)|Définit l’info-bulle pour le bouton.|
|[CMFCCaptionBar, :: SetFlatBorder](#setflatborder)|Définit le style de bordure de la barre de légende.|
|[CMFCCaptionBar, :: SetIcon](#seticon)|Définit l’icône pour une barre de légende.|
|[CMFCCaptionBar, :: SetImageToolTip](#setimagetooltip)|Définit l’info-bulle de l’image pour la barre de légende.|
|[CMFCCaptionBar, :: SetMargin](#setmargin)|Définit la distance entre le bord de l’élément de barre de légende et le bord du contrôle de barre de légende.|
|[CMFCCaptionBar, :: SetText](#settext)|Définit l’étiquette de texte de la barre de légende.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCCaptionBar, :: OnDrawBackground](#ondrawbackground)|Appelé par l’infrastructure pour remplir l’arrière-plan de la barre de légende.|
|[CMFCCaptionBar, :: OnDrawBorder](#ondrawborder)|Appelé par l’infrastructure pour dessiner la bordure de la barre de légende.|
|[CMFCCaptionBar, :: OnDrawButton](#ondrawbutton)|Appelé par l’infrastructure pour dessiner le bouton de barre de légende.|
|[CMFCCaptionBar, :: OnDrawImage](#ondrawimage)|Appelé par l’infrastructure pour dessiner l’image de la barre de légende.|
|[CMFCCaptionBar, :: OnDrawText](#ondrawtext)|Appelé par l’infrastructure pour dessiner le texte de la barre de légende.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCCaptionBar, :: m_clrBarBackground](#m_clrbarbackground)|Couleur d’arrière-plan de la barre de légende.|
|[CMFCCaptionBar, :: m_clrBarBorder](#m_clrbarborder)|Couleur de la bordure de la barre de légende.|
|[CMFCCaptionBar, :: m_clrBarText](#m_clrbartext)|Couleur du texte de la barre de légende.|

## <a name="remarks"></a>Notes

Pour créer une barre de légende, procédez comme suit :

1. Construisez l' `CMFCCaptionBar` objet. En règle générale, vous ajoutez la barre de légende à une classe de fenêtre frame.

1. Appelez la méthode [CMFCCaptionBar, :: Create](#create) pour créer le contrôle de barre de légende et l’attacher à l' `CMFCCaptionBar` objet.

1. Appelez [CMFCCaptionBar, :: SetButton](#setbutton), [CMFCCaptionBar, :: SetText](#settext), [CMFCCaptionBar, :: seticon](#seticon)et [CMFCCaptionBar, :: SetBitmap](#setbitmap) pour définir les éléments de barre de légende.

Lorsque vous définissez l’élément Button, vous devez assigner un ID de commande au bouton. Quand l’utilisateur clique sur le bouton, la barre de légende achemine le WM_COMMAND messages ayant cet ID vers la fenêtre frame parente.

La barre de légende peut également fonctionner en mode barre des messages, qui émule la barre des messages qui apparaît dans les applications Microsoft Office 2007. En mode barre de message, la barre de légende affiche une image bitmap, un message et un bouton (qui ouvre généralement une boîte de dialogue). Vous pouvez affecter une info-bulle à l’image bitmap.

Pour activer le mode de barre de messages, appelez [CMFCCaptionBar, :: Create](#create) et définissez le quatrième paramètre (bIsMessageBarMode) sur true.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser différentes méthodes de la classe `CMFCCaptionBar` . L’exemple montre comment créer le contrôle de barre de légende, définir une bordure 3D de la barre de légende, définir la distance, en pixels, entre le bord des éléments de la barre de légende et le bord du contrôle de barre de légende, définir le bouton pour la barre de légende, définir l’info-bulle pour le bouton, définir l’étiquette de texte pour la barre de légende et définissez l’info-bulle de l’image dans la barre de légende. Cet extrait de code fait partie de l' [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

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

**En-tête :** afxcaptionbar. h

## <a name="cmfccaptionbarcreate"></a><a name="create"></a> CMFCCaptionBar, :: Create

Crée le contrôle de barre de légende et l’attache à l' `CMFCCaptionBar` objet.

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Combinaison logique ou de styles de barre de légende.

*pParentWnd*<br/>
Fenêtre parente du contrôle de barre de légende.

*Codé*<br/>
ID du contrôle de barre de légende.

*nHeight*<br/>
Hauteur, en pixels, du contrôle de barre de légende. Si la valeur est-1, la hauteur est calculée en fonction de la hauteur de l’icône, du texte et du bouton affiché par le contrôle de barre de légende.

*bIsMessageBarMode*<br/>
TRUE si la barre de légende est en mode barre de messages ; FALSe dans le cas contraire.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le contrôle de barre de légende est correctement créé ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Vous construisez un `CMFCCaptionBar` objet en deux étapes. Tout d’abord, vous appelez le constructeur, puis vous appelez la `Create` méthode, qui crée le contrôle Windows et l’attache à l' `CMFCCaptionBar` objet.

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CMFCCaptionBar, ::D oesAllowDynInsertBefore

Indique si un autre volet peut être inséré dynamiquement entre la barre de légende et son frame parent.

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur FALSe sauf si elle est substituée.

### <a name="remarks"></a>Notes

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a> CMFCCaptionBar, :: EnableButton

Active ou désactive le bouton dans la barre de légende.

```cpp
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour activer le bouton, FALSe pour désactiver le bouton.

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a> CMFCCaptionBar, :: GetAlignment

Retourne l’alignement de l’élément spécifié.

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>Paramètres

*elem*<br/>
dans Élément de barre de légende dont l’alignement doit être récupéré.

### <a name="return-value"></a>Valeur renvoyée

Alignement d’un élément, tel qu’un bouton, une image bitmap, du texte ou une icône.

### <a name="remarks"></a>Notes

L’alignement de l’élément peut prendre l’une des valeurs suivantes :

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a> CMFCCaptionBar, :: GetBorderSize

Retourne la taille de bordure de la barre de légende.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille, en pixels, de la bordure.

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a> CMFCCaptionBar, :: GetButtonRect

Récupère le rectangle englobant du bouton sur la barre de légende.

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>Valeur renvoyée

`CRect`Objet qui contient les coordonnées du rectangle englobant du bouton sur la barre de légende.

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a> CMFCCaptionBar, :: GetMargin

Retourne la distance entre le bord des éléments de barre de légende et le bord du contrôle de barre de légende.

```
int GetMargin() const;
```

### <a name="return-value"></a>Valeur renvoyée

Distance, en pixels, entre le bord des éléments de barre de légende et le bord du contrôle de barre de légende.

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a> CMFCCaptionBar, :: IsMessageBarMode

Spécifie si la barre de légende est en mode barre de message.

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la barre de légende est en mode barre de messages ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Dans le mode de la barre de message, la barre de légende affiche une image avec une info-bulle, un texte de message et un bouton.

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a> CMFCCaptionBar, :: m_clrBarBackground

Couleur d’arrière-plan de la barre de légende.

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a> CMFCCaptionBar, :: m_clrBarBorder

Couleur de la bordure de la barre de légende.

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a> CMFCCaptionBar, :: m_clrBarText

Couleur du texte de la barre de légende.

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a> CMFCCaptionBar, :: OnDrawBackground

Appelé par l’infrastructure pour remplir l’arrière-plan de la barre de légende.

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers le contexte de périphérique de la barre de légende.

*rectangulaire*<br/>
dans Rectangle englobant à remplir.

### <a name="remarks"></a>Notes

La `OnDrawBackground` méthode est appelée lorsque l’arrière-plan de la barre de légende va être rempli. L’implémentation par défaut remplit l’arrière-plan à l’aide de la couleur [CMFCCaptionBar, :: m_clrBarBackground](#m_clrbarbackground) .

Substituez cette méthode dans une `CMFCCaptionBar` classe dérivée pour personnaliser l’apparence de la barre de légende.

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a> CMFCCaptionBar, :: OnDrawBorder

Appelé par l’infrastructure pour dessiner la bordure de la barre de légende.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Contexte de périphérique (Device Context) qui est utilisé pour afficher les bordures.

*rectangulaire*<br/>
dans Rectangle englobant.

### <a name="remarks"></a>Notes

Par défaut, les bordures ont le style à deux dimensions.

Substituez cette méthode dans une `CMFCCaptionBar` classe dérivée pour personnaliser l’apparence des bordures de la barre de légende.

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a> CMFCCaptionBar, :: OnDrawButton

Appelé par l’infrastructure pour dessiner le bouton de barre de légende.

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique qui est utilisé pour afficher le bouton.

*rectangulaire*<br/>
dans Rectangle englobant du bouton.

*strButton*<br/>
dans Étiquette de texte du bouton.

*bEnabled*<br/>
dans TRUE si le bouton est activé ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une `CMFCCaptionBar` classe dérivée pour personnaliser l’apparence du bouton de la barre de légende.

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a> CMFCCaptionBar, :: OnDrawImage

Appelé par l’infrastructure pour dessiner l’image de la barre de légende.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context) utilisé pour afficher l’image.

*rectangulaire*<br/>
dans Spécifie le rectangle englobant de l’image.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une `CMFCCaptionBar` classe dérivée pour personnaliser l’apparence de l’image.

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a> CMFCCaptionBar, :: OnDrawText

Appelé par l’infrastructure pour dessiner le texte de la barre de légende.

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique qui est utilisé pour afficher le bouton.

*rectangulaire*<br/>
dans Rectangle englobant du texte.

*strText*<br/>
dans Chaîne de texte à afficher.

### <a name="remarks"></a>Notes

L’implémentation par défaut affiche le texte à l’aide `CDC::DrawText` de et de [CMFCCaptionBar, :: m_clrBarText](#m_clrbartext) couleur.

Substituez cette méthode dans une `CMFCCaptionBar` classe dérivée pour personnaliser l’apparence du texte de la barre de légende.

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a> CMFCCaptionBar, :: RemoveBitmap

Supprime l’image bitmap de la barre de légende.

```cpp
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a> CMFCCaptionBar, :: RemoveButton

Supprime le bouton de la barre de légende.

```cpp
void RemoveButton();
```

### <a name="remarks"></a>Notes

La disposition des éléments de barre de légende est ajustée automatiquement.

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a> CMFCCaptionBar, :: RemoveIcon

Supprime l’icône de la barre de légende.

```cpp
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a> CMFCCaptionBar, :: RemoveText

Supprime l’étiquette de texte de la barre de légende.

```cpp
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a> CMFCCaptionBar, :: SetBitmap

Définit l’image bitmap pour la barre de légende.

```cpp
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

*hBitmap*<br/>
dans Handle de l’image bitmap à définir.

*clrTransparent*<br/>
dans Valeur RVB qui spécifie la couleur transparente de l’image bitmap.

*bStretch*<br/>
dans Si la valeur est TRUE, la bitmap est étirée si elle ne s’ajuste pas au rectangle englobant de l’image. Dans le cas contraire, la bitmap n’est pas étirée.

*bmpAlignment*<br/>
dans Alignement de l’image bitmap.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir une image bitmap sur une barre de légende.

La bitmap précédente est détruite automatiquement. Si la barre de légende affiche une icône parce que vous avez appelé la méthode [CMFCCaptionBar, :: seticon](#seticon) , l’image bitmap ne s’affiche pas, sauf si vous supprimez l’icône en appelant [CMFCCaptionBar, :: RemoveIcon](#removeicon).

La bitmap est alignée comme spécifié par le paramètre *bmpAlignment* .  Ce paramètre peut avoir l'une des valeurs `BarElementAlignment` suivantes :

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a> CMFCCaptionBar, :: SetBorderSize

Définit la taille de la bordure de la barre de légende.

```cpp
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>Paramètres

*nSize*<br/>
dans Nouvelle taille, en pixels, de la bordure de barre de légende.

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a> CMFCCaptionBar, :: SetButton

Définit le bouton pour la barre de légende.

```cpp
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
Étiquette de commande du bouton.

*uiCmdUI*<br/>
ID de commande du bouton.

*btnAlignmnet*<br/>
Alignement du bouton.

*bHasDropDownArrow*<br/>
TRUE si le bouton affiche une flèche déroulante ; sinon, FALSe.

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a> CMFCCaptionBar, :: SetButtonPressed

Spécifie si le bouton reste enfoncé.

```cpp
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>Paramètres

*bPresed*<br/>
TRUE si le bouton conserve son état enfoncé ; sinon, FALSe.

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a> CMFCCaptionBar, :: SetButtonToolTip

Définit l’info-bulle pour le bouton.

```cpp
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszToolTip*<br/>
dans Légende de l’info-bulle.

*lpszDescription*<br/>
dans Description de l’info-bulle.

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a> CMFCCaptionBar, :: SetFlatBorder

Définit le style de bordure de la barre de légende.

```cpp
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Paramètres

*bFlat*<br/>
dans TRUE si la bordure d’une barre de légende est plate. FALSe si la bordure est en 3D.

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a> CMFCCaptionBar, :: SetIcon

Définit l’icône pour une barre de légende.

```cpp
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Paramètres

*hIcon*<br/>
dans Handle de l’icône à définir.

*iconAlignment*<br/>
dans Alignement de l’icône.

### <a name="remarks"></a>Notes

Les barres de légende peuvent afficher des icônes ou des bitmaps. Consultez [CMFCCaptionBar, :: SetBitmap](#setbitmap) pour savoir comment afficher une image bitmap. Si vous définissez à la fois une icône et une image bitmap, l’icône est toujours affichée. Appelez [CMFCCaptionBar, :: RemoveIcon](#removeicon) pour supprimer une icône de la barre de légende.

L’icône est alignée en fonction du paramètre *iconAlignment* . Il peut s’agir de l’une des `BarElementAlignment` valeurs suivantes :

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a> CMFCCaptionBar, :: SetImageToolTip

Définit l’info-bulle de l’image dans la barre de légende.

```cpp
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>Paramètres

*lpszToolTip*<br/>
dans Texte de l’info-bulle.

*lpszDescription*<br/>
dans Description de l’info-bulle.

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a> CMFCCaptionBar, :: SetMargin

Définit la distance entre le bord de l’élément de barre de légende et le bord du contrôle de barre de légende.

```cpp
void SetMargin(int nMargin);
```

### <a name="parameters"></a>Paramètres

*nMargin*<br/>
dans Distance, en pixels, entre le bord des éléments de barre de légende et le bord du contrôle de barre de légende.

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a> CMFCCaptionBar, :: SetText

Définit l’étiquette de texte de la barre de légende.

```cpp
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>Paramètres

*strText*<br/>
dans Chaîne de texte à définir.

*textAlignment*<br/>
dans Alignement du texte.

### <a name="remarks"></a>Notes

L’étiquette de texte est alignée comme spécifié par le paramètre *textAlignment* . Il peut s’agir de l’une des `BarElementAlignment` valeurs suivantes :

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
