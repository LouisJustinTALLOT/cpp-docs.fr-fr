---
title: CMFCRibbonCustomizeDialog Classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: a66c0a19c04e0a900b91c0c28c45bb9c766d25c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375209"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog Classe

Affiche la page **de personnalisation** du ruban.

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
|`CMFCRibbonCustomizeDialog::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|

## <a name="remarks"></a>Notes

MFC instantanéise automatiquement cette classe si vous ne traitez pas le AFX_WM_ON_RIBBON_CUSTOMIZE message, ou si vous retournez 0 du gestionnaire de message.

Si vous souhaitez utiliser cette classe dans votre application pour afficher la boîte de `DoModal` dialogue **de personnalisation** du ruban, il suffit de l’instantanéiser et d’appeler la méthode.

Parce que cette classe est dérivée de [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) `CMFCPropertySheet` Class , vous pouvez ajouter des pages personnalisées en utilisant l’API.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a>CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

Construit un objet `CMFCRibbonCustomizeDialog`.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] Un pointeur à la fenêtre parente (généralement le cadre principal).

*pRibbon (pRibbon)*<br/>
[dans] Un pointeur `CMFCRibbonBar` à celui qui doit être personnalisé.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCRibbonCustomizeDialog` construire un objet.

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Notes

Le constructeur instantané un [objet CMFCRibbonCustomizePropertyPage Class](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) et l’ajoute à la collection de pages de feuilles de propriété.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
