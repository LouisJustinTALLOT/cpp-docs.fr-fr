---
title: Cmfccustomcolorspropertypage, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: b28711991835dd14929e5387709046c3867c715e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299880"
---
# <a name="cmfccustomcolorspropertypage-class"></a>Cmfccustomcolorspropertypage, classe

Représente une page de propriétés que vous pouvez sélectionner des couleurs personnalisées dans une boîte de dialogue couleur.

## <a name="syntax"></a>Syntaxe

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|`CMFCCustomColorsPropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objet qui est associé à ce type de classe.|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Définit les composants de couleur de la page de propriétés.|

### <a name="remarks"></a>Notes

Le `CMFCColorDialog` utilise cette classe pour afficher la page de propriété de couleur personnalisée. Pour plus d’informations sur `CMFCColorDialog`, consultez [cmfccolordialog, classe](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCCustomColorsPropertyPage` de l’objet et définir les composants de couleur de la page de propriétés.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxcustomcolorspropertypage.h

##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup

Définit les composants de couleur de la page de propriétés.

```
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*R*|[in] Le composant rouge de la valeur RVB.|
|*G*|[in] Le composant vert de la valeur RVB.|
|*B*|[in] La composante bleue de la valeur RVB.|

### <a name="remarks"></a>Notes

Cette méthode met à jour le RVB actuel et TSL (teinte, luminosité et saturation) couleur valeurs associées de la page de propriétés. Le [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) méthode appelle cette méthode lorsque le framework initialise la boîte de dialogue couleur ou l’utilisateur appuie sur le bouton gauche de la souris. Pour plus d’informations sur `CMFCColorDialog`, consultez [cmfccolordialog, classe](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage, classe](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
