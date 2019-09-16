---
title: CMFCRibbonEdit, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
ms.openlocfilehash: 4f973074fbec3d04b1c1a74852b02ff2564217c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504947"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit, classe

Implémente un contrôle d’édition qui se trouve sur une barre de ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construit un objet `CMFCRibbonEdit`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Indique si la hauteur du `CMFCRibbonEdit` contrôle peut augmenter verticalement à la hauteur d’une ligne de ruban.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construit un objet `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Copie l’état de l’objet `CMFCRibbonEdit` spécifié dans l’objet `CMFCRibbonEdit` actuel.|
|[CMFCRibbonEdit::CreateEdit](#createedit)|Crée une nouvelle zone de texte pour `CMFCRibbonEdit` l’objet.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Détruit l' `CMFCRibbonEdit` objet.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Ferme une zone de liste.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Active et définit la plage du bouton toupie (spin) pour la zone de texte.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Récupère la taille compacte de l' `CFMCRibbonEdit` objet.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Récupère le texte dans la zone de texte.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Récupère la taille intermédiaire de l' `CMFCRibbonEdit` objet.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Récupère l’alignement du texte dans la zone de texte.|
|[CMFCRibbonEdit::GetWidth](#getwidth)|Récupère la largeur, en pixels, du `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indique si la taille d’affichage du `CMFCRibbonEdit` contrôle peut être compacte.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indique si le `CMFCRIbbonEdit` contrôle a le focus.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indique si la taille d' `CMFCRibbonEdit` affichage du contrôle peut être grande.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indique si la zone de texte a un bouton toupie (spin).|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indique si le `CMFCRibbonEdit` contrôle est mis en surbrillance.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Appelée par l’infrastructure lorsque les dimensions du rectangle d’affichage pour le `CMFCRibbonEdit` contrôle sont modifiées.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner le `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Appelé par l’infrastructure pour dessiner l’étiquette et l’image du `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Appelé par l’infrastructure pour dessiner le `CMFCRibbonEdit` contrôle dans une zone de liste commandes.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Appelé par l’infrastructure pour activer ou désactiver le `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Appelée par l’infrastructure quand le pointeur entre dans ou quitte les limites du `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::OnKey](#onkey)|Appelée par l’infrastructure quand l’utilisateur appuie sur une touche d’appel `CMFCRibbonEdit` et que le contrôle a le focus.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Appelé par l’infrastructure pour mettre à `CMFCRibbonEdit` jour le contrôle lorsque l’utilisateur appuie sur le bouton gauche de la souris sur le contrôle.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Appelée par l’infrastructure quand l’utilisateur relâche le bouton gauche de la souris.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Appelé par l’infrastructure pour mettre à `CMFCRibbonEdit` jour le contrôle lorsque la disposition change de direction.|
|[CMFCRibbonEdit::OnShow](#onshow)|Appelé par le Framework pour afficher ou masquer le `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::Redraw](#redraw)|Met à jour l’affichage du `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Définit les données d’accessibilité pour `CMFCRibbonEdit` l’objet.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Définit le texte dans la zone de texte.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Définit l’alignement du texte de la zone de texte.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Définit la largeur de la zone de texte pour `CMFCRibbonEdit` le contrôle.|

## <a name="remarks"></a>Notes

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCRibbonEdit` objet, afficher des boutons de sélection numérique en regard du contrôle d’édition et définir le texte du contrôle d’édition. Cet extrait de code fait partie de l' [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** afxRibbonEdit. h

##  <a name="canbestretched"></a>  CMFCRibbonEdit::CanBeStretched

Indique si la hauteur du contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) peut augmenter verticalement à la hauteur d’une ligne de ruban.

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours FALSe.

### <a name="remarks"></a>Notes

##  <a name="cmfcribbonedit"></a>  CMFCRibbonEdit::CMFCRibbonEdit

Construit un objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
dans ID de commande pour `CMFCRibbonEdit` le contrôle.

*nWidth*<br/>
dans Largeur, en pixels, de la zone de texte pour le `CMFCRibbonEdit` contrôle.

*lpszLabel*<br/>
dans Étiquette `CMFCRibbonEdit` du contrôle.

*nImage*<br/>
dans Index de la petite image à utiliser pour le `CMFCRibbonEdit` contrôle. La collection de petites images est gérée par la catégorie de ruban parente.

### <a name="remarks"></a>Notes

Le `CMFCRibbonEdit` contrôle n’utilise pas une grande image.

##  <a name="copyfrom"></a>  CMFCRibbonEdit::CopyFrom

Copie l’état de l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) spécifié dans l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) actuel.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
dans Objet source `CMFCRibbonEdit` .

### <a name="remarks"></a>Notes

Le paramètre *src* doit être de type `CMFCRibbonEdit`.

##  <a name="createedit"></a>  CMFCRibbonEdit::CreateEdit

Crée une nouvelle zone de texte pour l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la fenêtre parente de l' `CMFCRibbonEdit` objet.

*dwEditStyle*<br/>
dans Spécifie le style de la zone de texte. Vous pouvez combiner les styles de fenêtre répertoriés dans la section Notes avec les [styles de contrôle d’édition](/windows/win32/Controls/edit-control-styles) décrits dans la SDK Windows.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la nouvelle zone de texte si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour créer une zone de texte personnalisée.

Vous pouvez appliquer les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à une zone de texte :

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>  CMFCRibbonEdit::DestroyCtrl

Détruit l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Notes

##  <a name="dropdownlist"></a>  CMFCRibbonEdit::DropDownList

Ferme une zone de liste.

```
virtual void DropDownList();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Substituez cette méthode pour dérouler une zone de liste.

##  <a name="enablespinbuttons"></a>  CMFCRibbonEdit::EnableSpinButtons

Active et définit la plage du bouton toupie (spin) pour la zone de texte.

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
dans Valeur minimale du bouton toupie.

*nMax*<br/>
dans Valeur maximale du bouton toupie.

### <a name="remarks"></a>Notes

Les boutons toupie affichent une flèche vers le haut et vers le bas et permettent aux utilisateurs de parcourir un ensemble fixe de valeurs.

##  <a name="getcompactsize"></a>  CMFCRibbonEdit::GetCompactSize

Récupère la taille compacte de l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique pour `CMFCRibbonEdit` l’objet.

### <a name="return-value"></a>Valeur de retour

Taille compacte de l' `CMFCRibbonEdit` objet.

### <a name="remarks"></a>Notes

##  <a name="getedittext"></a>  CMFCRibbonEdit::GetEditText

Récupère le texte dans la zone de texte.

```
CString GetEditText() const;
```

### <a name="return-value"></a>Valeur de retour

Texte de la zone de texte.

### <a name="remarks"></a>Notes

##  <a name="getintermediatesize"></a>  CMFCRibbonEdit::GetIntermediateSize

Récupère la taille intermédiaire de l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique pour `CMFCRibbonEdit` l’objet.

### <a name="return-value"></a>Valeur de retour

Taille intermédiaire de l' `CMFCRibbonEdit` objet.

### <a name="remarks"></a>Notes

##  <a name="gettextalign"></a>  CMFCRibbonEdit::GetTextAlign

Récupère l’alignement du texte dans la zone de texte.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur énumérée d’alignement de texte. Consultez la section Notes pour connaître les valeurs possibles.

### <a name="remarks"></a>Notes

La valeur retournée est l’un des styles de contrôle de modification suivants :

- **ES_LEFT** pour l’alignement à gauche

- **ES_CENTER** pour l’alignement du centre

- **ES_RIGHT** pour l’alignement à droite

Pour plus d’informations sur ces styles, consultez [modifier les styles de contrôle](/windows/win32/Controls/edit-control-styles).

##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth

Récupère la largeur, en pixels, du contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Paramètres

*bInFloatyMode*<br/>
dans TRUE si le `CMFCRibbonEdit` contrôle est en mode à virgule flottante ; sinon, false.

### <a name="return-value"></a>Valeur de retour

Largeur, en pixels, du `CMFCRibbonEdit` contrôle.

### <a name="remarks"></a>Notes

##  <a name="hascompactmode"></a>  CMFCRibbonEdit::HasCompactMode

Indique si la taille d’affichage pour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) peut être compacte.

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode retourne toujours TRUE. Substituez cette méthode pour indiquer si la taille d’affichage peut être compacte.

##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus

Indique si le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) a le focus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le `CMFCRibbonEdit` contrôle a le focus ; sinon, false.

### <a name="remarks"></a>Notes

##  <a name="haslargemode"></a>  CMFCRibbonEdit::HasLargeMode

Indique si la taille d’affichage pour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) peut être grande.

```
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours FALSe.

### <a name="remarks"></a>Notes

Par défaut, cette méthode retourne toujours FALSe. Substituez cette méthode pour indiquer si la taille d’affichage peut être grande.

##  <a name="hasspinbuttons"></a>  CMFCRibbonEdit::HasSpinButtons

Indique si la zone de texte a un bouton toupie (spin).

```
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la zone de texte a un bouton toupie (spin); Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="ishighlighted"></a>  CMFCRibbonEdit::IsHighlighted

Indique si le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) est mis en surbrillance.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le `CMFCRibbonEdit` contrôle est mis en surbrillance ; sinon, false.

### <a name="remarks"></a>Notes

##  <a name="onafterchangerect"></a>  CMFCRibbonEdit::OnAfterChangeRect

Appelée par l’infrastructure lorsque les dimensions du rectangle d’affichage pour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) changent.

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique ( `CMFCRibbonEdit` Device Context) pour le contrôle.

### <a name="remarks"></a>Notes

##  <a name="ondraw"></a>  CMFCRibbonEdit::OnDraw

Appelé par l’infrastructure pour dessiner le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique ( `CMFCRibbonEdit` Device Context) pour le contrôle.

### <a name="remarks"></a>Notes

##  <a name="ondrawlabelandimage"></a>  CMFCRibbonEdit::OnDrawLabelAndImage

Appelé par l’infrastructure pour dessiner l’étiquette et l’image du contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique ( `CMFCRibbonEdit` Device Context) pour le contrôle.

### <a name="remarks"></a>Notes

##  <a name="ondrawonlist"></a>  CMFCRibbonEdit::OnDrawOnList

Appelé par l’infrastructure pour dessiner le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) dans une zone de liste commandes.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers un contexte de périphérique ( `CMFCRibbonEdit` Device Context) pour le contrôle.

*strText*<br/>
[in] Le texte d’affichage [](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit classe").

*nTextOffset*<br/>
dans Distance, en pixels, entre le côté gauche de la zone de liste et le texte affiché.

*rect*<br/>
dans Rectangle d' `CMFCRibbonEdit` affichage du contrôle.

*bIsSelected*<br/>
dans Ce paramètre n’est pas utilisé.

*bHighlighted*<br/>
dans Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

La zone de liste commandes affiche des contrôles de ruban pour permettre aux utilisateurs de personnaliser la barre d’outils accès rapide.

##  <a name="onenable"></a>  CMFCRibbonEdit::OnEnable

Appelé par l’infrastructure pour activer ou désactiver le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour activer le contrôle ; FALSe pour désactiver le contrôle.

### <a name="remarks"></a>Notes

##  <a name="onhighlight"></a>  CMFCRibbonEdit::OnHighlight

Appelée par l’infrastructure quand le pointeur entre dans ou quitte les limites du contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Paramètres

*bHighlight*<br/>
dans TRUE si le pointeur se trouve dans les limites du `CMFCRibbonEdit` contrôle ; sinon, false.

### <a name="remarks"></a>Notes

##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey

Appelée par l’infrastructure quand l’utilisateur appuie sur une touche d’appel et que le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) a le focus.

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Paramètres

*bIsMenuKey*<br/>
dans TRUE si la touche d’accès affiche un menu contextuel ; Sinon, FALSe.

### <a name="return-value"></a>Valeur de retour

TRUE si l’événement a été géré ; Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="onlbuttondown"></a>  CMFCRibbonEdit::OnLButtonDown

Appelé par l’infrastructure pour mettre à jour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) lorsque l’utilisateur appuie sur le bouton gauche de la souris sur le contrôle.

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
dans Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

##  <a name="onlbuttonup"></a>  CMFCRibbonEdit::OnLButtonUp

Appelée par l’infrastructure quand l’utilisateur relâche le bouton gauche de la souris.

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
dans Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

##  <a name="onrtlchanged"></a>  CMFCRibbonEdit::OnRTLChanged

Appelé par l’infrastructure pour mettre à jour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) lorsque la disposition change de direction.

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Paramètres

*bIsRTL*<br/>
dans TRUE si la disposition est de droite à gauche ; FALSe si la disposition est de gauche à droite.

### <a name="remarks"></a>Notes

##  <a name="onshow"></a>  CMFCRibbonEdit::OnShow

Appelé par le Framework pour afficher ou masquer le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
dans TRUE pour afficher le contrôle ; FALSe pour masquer le contrôle.

### <a name="remarks"></a>Notes

##  <a name="redraw"></a>  CMFCRibbonEdit::Redraw

Met à jour l’affichage du contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual void Redraw();
```

### <a name="remarks"></a>Notes

Cette méthode redessine le rectangle d’affichage de `CMFCRibbonEdit` l’objet en appelant indirectement [CWnd :: RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) avec les indicateurs RDW_INVALIDATE, RDW_ERASE et RDW_UPDATENOW définis.

##  <a name="setaccdata"></a>  CMFCRibbonEdit::SetACCData

Définit les données d’accessibilité pour l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
Pointeur vers la fenêtre parente de `CMFCRibbonEdit` l’objet.

*data*<br/>
Données d’accessibilité pour l' `CMFCRibbonEdit` objet.

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

##  <a name="setedittext"></a>  CMFCRibbonEdit::SetEditText

Définit le texte dans la zone de texte.

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>Paramètres

*strText*<br/>
dans Texte de la zone de texte.

##  <a name="settextalign"></a>  CMFCRibbonEdit::SetTextAlign

Définit l’alignement du texte de la zone de texte.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Paramètres

*nAlign*<br/>
dans Valeur énumérée d’alignement de texte. Consultez la section Notes pour connaître les valeurs possibles.

### <a name="remarks"></a>Notes

Le paramètre *nAlign* est l’un des styles de contrôle de modification suivants :

- ES_LEFT pour l’alignement à gauche

- ES_CENTER pour l’alignement du centre

- ES_RIGHT pour l’alignement à droite

Pour plus d’informations sur ces styles, consultez [modifier les styles de contrôle](/windows/win32/Controls/edit-control-styles).

##  <a name="setwidth"></a>  CMFCRibbonEdit::SetWidth

Définit la largeur de la zone de texte pour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) .

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
dans Largeur, en pixels, de la zone de texte.

*bInFloatyMode*<br/>
TRUE pour définir la largeur du mode flottant ; FALSe pour définir la largeur du mode normal.

### <a name="remarks"></a>Notes

Le `CMFCRibbonEdit` contrôle a deux largeurs en fonction de son mode d’affichage : le mode flottant et le mode normal.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)
