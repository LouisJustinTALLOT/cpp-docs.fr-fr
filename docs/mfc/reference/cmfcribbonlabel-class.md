---
description: 'En savoir plus sur : classe CMFCRibbonLabel'
title: CMFCRibbonLabel, classe
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
ms.openlocfilehash: 0699e76dfe90b87cd813d18d076adf23f8512bee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321824"
---
# <a name="cmfcribbonlabel-class"></a>CMFCRibbonLabel, classe

Implémente une étiquette de texte non interactive pour un ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|Construit et initialise un `CMFCRibbonLabel` objet avec la chaîne de texte spécifiée.|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCRibbonLabel::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCRibbonLabel :: SetACCData](#setaccdata)|Détermine les données d’accessibilité pour l’élément d’étiquette de ruban actuel. (Substitue [CMFCRibbonButton :: SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

### <a name="remarks"></a>Notes

Après avoir créé une étiquette de ruban, ajoutez-la à un panneau en appelant [CMFCRibbonPanel :: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

Vous ne pouvez pas ajouter une étiquette de ruban à la barre d’outils accès rapide.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxRibbonLabel. h

## <a name="cmfcribbonlabelcmfcribbonlabel"></a><a name="cmfcribbonlabel"></a> CMFCRibbonLabel::CMFCRibbonLabel

Construit et initialise un objet [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) qui affiche la chaîne de texte spécifiée.

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>Paramètres

*lpszText*<br/>
dans Texte à afficher dans l’étiquette.

*bIsMultiLine*<br/>
dans TRUE pour spécifier que l’étiquette est une étiquette à plusieurs lignes ; Sinon, FALSe.

## <a name="cmfcribbonlabelsetaccdata"></a><a name="setaccdata"></a> CMFCRibbonLabel :: SetACCData

Détermine les données d’accessibilité pour l’élément d’étiquette de ruban actuel.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
dans Représente la fenêtre parente de l’étiquette de ruban actuelle.

*data*<br/>
à Objet de type `CAccessibilityData` qui est rempli avec les données d’accessibilité de l’étiquette de ruban actuelle.

### <a name="return-value"></a>Valeur renvoyée

TRUE si le paramètre de *données* a été correctement rempli avec les données d’accessibilité de l’étiquette de ruban actuelle ; Sinon, FALSe.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
