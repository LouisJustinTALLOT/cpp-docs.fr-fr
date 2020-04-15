---
title: Classe CMFCCaptionButton
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
ms.openlocfilehash: fb47e4373bf53e66dd4af17c89fe2f761858fbfd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367755"
---
# <a name="cmfccaptionbutton-class"></a>Classe CMFCCaptionButton

La `CMFCCaptionButton` classe implémente un bouton affiché sur la barre de légende pour une vitre d’amarrage ou une fenêtre à mini-cadre. En général, l'infrastructure crée les boutons de légende automatiquement.

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
|[CMFCCaptionButton::GetSize](#getsize)|Retourne la largeur et la hauteur du bouton.|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Indique si la hauteur de la barre de titre est réglée à la mini taille.|
|[CMFCCaptionButton::Déplacer](#move)|Définit l’emplacement du tirage au bouton et l’état du spectacle de fenêtre.|
|[CMFCCaptionButton::OnDraw](#ondraw)|Dessine le bouton de légende.|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Définit la mini taille de la barre de titre.|

## <a name="remarks"></a>Notes

Vous pouvez tirer une classe de [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) `AddButton`Class et utiliser la méthode protégée, pour ajouter des boutons de légende à une mini fenêtre de cadre.

CPaneFrameWnd.h définit les cartes d’image de commande pour deux types de boutons de légende :

- AFX_CAPTION_BTN_PIN, qui affiche un bouton d’épingle lorsque la vitre d’amarrage prend en charge le mode auto-cacher.

- AFX_CAPTION_BTN_CLOSE, qui affiche un bouton **Close** lorsque la vitre peut être fermée ou cachée.

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCCaptionButton` construire un objet et définir la mini taille de la barre de titre.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxcaptionbutton.h

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton

Construit un objet `CMFCCaptionButton`.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>Paramètres

*nHit*<br/>
[dans] La commande associée au bouton.

*bLeftAlign (en)*<br/>
[dans] Précise si le bouton est aligné sur la gauche.

Le tableau suivant répertorie les valeurs possibles pour le paramètre *nHit.*

|Value|Commande|
|-----------|-------------|
|AFX_HTCLOSE|Fermez le bouton.|
|HTMINBUTTON (EN)|Minimisez le bouton.|
|HTMAXBUTTON|Maximisez le bouton.|
|AFX_HTLEFTBUTTON|Bouton de flèche gauche.|
|AFX_HTRIGHTBUTTON|Bouton de flèche droite.|
|AFX_HTMENU|Bouton du menu de flèche vers le bas.|
|HTNOWHERE|La valeur par défaut; ne représente aucune commande.|

### <a name="remarks"></a>Notes

Par défaut, les boutons de légende ne sont pas associés à une commande.

Les boutons de légende sont alignés à droite ou à gauche.

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a>CMFCCaptionButton::GetHit

Retourne la commande représentée par le bouton.

```
UINT GetHit() const;
```

### <a name="return-value"></a>Valeur de retour

La commande représentée par le bouton.

Le tableau suivant énumère les valeurs de rendement possibles.

|Value|Commande|
|-----------|-------------|
|AFX_HTCLOSE|Fermez le bouton.|
|HTMINBUTTON (EN)|Minimisez le bouton.|
|HTMAXBUTTON|Maximisez le bouton.|
|AFX_HTLEFTBUTTON|Bouton de flèche gauche.|
|AFX_HTRIGHTBUTTON|Bouton de flèche droite.|
|AFX_HTMENU|Bouton du menu de flèche vers le bas.|
|HTNOWHERE|La valeur par défaut; ne représente aucune commande.|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a>CMFCCaptionButton::GetIconID

Retourne l’ID d’image associé au bouton.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>Paramètres

*bHorz (en)*<br/>
[dans] VRAI pour les UDI d’image de flèche gauche ou droite ; FALSE pour les pièces d’image de flèche vers le haut ou vers le bas.

*bMaximisé*<br/>
[dans] VRAI pour une carte d’image maximisée; FALSE pour un id d’image minimiser.

### <a name="return-value"></a>Valeur de retour

L’id d’image.

### <a name="remarks"></a>Notes

Les paramètres spécifient les ID d’image pour minimiser ou maximiser les boutons de légende.

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a>CMFCCaptionButton::GetRect

Retourne le rectangle occupé par le bouton.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>Valeur de retour

Le rectangle qui représente l’emplacement du bouton.

### <a name="remarks"></a>Notes

Si vous ne pouvez pas voir le bouton, la taille retournée est de 0.

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a>CMFCCaptionButton::GetSize

Retourne la largeur et la hauteur du bouton.

```
static CSize GetSize();
```

### <a name="return-value"></a>Valeur de retour

Les dimensions extérieures du bouton.

### <a name="remarks"></a>Notes

La taille retournée comprend la marge et la bordure des boutons.

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a>CMFCCaptionButton::IsMiniFrameButton

Indique si la hauteur de la barre de titre est réglée à la mini taille.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la légende est réglée à la mini taille; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a>CMFCCaptionButton::Déplacer

Définit l’emplacement du tirage au bouton et l’état du spectacle de fenêtre.

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

*ptTo*<br/>
[dans] Le nouvel emplacement.

*bHide (en)*<br/>
[dans] Que ce soit pour afficher le bouton.

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a>CMFCCaptionButton::OnDraw

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

*pDC*<br/>
[dans] Pointeur vers un contexte d’appareil pour le bouton.

*bActive (en)*<br/>
[dans] S’il faut dessiner une image de bouton actif.

*bHorz (en)*<br/>
[dans] Réservé pour une utilisation dans une classe dérivée.

*bMaximisé*<br/>
[dans] S’il faut dessiner une image bouton maximisée.

*bDissabled*<br/>
[dans] S’il faut dessiner une image bouton activée.

### <a name="remarks"></a>Notes

Le *paramètre bMaximized* est utilisé lorsque le bouton est un bouton maximiser ou minimiser.

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton

Définit la mini taille de la barre de titre.

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSet (en anglais)*<br/>
[dans] VRAI pour mini hauteur de barre de titre; FALSE pour la hauteur de barre de titre par défaut.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd, classe](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)
