---
description: 'En savoir plus sur : classe CMFCToolBarFontComboBox'
title: CMFCToolBarFontComboBox, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 900da03bab8fdc95d93a9c92a14932d7a5bdd9ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331756"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox, classe

Bouton de barre d’outils qui contient un contrôle zone de liste déroulante qui permet à l’utilisateur de sélectionner une police dans une liste de polices système.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Construit un objet `CMFCToolBarFontComboBox`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Retourne un pointeur vers l' `CMFCFontInfo` objet pour un index spécifié dans la zone de liste déroulante.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Sélectionne une police dans la zone de liste déroulante de police en fonction du nom de la police ou du préfixe et du jeu de caractères de la police.|

### <a name="data-members"></a>Données membres

[CMFCToolBarFontComboBox :: m_nFontHeight](#m_nfontheight)<br/>
Hauteur des caractères de la zone de liste déroulante de police.

## <a name="remarks"></a>Notes

Pour ajouter un bouton de zone de liste déroulante de police à une barre d’outils, procédez comme suit :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

1. Construisez un `CMFCToolBarFontComboBox` objet.

1. Dans le gestionnaire de messages qui traite le message AFX_WM_RESETTOOLBAR, remplacez le bouton d’origine par le nouveau bouton de zone de liste déroulante à l’aide de [CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Synchronisez la police sélectionnée dans la zone de liste déroulante avec la police dans le document à l’aide de la méthode [CMFCToolBarFontComboBox :: SetFont](#setfont) .

Pour synchroniser la police du document avec la police sélectionnée dans la zone de liste déroulante, utilisez la méthode [CMFCToolBarFontComboBox :: GetFontDesc](#getfontdesc) pour récupérer les attributs de la police sélectionnée et utilisez ces attributs pour créer un objet de [classe CFont](../../mfc/reference/cfont-class.md) .

Le bouton de zone de liste déroulante de police appelle la fonction Win32 [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) pour déterminer les polices d’écran et d’imprimante disponibles pour le système.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxtoolbarfontcombobox. h

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a> CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Construit un objet [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) .

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
dans ID de commande de la zone de liste déroulante.

*iImage*<br/>
dans Index de base zéro d’une image de barre d’outils. L’image se trouve dans l’objet de [classe CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) géré par la classe de [classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

*nFontType*<br/>
dans Types de polices que contient la zone de liste déroulante. Ce paramètre peut être une combinaison (booléenne ou) des valeurs suivantes :

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
dans Si la valeur est DEFAULT_CHARSET, la zone de liste déroulante contient toutes les polices portant un nom unique dans tous les jeux de caractères. (S’il existe deux polices portant le même nom, la zone de liste déroulante en contient une.) Si la valeur d’un jeu de caractères est valide, la zone de liste déroulante contient uniquement les polices du jeu de caractères spécifié. Pour obtenir la liste des jeux de caractères possibles, consultez [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*dwStyle*<br/>
dans Style de la zone de liste déroulante. (voir [styles de zone de liste déroulante](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
dans Largeur en pixels du contrôle d’édition.

*nPitchAndFamily*<br/>
dans Si la valeur est DEFAULT_PITCH, la zone de liste déroulante contient des polices, quelle que soit la hauteur. Si la valeur est FIXED_PITCH ou VARIABLE_PITCH, la zone de liste déroulante contient uniquement des polices avec ce type de tangage. Le filtrage basé sur la famille de polices n’est pas pris en charge actuellement.

*pLstFontsExternal*<br/>
à Pointeur vers un objet de [classe CObList](../../mfc/reference/coblist-class.md) qui stocke les polices disponibles.

### <a name="remarks"></a>Notes

En règle générale, `CMFCToolBarFontComboBox` les objets stockent la liste des polices disponibles dans un objet partagé unique `CObList` . Si vous utilisez la deuxième surcharge du constructeur et fournissez un pointeur valide vers *pLstFontsExternal*, cet `CMFCToolBarFontComboBox` objet remplira à la place le `CObList` point de *pLstFontsExternal* avec les polices disponibles.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCToolBarFontComboBox` objet. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a> CMFCToolBarFontComboBox::GetFontDesc

Retourne un pointeur vers l' `CMFCFontInfo` objet pour un index spécifié dans la zone de liste déroulante.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Spécifie l’index de base zéro d’un élément de zone de liste déroulante.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet `CMFCFontInfo`. Si *iIndex* ne spécifie pas un index d’élément valide, la valeur de retour est null.

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a> CMFCToolBarFontComboBox :: m_nFontHeight

Spécifie la hauteur, en pixels, des caractères de la zone de liste déroulante de police si la zone de liste déroulante a Owner Draw style.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Notes

Si la `m_nFontHeight` variable est égale à 0, la hauteur est calculée automatiquement en fonction de la police par défaut de la zone de liste déroulante. La hauteur comprend à la fois la hauteur des caractères au-dessus de la ligne de base et la profondeur des caractères sous la ligne de base.

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a> CMFCToolBarFontComboBox::SetFont

Sélectionne la police dans la zone de liste déroulante de police en fonction du nom de la police et du jeu de caractères spécifiés dans les paramètres.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
dans Spécifie le nom ou le préfixe de la police.

*nCharSet*<br/>
dans Spécifie le jeu de caractères.

*bExact*<br/>
dans Spécifie si *lpszName* contient le nom de police ou le préfixe de police.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la police a été sélectionnée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Si *bExact* a la valeur true, cette méthode sélectionne une police qui correspond exactement au nom que vous avez spécifié en tant que *lpszName*. Si *bExact* a la valeur false, cette méthode sélectionne une police qui commence par le texte spécifié en tant que *lpszName* et qui utilise le jeu de caractères que vous avez spécifié comme *nCharSet*. Si *nCharSet* a la valeur default_charset, le jeu de caractères est ignoré et seul *lpszName* est utilisé pour sélectionner une police.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton, classe](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar :: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : ajout de contrôles aux barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
