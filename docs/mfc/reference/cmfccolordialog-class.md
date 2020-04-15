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
ms.openlocfilehash: 987e4f1e5e89c3c56b58adaad76cfd23d5e26c52
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367718"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog, classe

La `CMFCColorDialog` classe représente une boîte de dialogue de sélection de couleurs.

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
|[CMFCColorDialog::GetColor](#getcolor)|Retourne la couleur sélectionnée actuelle.|
|[CMFCColorDialog::GetPalette](#getpalette)|Retourne la palette de la couleur.|
|`CMFCColorDialog::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows De TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Pour la syntaxe et plus d’informations, voir [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CDialogEx::PreTranslateMessage`.)|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Dérive une palette de la palette du système.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Définit la couleur sélectionnée en cours.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Définit la couleur la plus équivalente à une valeur RGB spécifiée.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Sélectionne une valeur RGB pour la première page de propriété.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Sélectionne une valeur RGB pour la deuxième page de propriété.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|`m_bIsMyPalette`|VRAI si la boîte de dialogue de sélection de couleur utilise sa propre palette de `CMFCColorDialog` couleurs, ou FALSE si la boîte de dialogue utilise une palette qui est spécifiée dans le constructeur.|
|`m_bPickerMode`|VRAI pendant que l’utilisateur sélectionne une couleur de la boîte de dialogue de sélection; autrement, FALSE.|
|`m_btnColorSelect`|Le bouton couleur que l’utilisateur a choisi.|
|`m_CurrentColor`|La couleur actuellement sélectionnée.|
|`m_hcurPicker`|Le curseur qui est utilisé pour choisir une couleur.|
|`m_NewColor`|La couleur sélectionnée prospective, qui peut être sélectionnée en permanence ou retournée à la couleur d’origine.|
|`m_pColourSheetOne`|Un pointeur à la première page de propriété de la feuille de propriété de sélection de couleur.|
|`m_pColourSheetTwo`|Un pointeur à la deuxième page de propriété de la feuille de propriété de sélection de couleur.|
|`m_pPalette`|La palette logique actuelle.|
|`m_pPropSheet`|Un pointeur à la feuille de propriété pour la boîte de dialogue de sélection de couleur.|
|`m_wndColors`|Un objet de contrôle de cueilleur de couleur.|
|`m_wndStaticPlaceHolder`|Un contrôle statique qui est un espace réservé pour la feuille de propriété de cueilleur de couleur.|

## <a name="remarks"></a>Notes

La boîte de dialogue de sélection de couleurs est affichée comme une feuille de propriété avec deux pages. Sur la première page, vous sélectionnez une couleur standard de la palette du système; sur la deuxième page, vous sélectionnez une couleur personnalisée.

Vous pouvez `CMFCColorDialog` construire un objet sur `DoModal`la pile, puis appeler, `CMFCColorDialog` en passant la couleur initiale comme un paramètre pour le constructeur. La boîte de dialogue de sélection de couleurs crée alors plusieurs objets [cmFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md) pour manipuler chaque palette de couleurs.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Exemple

L’exemple suivant montre comment configurer un dialogue de `CMFCColorDialog` couleur en utilisant diverses méthodes dans la classe. L’exemple montre comment définir le courant et les nouvelles couleurs du dialogue, et comment définir les composants rouges, verts et bleus d’une couleur sélectionnée sur les deux pages de propriété du dialogue de couleur. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête:** afxcolordialog.h

## <a name="cmfccolordialogcmfccolordialog"></a><a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog

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
[dans] La sélection de couleurs par défaut. Si aucune valeur n’est spécifiée, la valeur par défaut est RGB(0,0,0) (noir).

*dwFlags*<br/>
[in] Réservée.

*pParentWnd*<br/>
[dans] Un pointeur à la fenêtre parent ou propriétaire de la boîte de dialogue.

*hPal (en)*<br/>
[dans] Une poignée à une palette de couleurs.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfccolordialoggetcolor"></a><a name="getcolor"></a>CMFCColorDialog::GetColor

Récupère la couleur que l’utilisateur sélectionne à partir du dialogue couleur.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur [COLORREF](/windows/win32/gdi/colorref) qui contient les informations RGB pour la couleur sélectionnée dans la boîte de dialogue couleur.

### <a name="remarks"></a>Notes

Appelez cette fonction après `DoModal` avoir appelé la méthode.

## <a name="cmfccolordialoggetpalette"></a><a name="getpalette"></a>CMFCColorDialog::GetPalette

Récupère la palette de couleurs qui est disponible dans le dialogue de couleur actuel.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CPalette` de l’objet `CMFCColorDialog` qui a été spécifié dans le constructeur.

### <a name="remarks"></a>Notes

La palette de couleurs spécifie les couleurs que l’utilisateur peut choisir.

## <a name="cmfccolordialogrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette

Dérive une palette de la palette du système.

```
void RebuildPalette();
```

## <a name="cmfccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

Définit la couleur actuelle de la boîte de dialogue.

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Paramètres

*Rvb*<br/>
[dans] Une valeur de couleur RGB

### <a name="remarks"></a>Notes

## <a name="cmfccolordialogsetnewcolor"></a><a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

Définit la couleur actuelle à la couleur dans la palette actuelle qui est le plus similaire.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Paramètres

*Rvb*<br/>
[dans] Un [COLORREF](/windows/win32/gdi/colorref) qui spécifie une couleur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfccolordialogsetpageone"></a><a name="setpageone"></a>CMFCColorDialog::SetPageOne

Spécifie explicitement les composants rouges, verts et bleus d’une couleur sélectionnée sur la première page de propriété d’un dialogue de couleur.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Paramètres

*R*<br/>
[dans] Spécifie la composante rouge de la valeur RGB.

*G*<br/>
[dans] Spécifie la composante verte de la valeur RGB.

*B*<br/>
[dans] Spécifie le composant bleu de la valeur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfccolordialogsetpagetwo"></a><a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

Spécifie explicitement les composants rouges, verts et bleus d’une couleur sélectionnée sur la deuxième page de propriété d’un dialogue de couleur.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Paramètres

*R*<br/>
[dans] Spécifie une composante rouge de la valeur RGB

*G*<br/>
[dans] Spécifie une composante verte d’une valeur RGB

*B*<br/>
[dans] Spécifie un composant bleu d’une valeur RGB

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl, classe](../../mfc/reference/cmfccolorpickerctrl-class.md)
