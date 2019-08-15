---
title: CMFCRibbonFontComboBox, classe
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
ms.openlocfilehash: 186c4bc3e1b26529ed0e000d2893e1b2d81c4304
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504965"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox, classe

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
|`CMFCRibbonFontComboBox::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Remplit la zone de liste modifiable Police du ruban avec des polices du type, du jeu de caractères, du pas et de la famille spécifiés précédemment.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Sélectionne la police spécifiée dans la zone de liste modifiable.|

## <a name="remarks"></a>Notes

Après avoir créé un `CMFCRibbonFontComboBox` objet, ajoutez-le à un panneau du ruban en appelant [CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxRibbonComboBox. h

##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts

Remplit la zone de liste déroulante du ruban avec les polices.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Paramètres

*nFontType*<br/>
dans Spécifie le type de police des polices à ajouter.

*nCharSet*<br/>
dans Spécifie le jeu de caractères des polices à ajouter.

*nPitchAndFamily*<br/>
dans Spécifie le pas et la famille des polices à ajouter.

##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Construit et initialise un objet [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) .

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
dans ID de commande de la commande qui s’exécute lorsque l’utilisateur sélectionne un élément dans la zone de liste déroulante.

*nFontType*<br/>
dans Spécifie les types de police à afficher dans la zone de liste déroulante. Les options valides sont DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE ou toute autre combinaison au niveau du bit de ces options.

*nCharSet*<br/>
dans Filtre les polices de la zone de liste déroulante avec celles qui appartiennent au jeu de caractères spécifié.

*nPitchAndFamily*<br/>
dans Spécifie le pas et la famille des polices qui sont affichées dans la zone de liste déroulante.

*nWidth*<br/>
dans Spécifie la largeur, en pixels, de la zone de liste déroulante.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les valeurs de paramètre *nFontType* possibles, consultez [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) dans la documentation de SDK Windows.

Pour plus d’informations sur les jeux de caractères valides qui peuvent être assignés à *nCharSet*et les valeurs valides qui peuvent être assignées à *NPitchAndFamily*, consultez [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) dans la documentation SDK Windows.

##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc

Pour plus d’informations, consultez le code source situé dans le dossier **VC\\ATLMFC\\SRC\\MFC** de votre installation de Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Paramètres

dans *iIndex*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts

Remplit la zone de liste déroulante du ruban avec les polices d’un type de police, un jeu de caractères et une famille spécifiés précédemment.

```
void RebuildFonts();
```

### <a name="remarks"></a>Notes

Vous pouvez spécifier le type de police, le jeu de caractères, le pas et la famille des polices à inclure dans la zone de liste déroulante police du ruban dans le [constructeur](#cmfcribbonfontcombobox) de cette classe, ou en appelant [CMFCRibbonFontComboBox:: BuildFonts](#buildfonts).

##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont

Sélectionne la police spécifiée dans la zone de liste modifiable.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Paramètres

«lpszName *» spécifie le nom de la police à sélectionner.

*nCharSet*<br/>
Spécifie le jeu de caractères pour la police sélectionnée.

*bExact*<br/>
TRUE pour spécifier que le jeu de caractères doit correspondre lors de la sélection d’une police; FALSe pour indiquer que le jeu de caractères peut être ignoré lors de la sélection d’une police.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la police spécifiée a été trouvée et sélectionnée; Sinon, zéro.

### <a name="remarks"></a>Notes

##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet

Retourne le jeu de caractères spécifié.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Valeur de retour

Jeu de caractères (consultez LOGFONT dans la documentation de SDK Windows).

### <a name="remarks"></a>Notes

##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType

Retourne les types de police à afficher dans la zone de liste modifiable. Les options valides sont DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE ou toute autre combinaison au niveau du bit de ces options.

```
int GetFontType() const;
```

### <a name="return-value"></a>Valeur de retour

Types de police (consultez EnumFontFamProc dans la documentation de SDK Windows).

### <a name="remarks"></a>Notes

##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily

Retourne le pas et la famille des polices affichées dans la zone de liste modifiable.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur et la famille (consultez LOGFONT dans la documentation de SDK Windows).

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox, classe](../../mfc/reference/cmfcribboncombobox-class.md)
