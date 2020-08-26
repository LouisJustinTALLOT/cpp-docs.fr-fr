---
title: CMFCCustomColorsPropertyPage, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
ms.openlocfilehash: 07b369e8c47419db31bed3e49e159e3e7925d5ae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844533"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage, classe

Représente une page de propriétés qui peut sélectionner des couleurs personnalisées dans une boîte de dialogue de couleur.

## <a name="syntax"></a>Syntaxe

```
class CMFCCustomColorsPropertyPage : public CPropertyPage
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|`CMFCCustomColorsPropertyPage::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCCustomColorsPropertyPage::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCCustomColorsPropertyPage :: Setup](#setup)|Définit les composants de couleur de la page de propriétés.|

### <a name="remarks"></a>Notes

La `CMFCColorDialog` classe utilise cette classe pour afficher la page de propriétés couleur personnalisée. Pour plus d’informations sur `CMFCColorDialog` , consultez [CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCCustomColorsPropertyPage` objet et définir les composants de couleur de la page de propriétés.

[!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcustomcolorspropertypage. h

## <a name="cmfccustomcolorspropertypagesetup"></a><a name="setup"></a> CMFCCustomColorsPropertyPage :: Setup

Définit les composants de couleur de la page de propriétés.

```cpp
void Setup(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Paramètres

*R*\
dans Composant rouge de la valeur RVB.

*Activée*\
dans Composant vert de la valeur RVB.

*P*\
dans Composant bleu de la valeur RVB.

### <a name="remarks"></a>Notes

Cette méthode met à jour la valeur RVB actuelle et les valeurs de couleur TSL (teinte, luminosité et saturation) associées de la page de propriétés. La méthode [CMFCColorDialog :: SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo) appelle cette méthode lorsque le Framework initialise la boîte de dialogue de couleur ou lorsque l’utilisateur appuie sur le bouton gauche de la souris. Pour plus d’informations sur `CMFCColorDialog` , consultez [CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog, classe](../../mfc/reference/cmfccolordialog-class.md)<br/>
[CMFCStandardColorsPropertyPage, classe](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)
