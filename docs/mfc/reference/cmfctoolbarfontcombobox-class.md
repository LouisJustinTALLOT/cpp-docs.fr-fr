---
title: Cmfctoolbarfontcombobox, classe
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
ms.openlocfilehash: 89767a3ed6880703c3c754700ea5669c0cc183e5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58779194"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Cmfctoolbarfontcombobox, classe

Un bouton de barre d’outils qui contient un contrôle de zone de liste déroulante qui permet à l’utilisateur à sélectionner une police dans une liste de polices système.

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
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Retourne un pointeur vers le `CMFCFontInfo` objet pour un index spécifié dans la zone de liste déroulante.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Sélectionne une police dans la zone de liste déroulante de police en fonction d’une, le nom de la police ou le préfixe et jeu de caractères de la police.|

### <a name="data-members"></a>Membres de données

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
La hauteur des caractères dans la zone de liste déroulante de police.

## <a name="remarks"></a>Notes

Pour ajouter un bouton de zone de liste déroulante de police à une barre d’outils, procédez comme suit :

1. Réservez un ID de ressource factice pour le bouton dans la ressource de la barre d'outils parente.

1. Construire un `CMFCToolBarFontComboBox` objet.

1. Dans le Gestionnaire de messages qui traite le message AFX_WM_RESETTOOLBAR, remplacer le bouton d’origine avec le nouveau bouton de zone de liste déroulante à l’aide de [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Synchroniser la police est sélectionnée dans la zone de liste déroulante avec la police dans le document à l’aide de la [CMFCToolBarFontComboBox::SetFont](#setfont) (méthode).

Pour synchroniser police du document l’avec la police sélectionnée dans la zone de liste déroulante, utilisez la [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) méthode pour récupérer les attributs de la police sélectionnée et utiliser ces attributs pour créer un [ CFont (classe)](../../mfc/reference/cfont-class.md) objet.

Le bouton de zone de liste déroulante Police appelle la fonction Win32 [EnumFontFamiliesEx](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesexa) pour déterminer les polices d’écran et d’imprimantes disponibles pour le système.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Construit un [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objet.

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
[in] L’ID de commande de la zone de liste déroulante.

*iImage*<br/>
[in] Index de base zéro d’une image de la barre d’outils. L’image se trouve dans le [cmfctoolbarimages, classe](../../mfc/reference/cmfctoolbarimages-class.md) objet [cmfctoolbar, classe](../../mfc/reference/cmfctoolbar-class.md) classe conserve.

*nFontType*<br/>
[in] Les types de polices qui contient la zone de liste déroulante. Ce paramètre peut être une combinaison (OR booléenne) des valeurs suivantes :

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[in] Si la valeur DEFAULT_CHARSET, la zone de liste déroulante contient tout-nommés de manière unique les polices dans tous les jeux de caractères. (S’il existe deux polices portant le même nom, la zone de liste déroulante contient un d’eux.) Si défini sur une valeur de jeu de caractères valide, la zone de liste déroulante contient uniquement les polices dans le jeu de caractères spécifié. Consultez [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) pour obtenir la liste de caractères possibles définit.

*dwStyle*<br/>
[in] Style de la zone de liste déroulante. (consultez [Styles de zone de liste déroulante](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
[in] La largeur en pixels du contrôle d’édition.

*nPitchAndFamily*<br/>
[in] Si la valeur DEFAULT_PITCH, la zone de liste déroulante contient des polices, quel que soit la tonalité. Si la valeur FIXED_PITCH ou VARIABLE_PITCH, la zone de liste déroulante contient uniquement les polices avec ce type de tonalité. Filtrage basé sur la famille de polices n’est pas pris en charge actuellement.

*pLstFontsExternal*<br/>
[out] Pointeur vers un [CObList, classe](../../mfc/reference/coblist-class.md) objet qui stocke les polices disponibles.

### <a name="remarks"></a>Notes

En règle générale, `CMFCToolBarFontComboBox` objets stockent la liste des polices disponibles dans un seul partagé `CObList` objet. Si vous utilisez la deuxième surcharge du constructeur et fournir un pointeur valide vers *pLstFontsExternal*, qui `CMFCToolBarFontComboBox` objet remplira à la place la `CObList` qui *pLstFontsExternal* pointe vers des polices disponibles.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCToolBarFontComboBox` objet. Cet extrait de code fait partie de l’ [exemple Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

Retourne un pointeur vers le `CMFCFontInfo` objet pour un index spécifié dans la zone de liste déroulante.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
[in] Spécifie l’index de base zéro d’un élément de zone de liste déroulante.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CMFCFontInfo` . Si *iIndex* ne spécifie pas un index d’élément valide, la valeur de retour est NULL.

##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight

Spécifie la hauteur, en pixels, de caractères dans la zone de liste déroulante police si la zone de liste déroulante possède un propriétaire de style de dessin.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Notes

Si le `m_nFontHeight` variable est 0, la hauteur est calculée automatiquement en fonction de la police par défaut de la zone de liste déroulante. La hauteur inclut à la fois la hauteur des caractères au-dessus de la ligne de base et la profondeur des caractères en dessous de la ligne de base.

##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont

Sélectionne que la police dans la zone de liste déroulante de police en fonction du nom de la police et le caractère défini qui est spécifiés dans les paramètres.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszName*<br/>
[in] Spécifie le nom de la police ou le préfixe.

*nCharSet*<br/>
[in] Spécifie le jeu de caractères.

*bExact*<br/>
[in] Spécifie si *le caractère* contient le nom de la police ou le préfixe de la police.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la police a été activée avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Si *bExact* a la valeur TRUE, cette méthode sélectionne une police qui correspond exactement au nom que vous avez spécifié en tant que *le caractère*. Si *bExact* est FALSE, cette sélectionne méthode une police qui commence par le texte spécifiée en tant que *le caractère* et qui utilise le jeu de caractères que vous avez spécifié en tant que *nCharSet*. Si *nCharSet* est définie à DEFAULT_CHARSET, le jeu de caractères sera ignoré et seule *le caractère* permet de sélectionner une police.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton, classe](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
