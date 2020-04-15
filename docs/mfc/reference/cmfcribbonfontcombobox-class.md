---
title: Classe CMFCRibbonFontComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 822f4f6fe76bb5b82b455daec54ed96568ea6ba7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375168"
---
# <a name="cmfcribbonfontcombobox-class"></a>Classe CMFCRibbonFontComboBox

Implémente une zone de liste déroulante contenant une liste de polices. Vous placez la zone de liste déroulante sur un panneau de ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destructeur.|

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Construit et initialise un objet `CMFCRibbonFontComboBox`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Remplit la zone de liste modifiable Police du ruban avec des polices du type, du jeu de caractères, du pas et de la famille spécifiés.|
|`CMFCRibbonFontComboBox::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Retourne le jeu de caractères spécifié.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Retourne les types de police à afficher dans la zone de liste modifiable. Les options valides sont DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE ou toute autre combinaison au niveau du bit de ces options.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Retourne le pas et la famille des polices affichées dans la zone de liste modifiable.|
|`CMFCRibbonFontComboBox::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Remplit la zone de liste modifiable Police du ruban avec des polices du type, du jeu de caractères, du pas et de la famille spécifiés précédemment.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Sélectionne la police spécifiée dans la zone de liste modifiable.|

## <a name="remarks"></a>Notes

Après avoir `CMFCRibbonFontComboBox` créé un objet, ajoutez-le à un panneau ruban en appelant [CMFCRibbonPanel::Ajouter](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxRibbonComboBox.h

## <a name="cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts

Remplit la boîte combo sur le ruban avec des polices.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Paramètres

*nFontType (en)*<br/>
[dans] Spécifie le type de police des polices à ajouter.

*nCharSet (en anglais)*<br/>
[dans] Spécifie l’ensemble de caractères des polices à ajouter.

*nPitchAndFamily (en)*<br/>
[dans] Spécifie le pitch et la famille des polices à ajouter.

## <a name="cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Construit et initialise un objet [CMFCRibbonFontComboBox.](../../mfc/reference/cmfcribbonfontcombobox-class.md)

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[dans] L’ID de commande de la commande qui s’exécute lorsque l’utilisateur sélectionne un élément de la boîte combo.

*nFontType (en)*<br/>
[dans] Précise quels types de police à afficher dans la boîte combo. Les options valides sont DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE ou toute autre combinaison au niveau du bit de ces options.

*nCharSet (en anglais)*<br/>
[dans] Filtre les polices dans la boîte combo à celles qui appartiennent à l’ensemble de caractère spécifié.

*nPitchAndFamily (en)*<br/>
[dans] Spécifie le pitch et la famille des polices qui sont affichées dans la boîte combo.

*nWidth (en)*<br/>
[dans] Spécifie la largeur, en pixels, de la boîte combo.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les valeurs de paramètres *nFontType* possibles, voir [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) dans la documentation Windows SDK.

Pour plus d’informations sur les ensembles de caractères valides qui peuvent être attribués à *nCharSet*, et les valeurs valides qui peuvent être attribuées à *nPitchAndFamily*, voir [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) dans la documentation Windows SDK.

## <a name="cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Paramètres

[dans] *iIndex (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts

Remplit la boîte de combo sur le ruban avec des polices d’un type de police, un ensemble de caractères, et le pitch et la famille.

```
void RebuildFonts();
```

### <a name="remarks"></a>Notes

Vous pouvez spécifier le type de police, l’ensemble de caractères, et le pitch et la famille des polices à inclure dans la boîte combo police ruban dans le [constructeur](#cmfcribbonfontcombobox) pour cette classe, ou en appelant [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).

## <a name="cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFCRibbonFontComboBox::SetFont

Sélectionne la police spécifiée dans la zone de liste modifiable.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Paramètres

'lpszNameMD précise le nom de la police à sélectionner.

*nCharSet (en anglais)*<br/>
Spécifie l’ensemble de caractères pour la police sélectionnée.

*bExact*<br/>
VRAI pour spécifier que l’ensemble de caractères doit correspondre lors de la sélection d’une police; FALSE pour spécifier que l’ensemble de caractères peut être ignoré lors de la sélection d’une police.

### <a name="return-value"></a>Valeur de retour

Nonzero si la police spécifiée a été trouvée et sélectionnée; autrement, zéro.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFCRibbonFontComboBox::GetCharSet

Retourne le jeu de caractères spécifié.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Valeur de retour

Ensemble de caractères (voir LOGFONT dans la documentation Windows SDK).

### <a name="remarks"></a>Notes

## <a name="cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType

Retourne les types de police à afficher dans la zone de liste modifiable. Les options valides sont DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE ou toute autre combinaison au niveau du bit de ces options.

```
int GetFontType() const;
```

### <a name="return-value"></a>Valeur de retour

Types de police (voir EnumFontFamProc dans la documentation Windows SDK).

### <a name="remarks"></a>Notes

## <a name="cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily

Retourne le pas et la famille des polices affichées dans la zone de liste modifiable.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Valeur de retour

Pitch et la famille (voir LOGFONT dans la documentation Windows SDK).

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox, classe](../../mfc/reference/cmfcribboncombobox-class.md)
