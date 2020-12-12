---
description: 'En savoir plus sur : classe CFontDialog'
title: CFontDialog, classe
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: c1f8637a6106db9220721dffe67a2ed1d53b26b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184346"
---
# <a name="cfontdialog-class"></a>CFontDialog, classe

Vous permet d’incorporer une boîte de dialogue de sélection de polices à votre application.

## <a name="syntax"></a>Syntaxe

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Construit un objet `CFontDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFontDialog ::D oModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer une sélection.|
|[CFontDialog::GetCharFormat](#getcharformat)|Récupère la mise en forme des caractères de la police sélectionnée.|
|[CFontDialog :: GetColor](#getcolor)|Retourne la couleur de la police sélectionnée.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Assigne les caractéristiques de la police actuellement sélectionnée à une `LOGFONT` structure.|
|[CFontDialog::GetFaceName](#getfacename)|Retourne le nom de police de la police sélectionnée.|
|[CFontDialog :: est à obtenir](#getsize)|Retourne la taille en points de la police sélectionnée.|
|[CFontDialog::GetStyleName](#getstylename)|Retourne le nom du style de la police sélectionnée.|
|[CFontDialog::GetWeight](#getweight)|Retourne l’épaisseur de la police sélectionnée.|
|[CFontDialog::IsBold](#isbold)|Détermine si la police est en gras.|
|[CFontDialog::IsItalic](#isitalic)|Détermine si la police est en italique.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Détermine si la police est affichée avec un barré.|
|[CFontDialog::IsUnderline](#isunderline)|Détermine si la police est soulignée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFontDialog :: m_cf](#m_cf)|Structure utilisée pour personnaliser un `CFontDialog` objet.|

## <a name="remarks"></a>Notes

Un `CFontDialog` objet est une boîte de dialogue avec une liste des polices qui sont actuellement installées dans le système. L’utilisateur peut sélectionner une police particulière dans la liste, et cette sélection est ensuite renvoyée à l’application.

Pour construire un `CFontDialog` objet, utilisez le constructeur fourni ou dérivez une nouvelle sous-classe et utilisez votre propre constructeur personnalisé.

Une fois qu’un `CFontDialog` objet a été construit, vous pouvez utiliser la `m_cf` structure pour initialiser les valeurs ou les États des contrôles dans la boîte de dialogue. La structure [m_cf](#m_cf) est de type [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Pour plus d’informations sur cette structure, consultez la SDK Windows.

Après l’initialisation des contrôles de l’objet Dialog, appelez la `DoModal` fonction membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner une police. `DoModal` retourne une valeur indiquant si l’utilisateur a sélectionné le bouton OK (IDOK) ou CANCEL (IDCANCEL).

Si `DoModal` retourne IDOK, vous pouvez utiliser l’une des `CFontDialog` fonctions membres de pour récupérer les informations entrées par l’utilisateur.

Vous pouvez utiliser la fonction [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, consultez la SDK Windows.

`CFontDialog` s’appuie sur le fichier de COMMDLG.DLL fourni avec les versions de Windows 3,1 et ultérieures.

Pour personnaliser la boîte de dialogue, dérivez une classe de `CFontDialog` , fournissez un modèle de boîte de dialogue personnalisé et ajoutez une table des messages pour traiter les messages de notification des contrôles étendus. Tous les messages non traités doivent être passés à la classe de base.

La personnalisation de la fonction de raccordement n’est pas obligatoire.

Pour plus d’informations sur l’utilisation de `CFontDialog` , consultez [classes de boîtes de dialogue communes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdlgs. h

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a> CFontDialog::CFontDialog

Construit un objet `CFontDialog`.

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Paramètres

*plfInitial*<br/>
Pointeur vers une structure de données [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) qui vous permet de définir certaines caractéristiques de la police.

*charFormat*<br/>
Pointeur vers une structure de données [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) qui vous permet de définir certaines caractéristiques de la police dans un contrôle RichEdit.

*dwFlags*<br/>
Spécifie un ou plusieurs indicateurs de choix de police. Une ou plusieurs valeurs prédéfinies peuvent être combinées à l'aide de l'opérateur de bits OR. Si vous changez le membre de structure de `m_cf.Flag`, veillez à utiliser un opérateur de bits OR dans les changements pour préserver le comportement par défaut. Pour plus d’informations sur chacun de ces indicateurs, consultez la description de la structure [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) dans le SDK Windows.

*pdcPrinter*<br/>
Pointeur vers un contexte de périphérique d'impression. Si ce paramètre est fourni, il pointe vers un contexte de périphérique d'impression pour l'imprimante sur laquelle les polices doivent être sélectionnées.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou la fenêtre propriétaire de la boîte de dialogue de police.

### <a name="remarks"></a>Notes

Notez que le constructeur remplit automatiquement les membres de la structure `CHOOSEFONT`. Ne les modifiez que si vous souhaitez une autre boîte de dialogue de police que celle par défaut.

> [!NOTE]
> La première version de cette fonction n'existe que s'il n'y a aucune prise en charge du contrôle RichEdit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a> CFontDialog ::D oModal

Appelez cette fonction pour afficher la boîte de dialogue police commune Windows et autoriser l’utilisateur à choisir une police.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur renvoyée

IDOK ou IDCANCEL. Si IDCANCEL est retourné, appelez la fonction [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows pour déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les différents contrôles de boîte de dialogue de police en définissant les membres de la structure [m_cf](#m_cf) , vous devez effectuer cette opération avant d’appeler `DoModal` , mais après la construction de l’objet de boîte de dialogue.

Si `DoModal` retourne IDOK, vous pouvez appeler d’autres fonctions membres pour récupérer les paramètres ou les informations entrées par l’utilisateur dans la boîte de dialogue.

### <a name="example"></a>Exemple

  Consultez les exemples pour [CFontDialog :: CFontDialog](#cfontdialog) et [CFontDialog :: GetColor](#getcolor).

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a> CFontDialog::GetCharFormat

Récupère la mise en forme des caractères de la police sélectionnée.

```cpp
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Paramètres

*Trésor*<br/>
Structure [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) contenant des informations sur la mise en forme des caractères de la police sélectionnée.

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a> CFontDialog :: GetColor

Appelez cette fonction pour récupérer la couleur de police sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur renvoyée

Couleur de la police sélectionnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a> CFontDialog::GetCurrentFont

Appelez cette fonction pour assigner les caractéristiques de la police actuellement sélectionnée aux membres d’une structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

```cpp
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Paramètres

*lplf*<br/>
Pointeur vers une `LOGFONT` structure.

### <a name="remarks"></a>Notes

D’autres `CFontDialog` fonctions membres sont fournies pour accéder aux caractéristiques individuelles de la police actuelle.

Si cette fonction est appelée pendant un appel à [DoModal](#domodal), elle retourne la sélection actuelle à l’heure (ce que l’utilisateur voit ou a modifié dans la boîte de dialogue). Si cette fonction est appelée après un appel à `DoModal` (uniquement si `DoModal` retourne IDOK), elle retourne ce que l’utilisateur a réellement sélectionné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a> CFontDialog::GetFaceName

Appelez cette fonction pour récupérer le nom de police de la police sélectionnée.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nom de police de la police sélectionnée dans la `CFontDialog` boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a> CFontDialog :: est à obtenir

Appelez cette fonction pour récupérer la taille de la police sélectionnée.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille de la police, en dixièmes de point.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a> CFontDialog::GetStyleName

Appelez cette fonction pour récupérer le nom de style de la police sélectionnée.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nom de style de la police.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a> CFontDialog::GetWeight

Appelez cette fonction pour récupérer le poids de la police sélectionnée.

```
int GetWeight() const;
```

### <a name="return-value"></a>Valeur renvoyée

Poids de la police sélectionnée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le poids d’une police, consultez [CFont :: CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a> CFontDialog::IsBold

Appelez cette fonction pour déterminer si la police sélectionnée est en gras.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la police sélectionnée a la caractéristique gras activée ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a> CFontDialog::IsItalic

Appelez cette fonction pour déterminer si la police sélectionnée est en italique.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la police sélectionnée a la caractéristique italique activée ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a> CFontDialog::IsStrikeOut

Appelez cette fonction pour déterminer si la police sélectionnée est affichée avec un barré.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la police sélectionnée a la caractéristique de barré activée ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a> CFontDialog::IsUnderline

Appelez cette fonction pour déterminer si la police sélectionnée est soulignée.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la police sélectionnée a la caractéristique souligné activée ; Sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a> CFontDialog :: m_cf

Structure dont les membres stockent les caractéristiques de l’objet Dialog.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CFontDialog` objet, vous pouvez utiliser `m_cf` pour modifier différents aspects de la boîte de dialogue avant d’appeler la `DoModal` fonction membre. Pour plus d’informations sur cette structure, consultez [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
