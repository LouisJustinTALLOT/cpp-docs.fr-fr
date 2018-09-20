---
title: Cmfcdisablemenuanimation, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
dev_langs:
- C++
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 431b7caf3efcf9e569d6eee3c309b409d8479730
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443317"
---
# <a name="cmfcdisablemenuanimation-class"></a>Cmfcdisablemenuanimation, classe

Désactive l’animation de menu contextuel.

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
|[CMFCDisableMenuAnimation::Restore](#restore)|Restaure l’animation précédente l’infrastructure utilisée pour afficher un menu contextuel.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|Name|Description|
|`CMFCDisableMenuAnimation::m_animType`|Stocke le type d’animation de menu déroulant précédent.|

### <a name="remarks"></a>Notes

Utilisez cette classe d’assistance pour désactiver temporairement d’animation de menu contextuel (par exemple, lorsque vous traitez la souris ou le clavier).

Un `CMFCDisableMenuAnimation` objet désactive l’animation de menu contextuel pendant sa durée de vie. Le constructeur stocke le type d’animation de menu contextuel actuel dans le `m_animType` champ et comment l’animation actuelle type `CMFCPopupMenu::NO_ANIMATION`. Le destructeur restaure le type d’animation précédente.

Vous pouvez créer un `CMFCDisableMenuAnimation` objet sur la pile pour désactiver l’animation de menu contextuel dans une seule fonction. Si vous souhaitez désactiver l’animation de menu contextuel entre les fonctions, créez un `CMFCDisableMenuAnimation` de l’objet sur le tas, puis le supprimer lorsque vous souhaitez restaurer l’animation de menu contextuel.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la pile pour désactiver temporairement d’animation de menu.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxpopupmenu.h

##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore

Restaure l’animation précédente l’infrastructure utilisée pour afficher un menu contextuel.

```
void Restore ();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée par le `CMFCDisableMenuAnimation` destructeur pour restaurer l’animation précédente l’infrastructure utilisée pour afficher un menu contextuel.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu, classe](../../mfc/reference/cmfcpopupmenu-class.md)
