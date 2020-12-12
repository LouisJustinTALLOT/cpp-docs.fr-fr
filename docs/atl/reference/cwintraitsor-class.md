---
description: 'En savoir plus sur : classe CWinTraitsOR'
title: CWinTraitsOR, classe
ms.date: 11/04/2016
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
ms.openlocfilehash: 1d0a7ff8a78ebbdc416bdace2a1ea1f0199c292f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140060"
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR, classe

Cette classe fournit une méthode permettant de standardiser les styles utilisés lors de la création d’un objet Window.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0,
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```

#### <a name="parameters"></a>Paramètres

*t_dwStyle*<br/>
Styles de fenêtre par défaut.

*t_dwExStyle*<br/>
Styles de fenêtre étendus par défaut.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|Récupère les styles étendus pour l' `CWinTraitsOR` objet.|
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|Récupère les styles standard pour l' `CWinTraitsOR` objet.|

## <a name="remarks"></a>Notes

Cette classe de [traits de fenêtre](../../atl/understanding-window-traits.md) fournit une méthode simple pour standardiser les styles utilisés pour la création d’un objet de fenêtre ATL. Utilisez une spécialisation de cette classe en tant que paramètre de modèle dans [CWindowImpl](../../atl/reference/cwindowimpl-class.md) ou une autre des classes de fenêtre d’ATL pour spécifier l’ensemble minimal de styles standard et étendus à utiliser pour les instances de cette classe de fenêtre.

Utilisez une spécialisation de ce modèle si vous souhaitez vous assurer que certains styles sont définis pour toutes les instances de la classe de fenêtre tout en autorisant la définition d’autres styles pour chaque instance dans l’appel de [CWindowImpl :: Create](../../atl/reference/cwindowimpl-class.md#create).

Si vous souhaitez fournir des styles de fenêtre par défaut qui seront utilisés uniquement quand aucun autre style n’est spécifié dans l’appel à `CWindowImpl::Create` , utilisez [CWinTraits](../../atl/reference/cwintraits-class.md) à la place.

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a> CWinTraitsOR::GetWndStyle

Appelez cette fonction pour récupérer une combinaison (à l’aide de l’opérateur OR logique) des styles standard de l' `CWinTraits` objet et les styles par défaut spécifiés par *t_dwStyle*.

```
static DWORD GetWndStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Styles utilisés pour la création d’une fenêtre.

### <a name="return-value"></a>Valeur renvoyée

Combinaison de styles passés dans *dwStyle* et des styles par défaut spécifiés par `t_dwStyle` , à l’aide de l’opérateur OR logique.

## <a name="cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a> CWinTraitsOR::GetWndExStyle

Appelez cette fonction pour récupérer une combinaison (à l’aide de l’opérateur OR logique) des styles étendus de l' `CWinTraits` objet et les styles par défaut spécifiés par `t_dwStyle` .

```
static DWORD GetWndExStyle(DWORD dwExStyle);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Styles étendus utilisés pour la création d’une fenêtre.

### <a name="return-value"></a>Valeur renvoyée

Combinaison de styles étendus passés dans *dwExStyle* et par défaut spécifiés par `t_dwExStyle` , à l’aide de l’opérateur OR logique

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctionnement des traits de fenêtre](../../atl/understanding-window-traits.md)
