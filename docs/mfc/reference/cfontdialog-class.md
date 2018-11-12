---
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
ms.openlocfilehash: 5c9e3a7de10b6ba0913b02c5f79dcc63c89adce5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525175"
---
# <a name="cfontdialog-class"></a>CFontDialog, classe

Vous pouvez ainsi incorporer une boîte de dialogue de sélection de la police dans votre application.

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
|[CFontDialog::DoModal](#domodal)|Affiche la boîte de dialogue et permet à l’utilisateur d’effectuer une sélection.|
|[CFontDialog::GetCharFormat](#getcharformat)|Récupère la mise en forme des caractères de la police sélectionnée.|
|[CFontDialog::GetColor](#getcolor)|Retourne la couleur de la police sélectionnée.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Assigne les caractéristiques de la police actuellement sélectionnée pour un `LOGFONT` structure.|
|[CFontDialog::GetFaceName](#getfacename)|Retourne le nom de police de la police sélectionnée.|
|[CFontDialog::GetSize](#getsize)|Retourne la taille du point de la police sélectionnée.|
|[CFontDialog::GetStyleName](#getstylename)|Retourne le nom de style de la police sélectionnée.|
|[CFontDialog::GetWeight](#getweight)|Retourne le poids de la police sélectionnée.|
|[CFontDialog::IsBold](#isbold)|Détermine si la police est gras.|
|[CFontDialog::IsItalic](#isitalic)|Détermine si la police est italique.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Détermine si la police est affichée avec barré.|
|[CFontDialog::IsUnderline](#isunderline)|Détermine si la police est soulignée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Une structure utilisée pour personnaliser un `CFontDialog` objet.|

## <a name="remarks"></a>Notes

Un `CFontDialog` objet est une boîte de dialogue avec une liste de polices qui sont actuellement installés dans le système. L’utilisateur peut sélectionner une police particulière dans la liste, et cette sélection est ensuite renvoyée à l’application.

Pour construire un `CFontDialog` de l’objet, utilisez le constructeur fourni ou dériver une nouvelle sous-classe et utiliser votre propre constructeur personnalisé.

Une fois un `CFontDialog` objet a été construit, vous pouvez utiliser le `m_cf` structure pour initialiser les valeurs ou les États de contrôles dans la boîte de dialogue. Le [m_cf](#m_cf) structure est de type [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta). Pour plus d’informations sur cette structure, consultez le Kit de développement Windows.

Après l’initialisation de contrôles de l’objet de boîte de dialogue, appelez le `DoModal` fonction membre pour afficher la boîte de dialogue et autoriser l’utilisateur à sélectionner une police. `DoModal` Retourne si l’utilisateur a sélectionné le bouton OK (IDOK) ou Annuler (IDCANCEL).

Si `DoModal` retourne IDOK, vous pouvez utiliser une des `CFontDialog`de fonctions membres pour récupérer les informations entrées par l’utilisateur.

Vous pouvez utiliser le Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) fonction pour déterminer si une erreur s’est produite lors de l’initialisation de la boîte de dialogue et pour en savoir plus sur l’erreur. Pour plus d’informations sur cette fonction, consultez le Kit de développement Windows.

`CFontDialog` s’appuie sur le COMMDLG. Fichier DLL qui est livré avec Windows 3.1 et versions ultérieures.

Pour personnaliser la boîte de dialogue, dérivez une classe de `CFontDialog`, de fournir un modèle de boîte de dialogue personnalisée et ajouter une table des messages pour traiter les messages de notification à partir de contrôles étendus. Tous les messages non traités doivent être passés à la classe de base.

Personnalisation de la fonction de raccordement n’est pas nécessaire.

Pour plus d’informations sur l’utilisation de `CFontDialog`, consultez [des Classes de boîte de dialogue communes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdlgs.h

##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog

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
Un pointeur vers un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure de données qui vous permet de définir certaines caractéristiques de la police.

*charFormat*<br/>
Un pointeur vers un [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) contrôle d’édition de structure de données qui vous permet de définir certaines caractéristiques de la police dans une riche.

*dwFlags*<br/>
Spécifie un ou plusieurs indicateurs de choix de police. Une ou plusieurs valeurs prédéfinies peuvent être combinées à l'aide de l'opérateur de bits OR. Si vous changez le membre de structure de `m_cf.Flag`, veillez à utiliser un opérateur de bits OR dans les changements pour préserver le comportement par défaut. Pour plus d’informations sur chacun de ces indicateurs, consultez la description de la [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) structure dans le SDK Windows.

*pdcPrinter*<br/>
Pointeur vers un contexte de périphérique d'impression. Si ce paramètre est fourni, il pointe vers un contexte de périphérique d'impression pour l'imprimante sur laquelle les polices doivent être sélectionnées.

*pParentWnd*<br/>
Pointeur vers la fenêtre parente ou la fenêtre propriétaire de la boîte de dialogue de police.

### <a name="remarks"></a>Notes

Notez que le constructeur remplit automatiquement les membres de la structure `CHOOSEFONT`. Ne les modifiez que si vous souhaitez une autre boîte de dialogue de police que celle par défaut.

> [!NOTE]
>  La première version de cette fonction n'existe que s'il n'y a aucune prise en charge du contrôle RichEdit.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>  CFontDialog::DoModal

Appelez cette fonction pour afficher la boîte de dialogue police Windows courants et permettre à l’utilisateur de choisir une police.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

IDOK ou IDCANCEL. Si IDCANCEL est retournée, appelez le Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) fonction permettant de déterminer si une erreur s’est produite.

IDOK et IDCANCEL sont des constantes qui indiquent si l’utilisateur a sélectionné le bouton OK ou sur Annuler.

### <a name="remarks"></a>Notes

Si vous souhaitez initialiser les divers contrôles de boîte de dialogue de police en définissant les membres de la [m_cf](#m_cf) structure, vous devez le faire avant d’appeler `DoModal`, mais une fois que l’objet de la boîte de dialogue est construit.

Si `DoModal` retourne IDOK, vous pouvez appeler des fonctions pour récupérer les paramètres ou les informations saisies par l’utilisateur dans la boîte de dialogue autres membres.

### <a name="example"></a>Exemple

  Reportez-vous aux exemples de [CFontDialog::CFontDialog](#cfontdialog) et [CFontDialog::GetColor](#getcolor).

##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat

Récupère la mise en forme des caractères de la police sélectionnée.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Paramètres

*CF*<br/>
Un [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) structure contenant des informations sur la mise en forme des caractères de la police sélectionnée.

##  <a name="getcolor"></a>  CFontDialog::GetColor

Appelez cette fonction pour récupérer la couleur de police sélectionnée.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Couleur de la police sélectionnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont

Appelez cette fonction pour affecter les caractéristiques de la police actuellement sélectionnée pour les membres d’un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure.

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Paramètres

*lplf*<br/>
Un pointeur vers un `LOGFONT` structure.

### <a name="remarks"></a>Notes

Autres `CFontDialog` fonctions membres sont fournies pour accéder aux caractéristiques individuelles de la police actuelle.

Si cette fonction est appelée pendant un appel à [DoModal](#domodal), elle retourne la sélection actuelle au moment (l’utilisateur voit ou a changé dans la boîte de dialogue). Si cette fonction est appelée après un appel à `DoModal` (uniquement si `DoModal` retourne IDOK), il retourne ce que l’utilisateur réellement sélectionnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>  CFontDialog::GetFaceName

Appelez cette fonction pour récupérer le nom de police de la police sélectionnée.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de police de la police sélectionnée dans le `CFontDialog` boîte de dialogue.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>  CFontDialog::GetSize

Appelez cette fonction pour extraire la taille de la police sélectionnée.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille de police, en dixièmes d’un point.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>  CFontDialog::GetStyleName

Appelez cette fonction pour récupérer le nom du style de la police sélectionnée.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom de style de la police.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>  CFontDialog::GetWeight

Appelez cette fonction pour récupérer le poids de la police sélectionnée.

```
int GetWeight() const;
```

### <a name="return-value"></a>Valeur de retour

Le poids de la police sélectionnée.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le poids d’une police, consultez [CFont::CreateFont ne](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>  CFontDialog::IsBold

Appelez cette fonction pour déterminer si la police sélectionnée est en gras.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la police sélectionnée a les caractéristiques en gras est activée ; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>  CFontDialog::IsItalic

Appelez cette fonction pour déterminer si la police sélectionnée est en italique.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la police sélectionnée a les caractéristiques en italique est activée ; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut

Appelez cette fonction pour déterminer si la police sélectionnée est affichée avec barré.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la police sélectionnée a la caractéristique barré est activée ; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>  CFontDialog::IsUnderline

Appelez cette fonction pour déterminer si la police sélectionnée est soulignée.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la police sélectionnée a les caractéristiques de trait de soulignement est activée ; sinon 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

Une structure dont les membres stockent les caractéristiques de l’objet de la boîte de dialogue.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Notes

Après avoir construit un `CFontDialog` de l’objet, vous pouvez utiliser `m_cf` pour modifier les différents aspects de la boîte de dialogue avant d’appeler le `DoModal` fonction membre. Pour plus d’informations sur cette structure, consultez [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

