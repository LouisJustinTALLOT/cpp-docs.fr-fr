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
ms.openlocfilehash: 97a93e000b3e12d8ec4824100059581216b1b8d9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840763"
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation, classe

Désactive l’animation des menus contextuels.

## <a name="syntax"></a>Syntaxe

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|-|-|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Construit un objet `CMFCDisableMenuAnimation`.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|-|-|
|[CMFCDisableMenuAnimation :: Restore](#restore)|Restaure l’animation précédente que le Framework a utilisé pour afficher un menu contextuel.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|-|-|
|`CMFCDisableMenuAnimation::m_animType`|Stocke le type d’animation du menu contextuel précédent.|

### <a name="remarks"></a>Notes

Utilisez cette classe d’assistance pour désactiver temporairement l’animation des menus contextuels (par exemple, lorsque vous traitez des commandes de souris ou de clavier).

Un `CMFCDisableMenuAnimation` objet désactive l’animation du menu contextuel pendant sa durée de vie. Le constructeur stocke le type d’animation du menu contextuel actuel dans le `m_animType` champ et définit le type d’animation actuel sur `CMFCPopupMenu::NO_ANIMATION` . Le destructeur restaure le type d’animation précédent.

Vous pouvez créer un `CMFCDisableMenuAnimation` objet sur la pile pour désactiver l’animation du menu contextuel tout au long d’une seule fonction. Si vous souhaitez désactiver l’animation des menus contextuels entre les fonctions, créez un `CMFCDisableMenuAnimation` objet sur le tas, puis supprimez-le lorsque vous souhaitez restaurer l’animation du menu contextuel.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la pile pour désactiver temporairement l’animation de menu.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxpopupmenu. h

## <a name="cmfcdisablemenuanimationrestore"></a><a name="restore"></a> CMFCDisableMenuAnimation :: Restore

Restaure l’animation précédente que le Framework a utilisé pour afficher un menu contextuel.

```cpp
void Restore ();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le `CMFCDisableMenuAnimation` destructeur pour restaurer l’animation précédente que le Framework a utilisé pour afficher un menu contextuel.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)
