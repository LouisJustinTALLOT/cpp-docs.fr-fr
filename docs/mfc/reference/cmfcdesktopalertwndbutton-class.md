---
description: 'En savoir plus sur : classe CMFCDesktopAlertWndButton'
title: CMFCDesktopAlertWndButton, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: 0c645f4ec79aaa58364cfa9688d19915ece205bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330075"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton, classe

Permet d’ajouter des boutons à une boîte de dialogue d’alerte sur le bureau.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Constructeur par défaut.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Détermine si le bouton est affiché dans la zone légende de la boîte de dialogue d’alerte.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Détermine si le bouton ferme la boîte de dialogue d’alerte.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|-|-|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Valeur booléenne qui spécifie si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Valeur booléenne qui spécifie si le bouton ferme la boîte de dialogue d’alerte.|

### <a name="remarks"></a>Notes

Par défaut, le constructeur affecte la `m_bIsCaptionButton` `m_bIsCloseButton` valeur false aux membres de données et. L' `CMFCDesktopAlertDialog` objet parent affecte `m_bIsCaptionButton` à la valeur true si le bouton est positionné dans la zone de légende de la boîte de dialogue d’alerte. La `CMFCDesktopAlertDialog` classe crée un `CMFCDesktopAlertWndButton` objet qui sert de bouton pour fermer la boîte de dialogue d’alerte et définit `m_bIsCloseButton` sur true.

Ajoutez `CMFCDesktopAlertWndButton` des objets à un `CMFCDesktopAlertDialog` objet comme vous ajouteriez n’importe quel bouton. Pour plus d’informations sur `CMFCDesktopAlertDialog` , consultez [CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `SetImage` méthode dans la `CMFCDesktopAlertWndButton` classe. Cet extrait de code fait partie de l' [exemple de démonstration](../../overview/visual-cpp-samples.md)de l’alerte sur le bureau.

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxdesktopalertwnd. h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a> CMFCDesktopAlertWndButton::IsCaptionButton

Détermine si le bouton est affiché dans la zone légende de la boîte de dialogue d’alerte.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le bouton est affiché dans la zone légende de la boîte de dialogue d’alerte ; Sinon, 0.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a> CMFCDesktopAlertWndButton::IsCloseButton

Détermine si le bouton ferme la boîte de dialogue d’alerte.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le bouton ferme la boîte de dialogue d’alerte ; Sinon, 0.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md)
