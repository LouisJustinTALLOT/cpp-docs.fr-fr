---
title: Classe CMFCFontComboBox
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
ms.openlocfilehash: 60b4b7cdfdace2332de35dd93c43eacf592e99e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367489"
---
# <a name="cmfcfontcombobox-class"></a>Classe CMFCFontComboBox

La `CMFCFontComboBox` classe crée un contrôle de boîte combo qui contient une liste de polices.

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
|`CMFCFontComboBox::CompareItem`|Appelé par le cadre pour déterminer la position relative d’un nouvel élément dans la boîte de liste triée de la police actuelle combo box contrôle. (Overrides [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Appelé par le cadre pour dessiner un élément spécifié dans le contrôle actuel de boîte combo police. (Overrides [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Récupère des informations sur la police actuellement sélectionnée.|
|`CMFCFontComboBox::MeasureItem`|Appelé par le cadre pour informer Windows des dimensions de la boîte de liste dans le contrôle actuel de la boîte combo police. (Overrides [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows De TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::SelectFont](#selectfont)|Sélectionne la police qui correspond aux critères spécifiés à partir de la boîte combo police.|
|[CMFCFontComboBox::Configuration](#setup)|Initialise la liste des éléments de la boîte combo police.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Indique au cadre quelle police utiliser pour dessiner les étiquettes d’objets dans la boîte combo de police actuelle.|

## <a name="remarks"></a>Notes

Pour utiliser `CMFCFontComboBox` un objet dans une `CMFCFontComboBox` boîte de dialogue, ajoutez une variable à la classe de boîte de dialogue. Ensuite, `OnInitDialog` dans la méthode de la classe boîte de dialogue, appelez le [CMFCFontComboBox::Méthode d’installation](#setup) pour initialiser la liste des éléments dans le contrôle de la boîte combo.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxfontcombobox.h

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox

Construit un objet `CMFCFontComboBox`.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a>CMFCFontComboBox::GetSelFont

Récupère des informations sur la police actuellement sélectionnée.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à [l’objet cmFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md) qui décrit une police. Il peut être NULL si aucune police n’est sélectionnée dans la boîte combo.

### <a name="remarks"></a>Notes

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont

Indique au cadre quelle police utiliser pour dessiner les étiquettes d’objets dans la boîte combo de police actuelle.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Notes

Définissez ce membre à TRUE pour diriger le cadre à utiliser la même police pour dessiner chaque étiquette d’article. Définissez ce membre à FALSE pour diriger le cadre pour dessiner chaque étiquette d’article avec la police dont le nom est le même que l’étiquette. La valeur par défaut de ce membre est FALSE.

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a>CMFCFontComboBox::SelectFont

Sélectionne la police qui correspond aux critères spécifiés à partir de la boîte combo police.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Paramètres

*pDesc*<br/>
[dans] Points à un objet de description de police.

*lpszName (en)*<br/>
[dans] Spécifie un nom de police.

*nCharSet (en anglais)*<br/>
[dans] Spécifie un ensemble de personnages. La valeur par défaut est DEFAULT_CHARSET. Pour plus d’informations, consultez le `lfCharSet` membre de la structure [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

### <a name="return-value"></a>Valeur de retour

VRAI si un élément de la boîte combo de police correspond à l’objet de description de police spécifié ou nom de police et charset ; autrement, FALSE.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour sélectionner et faire défiler l’élément dans la boîte combo de police qui correspond à la police spécifiée.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `SelectFont` utiliser `CMFCFontComboBox` la méthode dans la classe. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a>CMFCFontComboBox::Configuration

Initialise la liste des éléments de la boîte combo police.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Paramètres

*nFontType (en)*<br/>
[dans] Spécifie le type de police. La valeur par défaut est la combinaison bitwise (OU) de DEVICE_FONTTYPE, RASTER_FONTTYPE et TRUETYPE_FONTTYPE.

*nCharSet (en anglais)*<br/>
[dans] Spécifie l’ensemble de caractères de police. La valeur par défaut est DEFAULT_CHARSET.

*nPitchAndFamily (en)*<br/>
[dans] Spécifie le pitch de police et la famille. La valeur par défaut est DEFAULT_PITCH.

### <a name="return-value"></a>Valeur de retour

VRAI si la boîte combo police a été parascé avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode initialise la boîte combo de police en énumérant les polices actuellement installées qui correspondent aux paramètres spécifiés et en insérant ces noms de police dans la boîte combo de police.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `Setup` utiliser `CMFCFontComboBox` la méthode dans la classe. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo, classe](../../mfc/reference/cmfcfontinfo-class.md)
