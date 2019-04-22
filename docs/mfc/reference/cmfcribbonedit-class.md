---
title: Cmfcribbonedit, classe
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
ms.openlocfilehash: 80ee43ae32416f9f62df419c4afbd46a0aa63cc8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780481"
---
# <a name="cmfcribbonedit-class"></a>Cmfcribbonedit, classe

Implémente un contrôle d’édition qui se trouve sur une barre du ruban.

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
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Indique si la hauteur de la `CMFCRibbonEdit` contrôle peut augmenter verticalement à la hauteur d’une ligne de ruban.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construit un objet `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Copie l’état de l’objet `CMFCRibbonEdit` objet actuel `CMFCRibbonEdit` objet.|
|[CMFCRibbonEdit::CreateEdit](#createedit)|Crée une nouvelle zone de texte pour le `CMFCRibbonEdit` objet.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Détruit le `CMFCRibbonEdit` objet.|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Supprime une zone de liste déroulante.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Active et définit la plage du bouton toupie (spin) pour la zone de texte.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Récupère la taille réduite de la `CFMCRibbonEdit` objet.|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Récupère le texte dans la zone de texte.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Récupère la taille intermédiaire de la `CMFCRibbonEdit` objet.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Récupère l’alignement du texte dans la zone de texte.|
|[CMFCRibbonEdit::GetWidth](#getwidth)|Récupère la largeur, en pixels, de la `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indique si l’affichage taille pour le `CMFCRibbonEdit` contrôle peut être compact.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indique si le `CMFCRIbbonEdit` contrôle a le focus.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indique si l’affichage taille pour le `CMFCRibbonEdit` contrôle peut être volumineux.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indique si la zone de texte a un bouton de sélection numérique.|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indique si le `CMFCRibbonEdit` contrôle est mis en surbrillance.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Appelé par l’infrastructure lorsque les dimensions du rectangle d’affichage pour le `CMFCRibbonEdit` contrôle change.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner le `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Appelé par l’infrastructure pour dessiner l’étiquette et de l’image pour le `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Appelé par l’infrastructure pour dessiner le `CMFCRibbonEdit` contrôle dans une zone de liste de commandes.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Appelé par l’infrastructure pour activer ou désactiver la `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Appelé par le framework lorsque le pointeur entre ou quitte les limites de la `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::OnKey](#onkey)|Appelé par le framework lorsque l’utilisateur appuie sur une touche d’accès et le `CMFCRibbonEdit` contrôle a le focus.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Appelé par l’infrastructure pour mettre à jour la `CMFCRibbonEdit` contrôle lorsque l’utilisateur appuie sur le bouton gauche de la souris sur le contrôle.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton gauche de la souris.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Appelé par l’infrastructure pour mettre à jour le `CMFCRibbonEdit` contrôler quand la disposition change de direction.|
|[CMFCRibbonEdit::OnShow](#onshow)|Appelé par l’infrastructure pour afficher ou masquer la `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::Redraw](#redraw)|Met à jour l’affichage de la `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Définit les données d’accessibilité pour le `CMFCRibbonEdit` objet.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Définit le texte dans la zone de texte.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Définit l’alignement du texte de la zone de texte.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Définit la largeur de la zone de texte pour le `CMFCRibbonEdit` contrôle.|

## <a name="remarks"></a>Notes

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCRibbonEdit` de l’objet, afficher les boutons de sélection numérique en regard du contrôle d’édition et définir le texte du contrôle d’édition. Cet extrait de code fait partie de la [exemple de démonstration de MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** afxRibbonEdit.h

##  <a name="canbestretched"></a>  CMFCRibbonEdit::CanBeStretched

Indique si la hauteur de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle peut augmenter verticalement à la hauteur d’une ligne de ruban.

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours FALSE.

### <a name="remarks"></a>Notes

##  <a name="cmfcribbonedit"></a>  CMFCRibbonEdit::CMFCRibbonEdit

Construit un [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.

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
[in] Commande ID pour le `CMFCRibbonEdit` contrôle.

*nWidth*<br/>
[in] La largeur, en pixels, de la zone de texte pour le `CMFCRibbonEdit` contrôle.

*lpszLabel*<br/>
[in] L’étiquette pour le `CMFCRibbonEdit` contrôle.

*nImage*<br/>
[in] Index de la petite image à utiliser pour le `CMFCRibbonEdit` contrôle. La collection de petites images est gérée par la catégorie de ruban parent.

### <a name="remarks"></a>Notes

Le `CMFCRibbonEdit` contrôle n’utilise pas une grande image.

##  <a name="copyfrom"></a>  CMFCRibbonEdit::CopyFrom

Copie l’état de l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet actuel [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[in] La source `CMFCRibbonEdit` objet.

### <a name="remarks"></a>Notes

Le *src* paramètre doit être de type `CMFCRibbonEdit`.

##  <a name="createedit"></a>  CMFCRibbonEdit::CreateEdit

Crée une nouvelle zone de texte pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[in] Un pointeur vers la fenêtre parente de la `CMFCRibbonEdit` objet.

*dwEditStyle*<br/>
[in] Spécifie le style de la zone de texte. Vous pouvez combiner les styles de fenêtre répertoriés dans la section Notes avec le [modifier les styles de contrôle](/windows/desktop/Controls/edit-control-styles) qui sont décrits dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la nouvelle zone de texte si la méthode a réussi ; Sinon, NULL.

### <a name="remarks"></a>Notes

Substituez cette méthode dans une classe dérivée pour créer une zone de texte personnalisé.

Vous pouvez appliquer ce qui suit [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) à une zone de texte :

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>  CMFCRibbonEdit::DestroyCtrl

Détruit le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Notes

##  <a name="dropdownlist"></a>  CMFCRibbonEdit::DropDownList

Supprime une zone de liste déroulante.

```
virtual void DropDownList();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Substituez cette méthode pour une zone de liste déroulante.

##  <a name="enablespinbuttons"></a>  CMFCRibbonEdit::EnableSpinButtons

Active et définit la plage du bouton toupie (spin) pour la zone de texte.

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*nMin*<br/>
[in] La valeur minimale du bouton toupie (spin).

*nMax*<br/>
[in] La valeur maximale du bouton toupie (spin).

### <a name="remarks"></a>Notes

Boutons de sélection numérique affichent le haut et flèche vers le bas et permettent aux utilisateurs de parcourir un ensemble fixe de valeurs.

##  <a name="getcompactsize"></a>  CMFCRibbonEdit::GetCompactSize

Récupère la taille réduite de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` objet.

### <a name="return-value"></a>Valeur de retour

La taille réduite de la `CMFCRibbonEdit` objet.

### <a name="remarks"></a>Notes

##  <a name="getedittext"></a>  CMFCRibbonEdit::GetEditText

Récupère le texte dans la zone de texte.

```
CString GetEditText() const;
```

### <a name="return-value"></a>Valeur de retour

Le texte dans la zone de texte.

### <a name="remarks"></a>Notes

##  <a name="getintermediatesize"></a>  CMFCRibbonEdit::GetIntermediateSize

Récupère la taille intermédiaire de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` objet.

### <a name="return-value"></a>Valeur de retour

La taille intermédiaire de la `CMFCRibbonEdit` objet.

### <a name="remarks"></a>Notes

##  <a name="gettextalign"></a>  CMFCRibbonEdit::GetTextAlign

Récupère l’alignement du texte dans la zone de texte.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Valeur de retour

Un alignement de texte de valeur énumérée. Consultez la section Notes pour les valeurs possibles.

### <a name="remarks"></a>Notes

La valeur retournée est un des styles de contrôle d’édition suivants :

- **ES_LEFT** pour l’alignement à gauche

- **ES_CENTER** pour alignement au centre

- **ES_RIGHT** pour l’alignement à droite

Pour plus d’informations sur ces styles, consultez [modifier les Styles de contrôle](/windows/desktop/Controls/edit-control-styles).

##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth

Récupère la largeur, en pixels, de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Paramètres

*bInFloatyMode*<br/>
[in] TRUE si le `CMFCRibbonEdit` contrôle est en mode flottant ; sinon, FALSE.

### <a name="return-value"></a>Valeur de retour

La largeur, en pixels, de la `CMFCRibbonEdit` contrôle.

### <a name="remarks"></a>Notes

##  <a name="hascompactmode"></a>  CMFCRibbonEdit::HasCompactMode

Indique si l’affichage taille pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle peut être compact.

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Valeur de retour

Renvoie toujours TRUE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode retourne toujours TRUE. Substituez cette méthode pour indiquer si la taille d’affichage peut être compacte.

##  <a name="hasfocus"></a>  CMFCRibbonEdit::HasFocus

Indique si le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle a le focus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le `CMFCRibbonEdit` contrôle a le focus ; sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="haslargemode"></a>  CMFCRibbonEdit::HasLargeMode

Indique si l’affichage taille pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle peut être volumineux.

```
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours FALSE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode retourne toujours FALSE. Substituez cette méthode pour indiquer si la taille d’affichage peut être volumineux.

##  <a name="hasspinbuttons"></a>  CMFCRibbonEdit::HasSpinButtons

Indique si la zone de texte a un bouton de sélection numérique.

```
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la zone de texte a un bouton toupie (spin) ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="ishighlighted"></a>  CMFCRibbonEdit::IsHighlighted

Indique si le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle est mis en surbrillance.

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le `CMFCRibbonEdit` contrôle est mis en surbrillance ; sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="onafterchangerect"></a>  CMFCRibbonEdit::OnAfterChangeRect

Appelé par l’infrastructure lorsque les dimensions du rectangle d’affichage pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle le changement.

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` contrôle.

### <a name="remarks"></a>Notes

##  <a name="ondraw"></a>  CMFCRibbonEdit::OnDraw

Appelé par l’infrastructure pour dessiner le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` contrôle.

### <a name="remarks"></a>Notes

##  <a name="ondrawlabelandimage"></a>  CMFCRibbonEdit::OnDrawLabelAndImage

Appelé par l’infrastructure pour dessiner l’étiquette et de l’image pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[in] Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` contrôle.

### <a name="remarks"></a>Notes

##  <a name="ondrawonlist"></a>  CMFCRibbonEdit::OnDrawOnList

Appelé par l’infrastructure pour dessiner le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle dans une zone de liste de commandes.

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
[in] Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` contrôle.

*strText*<br/>
[in] Le texte d’affichage [ ] (../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit, classe").

*nTextOffset*<br/>
[in] Distance, en pixels, du côté gauche de la zone de liste pour afficher un texte.

*rect*<br/>
[in] Le rectangle d’affichage pour le `CMFCRibbonEdit` contrôle.

*bIsSelected*<br/>
[in] Ce paramètre n’est pas utilisé.

*bHighlighted*<br/>
[in] Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

La zone de liste de commandes affiche les contrôles de ruban pour permettre aux utilisateurs de personnaliser la barre d’outils Accès rapide.

##  <a name="onenable"></a>  CMFCRibbonEdit::OnEnable

Appelé par l’infrastructure pour activer ou désactiver la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[in] TRUE pour activer le contrôle ; FALSE pour désactiver le contrôle.

### <a name="remarks"></a>Notes

##  <a name="onhighlight"></a>  CMFCRibbonEdit::OnHighlight

Appelé par le framework lorsque le pointeur entre ou quitte les limites de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Paramètres

*bHighlight*<br/>
[in] TRUE si le pointeur se trouve dans les limites de la `CMFCRibbonEdit` contrôle ; sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey

Appelé par le framework lorsque l’utilisateur appuie sur une touche d’accès et le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle a le focus.

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Paramètres

*bIsMenuKey*<br/>
[in] TRUE si la touche d’accès affiche un menu contextuel. Sinon, FALSE.

### <a name="return-value"></a>Valeur de retour

TRUE si l’événement a été géré ; Sinon, FALSE.

### <a name="remarks"></a>Notes

##  <a name="onlbuttondown"></a>  CMFCRibbonEdit::OnLButtonDown

Appelé par l’infrastructure pour mettre à jour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôler quand l’utilisateur appuie sur le bouton gauche de la souris sur le contrôle.

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
[in] Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

##  <a name="onlbuttonup"></a>  CMFCRibbonEdit::OnLButtonUp

Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton gauche de la souris.

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Paramètres

*point*<br/>
[in] Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

##  <a name="onrtlchanged"></a>  CMFCRibbonEdit::OnRTLChanged

Appelé par l’infrastructure pour mettre à jour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôler quand la disposition change de direction.

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Paramètres

*bIsRTL*<br/>
[in] TRUE si la disposition est de droite à gauche ; FALSE si la disposition est de gauche à droite.

### <a name="remarks"></a>Notes

##  <a name="onshow"></a>  CMFCRibbonEdit::OnShow

Appelé par l’infrastructure pour afficher ou masquer la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
[in] TRUE pour afficher le contrôle ; FALSE pour masquer le contrôle.

### <a name="remarks"></a>Notes

##  <a name="redraw"></a>  CMFCRibbonEdit::Redraw

Met à jour l’affichage de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.

```
virtual void Redraw();
```

### <a name="remarks"></a>Notes

Cette méthode redessine le rectangle d’affichage pour le `CMFCRibbonEdit` objet en appelant indirectement [CWnd::RedrawWindow](/windows/desktop/api/winuser/nf-winuser-redrawwindow) avec les indicateurs RDW_INVALIDATE, RDW_ERASE et RDW_UPDATENOW définie.

##  <a name="setaccdata"></a>  CMFCRibbonEdit::SetACCData

Définit les données d’accessibilité pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
Pointeur vers la fenêtre parente pour le `CMFCRibbonEdit` objet.

*data*<br/>
Les données d’accessibilité pour le `CMFCRibbonEdit` objet.

### <a name="return-value"></a>Valeur de retour

Renvoie toujours TRUE.

### <a name="remarks"></a>Notes

##  <a name="setedittext"></a>  CMFCRibbonEdit::SetEditText

Définit le texte dans la zone de texte.

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>Paramètres

*strText*<br/>
[in] Le texte de la zone de texte.

##  <a name="settextalign"></a>  CMFCRibbonEdit::SetTextAlign

Définit l’alignement du texte de la zone de texte.

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Paramètres

*nAlign*<br/>
[in] Un alignement de texte de valeur énumérée. Consultez la section Notes pour les valeurs possibles.

### <a name="remarks"></a>Notes

Le paramètre *nAlign* fait partie de la modification suivante des styles de contrôle :

- ES_LEFT pour l’alignement à gauche

- ES_CENTER pour alignement au centre

- ES_RIGHT pour l’alignement à droite

Pour plus d’informations sur ces styles, consultez [modifier les Styles de contrôle](/windows/desktop/Controls/edit-control-styles).

##  <a name="setwidth"></a>  CMFCRibbonEdit::SetWidth

Définit la largeur de la zone de texte pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Paramètres

*nWidth*<br/>
[in] La largeur, en pixels, de la zone de texte.

*bInFloatyMode*<br/>
TRUE pour définir la largeur pour le mode flottante ; Pour définir la largeur pour le mode normal, la valeur est FALSE.

### <a name="remarks"></a>Notes

Le `CMFCRibbonEdit` contrôle a deux largeurs en fonction de son mode d’affichage : flottante mode et le mode normal.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar, classe](../../mfc/reference/cmfcribbonbar-class.md)
