---
title: CMFCDisableMenuAnimation, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 990f41d2dfa6491d246797322ee275c9648d52a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367567"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation, classe

Désactiver l’animation du menu pop-up.

## <a name="syntax"></a>Syntaxe

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Construit un objet `CMFCDisableMenuAnimation`.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCDisableMenuAnimation::Restaurer](#restore)|Restaure l’animation précédente que le cadre utilisé pour afficher un menu pop-up.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|Nom|Description|
|`CMFCDisableMenuAnimation::m_animType`|Stocke le type d’animation de menu pop-up précédent.|

### <a name="remarks"></a>Notes

Utilisez cette classe d’aide pour désactiver temporairement l’animation du menu pop-up (par exemple, lorsque vous traitez les commandes de souris ou de clavier).

Un `CMFCDisableMenuAnimation` objet désactive l’animation du menu pop-up au cours de sa vie. Le constructeur stocke le type d’animation `m_animType` de menu pop-up `CMFCPopupMenu::NO_ANIMATION`actuel dans le domaine et définit le type d’animation actuel à . Le destructeur restaure le type d’animation précédent.

Vous pouvez `CMFCDisableMenuAnimation` créer un objet sur la pile pour désactiver l’animation du menu pop-up tout au long d’une seule fonction. Si vous souhaitez désactiver l’animation du menu `CMFCDisableMenuAnimation` popup entre les fonctions, créez un objet sur le tas, puis supprimez-le lorsque vous souhaitez restaurer l’animation du menu pop-up.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la pile pour désactiver temporairement l’animation du menu.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxpopupmenu.h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a>CMFCDisableMenuAnimation::Restaurer

Restaure l’animation précédente que le cadre utilisé pour afficher un menu pop-up.

```
void Restore ();
```

### <a name="remarks"></a>Notes

Cette méthode est `CMFCDisableMenuAnimation` appelée par le destructeur pour restaurer l’animation précédente que le cadre utilisé pour afficher un menu pop-up.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)
