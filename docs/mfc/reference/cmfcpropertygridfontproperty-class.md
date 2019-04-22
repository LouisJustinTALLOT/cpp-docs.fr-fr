---
title: Cmfcpropertygridfontproperty, classe
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
ms.openlocfilehash: b348dc2ac68ced89fb0702073f57a114befaf1cb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769353"
---
# <a name="cmfcpropertygridfontproperty-class"></a>Cmfcpropertygridfontproperty, classe

Le `CMFCPropertyGridFileProperty` classe prend en charge un élément de contrôle de liste de propriétés qui ouvre une boîte de dialogue de sélection de police.

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
|`CMFCPropertyGridFontProperty::FormatProperty`|Met en forme la représentation textuelle d'une valeur de propriété. (Substitue [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Récupère la couleur de police que l’utilisateur sélectionne à partir de la boîte de dialogue Police.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Récupère la police de l’utilisateur sélectionne dans la boîte de dialogue Police.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Appelé par l'infrastructure quand l'utilisateur clique sur un bouton contenu dans une propriété. (Substitue [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Notes

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

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
[in] Le nom de la propriété.

*lf*<br/>
[in] Une structure de police logique qui spécifie les attributs de la police.

*dwFontDialogFlags*<br/>
[in] Styles sont appliqués à la boîte de dialogue de police qui s’affiche lorsque vous cliquez sur le bouton de liste déroulante de valeur de propriété. La valeur par défaut est la combinaison au niveau du bit (ou) de CF_EFFECTS et CF_SCREENFONTS. Pour plus d’informations, consultez le *indicateurs* paramètre de la [CHOOSEFONT Structure](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta).

*lpszDescr*<br/>
[in] Description de la propriété de police. La valeur par défaut est NULL.

*dwData*<br/>
[in] Données spécifiques à l’application, par exemple un entier ou un pointeur à d’autres données qui sont associés à la propriété. La valeur par défaut est 0.

*color*<br/>
[in] La couleur de la police. La valeur par défaut est la couleur par défaut.

### <a name="remarks"></a>Notes

Un `CMFCPropertyGridFontProperty` objet représente une propriété de police dans un contrôle de police de grille de propriétés.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCPropertyGridFontProperty` classe. Cet exemple fait partie de la [exemple nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor

Récupère la couleur de police que l’utilisateur sélectionne à partir de la boîte de dialogue Police.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de couleur RVB qui représente la couleur de police sélectionnée.

### <a name="remarks"></a>Notes

##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont

Récupère la police de l’utilisateur sélectionne dans la boîte de dialogue Police.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) structure qui décrit la police sélectionnée.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty, classe](../../mfc/reference/cmfcpropertygridproperty-class.md)
