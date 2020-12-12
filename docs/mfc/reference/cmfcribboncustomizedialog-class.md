---
description: 'En savoir plus sur : classe CMFCRibbonCustomizeDialog'
title: CMFCRibbonCustomizeDialog, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: 9420ebdf32a1c26cba6efee17467fd3dfe202574
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293610"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog, classe

Affiche la page **personnaliser** du ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Construit un objet `CMFCRibbonCustomizeDialog`.|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|

## <a name="remarks"></a>Notes

MFC instancie automatiquement cette classe si vous ne traitez pas le message AFX_WM_ON_RIBBON_CUSTOMIZE ou si vous retournez 0 à partir du gestionnaire de messages.

Si vous souhaitez utiliser cette classe dans votre application pour afficher la boîte de dialogue de **personnalisation** du ruban, il vous suffit de l’instancier et d’appeler la `DoModal` méthode.

Étant donné que cette classe est dérivée de la [classe CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md), vous pouvez ajouter des pages personnalisées à l’aide de l' `CMFCPropertySheet` API.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxribboncustomizedialog. h

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a> CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

Construit un objet `CMFCRibbonCustomizeDialog`.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Pointeur vers la fenêtre parente (généralement le frame principal).

*pRibbon*<br/>
dans Pointeur vers le `CMFCRibbonBar` qui doit être personnalisé.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCRibbonCustomizeDialog` objet.

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Notes

Le constructeur instancie un objet de [classe CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) et l’ajoute à la collection de pages de feuille de propriétés.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
