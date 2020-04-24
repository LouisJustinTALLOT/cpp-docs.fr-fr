---
title: Classe CFontDialog
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
ms.openlocfilehash: 6a8e24b68f377235c1f1e21fbcd5618aebbe299a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755015"
---
# <a name="cfontdialog-class"></a>Classe CFontDialog

Vous permet d’incorporer une boîte de dialogue de sélection de polices dans votre application.

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
|[CFontDialog::DoModal](#domodal)|Affiche le dialogue et permet à l’utilisateur de faire une sélection.|
|[CFontDialog::GetCharFormat](#getcharformat)|Récupère le formatage des personnages de la police sélectionnée.|
|[CFontDialog::GetColor](#getcolor)|Retourne la couleur de la police sélectionnée.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Attribue les caractéristiques de la `LOGFONT` police actuellement sélectionnée à une structure.|
|[CFontDialog::GetFaceName](#getfacename)|Retourne le nom du visage de la police sélectionnée.|
|[CFontDialog::GetSize](#getsize)|Retourne la taille du point de la police sélectionnée.|
|[CFontDialog::GetStyleName](#getstylename)|Retourne le nom de style de la police sélectionnée.|
|[CFontDialog::GetWeight](#getweight)|Retourne le poids de la police sélectionnée.|
|[CFontDialog::IsBold](#isbold)|Détermine si la police est audacieuse.|
|[CFontDialog::IsItalic](#isitalic)|Détermine si la police est italique.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Détermine si la police est affichée avec strikeout.|
|[CFontDialog::IsUnderline](#isunderline)|Détermine si la police est soulignée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Une structure utilisée pour `CFontDialog` personnaliser un objet.|

## <a name="remarks"></a>Notes

Un `CFontDialog` objet est une boîte de dialogue avec une liste de polices qui sont actuellement installées dans le système. L’utilisateur peut sélectionner une police particulière de la liste, et cette sélection est ensuite signalée à l’application.

Pour construire `CFontDialog` un objet, utilisez le constructeur fourni ou dérivez une nouvelle sous-classe et utilisez votre propre constructeur personnalisé.

Une `CFontDialog` fois qu’un objet a `m_cf` été construit, vous pouvez utiliser la structure pour initialiser les valeurs ou les états de contrôles dans la boîte de dialogue. La structure [m_cf](#m_cf) est de type [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Pour plus d’informations sur cette structure, voir le SDK Windows.

Après avoir paralysé les commandes `DoModal` de l’objet de dialogue, appelez la fonction du membre pour afficher la boîte de dialogue et permettre à l’utilisateur de sélectionner une police. `DoModal`l’utilisateur a choisi le bouton OK (IDOK) ou Annuler (IDCANCEL).

Si `DoModal` vous retournez IDOK, `CFontDialog`vous pouvez utiliser l’une des fonctions des membres pour récupérer l’entrée d’informations par l’utilisateur.

Vous pouvez utiliser la fonction Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, voir le SDK Windows.

`CFontDialog`s’appuie sur le COMMDLG. Fichier DLL qui expédie avec les versions Windows 3.1 et plus tard.

Pour personnaliser la boîte de dialogue, `CFontDialog`dérivez une classe, fournissez un modèle de dialogue personnalisé et ajoutez une carte de message pour traiter les messages de notification à partir des contrôles étendus. Tous les messages non traités doivent être transmis à la classe de base.

Personnaliser la fonction de crochet n’est pas nécessaire.

Pour plus d’informations sur l’utilisation `CFontDialog`, voir Classes de dialogue [commun](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdlgs.h

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a>CFontDialog::CFontDialog

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
Un pointeur vers une structure de données [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) qui vous permet de définir certaines caractéristiques de la police.

*charFormat*<br/>
Un pointeur vers une structure de données [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) qui vous permet de définir certaines des caractéristiques de la police dans un contrôle d’édition riche.

*dwFlags*<br/>
Spécifie un ou plusieurs indicateurs de choix de police. Une ou plusieurs valeurs prédéfinies peuvent être combinées à l'aide de l'opérateur de bits OR. Si vous changez le membre de structure de `m_cf.Flag`, veillez à utiliser un opérateur de bits OR dans les changements pour préserver le comportement par défaut. Pour plus de détails sur chacun de ces drapeaux, consultez la description de la structure [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) dans le SDK Windows.

*pdcPrinter (en)*<br/>
Pointeur vers un contexte de périphérique d'impression. Si ce paramètre est fourni, il pointe vers un contexte de périphérique d'impression pour l'imprimante sur laquelle les polices doivent être sélectionnées.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou la fenêtre propriétaire de la boîte de dialogue de police.

### <a name="remarks"></a>Notes

Notez que le constructeur remplit automatiquement les membres de la structure `CHOOSEFONT`. Ne les modifiez que si vous souhaitez une autre boîte de dialogue de police que celle par défaut.

> [!NOTE]
> La première version de cette fonction n'existe que s'il n'y a aucune prise en charge du contrôle RichEdit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a>CFontDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue de police commune de Windows et permettre à l’utilisateur de choisir une police.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retourné, appelez la fonction Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) pour déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a choisi le bouton OK ou Annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez paralyser les différents contrôles de dialogue de police en fixant `DoModal`les membres de la structure [m_cf,](#m_cf) vous devriez le faire avant d’appeler, mais après la construction de l’objet de dialogue.

Si `DoModal` vous retournez IDOK, vous pouvez appeler d’autres fonctions de membre pour récupérer les paramètres ou l’entrée d’informations par l’utilisateur dans la boîte de dialogue.

### <a name="example"></a>Exemple

  Voir les exemples de [CFontDialog::CFontDialog](#cfontdialog) et [CFontDialog::GetColor](#getcolor).

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a>CFontDialog::GetCharFormat

Récupère le formatage des personnages de la police sélectionnée.

```cpp
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Paramètres

*Cf*<br/>
Une structure [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) contenant des informations sur le formatage des personnages de la police sélectionnée.

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a>CFontDialog::GetColor

Appelez cette fonction pour récupérer la couleur de police sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Couleur de la police sélectionnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

Appelez cette fonction pour attribuer les caractéristiques de la police actuellement sélectionnée aux membres d’une structure [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

```cpp
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Paramètres

*lplf (lplf)*<br/>
Un pointeur `LOGFONT` vers une structure.

### <a name="remarks"></a>Notes

D’autres `CFontDialog` fonctions de membre sont fournies pour accéder aux caractéristiques individuelles de la police actuelle.

Si cette fonction est appelée lors d’un appel à [DoModal](#domodal), il renvoie la sélection actuelle à l’époque (ce que l’utilisateur voit ou a changé dans le dialogue). Si cette fonction est appelée `DoModal` après `DoModal` un appel à (seulement si retourne IDOK), il renvoie ce que l’utilisateur effectivement sélectionné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a>CFontDialog::GetFaceName

Appelez cette fonction pour récupérer le nom du visage de la police sélectionnée.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du visage de `CFontDialog` la police sélectionnée dans la boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a>CFontDialog::GetSize

Appelez cette fonction pour récupérer la taille de la police sélectionnée.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille de la police, en dixièmes de point.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a>CFontDialog::GetStyleName

Appelez cette fonction pour récupérer le nom de style de la police sélectionnée.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de style de la police.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a>CFontDialog::GetWeight

Appelez cette fonction pour récupérer le poids de la police sélectionnée.

```
int GetWeight() const;
```

### <a name="return-value"></a>Valeur de retour

Le poids de la police sélectionnée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le poids d’une police, voir [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a>CFontDialog::IsBold

Appelez cette fonction pour déterminer si la police sélectionnée est audacieuse.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la police sélectionnée a la caractéristique audacieuse activée; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a>CFontDialog::IsItalic

Appelez cette fonction pour déterminer si la police sélectionnée est italique.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la police sélectionnée a la caractéristique italique activée; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a>CFontDialog::IsStrikeOut

Appelez cette fonction pour déterminer si la police sélectionnée est affichée avec strikeout.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la police sélectionnée a la caractéristique Strikeout activé; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a>CFontDialog::IsUnderline

Appelez cette fonction pour déterminer si la police sélectionnée est soulignée.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la police sélectionnée a la caractéristique De souligné activé; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a>CFontDialog::m_cf

Une structure dont les membres stockent les caractéristiques de l’objet de dialogue.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Notes

Après la `CFontDialog` construction d’un `m_cf` objet, vous pouvez utiliser pour `DoModal` modifier divers aspects de la boîte de dialogue avant d’appeler la fonction membre. Pour plus d’informations sur cette structure, voir [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Classe CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
