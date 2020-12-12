---
description: 'En savoir plus sur : classe CMFCStandardColorsPropertyPage'
title: CMFCStandardColorsPropertyPage, classe
ms.date: 11/04/2016
helpviewer_keywords:
- CMFCStandardColorsPropertyPage class [MFC]
ms.assetid: b84b7cfb-bb24-4c65-804a-5b642cb64400
ms.openlocfilehash: cffce34642bd4df40ceda3156fe846e60db4b3a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164092"
---
# <a name="cmfcstandardcolorspropertypage-class"></a>CMFCStandardColorsPropertyPage, classe

Représente une page de propriétés que les utilisateurs utilisent pour sélectionner des couleurs standard dans une boîte de dialogue de couleur.

## <a name="syntax"></a>Syntaxe

```
class CMFCStandardColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|`CMFCStandardColorsPropertyPage::CMFCStandardColorsPropertyPage`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|`CMFCStandardColorsPropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCStandardColorsPropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|

### <a name="remarks"></a>Notes

La `CMFCColorDialog` classe utilise cette classe pour afficher la page de propriétés couleur standard. Pour plus d’informations sur `CMFCColorDialog` , consultez [CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCStandardColorsPropertyPage](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxstandardcolorspropertypage. h

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCCustomColorsPropertyPage, classe](../../mfc/reference/cmfccustomcolorspropertypage-class.md)
