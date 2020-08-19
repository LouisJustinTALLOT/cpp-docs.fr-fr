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
ms.openlocfilehash: d36e3a301aa5b861c296b0bb4859e9442dbdb75e
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560879"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage, classe

Implémente une page personnalisée pour la boîte de dialogue **personnaliser** dans des applications basées sur le ruban.

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
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Ajoute une catégorie personnalisée à la zone de liste déroulante **commandes** .|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCRibbonCustomizePropertyPage :: OnOK](#onok)|Appelé par le système lorsqu’un utilisateur clique sur **OK** dans la boîte de dialogue **personnaliser** .|

## <a name="remarks"></a>Notes

Si vous souhaitez ajouter des commandes personnalisées à la boîte de dialogue **personnaliser** , vous devez gérer le message de AFX_WM_ON_RIBBON_CUSTOMIZE. Dans le gestionnaire de messages, instanciez un `CMFCRibbonCustomizePropertyPage` objet sur la pile. Créez une liste de commandes personnalisées, puis appelez `AddCustomCategory` pour ajouter la nouvelle page à la boîte de dialogue **personnaliser** .

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCRibbonCustomizePropertyPage` objet et ajouter une catégorie personnalisée.

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

**En-tête :** afxribboncustomizedialog. h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a> CMFCRibbonCustomizePropertyPage::AddCustomCategory

Ajoute une catégorie personnalisée à la zone de liste déroulante **commandes** .

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Paramètres

*lpszName*\
dans Spécifie le nom de la catégorie personnalisée.

*lstIDS*\
dans Contient les ID de commande du ruban à afficher dans la catégorie personnalisée.

### <a name="remarks"></a>Notes

Cette méthode ajoute une catégorie nommée *lpszName* à la zone de liste déroulante **commandes** . Lorsque l’utilisateur sélectionne la catégorie, les commandes spécifiées dans *lstIDS* s’affichent dans la liste des commandes.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a> CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Construit un objet `CMFCRibbonCustomizePropertyPage`.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Paramètres

*pRibbonBar*<br/>
dans Pointeur vers un contrôle de ruban pour lequel les options à personnaliser.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a> CMFCRibbonCustomizePropertyPage :: OnOK

Calleld par le système lorsqu’un utilisateur clique sur **OK** dans la boîte de dialogue **personnaliser** .

```
virtual void OnOK();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut applique les options sélectionnées dans la boîte de dialogue **personnaliser** à la barre d’outils accès rapide.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
