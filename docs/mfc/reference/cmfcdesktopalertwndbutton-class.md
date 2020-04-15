---
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
ms.openlocfilehash: 5b18a15f8bfd98396acae0558d121b32bc4127c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367627"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton, classe

Permet d’ajouter des boutons à une boîte de dialogue d’alerte de bureau.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Constructeur par défaut.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Détermine si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Détermine si le bouton ferme la boîte de dialogue d’alerte.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|Nom|Description|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Une valeur Boolean qui précise si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Une valeur Boolean qui précise si le bouton ferme la boîte de dialogue d’alerte.|

### <a name="remarks"></a>Notes

Par défaut, le constructeur `m_bIsCaptionButton` `m_bIsCloseButton` définit les membres et les données à FALSE. L’objet `CMFCDesktopAlertDialog` `m_bIsCaptionButton` parent se définit vers TRUE si le bouton est positionné dans la zone de légende de la boîte de dialogue d’alerte. La `CMFCDesktopAlertDialog` classe `CMFCDesktopAlertWndButton` crée un objet qui sert de bouton qui `m_bIsCloseButton` ferme la boîte de dialogue d’alerte et se couche à VRAI.

Ajoutez `CMFCDesktopAlertWndButton` des `CMFCDesktopAlertDialog` objets à un objet car vous ajoutez n’importe quel bouton. Pour plus `CMFCDesktopAlertDialog`d’informations sur , voir [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment `SetImage` utiliser `CMFCDesktopAlertWndButton` la méthode dans la classe. Cet extrait de code fait partie de [l’échantillon de démonstration d’alerte de bureau](../../overview/visual-cpp-samples.md).

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

**En-tête:** afxdesktopalertwnd.h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a>CMFCDesktopAlertWndButton::IsCaptionButton

Détermine si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte; autrement, 0.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a>CMFCDesktopAlertWndButton::IsCloseButton

Détermine si le bouton ferme la boîte de dialogue d’alerte.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton ferme la boîte de dialogue d’alerte; autrement, 0.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md)
