---
description: 'En savoir plus sur : classe CMFCCaptionButton'
title: CMFCCaptionButton, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: 6c3c1cbeea4a548f2951276b3ad43cb598cf22a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327756"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton, classe

La `CMFCCaptionButton` classe implémente un bouton qui est affiché dans la barre de légende pour un volet d’ancrage ou une fenêtre mini-frame. En général, l'infrastructure crée les boutons de légende automatiquement.

## <a name="syntax"></a>Syntaxe

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Nom|Description|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Construit un objet CMFCCaptionButton.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|Retourne la commande représentée par le bouton.|
|[CMFCCaptionButton::GetIconID](#geticonid)|Retourne l’ID d’image associé au bouton.|
|[CMFCCaptionButton::GetRect](#getrect)|Retourne le rectangle occupé par le bouton.|
|[CMFCCaptionButton :: est à obtenir](#getsize)|Retourne la largeur et la hauteur du bouton.|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Indique si la hauteur de la barre de titre est définie sur mini-taille.|
|[CMFCCaptionButton :: Move](#move)|Définit l’état de l’emplacement du dessin du bouton et de l’affichage de la fenêtre.|
|[CMFCCaptionButton :: OnDraw](#ondraw)|Dessine le bouton de légende.|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Définit la taille minimale de la barre de titre.|

## <a name="remarks"></a>Notes

Vous pouvez dériver une classe de la [classe CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) et utiliser la méthode protégée, `AddButton` , pour ajouter des boutons de légende à une fenêtre mini-frame.

CPaneFrameWnd. h définit les ID de commande de deux types de boutons de légende :

- AFX_CAPTION_BTN_PIN, qui affiche un bouton épingler lorsque le volet d’ancrage prend en charge le mode de masquage automatique.

- AFX_CAPTION_BTN_CLOSE, qui affiche un bouton **Fermer** lorsque le volet peut être fermé ou masqué.

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCCaptionButton` objet et définir la taille minimale de la barre de titre.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxcaptionbutton. h

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a> CMFCCaptionButton::CMFCCaptionButton

Construit un objet `CMFCCaptionButton`.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>Paramètres

*nHit*<br/>
dans Commande associée au bouton.

*bLeftAlign*<br/>
dans Spécifie si le bouton est aligné à gauche.

Le tableau suivant répertorie les valeurs possibles pour le paramètre *nHit* .

|Valeur|Commande|
|-----------|-------------|
|AFX_HTCLOSE|Bouton Fermer.|
|HTMINBUTTON|Bouton réduire.|
|HTMAXBUTTON|Agrandissez le bouton.|
|AFX_HTLEFTBUTTON|Bouton de direction gauche.|
|AFX_HTRIGHTBUTTON|Bouton fléché droit.|
|AFX_HTMENU|Bouton de menu de la flèche vers le bas.|
|HTNOWHERE|Valeur par défaut ; ne représente aucune commande.|

### <a name="remarks"></a>Notes

Par défaut, les boutons de légende ne sont pas associés à une commande.

Les boutons de légende sont alignés à droite ou à gauche.

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a> CMFCCaptionButton::GetHit

Retourne la commande représentée par le bouton.

```
UINT GetHit() const;
```

### <a name="return-value"></a>Valeur renvoyée

Commande représentée par le bouton.

Le tableau suivant répertorie les valeurs de retour possibles.

|Valeur|Commande|
|-----------|-------------|
|AFX_HTCLOSE|Bouton Fermer.|
|HTMINBUTTON|Bouton réduire.|
|HTMAXBUTTON|Agrandissez le bouton.|
|AFX_HTLEFTBUTTON|Bouton de direction gauche.|
|AFX_HTRIGHTBUTTON|Bouton fléché droit.|
|AFX_HTMENU|Bouton de menu de la flèche vers le bas.|
|HTNOWHERE|Valeur par défaut ; ne représente aucune commande.|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a> CMFCCaptionButton::GetIconID

Retourne l’ID d’image associé au bouton.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>Paramètres

*bHorz*<br/>
dans TRUE pour les ID d’image des flèches gauche et droite ; FALSe pour les ID d’image des flèches haut ou bas.

*bMaximized*<br/>
dans TRUE pour obtenir un ID d’image agrandi ; FALSe pour un ID d’image réduit.

### <a name="return-value"></a>Valeur renvoyée

ID de l’image.

### <a name="remarks"></a>Notes

Les paramètres spécifient des ID d’image pour réduire ou agrandir les boutons de légende.

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a> CMFCCaptionButton::GetRect

Retourne le rectangle occupé par le bouton.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>Valeur renvoyée

Rectangle qui représente l’emplacement du bouton.

### <a name="remarks"></a>Notes

Si vous ne voyez pas le bouton, la taille retournée est 0.

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a> CMFCCaptionButton :: est à obtenir

Retourne la largeur et la hauteur du bouton.

```
static CSize GetSize();
```

### <a name="return-value"></a>Valeur renvoyée

Dimensions externes du bouton.

### <a name="remarks"></a>Notes

La taille retournée comprend des marges et des bordures de bouton.

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a> CMFCCaptionButton::IsMiniFrameButton

Indique si la hauteur de la barre de titre est définie sur mini-taille.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la légende est définie sur mini Size ; Sinon, FALSe.

### <a name="remarks"></a>Notes

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a> CMFCCaptionButton :: Move

Définit l’état de l’emplacement du dessin du bouton et de l’affichage de la fenêtre.

```cpp
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

*ptTo*<br/>
dans Nouvel emplacement.

*bHide*<br/>
dans Indique s’il faut afficher le bouton.

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a> CMFCCaptionButton :: OnDraw

Dessine le bouton de légende.

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique pour le bouton.

*bActive*<br/>
dans Indique si une image de bouton active doit être dessinée.

*bHorz*<br/>
dans Réservé à une utilisation dans une classe dérivée.

*bMaximized*<br/>
dans Indique s’il faut dessiner une image de bouton agrandie.

*bDisabled*<br/>
dans Indique si une image de bouton activée doit être dessinée.

### <a name="remarks"></a>Notes

Le paramètre *bMaximized* est utilisé lorsque le bouton est un bouton agrandir ou réduire.

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a> CMFCCaptionButton::SetMiniFrameButton

Définit la taille minimale de la barre de titre.

```cpp
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSet*<br/>
dans TRUE pour la hauteur de la mini-barre de titre ; FALSe pour la hauteur de la barre de titre par défaut.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd, classe](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)
