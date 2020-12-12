---
description: 'En savoir plus sur : classe CMFCFontComboBox'
title: CMFCFontComboBox, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: dc8e6d2a3c2c10d59cc6b7ce173d66df8b27ae62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265426"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox, classe

La `CMFCFontComboBox` classe crée un contrôle de zone de liste déroulante qui contient une liste de polices.

## <a name="syntax"></a>Syntaxe

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Construit un objet `CMFCFontComboBox`.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Appelé par l’infrastructure pour déterminer la position relative d’un nouvel élément dans la zone de liste triée du contrôle de zone de liste déroulante de la police actuelle. (Substitue [CComboBox :: CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Appelé par l’infrastructure pour dessiner un élément spécifié dans le contrôle de zone de liste déroulante de police actuel. (Substitue [CComboBox ::D rawitem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Récupère des informations sur la police actuellement sélectionnée.|
|`CMFCFontComboBox::MeasureItem`|Appelé par l’infrastructure pour informer les fenêtres des dimensions de la zone de liste dans le contrôle de zone de liste déroulante de police actuel. (Substitue [CComboBox :: MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::SelectFont](#selectfont)|Sélectionne la police qui correspond aux critères spécifiés à partir de la zone de liste déroulante de police.|
|[CMFCFontComboBox :: Setup](#setup)|Initialise la liste d’éléments dans la zone de liste déroulante de police.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCFontComboBox :: m_bDrawUsingFont](#m_bdrawusingfont)|Indique au Framework la police à utiliser pour dessiner les étiquettes d’élément dans la zone de liste déroulante de police actuelle.|

## <a name="remarks"></a>Notes

Pour utiliser un `CMFCFontComboBox` objet dans une boîte de dialogue, ajoutez une `CMFCFontComboBox` variable à la classe de boîte de dialogue. Ensuite, dans la `OnInitDialog` méthode de la classe de boîte de dialogue, appelez la méthode [CMFCFontComboBox :: Setup](#setup) pour initialiser la liste d’éléments dans le contrôle de zone de liste déroulante.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxfontcombobox. h

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a> CMFCFontComboBox::CMFCFontComboBox

Construit un objet `CMFCFontComboBox`.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a> CMFCFontComboBox::GetSelFont

Récupère des informations sur la police actuellement sélectionnée.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet de [classe CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md) qui décrit une police. Elle peut avoir la valeur NULL si aucune police n’est sélectionnée dans la zone de liste déroulante.

### <a name="remarks"></a>Notes

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a> CMFCFontComboBox :: m_bDrawUsingFont

Indique au Framework la police à utiliser pour dessiner les étiquettes d’élément dans la zone de liste déroulante de police actuelle.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Notes

Affectez la valeur TRUE à ce membre pour indiquer à l’infrastructure d’utiliser la même police pour dessiner chaque étiquette d’élément. Affectez la valeur FALSe à ce membre pour indiquer à l’infrastructure de dessiner chaque étiquette d’élément avec la police dont le nom est identique à l’étiquette. La valeur par défaut de ce membre est FALSe.

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a> CMFCFontComboBox::SelectFont

Sélectionne la police qui correspond aux critères spécifiés à partir de la zone de liste déroulante de police.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Paramètres

*pDesc*<br/>
dans Pointe vers un objet de description de police.

*lpszName*<br/>
dans Spécifie un nom de police.

*nCharSet*<br/>
dans Spécifie un jeu de caractères. La valeur par défaut est DEFAULT_CHARSET. Pour plus d’informations, consultez le `lfCharSet` membre de la structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

### <a name="return-value"></a>Valeur renvoyée

TRUE si un élément de la zone de liste déroulante de police correspond à l’objet de description de police spécifié ou au nom de police et au jeu de caractères ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour sélectionner et faire défiler jusqu’à l’élément dans la zone de liste déroulante de police qui correspond à la police spécifiée.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `SelectFont` méthode dans la `CMFCFontComboBox` classe. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a> CMFCFontComboBox :: Setup

Initialise la liste d’éléments dans la zone de liste déroulante de police.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Paramètres

*nFontType*<br/>
dans Spécifie le type de police. La valeur par défaut est la combinaison au niveau du bit (OR) de DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE.

*nCharSet*<br/>
dans Spécifie le jeu de caractères de police. La valeur par défaut est DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
dans Spécifie l’espacement et la famille de la police. La valeur par défaut est DEFAULT_PITCH.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la zone de liste déroulante de police a été initialisée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode initialise la zone de liste déroulante de police en énumérant les polices actuellement installées qui correspondent aux paramètres spécifiés et en insérant ces noms de police dans la zone de liste déroulante de police.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `Setup` méthode dans la `CMFCFontComboBox` classe. Cet exemple fait partie de l' [exemple New Controls](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)
