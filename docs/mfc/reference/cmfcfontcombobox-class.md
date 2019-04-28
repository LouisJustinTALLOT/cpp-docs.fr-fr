---
title: Cmfcfontcombobox, classe
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
ms.openlocfilehash: ccc4e545b2274d6dbb9989cfb9c047de819b8d32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237468"
---
# <a name="cmfcfontcombobox-class"></a>Cmfcfontcombobox, classe

Le `CMFCFontComboBox` classe crée un contrôle de zone de liste déroulante qui contient une liste de polices.

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
|`CMFCFontComboBox::CompareItem`|Appelé par l’infrastructure pour déterminer la position relative d’un nouvel élément dans la zone de liste triée du contrôle de zone de liste déroulante police actuelle. (Substitue [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Appelé par l’infrastructure pour dessiner un élément spécifié dans le contrôle de zone de liste déroulante police actuelle. (Substitue [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Récupère des informations sur la police actuellement sélectionnée.|
|`CMFCFontComboBox::MeasureItem`|Appelé par l’infrastructure pour informer Windows des dimensions de la zone de liste dans le contrôle de zone de liste déroulante police actuelle. (Substitue [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils soient distribués à le [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) des fonctions de Windows. (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::SelectFont](#selectfont)|Sélectionne la police qui correspond aux critères spécifiés dans la zone de liste déroulante de police.|
|[CMFCFontComboBox::Setup](#setup)|Initialise la liste des éléments dans la zone de liste déroulante de police.|

### <a name="data-members"></a>Membres de données

|Nom|Description|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Indique à l’infrastructure de police à utiliser pour dessiner les étiquettes d’élément dans la zone de liste déroulante police actuelle.|

## <a name="remarks"></a>Notes

Pour utiliser un `CMFCFontComboBox` de l’objet dans une boîte de dialogue, ajoutez un `CMFCFontComboBox` variable à la classe de boîte de dialogue. Ensuite, dans le `OnInitDialog` méthode de la classe de boîte de dialogue, appel le [CMFCFontComboBox::Setup](#setup) méthode pour initialiser la liste des éléments dans le contrôle de zone de liste déroulante.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxfontcombobox.h

##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox

Construit un objet `CMFCFontComboBox`.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont

Récupère des informations sur la police actuellement sélectionnée.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers [cmfcfontinfo, classe](../../mfc/reference/cmfcfontinfo-class.md) objet qui décrit une police. Il peut être NULL si aucune police n’est sélectionné dans la zone de liste déroulante.

### <a name="remarks"></a>Notes

##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont

Indique à l’infrastructure de police à utiliser pour dessiner les étiquettes d’élément dans la zone de liste déroulante police actuelle.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Notes

Définissez ce membre sur TRUE pour indiquer à l’infrastructure d’utiliser la même police pour dessiner chaque étiquette d’élément. Définissez ce membre sur FALSE pour indiquer à l’infrastructure pour dessiner chaque étiquette d’élément avec la police dont le nom est identique à l’étiquette. La valeur par défaut de ce membre a la valeur FALSE.

##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont

Sélectionne la police qui correspond aux critères spécifiés dans la zone de liste déroulante de police.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Paramètres

*pDesc*<br/>
[in] Pointe vers un objet de description de police.

*lpszName*<br/>
[in] Spécifie un nom de police.

*nCharSet*<br/>
[in] Spécifie un jeu de caractères. La valeur par défaut est DEFAULT_CHARSET. Pour plus d’informations, consultez le `lfCharSet` membre de la [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure.

### <a name="return-value"></a>Valeur de retour

TRUE si un élément dans la zone de liste déroulante police correspond à l’objet de description de police spécifiée ou de nom de la police et de jeu de caractères ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour sélectionner et faites défiler jusqu'à l’élément dans la zone de liste déroulante de police qui correspond à la police spécifiée.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `SelectFont` méthode dans la `CMFCFontComboBox` classe. Cet exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>  CMFCFontComboBox::Setup

Initialise la liste des éléments dans la zone de liste déroulante de police.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Paramètres

*nFontType*<br/>
[in] Spécifie le type de police. La valeur par défaut est la combinaison au niveau du bit (ou) de DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE.

*nCharSet*<br/>
[in] Spécifie le jeu de caractères de police. La valeur par défaut est DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
[in] Spécifie la hauteur de police et de la famille. La valeur par défaut est DEFAULT_PITCH.

### <a name="return-value"></a>Valeur de retour

TRUE si la zone de liste déroulante police a été initialisée avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Cette méthode initialise la zone de liste déroulante de police en énumérant les polices actuellement installées qui correspondent aux paramètres spécifiés et en insérant ces noms de police dans la zone de liste déroulante de police.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `Setup` méthode dans la `CMFCFontComboBox` classe. Cet exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox, classe](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)
