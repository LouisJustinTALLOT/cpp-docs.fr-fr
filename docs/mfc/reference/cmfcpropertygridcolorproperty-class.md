---
title: Classe CMFCPropertyGridColorProperty
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 62015f384fa5f72ceeceed2605cbf9a6b646a1eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375317"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>Classe CMFCPropertyGridColorProperty

La classe `CMFCPropertyGridColorProperty` prend en charge un élément de contrôle de liste de propriétés qui ouvre une boîte de dialogue de sélection de couleur.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Construit un objet `CMFCPropertyGridColorProperty`.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Permet le bouton *automatique* sur la boîte de dialogue de sélection des couleurs. (Le bouton automatique standard est étiqueté **automatique**.)|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Permet *l’autre* bouton sur la boîte de dialogue de sélection des couleurs. (L’autre bouton standard est étiqueté **Plus de couleurs**.)|
|`CMFCPropertyGridColorProperty::FormatProperty`|Met en forme la représentation textuelle d'une valeur de propriété. (Overrides [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Obtient la couleur actuelle de la propriété.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Appelé par l'infrastructure quand l'utilisateur clique sur un bouton contenu dans une propriété. (Overrides [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Appelé par l'infrastructure pour afficher la valeur de propriété. (Overrides [CMFCPropertyGridProperty::OnDrawValue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue).)|
|`CMFCPropertyGridColorProperty::OnEdit`|Appelé par l'infrastructure quand l'utilisateur s'apprête à modifier une valeur de propriété. (Overrides [CMFCPropertyGridProperty::OnEdit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit).)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Appelé par l'infrastructure quand la valeur d'une propriété modifiable a changé. (Overrides [CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Définit une nouvelle couleur pour la propriété.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Spécifie le nombre de colonnes de la grille de propriétés de couleur actuelle.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Définit la valeur d'origine d'une propriété modifiable.|

## <a name="remarks"></a>Notes

La classe `CMFCPropertyGridColorProperty` prend en charge une propriété de couleur qui peut être ajoutée à un contrôle de liste de propriétés. Pour plus d’informations, voir la [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet de la classe `CMFCPropertyGridColorProperty` et configurer cet objet à l'aide de différentes méthodes de la classe `CMFCPropertyGridColorProperty`. Le code explique comment activer les boutons automatique et autre et comment définir la couleur et le nombre de colonnes. Cet exemple fait partie de [l’échantillon De nouveaux contrôles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpropertygridctrl.h

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a>CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

Construit un objet `CMFCPropertyGridColorProperty`.

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
[in] Nom de la propriété.

*Couleur*<br/>
[dans] La valeur de couleur de la propriété.

*pPalette (pPalette)*<br/>
[dans] Pointeur vers une palette de couleurs. La valeur par défaut est NULL.

*lpszDescr*<br/>
[dans] La description de la propriété. La valeur par défaut est NULL.

*dwData dwData*<br/>
[dans] Données spécifiques à l’application, telles qu’un intégrant ou un pointeur à d’autres données qui sont associées à la propriété. La valeur par défaut est 0.

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCPropertyGridColorProperty::EnableAutomaticButton

Permet le bouton *automatique* sur la boîte de dialogue de sélection des couleurs. (Le bouton automatique standard est étiqueté **automatique**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Le texte d’étiquette du bouton automatique.

*couleurAutomatique*<br/>
[dans] La valeur couleur RGB de la couleur automatique (par défaut).

*bEnable*<br/>
[dans] VRAI pour activer le bouton automatique; autrement, FALSE. La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a>CMFCPropertyGridColorProperty::EnableOtherButton

Permet *l’autre* bouton sur la boîte de dialogue de sélection des couleurs. (L’autre bouton standard est étiqueté **Plus de couleurs**.)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszLabel*<br/>
[dans] Le texte d’étiquette de l’autre bouton.

*bAltColorDlg*<br/>
[dans] VRAI pour `CMFCColorDialog` afficher la boîte de dialogue; FALSE pour afficher la boîte de dialogue de sélection de couleur standard. La valeur par défaut est TRUE.

*bEnable*<br/>
[dans] VRAI pour afficher l’autre bouton; autrement, FALSE.  La valeur par défaut est TRUE.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridColorProperty::GetColor

Obtient la couleur actuelle de la propriété.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur de couleur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a>CMFCPropertyGridColorProperty::SetColor

Définit une nouvelle couleur pour la propriété.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Paramètres

*Couleur*<br/>
[dans] Une valeur de couleur RGB.

### <a name="remarks"></a>Notes

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCPropertyGridColorProperty::SetColumnsNumber

Spécifie le nombre de colonnes de la grille de propriétés de couleur actuelle.

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Paramètres

*nColumnsNumber*<br/>
[dans] Le nombre préféré de colonnes dans la grille de propriété de couleur.

### <a name="remarks"></a>Notes

Cette méthode définit la `m_nColumnsNumber` valeur du membre des données protégées.

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a>CMFCPropertyGridColorProperty::SetOriginalValue

Définit la valeur d'origine d'une propriété modifiable.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Paramètres

*varValue*<br/>
[dans] Une valeur.

### <a name="remarks"></a>Notes

Utilisez la méthode [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) pour réinitialiser la valeur originale d’une propriété modifiée.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl, classe](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Classe CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
