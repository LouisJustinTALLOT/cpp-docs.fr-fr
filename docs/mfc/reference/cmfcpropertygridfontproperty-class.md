---
title: CMFCPropertyGridFontProperty, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: a1c9905d8d7f32a049496c4e164c9eaac13455d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361834"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty, classe

La `CMFCPropertyGridFileProperty` classe prend en charge un élément de contrôle de liste de propriété qui ouvre une boîte de dialogue de sélection de police.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Construit un objet `CMFCPropertyGridFontProperty`.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Met en forme la représentation textuelle d'une valeur de propriété. (Overrides [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Récupère la couleur de police que l’utilisateur sélectionne dans la boîte de dialogue de police.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Récupère la police que l’utilisateur sélectionne dans la boîte de dialogue de police.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Appelé par l'infrastructure quand l'utilisateur clique sur un bouton contenu dans une propriété. (Overrides [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

Construit un objet `CMFCPropertyGridFontProperty`.

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
[in] Nom de la propriété.

*Si*<br/>
[dans] Une structure de police logique qui spécifie les attributs de la police.

*dwFontDialogFlags dwFontDialogFlags*<br/>
[dans] Styles qui sont appliqués à la boîte de dialogue de police qui s’affiche lorsque vous cliquez sur le bouton de baisse de la valeur de la propriété. La valeur par défaut est la combinaison bitwise (OU) de CF_EFFECTS et CF_SCREENFONTS. Pour plus d’informations, consultez le paramètre *drapeaux* de la [structure CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszDescr*<br/>
[dans] Description de la propriété de police. La valeur par défaut est NULL.

*dwData dwData*<br/>
[dans] Données spécifiques à l’application, telles qu’un intégrant ou un pointeur à d’autres données qui sont associées à la propriété. La valeur par défaut est 0.

*Couleur*<br/>
[dans] La couleur de la police. La valeur par défaut est la couleur par défaut.

### <a name="remarks"></a>Notes

Un `CMFCPropertyGridFontProperty` objet représente une propriété de police dans un contrôle de police de réseau de propriété.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCPropertyGridFontProperty` un objet de la classe. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

## <a name="cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridFontProperty::GetColor

Récupère la couleur de police que l’utilisateur sélectionne dans la boîte de dialogue de police.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de couleur RGB qui représente la couleur de police sélectionnée.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont

Récupère la police que l’utilisateur sélectionne dans la boîte de dialogue de police.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une structure [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) qui décrit la police sélectionnée.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Classe CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
