---
title: CMFCColorDialog, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 9e018c122cded09e5366c3b349525fa7cc004897
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505343"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog, classe

La `CMFCColorDialog` classe représente une boîte de dialogue de sélection de couleur.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Construit un objet `CMFCColorDialog`.|
|`CMFCColorDialog::~CMFCColorDialog`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCColorDialog:: GetColor](#getcolor)|Retourne la couleur actuellement sélectionnée.|
|[CMFCColorDialog::GetPalette](#getpalette)|Retourne la palette de la couleur.|
|`CMFCColorDialog::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Pour plus d’informations sur la syntaxe et plus d’informations, consultez [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CDialogEx::PreTranslateMessage`.)|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Dérive une palette de la palette système.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Définit la couleur actuellement sélectionnée.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Définit la couleur la plus équivalente à une valeur RVB spécifiée.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Sélectionne une valeur RVB pour la première page de propriétés.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Sélectionne une valeur RVB pour la deuxième page de propriétés.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|`m_bIsMyPalette`|TRUE si la boîte de dialogue de sélection de couleurs utilise sa propre palette de couleurs, ou false si la boîte de dialogue utilise une `CMFCColorDialog` palette spécifiée dans le constructeur.|
|`m_bPickerMode`|TRUE lorsque l’utilisateur sélectionne une couleur dans la boîte de dialogue de sélection; Sinon, FALSe.|
|`m_btnColorSelect`|Bouton de couleur sélectionné par l’utilisateur.|
|`m_CurrentColor`|Couleur actuellement sélectionnée.|
|`m_hcurPicker`|Curseur utilisé pour choisir une couleur.|
|`m_NewColor`|Couleur sélectionnée potentielle, qui peut être sélectionnée ou restaurée définitivement à la couleur d’origine.|
|`m_pColourSheetOne`|Pointeur vers la première page de propriétés de la feuille de propriétés de sélection de couleurs.|
|`m_pColourSheetTwo`|Pointeur vers la deuxième page de propriétés de la feuille de propriétés de sélection de couleurs.|
|`m_pPalette`|Palette logique actuelle.|
|`m_pPropSheet`|Pointeur vers la feuille de propriétés de la boîte de dialogue de sélection de couleur.|
|`m_wndColors`|Objet de contrôle de sélecteur de couleurs.|
|`m_wndStaticPlaceHolder`|Contrôle statique qui est un espace réservé pour la feuille de propriétés du sélecteur de couleurs.|

## <a name="remarks"></a>Notes

La boîte de dialogue de sélection de couleur s’affiche sous la forme d’une feuille de propriétés avec deux pages. Sur la première page, vous sélectionnez une couleur standard dans la palette système. dans la deuxième page, vous sélectionnez une couleur personnalisée.

Vous pouvez construire un `CMFCColorDialog` objet sur la pile, puis appeler `DoModal`, `CMFCColorDialog` en passant la couleur initiale en tant que paramètre au constructeur. La boîte de dialogue de sélection de couleur crée alors plusieurs objets de [classe CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) pour gérer chaque palette de couleurs.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer une boîte de dialogue de couleur à l’aide de `CMFCColorDialog` différentes méthodes dans la classe. L’exemple montre comment définir les couleurs actuelles et nouvelles de la boîte de dialogue, et comment définir les composants rouge, vert et bleu d’une couleur sélectionnée dans les deux pages de propriétés de la boîte de dialogue de couleurs. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête:** afxcolordialog. h

##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog

Construit un objet `CMFCColorDialog`.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>Paramètres

*clrInit*<br/>
dans Sélection de couleur par défaut. Si aucune valeur n’est spécifiée, la valeur par défaut est RVB (0, 0, 0) (noir).

*dwFlags*<br/>
[in] Réservée.

*pParentWnd*<br/>
dans Pointeur vers la fenêtre parente ou propriétaire de la boîte de dialogue.

*hPal*<br/>
dans Handle d’une palette de couleurs.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getcolor"></a>CMFCColorDialog:: GetColor

Récupère la couleur que l’utilisateur sélectionne dans la boîte de dialogue de couleur.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur [COLORREF](/windows/win32/gdi/colorref) qui contient les informations RVB de la couleur sélectionnée dans la boîte de dialogue couleur.

### <a name="remarks"></a>Notes

Appelez cette fonction après avoir appelé la `DoModal` méthode.

##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette

Récupère la palette de couleurs qui est disponible dans la boîte de dialogue de couleur actuelle.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l' `CPalette` objet qui a été spécifié dans le `CMFCColorDialog` constructeur.

### <a name="remarks"></a>Notes

La palette de couleurs spécifie les couleurs que l’utilisateur peut choisir.

##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette

Dérive une palette de la palette système.

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

Définit la couleur actuelle de la boîte de dialogue.

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Paramètres

*rgb*<br/>
dans Une valeur de couleur RVB

### <a name="remarks"></a>Notes

##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor

Définit la couleur actuelle sur la couleur de la palette actuelle qui est la plus similaire.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Paramètres

*rgb*<br/>
dans [COLORREF](/windows/win32/gdi/colorref) qui spécifie une couleur RVB.

### <a name="remarks"></a>Notes

##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne

Spécifie explicitement les composants rouge, vert et bleu d’une couleur sélectionnée sur la première page de propriétés d’une boîte de dialogue de couleur.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Paramètres

*R*<br/>
dans Spécifie le composant rouge de la valeur RVB.

*G*<br/>
dans Spécifie le composant vert de la valeur RVB.

*B*<br/>
dans Spécifie le composant bleu de la valeur RVB.

### <a name="remarks"></a>Notes

##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo

Spécifie explicitement les composants rouge, vert et bleu d’une couleur sélectionnée dans la deuxième page de propriétés d’une boîte de dialogue de couleur.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Paramètres

*R*<br/>
dans Spécifie un composant rouge de la valeur RVB

*G*<br/>
dans Spécifie un composant vert d’une valeur RVB

*B*<br/>
dans Spécifie un composant bleu d’une valeur RVB

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl, classe](../../mfc/reference/cmfccolorpickerctrl-class.md)
