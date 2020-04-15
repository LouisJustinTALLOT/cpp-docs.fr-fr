---
title: Classe CMFCRibbonLabel
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: cd30e374441661368d3ea7abf5177424f8dffb3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375122"
---
# <a name="cmfcribbonlabel-class"></a>Classe CMFCRibbonLabel

Implémente une étiquette de texte non interactive pour un ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Construit et initialise `CMFCRibbonLabel` un objet avec la chaîne de texte spécifiée.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCRibbonLabel::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|Détermine les données d’accessibilité de l’élément d’étiquette de ruban actuel. (Overrides [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>Notes

Après avoir créé une étiquette de ruban, ajoutez-la à un panneau en appelant [CMFCRibbonPanel: :Ajouter](../../mfc/reference/cmfcribbonpanel-class.md#add).

Vous ne pouvez pas ajouter une étiquette ruban à la barre d’outils d’accès rapide.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxRibbonLabel.h

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a>CMFCRibbonLabel::CMFCRibbonLabel

Construit et initialise un objet [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) qui affiche la chaîne de texte spécifiée.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
[dans] Le texte à apparaître dans l’étiquette.

*bIsMultiLine (en)*<br/>
[dans] VRAI pour spécifier que l’étiquette est une étiquette multi-lignes; autrement, FALSE.

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonLabel::SetACCData

Détermine les données d’accessibilité de l’élément d’étiquette de ruban actuel.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
[dans] Représente la fenêtre parente de l’étiquette de ruban actuelle.

*data*<br/>
[out] Un objet `CAccessibilityData` de type qui est peuplé avec les données d’accessibilité de l’étiquette de ruban actuelle.

### <a name="return-value"></a>Valeur de retour

VRAI si le paramètre *de données* a été peuplé avec succès avec les données d’accessibilité de l’étiquette de ruban actuelle; autrement, FALSE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
