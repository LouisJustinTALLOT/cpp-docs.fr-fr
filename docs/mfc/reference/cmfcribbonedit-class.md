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
ms.openlocfilehash: ab621a05f9b658eee9babb14e257680fa95e0f96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375178"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit, classe

Implémente un contrôle de modification qui est situé sur une barre de ruban.

## <a name="syntax"></a>Syntaxe

```cpp
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
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Indique si la `CMFCRibbonEdit` hauteur du contrôle peut augmenter verticalement jusqu’à la hauteur d’une rangée de rubans.|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construit un objet `CMFCRibbonEdit`.|
|[CMFCRibbonEdit::CopyDe](#copyfrom)|Copie l’état `CMFCRibbonEdit` de l’objet spécifié à l’objet actuel. `CMFCRibbonEdit`|
|[CMFCRibbonEdit::CréerEdit](#createedit)|Crée une nouvelle boîte `CMFCRibbonEdit` de texte pour l’objet.|
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Détruit l’objet. `CMFCRibbonEdit`|
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Dépose une boîte de liste.|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Permet et définit la gamme du bouton de spin pour la boîte de texte.|
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Récupère la taille compacte de l’objet. `CFMCRibbonEdit`|
|[CMFCRibbonEdit::GetEditText](#getedittext)|Récupère le texte dans la boîte à texte.|
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Récupère la taille intermédiaire `CMFCRibbonEdit` de l’objet.|
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Récupère l’alignement du texte dans la boîte à texte.|
|[CMFCRibbonEdit::GetWidth](#getwidth)|Récupère la largeur, en pixels, du `CMFCRibbonEdit` contrôle.|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indique si la taille `CMFCRibbonEdit` de l’écran pour le contrôle peut être compacte.|
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indique si `CMFCRIbbonEdit` le contrôle a l’accent.|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indique si la taille `CMFCRibbonEdit` de l’affichage pour le contrôle peut être grande.|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indique si la boîte de texte a un bouton de rotation.|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indique si `CMFCRibbonEdit` le contrôle est mis en évidence.|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Appelé par le cadre lorsque les dimensions `CMFCRibbonEdit` du rectangle d’affichage pour le contrôle change.|
|[CMFCRibbonEdit::OnDraw](#ondraw)|Appelé par le cadre `CMFCRibbonEdit` pour tirer le contrôle.|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Appelé par le cadre pour dessiner `CMFCRibbonEdit` l’étiquette et l’image pour le contrôle.|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Appelé par le cadre `CMFCRibbonEdit` pour dessiner le contrôle dans une boîte de liste de commandes.|
|[CMFCRibbonEdit::OnEnable](#onenable)|Appelé par le cadre pour `CMFCRibbonEdit` activer ou désactiver le contrôle.|
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Appelé par le cadre lorsque le pointeur entre `CMFCRibbonEdit` ou quitte les limites du contrôle.|
|[CMFCRibbonEdit::OnKey](#onkey)|Appelé par le cadre lorsque l’utilisateur appuie `CMFCRibbonEdit` sur un keytip et le contrôle a la mise au point.|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Appelé par le cadre `CMFCRibbonEdit` pour mettre à jour le contrôle lorsque l’utilisateur appuie sur le bouton de la souris gauche sur le contrôle.|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Appelé par le cadre lorsque l’utilisateur libère le bouton de la souris gauche.|
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Appelé par le cadre `CMFCRibbonEdit` pour mettre à jour le contrôle lorsque la mise en page change de direction.|
|[CMFCRibbonEdit::OnShow](#onshow)|Appelé par le cadre pour `CMFCRibbonEdit` montrer ou cacher le contrôle.|
|[CMFCRibbonEdit::Redraw](#redraw)|Mise à jour `CMFCRibbonEdit` de l’affichage du contrôle.|
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Définit les données `CMFCRibbonEdit` d’accessibilité de l’objet.|
|[CMFCRibbonEdit::SetEditText](#setedittext)|Définit le texte dans la boîte à texte.|
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Définit l’alignement de texte de la boîte de texte.|
|[CMFCRibbonEdit::SetWidth](#setwidth)|Définit la largeur de la `CMFCRibbonEdit` boîte de texte pour le contrôle.|

## <a name="remarks"></a>Notes

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCRibbonEdit` construire un objet, afficher les boutons de rotation à côté du contrôle de modification et définir le texte du contrôle de modification. Cet extrait de code fait partie de [l’échantillon de démonstration ms Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** afxRibbonEdit.h

## <a name="cmfcribboneditcanbestretched"></a><a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched

Indique si la hauteur du contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) peut augmenter verticalement jusqu’à la hauteur d’une rangée de rubans.

```cpp
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditcmfcribbonedit"></a><a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit

Construit un objet [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[dans] Carte d’identité pour le `CMFCRibbonEdit` contrôle.

*nWidth (en)*<br/>
[dans] La largeur, en pixels, de `CMFCRibbonEdit` la boîte de texte pour le contrôle.

*lpszLabel*<br/>
[dans] L’étiquette `CMFCRibbonEdit` pour le contrôle.

*nImage (en)*<br/>
[dans] Index de la petite image `CMFCRibbonEdit` à utiliser pour le contrôle. La collection de petites images est maintenue par la catégorie ruban parent.

### <a name="remarks"></a>Notes

Le `CMFCRibbonEdit` contrôle n’utilise pas une grande image.

## <a name="cmfcribboneditcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonEdit::CopyDe

Copie de l’état de l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) spécifié à l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) actuel.

```cpp
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[dans] L’objet source. `CMFCRibbonEdit`

### <a name="remarks"></a>Notes

Le paramètre *de* cr `CMFCRibbonEdit`doit être de type .

## <a name="cmfcribboneditcreateedit"></a><a name="createedit"></a>CMFCRibbonEdit::CréerEdit

Crée une nouvelle boîte de texte pour l’objet [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Un pointeur à la `CMFCRibbonEdit` fenêtre parente de l’objet.

*dwEditStyle (en)*<br/>
[dans] Spécifie le style de la boîte à texte. Vous pouvez combiner les styles de fenêtre répertoriés dans la section Remarques avec les [styles de contrôle de modification](/windows/win32/Controls/edit-control-styles) qui sont décrits dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la nouvelle boîte de texte si la méthode a été réussie; autrement, NULL.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée pour créer une boîte de texte personnalisée.

Vous pouvez appliquer les [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) suivants à une boîte de texte :

- **WS_CHILD**

- **Ws_visible**

- **WS_DISABLED**

- **WS_GROUP**

- **Ws_tabstop**

## <a name="cmfcribboneditdestroyctrl"></a><a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl

Détruit l’objet [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditdropdownlist"></a><a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList

Dépose une boîte de liste.

```cpp
virtual void DropDownList();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode ne fait rien. Remplacez cette méthode pour déposer une boîte de liste.

## <a name="cmfcribboneditenablespinbuttons"></a><a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons

Permet et définit la gamme du bouton de spin pour la boîte de texte.

```cpp
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Paramètres

*Nmin*<br/>
[dans] La valeur minimale du bouton de spin.

*Nmax*<br/>
[dans] La valeur maximale du bouton de rotation.

### <a name="remarks"></a>Notes

Les boutons de rotation affichent une flèche de haut en bas et permettent aux utilisateurs de se déplacer à travers un ensemble fixe de valeurs.

## <a name="cmfcribboneditgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize

Récupère la taille compacte de l’objet [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un `CMFCRibbonEdit` contexte d’appareil pour l’objet.

### <a name="return-value"></a>Valeur de retour

La taille compacte de l’objet. `CMFCRibbonEdit`

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditgetedittext"></a><a name="getedittext"></a>CMFCRibbonEdit::GetEditText

Récupère le texte dans la boîte à texte.

```cpp
CString GetEditText() const;
```

### <a name="return-value"></a>Valeur de retour

Le texte dans la boîte à texte.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize

Récupère la taille intermédiaire de l’objet [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un `CMFCRibbonEdit` contexte d’appareil pour l’objet.

### <a name="return-value"></a>Valeur de retour

La taille intermédiaire `CMFCRibbonEdit` de l’objet.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditgettextalign"></a><a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign

Récupère l’alignement du texte dans la boîte à texte.

```cpp
int GetTextAlign() const;
```

### <a name="return-value"></a>Valeur de retour

Un alignement de texte énumère la valeur. Consultez la section Remarques pour les valeurs possibles.

### <a name="remarks"></a>Notes

La valeur retournée est l’un des styles de contrôle de modification suivants :

- **ES_LEFT** pour l’alignement gauche

- **ES_CENTER** pour l’alignement du centre

- **ES_RIGHT** pour un bon alignement

Pour plus d’informations sur ces styles, voir [Edit Control Styles](/windows/win32/Controls/edit-control-styles).

## <a name="cmfcribboneditgetwidth"></a><a name="getwidth"></a>CMFCRibbonEdit::GetWidth

Récupère la largeur, en pixels, du contrôle [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>Paramètres

*bInFloatyMode*<br/>
[dans] VRAI si `CMFCRibbonEdit` le contrôle est en mode flottant; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

La largeur, en pixels, du `CMFCRibbonEdit` contrôle.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonedithascompactmode"></a><a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode

Indique si la taille d’affichage du contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) peut être compacte.

```cpp
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours VRAI.

### <a name="remarks"></a>Notes

Par défaut, cette méthode renvoie toujours VRAI. Remplacez cette méthode pour indiquer si la taille de l’écran peut être compacte.

## <a name="cmfcribbonedithasfocus"></a><a name="hasfocus"></a>CMFCRibbonEdit::HasFocus

Indique si le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) a l’accent.

```cpp
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si `CMFCRibbonEdit` le contrôle a l’accent; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonedithaslargemode"></a><a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode

Indique si la taille d’affichage pour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) peut être grande.

```cpp
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne toujours FALSE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode renvoie toujours FALSE. Remplacer cette méthode pour indiquer si la taille de l’écran peut être grande.

## <a name="cmfcribbonedithasspinbuttons"></a><a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons

Indique si la boîte de texte a un bouton de rotation.

```cpp
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la boîte de texte a un bouton de spin; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditishighlighted"></a><a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted

Indique si le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) est mis en évidence.

```cpp
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si `CMFCRibbonEdit` le contrôle est mis en évidence; autrement FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditonafterchangerect"></a><a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect

Appelé par le cadre lorsque les dimensions du rectangle d’affichage pour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) changent.

```cpp
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un `CMFCRibbonEdit` contexte d’appareil pour le contrôle.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditondraw"></a><a name="ondraw"></a>CMFCRibbonEdit::OnDraw

Appelé par le cadre pour dessiner le contrôle [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un `CMFCRibbonEdit` contexte d’appareil pour le contrôle.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditondrawlabelandimage"></a><a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage

Appelé par le cadre pour dessiner l’étiquette et l’image pour le contrôle [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers un `CMFCRibbonEdit` contexte d’appareil pour le contrôle.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList

Appelé par le cadre pour dessiner le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) dans une boîte de liste de commandes.

```cpp
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
[dans] Pointeur vers un `CMFCRibbonEdit` contexte d’appareil pour le contrôle.

*strText (en)*<br/>
[dans] Le texte [ ](../../mfc/reference/cmfcribbonedit-class.md "classe cmfcribbonedit")d’affichage .

*nTextOffset (en anglais)*<br/>
[dans] Distance, en pixels, du côté gauche de la boîte de liste au texte d’affichage.

*Rect*<br/>
[dans] Le rectangle d’affichage pour le `CMFCRibbonEdit` contrôle.

*bIsSelected*<br/>
[dans] Ce paramètre n’est pas utilisé.

*bHighlighted*<br/>
[dans] Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

La boîte de liste de commandes affiche les commandes de ruban pour permettre aux utilisateurs de personnaliser la barre d’outils d’accès rapide.

## <a name="cmfcribboneditonenable"></a><a name="onenable"></a>CMFCRibbonEdit::OnEnable

Appelé par le cadre pour activer ou désactiver le contrôle [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour permettre le contrôle; FALSE pour désactiver le contrôle.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditonhighlight"></a><a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight

Appelé par le cadre lorsque le pointeur entre ou quitte les limites du contrôle [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>Paramètres

*bHighlight (en)*<br/>
[dans] VRAI si le pointeur est `CMFCRibbonEdit` dans les limites du contrôle; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditonkey"></a><a name="onkey"></a>CMFCRibbonEdit::OnKey

Appelé par le cadre lorsque l’utilisateur appuie sur un keytip et le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) a la mise au point.

```cpp
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>Paramètres

*bIsMenuKey (en anglais)*<br/>
[dans] VRAI si le keytip affiche un menu pop-up; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

VRAI si l’événement a été géré; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditonlbuttondown"></a><a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown

Appelé par le cadre pour mettre à jour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) lorsque l’utilisateur appuie sur le bouton de la souris gauche sur le contrôle.

```cpp
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
[dans] Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditonlbuttonup"></a><a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

Appelé par le cadre lorsque l’utilisateur libère le bouton de la souris gauche.

```cpp
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>Paramètres

*Point*<br/>
[dans] Ce paramètre n’est pas utilisé.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditonrtlchanged"></a><a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged

Appelé par le cadre pour mettre à jour le contrôle [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) lorsque la mise en page change de direction.

```cpp
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>Paramètres

*bIsRTL (en)*<br/>
[dans] VRAI si la disposition est de droite à gauche; FALSE si la disposition est de gauche à droite.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditonshow"></a><a name="onshow"></a>CMFCRibbonEdit::OnShow

Appelé par le cadre pour montrer ou cacher le contrôle [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
[dans] VRAI pour montrer le contrôle; FALSE pour cacher le contrôle.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditredraw"></a><a name="redraw"></a>CMFCRibbonEdit::Redraw

Mise à jour de l’affichage du contrôle [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>Notes

Cette méthode redessine le `CMFCRibbonEdit` rectangle d’affichage pour l’objet en appelant indirectement [CWnd::RedrawWindow](/windows/win32/api/winuser/nf-winuser-redrawwindow) avec le RDW_INVALIDATE, RDW_ERASE, et RDW_UPDATENOW drapeaux ensemble.

## <a name="cmfcribboneditsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonEdit::SetACCData

Définit les données d’accessibilité de l’objet [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
Pointeur vers la `CMFCRibbonEdit` fenêtre parente de l’objet.

*data*<br/>
Les données d’accessibilité de l’objet. `CMFCRibbonEdit`

### <a name="return-value"></a>Valeur de retour

Retourne toujours VRAI.

### <a name="remarks"></a>Notes

## <a name="cmfcribboneditsetedittext"></a><a name="setedittext"></a>CMFCRibbonEdit::SetEditText

Définit le texte dans la boîte à texte.

```cpp
void SetEditText(CString strText);
```

### <a name="parameters"></a>Paramètres

*strText (en)*<br/>
[dans] Le texte de la boîte à texte.

## <a name="cmfcribboneditsettextalign"></a><a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign

Définit l’alignement de texte de la boîte de texte.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Paramètres

*nAlign*<br/>
[dans] Un alignement de texte énumère la valeur. Consultez la section Remarques pour les valeurs possibles.

### <a name="remarks"></a>Notes

Le paramètre *nAlign* est l’un des styles de contrôle de modification suivants:

- ES_LEFT pour l’alignement gauche

- ES_CENTER pour l’alignement du centre

- ES_RIGHT pour un bon alignement

Pour plus d’informations sur ces styles, voir [Edit Control Styles](/windows/win32/Controls/edit-control-styles).

## <a name="cmfcribboneditsetwidth"></a><a name="setwidth"></a>CMFCRibbonEdit::SetWidth

Définit la largeur de la boîte de texte pour le contrôle [CMFCRibbonEdit.](../../mfc/reference/cmfcribbonedit-class.md)

```cpp
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>Paramètres

*nWidth (en)*<br/>
[dans] La largeur, en pixels, de la boîte à texte.

*bInFloatyMode*<br/>
VRAI pour régler la largeur pour le mode flottant; FALSE pour définir la largeur pour le mode régulier.

### <a name="remarks"></a>Notes

Le `CMFCRibbonEdit` contrôle a deux largeurs en fonction de son mode d’affichage: mode flottant et mode régulier.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
