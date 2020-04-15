---
title: Classe CMFCToolBarFontComboBox
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
ms.openlocfilehash: 7b31f4b725a6983171162d9805d08224ad787808
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360465"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Classe CMFCToolBarFontComboBox

Un bouton de barre d’outils qui contient un contrôle de boîte combo qui permet à l’utilisateur de sélectionner une police à partir d’une liste de polices système.

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
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Retourne un pointeur à l’objet `CMFCFontInfo` pour un index spécifié dans la boîte combo.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Sélectionne une police dans la boîte combo police en fonction soit du nom de la police, soit du préfixe et de l’ensemble de caractères de la police.|

### <a name="data-members"></a>Données membres

[CMFCToolBarFontComboBox:m_nFontHeight](#m_nfontheight)<br/>
La hauteur des personnages dans la boîte combo police.

## <a name="remarks"></a>Notes

Pour ajouter un bouton de boîte combo police à une barre d’outils, suivez ces étapes :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

1. Construire `CMFCToolBarFontComboBox` un objet.

1. Dans le gestionnaire de message qui traite le message AFX_WM_RESETTOOLBAR, remplacez le bouton d’origine par le nouveau bouton de boîte combo en utilisant [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Synchroniser la police sélectionnée dans la boîte combo avec la police dans le document en utilisant la [CMFCToolBarFontComboBox::SetFont](#setfont) méthode.

Pour synchroniser la police du document avec la police sélectionnée dans la boîte combo, utilisez la [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) méthode pour récupérer les attributs de la police sélectionnée, et utilisez ces attributs pour créer un objet [de classe CFont.](../../mfc/reference/cfont-class.md)

Le bouton de la boîte combo de police appelle la fonction Win32 [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) pour déterminer les polices d’écran et d’imprimante disponibles au système.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Construit un objet [CMFCToolBarFontComboBox.](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

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
[dans] L’ID de commande de la boîte combo.

*iImage (en)*<br/>
[dans] L’index zéro d’une image de barre d’outils. L’image est située dans l’objet [cmFCToolBarImages Classe](../../mfc/reference/cmfctoolbarimages-class.md) que [cmFCToolBar Classe](../../mfc/reference/cmfctoolbar-class.md) Classe maintient.

*nFontType (en)*<br/>
[dans] Les types de polices que contient la boîte combo. Ce paramètre peut être une combinaison (boolean OU) des valeurs suivantes :

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet (en anglais)*<br/>
[dans] Si elle est réglée sur DEFAULT_CHARSET, la boîte combo contient toutes les polices de nom unique dans tous les ensembles de personnages. (S’il y a deux polices du même nom, la boîte combo contient l’une d’entre elles.) Si elle est définie à une valeur valide de jeu de caractère, la boîte de combo ne contient que des polices dans l’ensemble de caractères spécifié. Consultez [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) pour une liste d’ensembles de caractères possibles.

*dwStyle (en)*<br/>
[dans] Le style de la boîte combo. (voir [Styles Combo-Box](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth (en)*<br/>
[dans] La largeur des pixels du contrôle de modification.

*nPitchAndFamily (en)*<br/>
[dans] Si elle est réglée pour DEFAULT_PITCH, la boîte combo contient des polices indépendamment du pitch. Si elle est réglée sur FIXED_PITCH ou VARIABLE_PITCH, la boîte combo ne contient que des polices avec ce type de hauteur. Le filtrage basé sur la famille de police n’est pas actuellement pris en charge.

*pLstFontsExternal*<br/>
[out] Pointeur vers un objet [de classe CObList](../../mfc/reference/coblist-class.md) qui stocke les polices disponibles.

### <a name="remarks"></a>Notes

Habituellement, `CMFCToolBarFontComboBox` les objets stockent la liste `CObList` des polices disponibles dans un seul objet partagé. Si vous utilisez la deuxième surcharge du constructeur et de fournir un pointeur valide `CMFCToolBarFontComboBox` à *pLstFontsExternal*, cet objet remplira plutôt les `CObList` points qui *pLstFontsExternal* avec les polices disponibles.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCToolBarFontComboBox` construire un objet. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc

Retourne un pointeur à l’objet `CMFCFontInfo` pour un index spécifié dans la boîte combo.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] Spécifie l’index zéro d’un élément de boîte combo.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CMFCFontInfo`. Si *iIndex* ne spécifie pas un indice d’article valide, la valeur de rendement est NULL.

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox:m_nFontHeight

Spécifie la hauteur, en pixels, des caractères dans la boîte combo police si la boîte combo a le style de tirage propriétaire.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Notes

Si `m_nFontHeight` la variable est de 0, la hauteur est calculée automatiquement en fonction de la police par défaut de la boîte combo. La hauteur comprend à la fois l’ascension des caractères au-dessus de la ligne de base et la descente des caractères sous la ligne de base.

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontComboBox::SetFont

Sélectionne la police dans la boîte combo de police en fonction du nom de police et de l’ensemble de caractères spécifiés dans les paramètres.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
[dans] Spécifie le nom de police ou le préfixe.

*nCharSet (en anglais)*<br/>
[dans] Spécifie l’ensemble de personnages.

*bExact*<br/>
[dans] Précise si *lpszName* contient le nom de police ou le préfixe de police.

### <a name="return-value"></a>Valeur de retour

Nonzero si la police a été sélectionnée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Si *bExact* est VRAI, cette méthode sélectionne une police qui correspond exactement au nom que vous avez spécifié sous le nom *de lpszName*. Si *bExact* est FALSE, cette méthode sélectionne une police qui commence par le texte spécifié sous forme *de lpszName* et qui utilise l’ensemble de caractères que vous avez spécifié comme *nCharSet*. Si *nCharSet* est configuré pour DEFAULT_CHARSET, l’ensemble de caractères sera ignoré et seul *lpszName* sera utilisé pour sélectionner une police.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton, classe](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::RemplacerButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : placement de contrôles dans les barres d'outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
