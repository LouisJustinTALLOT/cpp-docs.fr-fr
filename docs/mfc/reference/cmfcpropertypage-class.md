---
description: 'En savoir plus sur : classe CMFCPropertyPage'
title: CMFCPropertyPage, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: 9acdce1fd2f6133d44699f7bea4cce00e9d6dadb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289853"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage, classe

La `CMFCPropertyPage` classe prend en charge l’affichage des menus contextuels dans une page de propriétés.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCPropertyPage :: CMFCPropertyPage](#cmfcpropertypage)|Construit un objet `CMFCPropertyPage`.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCPropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|`CMFCPropertyPage::OnSetActive`|Cette fonction membre est appelée par l’infrastructure lorsque la page est choisie par l’utilisateur et devient la page active. (Substitue [CPropertyPage :: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Pour plus d’informations et la syntaxe de méthode, consultez [CWnd ::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CPropertyPage::PreTranslateMessage`.)|

## <a name="remarks"></a>Notes

La `CMFCPropertyPage` classe représente des pages individuelles d’une feuille de propriétés, également appelée boîte de dialogue à onglets.

Utilisez la `CMFCPropertyPage` classe avec la classe [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) . Pour utiliser des menus sur une page de propriétés, remplacez toutes les occurrences de la `CPropertyPage` classe par la `CMFCPropertyPage` classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxpropertypage. h

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a> CMFCPropertyPage :: CMFCPropertyPage

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

*nIDTemplate*<br/>
ID de ressource du modèle pour cette page.

*nIDCaption*<br/>
ID de ressource de l’étiquette à placer dans l’onglet pour cette page. Si la valeur est 0, le nom est obtenu à partir du modèle de boîte de dialogue pour cette page. La valeur par défaut est 0.

*lpszTemplateName*<br/>
Pointe vers le nom du modèle pour cette page. Ne peut pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

Pour plus d’informations sur les paramètres du constructeur, consultez [CPropertyPage :: CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet, classe](../../mfc/reference/cmfcpropertysheet-class.md)
