---
title: CMFCCustomColorsProétyPage Classe
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 468d947947fc89f9ebc832cda722d854bb8b4be2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752467"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsProétyPage Classe

Représente une page de propriété qui peut sélectionner des couleurs personnalisées dans une boîte de dialogue de couleur.

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
|`CMFCCustomColorsPropertyPage::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCCustomColorsPropertyPage::Setup](#setup)|Définit les composants de couleur de la page de propriété.|

### <a name="remarks"></a>Notes

La `CMFCColorDialog` classe utilise cette classe pour afficher la page de propriété couleur personnalisée. Pour plus `CMFCColorDialog`d’informations sur , voir [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCCustomColorsPropertyPage` construire un objet et définir les composants de couleur de la page de propriété.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxcustomcolorspropertypage.h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a>CMFCCustomColorsPropertyPage::Setup

Définit les composants de couleur de la page de propriété.

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*R*|[dans] La composante rouge de la valeur RGB.|
|*G*|[dans] La composante verte de la valeur RGB.|
|*B*|[dans] La composante bleue de la valeur RGB.|

### <a name="remarks"></a>Notes

Cette méthode met à jour les valeurs de couleur actuelles du RGB et du HLS (teinte, légèreté et saturation) associées de la page de propriété. Le [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) méthode appelle cette méthode lorsque le cadre initialise la boîte de dialogue couleur ou l’utilisateur appuie sur le bouton de la souris gauche. Pour plus `CMFCColorDialog`d’informations sur , voir [CMFCColorDialog Class](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CmFCStandardColorsParertyPage Classe](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
