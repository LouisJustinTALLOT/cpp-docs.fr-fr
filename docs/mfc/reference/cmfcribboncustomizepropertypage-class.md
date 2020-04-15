---
title: CMFCRibbonCustomizePropertyPage, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: c77e2fed1067091c139eee664fb291b83742eb54
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375195"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage, classe

Implémente une page personnalisée pour la boîte de dialogue **Customize** dans les applications basées sur ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Construit un objet `CMFCRibbonCustomizePropertyPage`.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Ajoute une catégorie personnalisée à la boîte combo **Commands.**|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Appelé par le système quand un utilisateur clique **SUR OK** sur la boîte de dialogue **Personnaliser.**|

## <a name="remarks"></a>Notes

Si vous souhaitez ajouter des commandes personnalisées à la boîte de dialogue **Customize,** vous devez gérer le message AFX_WM_ON_RIBBON_CUSTOMIZE. Dans le gestionnaire de message, instantané d’un `CMFCRibbonCustomizePropertyPage` objet sur la pile. Créez une liste de commandes personnalisées, puis appelez `AddCustomCategory` pour ajouter la nouvelle page à la boîte de dialogue **Customize.**

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCRibbonCustomizePropertyPage` construire un objet et ajouter une catégorie personnalisée.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory

Ajoute une catégorie personnalisée à la boîte combo **Commands.**

```
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*lpszName (en)*|[dans] Spécifie le nom de la catégorie personnalisée.|
|*lstIDS (en)*|[dans] Contient des cartes d’ID de commande de ruban à montrer dans la catégorie personnalisée.|

### <a name="remarks"></a>Notes

Cette méthode ajoute une catégorie nommée *lpszName* à la boîte combo **Commands.** Lorsque l’utilisateur sélectionne la catégorie, les commandes spécifiées dans *lstIDS* apparaissent dans la liste de commande.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Construit un objet `CMFCRibbonCustomizePropertyPage`.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Paramètres

*pRibbonBar (en)*<br/>
[dans] Un pointeur à un contrôle de ruban pour lequel les options à personnaliser.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK

Calleld par le système quand un utilisateur clique **OK** sur la boîte de dialogue **Personnaliser.**

```
virtual void OnOK();
```

### <a name="remarks"></a>Notes

La mise en œuvre par défaut applique les options sélectionnées dans la boîte de dialogue **Customize** à la barre d’outils d’accès rapide.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
