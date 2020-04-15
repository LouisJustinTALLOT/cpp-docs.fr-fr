---
title: CMFCPropertyPage, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: e493f016b6384a768935186c31e3fc71ade6382f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361765"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage, classe

La `CMFCPropertyPage` classe prend en charge l’affichage de menus pop-up sur une page de propriété.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Construit un objet `CMFCPropertyPage`.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCPropertyPage::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|`CMFCPropertyPage::OnSetActive`|Cette fonction de membre est appelée par le cadre lorsque la page est choisie par l’utilisateur et devient la page active. (Overrides [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows De TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Pour plus d’informations et de syntaxe méthode, voir [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CPropertyPage::PreTranslateMessage`.)|

## <a name="remarks"></a>Notes

La `CMFCPropertyPage` classe représente les pages individuelles d’une feuille de propriété, autrement connue sous le nom de boîte de dialogue d’onglet.

Utilisez `CMFCPropertyPage` la classe avec la classe [CMFCPropertySheet.](../../mfc/reference/cmfcpropertysheet-class.md) Pour utiliser les menus sur une page `CPropertyPage` de propriété, remplacez tous les événements de la classe par la `CMFCPropertyPage` classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpropertypage.h

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage

Construit un objet `CMFCPropertyPage`.

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>Paramètres

*nIDTemplate (en)*<br/>
Id de ressources du modèle pour cette page.

*nIDCaption (en)*<br/>
Id de ressources de l’étiquette à mettre dans l’onglet pour cette page. Si 0, le nom est obtenu à partir du modèle de boîte de dialogue pour cette page. La valeur par défaut est 0.

*lpszTemplateName*<br/>
Indique le nom du modèle pour cette page. Ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

Pour plus d’informations sur les paramètres du constructeur, voir [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet, classe](../../mfc/reference/cmfcpropertysheet-class.md)
